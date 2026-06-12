---
title: "dpkg/synaptic - recovering installation canditates (versions)?"
date: 2011-03-30
forum: Installation &amp; Upgrades
---

### Post by sdaau on 2011-03-30
Hi all, 

Well, I was just doing an update, and there was an update for git that was held back. 

I decided to force this update using 'sudo apt-get dist-upgrade', and installation of git then failed. 

At this point in Synaptic - I could see versions listed as 'lucid', 'lucid-security', and then this ppa version. 

Then I barely managed to remove git - but now, if I try to install it again, *only* the ppa version is listed in Synaptic - no more 'lucid' and 'lucid-security' versions!!! 

Does anyone have an idea how I could recover the 'lucid', 'lucid-security' versions? I will try to salvage as much of the terminal with the problems as I can below...

Thanks in advance for any help, 
Cheers!

```

/var/lib/dpkg/tmp.ci/preinst: 12: dpkg-maintscript-helper: not found
dpkg: error processing /var/cache/apt/archives/git_1%3a1.7.4.1-3~ppa1~lucid2_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: 14: dpkg-maintscript-helper: not found
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/git_1%3a1.7.4.1-3~ppa1~lucid2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

$ ls /var/lib/dpkg/tmp.ci/postrm
ls: cannot access /var/lib/dpkg/tmp.ci/postrm: No such file or directory

$ ls /var/lib/dpkg/tmp.ci/
ls: cannot access /var/lib/dpkg/tmp.ci/: No such file or directory

$ sudo mkdir /var/lib/dpkg/tmp.ci/
$ sudo touch /var/lib/dpkg/tmp.ci/postrm
$ sudo apt-get install git
...
Suggested packages:
  git-doc git-el git-arch git-cvs git-svn git-email git-daemon-run git-gui gitk gitweb
The following packages will be upgraded:
  git
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/4.553kB of archives.
After this operation, 9.859kB of additional disk space will be used.
(Reading database ... 
dpkg: warning: files list file for package `git' missing, assuming package has no files currently installed.
(Reading database ... 230469 files and directories currently installed.)
Preparing to replace git 1:1.7.4.1-3~ppa1~lucid2 (using .../git_1%3a1.7.4.1-3~ppa1~lucid2_i386.deb) ...
/var/lib/dpkg/tmp.ci/preinst: 12: dpkg-maintscript-helper: not found
dpkg: error processing /var/cache/apt/archives/git_1%3a1.7.4.1-3~ppa1~lucid2_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: 14: dpkg-maintscript-helper: not found
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/git_1%3a1.7.4.1-3~ppa1~lucid2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

$ sudo dpkg --remove --force-remove-reinstreq git
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 
dpkg: warning: files list file for package `git' missing, assuming package has no files currently installed.
(Reading database ... 230467 files and directories currently installed.)
Removing git ...

$ sudo apt-get update 
...

$ synaptic # no lucid versions
Discarding: 2 over 4

$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libdigest-sha1-perl liberror-perl
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 209kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 230467 files and directories currently installed.)
Removing libdigest-sha1-perl ...
Removing liberror-perl ...
Processing triggers for man-db ...
$ sudo apt-get purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
$ sudo apt-get clean

$ sudo apt-get update

$ synaptic # still no lucid versions

```

---

### Post by tommcd on 2011-03-31
This is unfortunately the chance you take when you decide to use those unsupported and all to often problematic PPA repositories. If you stay away from those PPA repos you will never have these problems. I never use third party repos; and I never have problems with Ubuntu. It is my belief that the majority of problems that people have with Ubuntu stem from using these unsupported third party repositories.

Try removing all PPA repos, git repos, or any and all third party repos you may have. Then run:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
And see if you can update your system.

---

