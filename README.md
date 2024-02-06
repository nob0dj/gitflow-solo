# gitflow-solo

## steps 
1. `git flow init`
    ```bash
    $ git flow init
    Initialized empty Git repository in D:/Dropbox/Coding/Git/gitflow-solo/.git/
    No branches exist yet. Base branches must be created now.
    Branch name for production releases: [master] 
    Branch name for "next release" development: [develop] 

    How to name your supporting branch prefixes?
    Feature branches? [feature/] 
    Bugfix branches? [bugfix/] 
    Release branches? [release/] 
    Hotfix branches? [hotfix/] 
    Support branches? [support/] 
    Version tag prefix? [] 
    Hooks and filters directory? [D:/Dropbox/Coding/Git/gitflow-solo/.git/hooks]
    ```
2. `git flow feature start 브랜치명`
    `feature/브랜치명`이 생성되며 checkout된다.
    ```bash
    $ git flow feature start docs
    Switched to a new branch 'feature/docs'

    Summary of actions:
    - A new branch 'feature/docs' was created, based on 'develop'
    - You are now on branch 'feature/docs'

    Now, start committing on your feature. When done, use:

        git flow feature finish docs
    ```
3. 작업후 commit   
4. `git flow feature finish 브랜치명`
  develop에서 `feature/브랜치명`를 병합하며 checkout된다.(`feature/브랜치명` 제거)
    ```bash
    $ git flow feature finish docs
    Switched to branch 'develop'
    Updating 74f803a..2634c64
    Fast-forward
    README.md | 37 +++++++++++++++++++++++++++++++++++++
    1 file changed, 37 insertions(+)
    create mode 100644 README.md
    Deleted branch feature/docs (was 2634c64).

    Summary of actions:
    - The feature branch 'feature/docs' was merged into 'develop'
    - Feature branch 'feature/docs' has been locally deleted
    - You are now on branch 'develop'
    ```
5. `git flow release start 버전`
	```bash
	$ git flow release start 1.0.0
	Switched to a new branch 'release/1.0.0'

	Summary of actions:
	- A new branch 'release/1.0.0' was created, based on 'develop'
	- You are now on branch 'release/1.0.0'

	Follow-up actions:
	- Bump the version number now!
	- Start committing last-minute fixes in preparing your release
	- When done, run:

		 git flow release finish '1.0.0'	

	```
6. 원격저장소에 배포 `git flow release publish 버전`
  배포된 소스를 가지고 QA부서원과 함께 테스트를 진행할 수 있다.
    ```bash
    $ git flow release publish 1.0.0
    Enumerating objects: 5, done.
    Counting objects: 100% (5/5), done.
    Delta compression using up to 12 threads
    Compressing objects: 100% (2/2), done.
    Writing objects: 100% (3/3), 1.67 KiB | 1.67 MiB/s, done.
    Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
    remote: 
    remote: Create a pull request for 'release/1.0.0' on GitHub by visiting:
    remote:      https://github.com/nob0dj/gitflow-solo/pull/new/release/1.1.0
    remote:
    To https://github.com/nob0dj/gitflow-solo.git
    * [new branch]      release/1.0.0 -> release/1.0.0
    branch 'release/1.0.0' set up to track 'origin/release/1.0.0'.
    Already on 'release/1.0.0'
    Your branch is up to date with 'origin/release/1.0.0'.

    Summary of actions:
    - The remote branch 'release/1.0.0' was created or updated
    - The local branch 'release/1.0.0' was configured to track the remote branch
    - You are now on branch 'release/1.0.0'
    ```
7. 로컬저장소 운영master에 배포 `git flow release finish 버젼`
  태그 메세지를 작성해야 한다.
	```bash
	$ git flow release finish 1.0.0
	Switched to branch 'master'
	Your branch is up to date with 'origin/master'.
	Merge made by the 'ort' strategy.
	 README.md | 37 +++++++++++++++++++++++++++++++++++++
	 1 file changed, 37 insertions(+)
	 create mode 100644 README.md
	Already on 'master'
	Your branch is ahead of 'origin/master' by 2 commits.
	  (use "git push" to publish your local commits)
	Switched to branch 'develop'
	Your branch is up to date with 'origin/develop'.
	Merge made by the 'ort' strategy.
	To https://github.com/nob0dj/gitflow-solo.git
	 - [deleted]         release/1.0.0
	Deleted branch release/1.0.0 (was 2634c64).

	Summary of actions:
	- Release branch 'release/1.0.0' has been merged into 'master'
	- The release was tagged '1.0.0'
	- Release tag '1.0.0' has been back-merged into 'develop'
	- Release branch 'release/1.0.0' has been locally deleted; it has been remotely deleted from 'origin'
	- You are now on branch 'develop'
	```
8. 원격저장소에 push 
	- 로컬 master에 생성된 tag를 원격 master로 push한다. 
	- 추가적인 release 작성이 필요하다.
	- 원격저장소 default 브랜치를 develop으로 수정한다.

최종 commit tree는 다음과 같다.
![소스트리 history뷰](https://d.pr/i/KxyRsx+)
