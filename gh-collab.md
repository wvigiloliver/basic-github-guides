# **Collaborating with GitHub**

## 1. **Contributor: Fork the original repo into your repo in GitHub.**

Contributors to a project can fork a project. Forking creates a copy of a GitHub repo in your ownGitHub account, (i.e., a fork). This is a must if you plan to contribute to a project by making your own edits. To fork a GitHub repo, simply click on the &#39;Fork&#39; button of the original GitHub repo of interest.

## 2. **Contributor: Create a clone of your fork locally on your computer.**

Once you&#39;ve created a fork you will then need to clone the repo locally on your computer. To do this, go to your fork on GitHub, click on the the &#39;Code&#39; button and copy the URL provided within the &quot;Clone with HTTPS&quot; option. The repo can be cloned by typing **git clone clone\_url** within your local directory of choice. Cloning a repo automatically configures the cloned repo as a &#39;remote&#39; labeled _origin_

Tip: A &#39;remote&#39; is a connection between a repo on your computer and remote repo. In this case, it would be connecting your cloned fork (on your computer) with your fork (on GitHub). You can now pull and push code from and to _origin_.

## 3. **Contributor: Connect your cloned copy to the original repo.**

By now you should have a fork of the original GitHub repo in your GitHub account and a clone of your fork on your computer. But what if the original GitHub repo is updated the day after you fork and clone it? Clearly, your fork and clone will be out-of-sync with the original GitHub repo. To stay in-sync, you&#39;ll need to establish a second &#39;remote&#39; connecting your cloned copy to the original GitHub. We&#39;ll call this second remote _upstream_. To set it up type **git remote add upstream clone\_url** within your local directory of choice (you&#39;ll first have to **cd** into the folder of your local cloned copy). The &quot;clone URL&quot; should be from the original GitHub repo and **not** your fork. It can be extracted by clicking on the &#39;Code&#39; button and copying the URL provided within the &quot;Clone with HTTPS&quot;. Having done this, you should have two remotes: _origin_ = your clone \&lt;\&gt; your fork; and _upstream_ = your clone \&lt;\&gt; original GitHub repo. To get a list of all configured remotes type **git remote –v****.**

Tip: _upstream_ is generally only for pulling, and not pulling and pushing like _origin_. But this will depend on your team&#39;s workflow and permissions.

## 4. **Contributor: Sync your cloned copy to the original repo.**

Before working on a new section of the code or feature always ensure you&#39;re working on the latest version of the project. To do so, you&#39;ll have to make use of the two remotes _upstream_ and _remote_. This can be accomplished by first checking out (or switching) into the _master_ branch – just in case you&#39;re on a different branch. Next, fetch the latest changes from the original GitHub repo using _upstream_ and then push these changes to your fork using _origin_. This can be carried out by typing the following within the local directory of your cloned copy:

**git checkout master # switch to the master branch**

**git pull upstream master &amp;&amp; git push origin master # update your cloned copy and then update your fork**

## 5. **Contributor: Create a new branch and start working within it.**

[Git-flow](https://guides.github.com/introduction/flow/) is recommended for most project. One of its core concepts is checking out to a new branch every time development for new feature or important part of the code is initiated. The starting point for most projects is to have a main branch called _master_. The final product will be released from _master_ so this branch should be reserved for final-as-possible code. Develop of features and code should take place in a different branch off _master_, which can be named after a feature or section of the code. The original GitHub repo will already contain a main branch called _master_ but it may or may not contain additional branches – it&#39;s best to coordinate with your team if the plan is for everyone to work within a given branch, or if each collaborator should create his/her own. Assuming you will be adding new code and a new branch is required then you&#39;ll have to branch off _master_ and create a branch for the code or feature you&#39;re developing. Creating a branch can be done via **git checkout -b update/code-x** where &#39;update/code-x&#39; can be any branch name. You can switch to branch using **git checkout branch** where &#39;branch&#39; is the branch you want to switch to. You can list all branches using **git branch.**

This and the previous step contain the key three steps to remember whenever you start working on a new feature or part of the code. 1. Switch to your _master_ branch, 2. Sync your cloned copy and fork with the original GitHub repo; and 3. Branch off your _master_ branch.

**git checkout master # switch to the master branch**

**git pull upstream master &amp;&amp; git push origin master # update your cloned copy and then update your fork**

**git checkout -b update/code-x # branch off your master branch by creating your own branch**

You can then start working on your code locally within the branch you created.

## 6. **Contributor: Push your local changes (incl. your branch) to your fork.**

After you&#39;ve added your code or edits locally, you&#39;ll want to **add** and **commit** your edits and finally **push** your branch with your edits to your fork in your GitHub account. This is possible thanks to the _origin_ remote established earlier.

**git add .**

**git commit -m &quot;commit message&quot;**

**git push -u origin update/code-x # push changes in your branch to your fork in GitHub**

Tip: GitHub allows you to view changes on different branches. So, after _pushing_ your branch with edits don&#39;t expect to view changes on the _master_ branch. Instead, changes will appear under your _update/code-x_ branch (or whatever you named your branch).

## 7. **Contributor: Create a pull request to the original GitHub repo from your fork.**

Once you&#39;ve pushed your updates to your forked repo in your GitHub you can then create a pull request into the original GitHub repo/project. To do this go to the fork on your GitHub, click on &#39;Pull Requests&#39; and press the &quot;New pull request&quot; button. Then click on &quot;compare across forks&quot;. Next, you&#39;ll have to select the &#39;base&#39; and &#39;head&#39; repos. The &#39;base&#39; repo is the original GitHub repo, wile &#39;head&#39; is your repo, containing your branch and changes. You can then submit your pull request via the GitHub interface.

## 8. **Code Reviewer: Merge pull request from contributor(s) into** _ **master** _ **of the original GitHub repo**

The code reviewer can accept the pull request a merge any changes into _master_ (or another branch) and after that delete the branch with the new code. This can be done within the GitHub interface or via the command-line by checking out to master, ensuring master is up-to-date and finally merging **update/code-x** into master. Altogether this come to:

**git checkout master # switch to master**

**git pull upstream master # download any changes**

**git merge update/code-x # merge the feature into the master branch**

**git push upstream master # push to original**

**git push origin master # push to forked version**

## 9. **Contributor: Working on the next feature or piece of code**

Having issued a pull-request for the code under branch &quot;update/code-x&quot; you&#39;ll have to see if the code was merged into the original GitHub repo. Let&#39;s say it was and you want to start working on your next feature or section of the code. The first step before proceeding is to sync your cloned copy and fork to be in line with to the original GitHub repo. If the code reviewer accepted your branch with the new code, then s/he may have also deleted it – the logic for this is why keep a branch with code when the code was accepted and merged into the _main_ branch. To sync things, follow the steps listed earlier in Step 4.

After that, you&#39;ll be ready to start working on a new piece of code. You again start off by creating a branch, adding your code, updating your fork and issuing a pull request – that is, restarting the whole process starting from Steps 5-7.

Most of the feature and code engineering should take in a different branch called _develop_.

_Git pull remotedepository_ __ _fetches all of the code from the remote_

_Check out a new branch: git checkout -b feature_

_Push this branch to the remote and then decide if we remote_

_Pull request: review_

**git push upstream update/code-x # send branch code-x for review**