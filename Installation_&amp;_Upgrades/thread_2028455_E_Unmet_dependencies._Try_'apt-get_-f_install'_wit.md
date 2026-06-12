---
title: "E: Unmet dependencies. Try 'apt-get -f install' with no packages (11.10 VPS)"
date: 2012-07-18
forum: Installation &amp; Upgrades
---

### Post by royevans on 2012-07-18
Hello again, as in the title, I'm running a VPS with 11.10 and my goal is to install webmin, however, during the installation process I get this:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libauthen-pam-perl : Depends: perlapi-5.14.2
 libc6 : Depends: libc-bin (= 2.13-20ubuntu5) but 2.13-27 is to be installed
 libc6-dbg : Depends: libc6 (= 2.13-27) but 2.13-20ubuntu5 is to be installed
 libc6-dev : Depends: libc6 (= 2.13-27) but 2.13-20ubuntu5 is to be installed
 libio-pty-perl : Depends: perlapi-5.14.2
 libnet-ssleay-perl : Depends: perlapi-5.14.2
 perl : Depends: perl-base (= 5.14.2-9) but 5.12.4-4 is to be installed
        Depends: perl-modules (>= 5.14.2-9) but 5.12.4-4 is to be installed
 python : Depends: python-minimal (= 2.7.2-10) but 2.7.2-7ubuntu2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

To be certain of what I thought the problem was I ran ```
sudo dpkg --configure -a
``` and got this return:

```
dpkg: dependency problems prevent configuration of libc6-dbg:
 libc6-dbg depends on libc6 (= 2.13-27); however:
  Version of libc6 on system is 2.13-20ubuntu5.
dpkg: error processing libc6-dbg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.13-27); however:
  Version of libc6 on system is 2.13-20ubuntu5.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6-dbg
 libc6-dev

```

So I now know that libc6-dbg and libc6-dev were the problems, however, when I run the "purge" command I get this:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.13-20ubuntu5) but 2.13-27 is to be installed
 libc6-dev : Depends: libc6 (= 2.13-27) but 2.13-20ubuntu5 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

And even when I *do* run  "-f install" I get this:

```

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
kittens@www:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc6 libc6-i686
Suggested packages:
  glibc-doc
The following NEW packages will be installed:
  libc6-i686
The following packages will be upgraded:
  libc6
1 upgraded, 1 newly installed, 0 to remove and 1049 not upgraded.
2 not fully installed or removed.
Need to get 0 B/5156 kB of archives.
After this operation, 1410 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libc6 libc6-i686
Install these packages without verification [y/N]? y
Preconfiguring packages ...
Can't exec "/tmp/libc6.config.39631": Permission denied at /usr/share/perl/5.12/IPC/Open3.pm line 168.
open2: exec of /tmp/libc6.config.39631 configure 2.13-20ubuntu5 failed at /usr/share/perl5/Debconf/ConfModule.pm line 59
libc6 failed to preconfigure, with exit status 255
(Reading database ... 134852 files and directories currently installed.)
Preparing to replace libc6 2.13-20ubuntu5 (using .../libc6_2.13-27_i386.deb) ...
WARNING: this version of the GNU libc requires kernel version
2.6.26 or later. Please upgrade your kernel before installing
glibc.

The installation of a 2.6 kernel _could_ ask you to install a new libc
first, this is NOT a bug, and should *NOT* be reported. In that case,
please add lenny sources to your /etc/apt/sources.list and run:
  apt-get install -t lenny linux-image-2.6
Then reboot into this new kernel, and proceed with your upgrade
dpkg: error processing /var/cache/apt/archives/libc6_2.13-27_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.13-27_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Sadly, I'm not sure what it is saying exactly, any help would be appreciated.

---

### Post by drmrgd on 2012-07-18
Have a look at this link.  I'm not familiar with VPS systems or that error.  But, it does look like this has been seen before on these systems, and the last post in the thread has a workaround that you might try:

[http://askubuntu.com/questions/126141/why-does-11-04-to-12-10-upgrade-on-openvz-vps-fail-with-libc-kernel-2-6-24-e](http://askubuntu.com/questions/126141/why-does-11-04-to-12-10-upgrade-on-openvz-vps-fail-with-libc-kernel-2-6-24-e)

Could be that someone has a more simple, more direct approach, though.

---

### Post by royevans on 2012-07-19
> **drmrgd said:**
> Have a look at this link.  I'm not familiar with VPS systems or that error.  But, it does look like this has been seen before on these systems, and the last post in the thread has a workaround that you might try:

[http://askubuntu.com/questions/126141/why-does-11-04-to-12-10-upgrade-on-openvz-vps-fail-with-libc-kernel-2-6-24-e](http://askubuntu.com/questions/126141/why-does-11-04-to-12-10-upgrade-on-openvz-vps-fail-with-libc-kernel-2-6-24-e)

Could be that someone has a more simple, more direct approach, though.

Sorry for the late response, procrastination and all that, anywho, the post at the bottom is detailing how to upgrade to 12.04, that isn't my intention, I'm trying to install webmin, however I did try most of the other things that were posted there, but none of them worked.

---

