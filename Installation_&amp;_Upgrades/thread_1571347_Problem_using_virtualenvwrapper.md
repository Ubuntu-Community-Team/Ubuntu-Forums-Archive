---
title: "Problem using virtualenvwrapper"
date: 2010-09-09
forum: Installation &amp; Upgrades
---

### Post by RobWilliams on 2010-09-09
I have been using Python and Ubuntu for several years, but I encountered an interesting twist recently.  I am configuring several robust Python development environments and I discovered that I want to use **virtualenvwrapper** to manage them.  However, installation turned out to be a bit interesting.  I found a little guidance on the web, but nothing that quite addressed my issue or solution.

I used [this installation note]("http://woot.foomor.com/post/445180489/installing-virtualenv-virtualenvwrapper-with-pip-on"), which starts with just the standard **python** (Python 2.6) installation.  It recommends installing **python-dev** (I didn't) and **build-essentials** (already had it).

I had previously installed **python-pip** and **python-virtualenv** packages, which I completely removed.  As advised, I wanted the latest versions and I wanted to be able to upgrade at my leisure.  I am willing to accept the risks associated with that choice, in this case.

Based on some other advice I found on the web that I mixed in, here is what I did.```
sudo apt-get update
sudo apt-get install python-setuptools
sudo easy_install pip
sudo pip install virtualenv
sudo pip install virtualenvwrapper
sudo pip install virtualenvwrapper.project
sudo pip install virtualenvwrapper.bitbucket
```
I then created a BASH script that I invoke from my *~/.bashrc*:```
# Configure Mercurial
export HGUSER=username

# Configure TMPDIR for virtualenvwrapper
export TMPDIR=$HOME/temp
[[ ! -e "$TMPDIR" ]] && mkdir "$TMPDIR"

# Configure WORKON_HOME for virtualenvwrapper
export WORKON_HOME=/var/user/$USERNAME/virtualenv
[[ ! -e "$WORKON_HOME" ]] && mkdir "$WORKON_HOME"

# Configure PIP to use virtualenvwrapper
export PIP_VIRTUALENV_BASE=$WORKON_HOME

# Configure virtualenvwrapper.bitbucket
export VIRTUALENVWRAPPER_BITBUCKET_USER=$HGUSER

# Activate virtualenvwrapper
source /usr/local/bin/virtualenvwrapper.sh
```
So, when I opened a new terminal, I got a nasty little message from Python:> ImportError: No module named virtualenvwrapper.hook_loader
I found a handful of references to this message on the web, but none of them addressed my situation.  They were focused on a different installation procedure, but I had already done what was recommended to fix this.  Something else was apparently wrong.

I hunted through my file system to find the files installed by my commands above, and I found them in */usr/local/lib/python2.6/dist-packages*.  Then I discovered the problem:  all the files were owned by *root* and lacked permissions to be accessed by "others".  Since my account is an "other", I could not see the installed packages.

I toyed with modifying the permissions, but I quickly realized that was a dead-end.  The problem would recur with each install or upgrade, and that seemed too much like chasing my tail.

But I also had noticed that the files are owned by group *staff*, which I had not seen on other files in my Ubuntu systems.  This suggested another solution that seems to work:  I merely added myself to the previously-empty group *staff*.  I used the Gnome GUI **System|Administration|Users and Groups**, although I know it can also be done from the shell.

I need to research this further, but I suspect that group *staff* was created for this purpose, and the installation occurs this way to facilitate exactly this kind of usage scenario.  I simply love discovering, like this, that my predecessors were thinking and they have my back!

I love all you wonderful Linux, Debian, Ubuntu, Python peoples!!!  ):P

---

### Post by RobWilliams on 2010-09-09
So now, as I have attempted to use my "solution", I have learned much more and found that my "solution" does not really work.  Much of that learning is summed up [here]("http://farmdev.com/thoughts/76/the-python-packaging-problem/").

Therefore, I will be preferring the packages installed by Ubuntu/Debian over the versions available otherwise, particularly for the components involved in managing Python components.  I will uninstall **pip**, **virtualenv**, **virtualenvwrapper**, **virtualenvwrapper.project**, **virtualenvwrapper.bitbucket**, and **zc.buildout**.

I learned that **setuptools**, **pip**, **virtualenv** (and its wrappers), and **zc.buildout** do not play well together.

I am going to restart with **python-setuptools**, **python-pip**, and **python-zc.buildout**.  I am dropping **virtualenv** for now since it seems to be overkill for my needs and incompatible with **zc.buildout**.  I am not really thrilled with **zc.buildout** (it's somewhat ugly), but it seems to be the best option available at the moment.

I also plan to shift my component selection to first use what I can get from the Ubuntu repositories, then to what I can get from PyPi via Pip when my needs demand it.

And, I have even MORE of an appreciation for what the package and system maintainers do for us.  Thank you all!!! \\:D/

---

### Post by flebber on 2011-07-28
You can now use pythonbrew and venv to manage virtualenvs and it installs pip to use by default. 

Another option is virualenv-burrito

---

