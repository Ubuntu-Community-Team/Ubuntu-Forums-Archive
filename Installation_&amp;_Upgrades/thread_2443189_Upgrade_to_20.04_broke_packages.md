---
title: "Upgrade to 20.04 broke packages"
date: 2020-05-12
forum: Installation &amp; Upgrades
---

### Post by MrSums on 2020-05-12
Upgraded to 20.04, but ran into issues with some packages. Carried on with install and the system is up an running, but now trying to fix. The packages that "seem" to be problematic are:

[LIST=1]
[*]Crossover-trial. This reports is depends on python-gtk2 and python-glade2 but these are not installable
[*]Pure-ftpd-common
[/LIST]

However, I can't seem to deinstall either of these, either using package manager or via CLI as they then return mysql errors

Trying via package manager returns the error:

```
Removing crossover-trial (12.5.1-0ubuntu3) ...
/usr/bin/env: &#8216;python&#8217;: No such file or directory
dpkg: error processing package crossover-trial (--remove):
 installed crossover-trial package pre-removal script subprocess returned error exit status 127
dpkg: too many errors, stopping
Errors were encountered while processing:
 crossover-trial
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mysql-server-8.0 (8.0.20-0ubuntu0.20.04.1) ...
mysqld will log errors to /var/log/mysql/error.log
mysqld is running as pid 48374

```

Any help appreciated

Robert

---

### Post by rsteinmetz70112 on 2020-05-12
It looks like something wasn't installed properly.
I assume by upgrade you mean:
```
sudo do-release-upgrade
```
or the GUI equivalent
did you:
```
sudo upgrade
sudo update
```
before starting the upgrade?

Doesn't matter now but it's always a good idea to do that. 
I've never understood why do-relase-upgrade doesn't do that first.

Lets try some basic stuff:
```
sudo apt update
sudo apt upgrade
```

If it cleans everything up great.
If not post the results and try 
```
sudo apt install -f
sudo dpkg --configure -a
```
If that cleans everything up great, if not post the results.

---

### Post by MrSums on 2020-05-12
Thanks for response.

1. Sudo apt update:
```
robert@lounge-lizard:~/Desktop$ sudo apt update
...
21 packages can be upgraded. Run 'apt list --upgradable' to see them.
```

2. Sudo apt upgrade:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies.
 crossover-trial : Depends: python-gtk2 but it is not installable
                   Depends: python-glade2 but it is not installable
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

3. Sudo apt install -f:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
[COLOR=#0000ff]{long list of packages}[/COLOR]
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED
  crossover-trial
0 to upgrade, 0 to newly install, 1 to remove and 21 not to upgrade.
2 not fully installed or removed.
After this operation, 3,331 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 620915 files and directories currently installed.)
Removing crossover-trial (12.5.1-0ubuntu3) ...
/usr/bin/env: ‘python’: No such file or directory
dpkg: error processing package crossover-trial (--remove):
 installed crossover-trial package pre-removal script subprocess returned error 
exit status 127
dpkg: too many errors, stopping
Errors were encountered while processing:
 crossover-trial
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

4. Sudo dpkg --configure -a:
```
robert@lounge-lizard:~/Desktop$ sudo dpkg --configure -a
Setting up mysql-server-8.0 (8.0.20-0ubuntu0.20.04.1) ...
mysqld will log errors to /var/log/mysql/error.log
mysqld is running as pid 58098
[COLOR=#0000ff]{long wait}[/COLOR]
Job for mysql.service failed because a timeout was exceeded.
See "systemctl status mysql.service" and "journalctl -xe" for details.
invoke-rc.d: initscript mysql, action "start" failed.
&#9679; mysql.service - MySQL Community Server
     Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: enabled)
     Active: activating (auto-restart) (Result: timeout) since Tue 2020-05-12 22:39:40 BST; 7ms ago
    Process: 58211 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=exited, status=0/SUCCESS)
    Process: 58225 ExecStart=/usr/sbin/mysqld (code=exited, status=0/SUCCESS)
   Main PID: 58225 (code=exited, status=0/SUCCESS)
dpkg: error processing package mysql-server-8.0 (--configure):
 installed mysql-server-8.0 package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-8.0; however:
  Package mysql-server-8.0 is not configured yet.

dpkg: error processing package mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-8.0
 mysql-server
```

Cheers

Robert

---

### Post by CatKiller on 2020-05-12
> **MrSums said:**
> /usr/bin/env: &#8216;python&#8217;: No such file or directory

Python 2 is deprecated, and has been removed from Ubuntu. For those that still need it, the python2 package is in the Universe repository. Installing that so that old stuff can still call 'python' may help you out here. Of course, since your package manager is broken by an old package that needs python so that it can remove itself, you might not be able to.

---

### Post by Impavidus on 2020-05-13
Installing Python 2 would work best, but may not be easy with package management already broken. If this script is actually compatible with Python 3 too, you could fix it by providing a symlink named /usr/bin/python pointing to /usr/bin/python3. But that's risky. If it doesn't work, things could get much worse.

It would have been better if crossover-trial were removed before the release upgrade.

---

### Post by slickymaster on 2020-05-13
@MrSums:

Please don't use quote tags when posting terminal output because it can lose its formatting and parts of it sometimes turn into smileys making it difficult to read and understand.

If you are using New Reply you can simply select the text you wish to have within a code box and use the # button on the reply editing toolbar.

---

### Post by ActionParsnip on 2020-05-13
[https://answers.launchpad.net/ubuntu/+question/690584](https://answers.launchpad.net/ubuntu/+question/690584)

Same answer here. Focal isn't supported yet

---

### Post by rsteinmetz70112 on 2020-05-13
Since Crossover is proprietary and since the OP tried to upgrade to Ubuntu there may be other issues as well.
Depending on what you want to do:

[LIST=1]
[*]You could try waiting for Crorssover to get 20 out, but it may not fix your problem.
[*]You could enable the Universe repository and see if
```
sudo apt update
sudo apt upgrade
```
will fix it but it might break more stuff.
[*]You could carry on and try to get Ubuntu 20.04 up and running by trying to delete the broken stuff (no guarantees)
[*]You could install 20.04 fresh and move away from crossover.

[/LIST]

If it were me I'd go with 2 above since it's already broke and I might learn something. You can always reinstall 20.04 in the end.

---

### Post by MrSums on 2020-05-14
Thanks for all the help guys. I have *mostly* fixed the problem.

I still had python2 installed, so I set up to use it, as described in this article - [https://linuxconfig.org/ubuntu-20-04-python-version-switch-manager](https://linuxconfig.org/ubuntu-20-04-python-version-switch-manager). Then I ran sudo apt auto-remove which got rid of most errors and then sudo apt upgrade which install most updates.

I am now left with "errors encountered while processing"
 mysql-server-8.0 
 mysql-server

Do I try and remove these and then reinstall?

Cheers

Robert

---

### Post by rsteinmetz70112 on 2020-05-14
Do you have any specific use for MySQL? 
What kind of errors do you get processing mysql error messages?
you could try 
```
sudo dpkg --configure -a [CODE]
that might fix it or shed some light on the nature of the problem
or:
[CODE]sudo apt install --reinstall mysql-server
```
however if the the issue is not with the package it might not work but might still reveal the something.

---

