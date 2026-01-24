# CLAUDE.md - AI Assistant Guide

This document provides guidance for AI assistants working with this repository.

## Repository Overview

This is a **GitHub Skills** educational repository that teaches new developers the fundamentals of using GitHub. It is an interactive, self-paced tutorial that guides learners through:

1. Creating a branch
2. Committing a file
3. Opening a pull request
4. Merging a pull request

The repository uses GitHub Actions workflows to automatically track learner progress and provide feedback through GitHub Issues.

## Codebase Structure

```
skills-introduction-to-github/
├── README.md                    # Main exercise landing page with instructions
├── LICENSE                      # MIT License (Copyright GitHub, Inc.)
├── .gitignore                   # Standard ignores for compiled files, packages, logs, OS files
├── .github/
│   ├── steps/                   # Step-by-step instruction files
│   │   ├── 1-create-a-branch.md
│   │   ├── 2-commit-a-file.md
│   │   ├── 3-open-a-pull-request.md
│   │   ├── 4-merge-your-pull-request.md
│   │   └── x-review.md          # Final review/congratulations
│   └── workflows/               # GitHub Actions automation
│       ├── 0-start-exercise.yml
│       ├── 1-create-a-branch.yml
│       ├── 2-commit-a-file.yml
│       ├── 3-open-a-pull-request.yml
│       └── 4-merge-your-pull-request.yml
```

## Key Components

### Step Files (`.github/steps/`)

Markdown files containing educational content for each step of the exercise:

- **1-create-a-branch.md**: Explains branches, repositories, and profile READMEs
- **2-commit-a-file.md**: Teaches about commits and creating files
- **3-open-a-pull-request.md**: Covers pull request creation and collaboration
- **4-merge-your-pull-request.md**: Explains merging changes
- **x-review.md**: Summary and next steps for learners

### Workflow Files (`.github/workflows/`)

GitHub Actions that automate the exercise progression:

| Workflow | Trigger | Purpose |
|----------|---------|---------|
| `0-start-exercise.yml` | Push to `main` | Initializes exercise, creates tracking issue |
| `1-create-a-branch.yml` | Push to `my-first-branch` | Validates branch creation |
| `2-commit-a-file.yml` | Push to `my-first-branch` | Checks for `PROFILE.md` file |
| `3-open-a-pull-request.yml` | PR opened/edited to `main` | Validates PR title and description |
| `4-merge-your-pull-request.yml` | PR closed (merged) | Completes exercise, provides review |

### Workflow Behavior

- Workflows are enabled/disabled sequentially as learners progress
- Each workflow posts progress updates to a GitHub Issue
- Uses `skills/exercise-toolkit` for shared templates and utilities
- Workflows validate specific criteria before allowing progression

## Development Guidelines

### For Modifying Step Content

- Step files use GitHub-flavored Markdown with emojis
- Include helpful screenshots and visual guides
- Provide troubleshooting tips in collapsible `<details>` sections
- Link to official GitHub documentation where appropriate

### For Modifying Workflows

- Workflows use reusable workflows from `skills/exercise-toolkit@v0.1.0`
- Common pattern: `find_exercise` → `check_step_work` → `post_next_step_content`
- Use `gh` CLI for GitHub API interactions
- Workflows self-disable after successful completion

### Important Conventions

1. **Branch naming**: The exercise expects `my-first-branch` exactly
2. **File naming**: Step 2 expects `PROFILE.md` in the repository root
3. **PR requirements**: Step 3 requires title "Add my first file" and a non-empty description
4. **Issue tracking**: An issue titled "Exercise: Introduction to GitHub" tracks all progress

## Dependencies

- **skills/exercise-toolkit**: Provides reusable workflows and markdown templates
- **skills/action-text-variables**: Used for template variable substitution
- **actions/checkout@v4**: Standard checkout action

## License

MIT License - Copyright (c) GitHub, Inc.

## Notes for AI Assistants

- This is an educational template repository, not a production application
- The primary audience is new GitHub users learning version control basics
- When helping with this repository, focus on clear explanations suitable for beginners
- The workflows are designed to be self-contained and not require manual intervention
- Do not modify the expected branch names, file names, or PR requirements without updating corresponding workflows
