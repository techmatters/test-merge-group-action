# Overview

This is a test repo for github action [merge groups](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/managing-a-merge-queue#triggering-merge-group-checks-with-github-actions).

## Key Learnings

- The check for the merge group job must be a required check under the repository's
Settings > Branches > Branch protection rules
- Merge groups don't work with branch protection that targets a wildcard. You must specify a full branch name. This means that we'd forced into a long running release branch if we want to leverage merge groups for release branch PRs.
- Merge group triggers WILL run on PR actions. We have to use a hacky if statement to work around this limitation. That causes a lot of noise in the action history.
- Merge strategy has to be set to squash or merge commit as part of the merge group config. Can't be specified by developer.