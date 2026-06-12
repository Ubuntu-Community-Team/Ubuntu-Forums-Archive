---
title: "git-man: libcgi-pm-perl Has unmet dependencies"
date: 2019-06-04
forum: Installation &amp; Upgrades
---

### Post by maquiner on 2019-06-04
Hello everyone, I cannot figure how to solve the following problem. 


```
jaime@jaime-VirtualBox:~$ sudo apt install git 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.18.0-15 linux-headers-4.18.0-15-generic
  linux-image-4.18.0-15-generic linux-modules-4.18.0-15-generic
  linux-modules-extra-4.18.0-15-generic
Use 'sudo apt autoremove' to remove them.
Suggested packages:
  git-daemon-run | git-daemon-sysvinit git-doc git-el git-email git-gui gitk
  gitweb git-cvs git-mediawiki git-svn
The following packages will be upgraded:
  git
1 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
1 not fully installed or removed.
Need to get 0 B/3,907 kB of archives.
After this operation, 32.2 MB of additional disk space will be used.
(Reading database ... 204865 files and directories currently installed.)
Preparing to unpack .../git_1%3a2.17.1-1ubuntu0.4_amd64.deb ...
stat: cannot stat '/usr/lib/git-core/git-add': No such file or directory
dpkg: error processing archive /var/cache/apt/archives/git_1%3a2.17.1-1ubuntu0.4_amd64.deb (--unpack):
 new git package pre-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/git_1%3a2.17.1-1ubuntu0.4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
jaime@jaime-VirtualBox:~$ sudo apt auto remove 
E: Invalid operation auto
jaime@jaime-VirtualBox:~$ sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies.
 git-man : Breaks: git (< 1:1.7.4~rc1)
 libcgi-pm-perl : Breaks: git (< 1:2.1.3)
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
jaime@jaime-VirtualBox:~$ "
```

I have treid force installing and it doesn't work. 
Any ideas?? 

Thanks a lot guys!!

---

### Post by TheFu on 2019-06-04
sudo apt remove libcgi-pm-perl

---

### Post by maquiner on 2019-06-04
didn't solve it :( 
```
jaime@jaime-VirtualBox:~$ sudo apt remove libcgi-pm-perl 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies.
 git-man : Breaks: git (< 1:1.7.4~rc1)
 libcgi-fast-perl : Depends: libcgi-pm-perl (>= 4)
 libparse-debianchangelog-perl : Depends: libcgi-pm-perl or
                                          perl (< 5.19) but 5.26.1-6ubuntu0.3 is to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

---

### Post by TheFu on 2019-06-04
Ok - so it isn't a trivial dependency issue.
**sudo apt --fix-broken install** ??

Also, please when you post, post using *code tags* around the shell commands and output.
If that command doesn't fix it, then we have to remove any manually installed .deb files, remove any PPAs, and get back to a known, clean, Canonical-only, package management state.

Sometimes it is easier to restore a backup from prior to the package management issues and work forward again.  I have systems that I've been pulling forward since 2008 that don't and never have had dependencies problems. The trick is to avoid manually installing any .deb files and limiting any PPAs to only the most trusted teams.

Are you a "perl guy?"  If so, we can head in a completely different direction for the perl stuff you need, but stay with the core Canonical perl packages only for the needs of the OS.

---

