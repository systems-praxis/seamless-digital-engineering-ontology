# Contributing to the Seamless Digital Engineering Ontology

We are seeking contributions to improve the ontology. This document includes general instructions on how to contribute using the GitHub model.

## Getting started with GitHub

Direct feedback may be initiated by [creating a GitHub Issue](https://docs.github.com/en/issues/tracking-your-work-with-issues/using-issues/creating-an-issue) with a topical title, or [commenting on an existing issue](https://docs.github.com/en/issues/tracking-your-work-with-issues/configuring-issues/quickstart#communicating).

Contributions to the repository should follow the GitHub model of forking the repository; creating a feature/issue branch; committing small, briefly described changes; pushing changes to the personal fork, without 'force push'; and creating a pull request to the main repository using the dialog provided on the personal fork frontpage. Details of this process are provided on GitHub's documentation site: [here](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests) and [here](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/getting-started/best-practices-for-pull-requests).

> _Note: **Do not commit changes that result in a broken state. In other words, every commit in the merged history must be a valid version of the ontology.** Commits may be squashed on personal branches using `git rebase -i` ([see GitHub documentation](https://docs.github.com/en/get-started/using-git/about-git-rebase))._

Contributors shall acknowledge that their merged changes fall under the appropriate license described below. Contributors should add themselves to the ontology annotations using the `dc:contributor` annotation property, as a single commit included in the pull request.

## Reviewing a Pull Request (PR)

First, ensure that you have successfully synced the Git submodules containing the ontology dependencies, and stashed any changes you may be working on:

```
git submodule update --init --recommend-shallow --recursive --force
git stash
```

With those preparations completed, your local repository is ready to review the changes in a pull request. On the pull request's main page, scroll down to the merge information green box. On the right of the green "Merge pull request" button are the command-line instructions for pulling the proposed changes locally for review.

![Screenshot from GitHub pull request](/figures/GitHub_Pull_Request.png)

The instructions provided are specific to the pull request you are reviewing. For example, PR #14 looks like this:

![Screenshot of Git CLI instructions for PR #14](/figures/GitHub_Pull_Request_CLI_instructions.png)

By clicking the 'copy to clipboard' button on the right, you can run those commands to safely checkout the PR changes in a local branch. For example:

```
git checkout -b systems-praxis-catalog-XML-use-relative-paths main
git pull git@github.com:systems-praxis/seamless-digital-engineering-ontology.git catalog-XML-use-relative-paths
```

> _Note: Notice the above command uses the Git SSH protocol rather than HTTPS. Look for `git@github.com:` at the beginning of the remote path to confirm._

If you have the ontology open in Protégé, it will now prompt you to reload the ontology with the new changes. Click "yes" to reload the ontology, and then go to the top menu Reasoner > Start reasoner to do a logical consistency check. You may also check for any `owl:Nothing` inference errors by selecting "Inferred" from the right-side dropdown menu in the Classes tab.

Merging the pull request may be done by clicking the "Merge pull request" green button, or it can be done locally if you have a developer role in the repository. For example:

```
git checkout main
git merge --no-ff systems-praxis-catalog-XML-use-relative-paths
git push origin main
```

## Updating

Periodically update your local copy of the repository using `git pull`. First, ensure that your "working tree is clean" by stashing (`git stash`) or committing changes in a separate branch, then run the following commands:

```
git checkout main
git pull --rebase origin main
```

> _Note: The use of `--rebase` here is to avoid creating empty "merge" commits in the history._

If you have forked the repository to work on pull requests, then you should use the GitHub sync feature by going to your fork's GitHub page, and clicking "Sync fork". Detailed instructions are provided in [GitHub's documentation](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/syncing-a-fork).

## 'Compare ontologies'

_TBD_

## 'Ontology differences'

_TBD_
