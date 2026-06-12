---
title: "Can't install/upgrade software"
date: 2007-07-21
forum: Installation &amp; Upgrades
---

### Post by allesklar108 on 2007-07-21
Here is the background.

I have tried out Linux a couple times over the years but never made it. I'm a Windows power user running lots of apps. However I think now is the time iI'll be able to switch permanently.

I have installed Kubuntu 7.04 on my 4-year old Dell Inspiron 5150 laptop in a dual-boot setup alongside Win XP. The news OS is so fast and I find easy to use, I already know how to do most basic operations, install programs etc. Anyway I'm still stuck with one major problem.

First let me assure you I spent several hours on these forums and googling before posting this.

When I tried to install any programs, let's say Firefox as an example, I get the error message below.
```

username@dell-laptop:~$ sudo apt-get install  firefox
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libnspr4 libnss3
Suggested packages:
  firefox-gnome-support latex-xft-fonts firefox-libthai
The following NEW packages will be installed:
  firefox libnspr4 libnss3
0 upgraded, 3 newly installed, 0 to remove and 83 not upgraded.
Need to get 10.2MB of archives.
After unpacking 31.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://security.ubuntu.com feisty-security/main libnspr4 2:1.firefox2.0.0.5+1-0ubuntu1 [162kB]
Get:2 http://security.ubuntu.com feisty-security/main libnss3 2:1.firefox2.0.0.5+1-0ubuntu1 [802kB]
Get:3 http://security.ubuntu.com feisty-security/main firefox 2.0.0.5+1-0ubuntu1 [9262kB]
Fetched 10.2MB in 32s (311kB/s)
dpkg-deb: subprocess tar killed by signal (Segmentation fault), core dumped
dpkg: error processing /var/cache/apt/archives/libnspr4_2%3a1.firefox2.0.0.5+1-0ubuntu1_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: subprocess tar killed by signal (Segmentation fault), core dumped
dpkg: error processing /var/cache/apt/archives/libnss3_2%3a1.firefox2.0.0.5+1-0ubuntu1_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: subprocess tar killed by signal (Segmentation fault), core dumped
dpkg: error processing /var/cache/apt/archives/firefox_2.0.0.5+1-0ubuntu1_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libnspr4_2%3a1.firefox2.0.0.5+1-0ubuntu1_i386.deb
 /var/cache/apt/archives/libnss3_2%3a1.firefox2.0.0.5+1-0ubuntu1_i386.deb
 /var/cache/apt/archives/firefox_2.0.0.5+1-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I'm not sure if that's helpful but trying out this command:
```
tar -v
```
I got this message:
```
Segmentation fault (core dumped)
```
That gave me the idea of uninstalling and reinstalling tar but the OS gave a stern warning that this could be very destructive so I backed out and decided to ask you guys for help.

I'm a complete Linux newbie but I think if you help me get off the ground, I'll become a regular user and won't look back.

So what is this problem about? How can I fix it?

---

### Post by overdrank on 2007-07-22
Hi I do not use kde but I did a search and this is what I found to be most important 
[http://ubuntuforums.org/showthread.php?t=110353](http://ubuntuforums.org/showthread.php?t=110353)
Hope this helps, good luck!

---

### Post by chandra on 2007-08-19
I have tried to install Kubuntu Feisty from the Desktop CD for a friend on his HP Pavilion desktop.

The installation is completed successfully, but on reboot and upgrading of packages, we are stymied by the same error as reported here:

```
dpkg-deb: subprocess tar killed by signal (Segmentation fault), core dumped
```

Does anyone know of a workaround?

Thanks.

---

### Post by chandra on 2007-08-21
The solution that finally worked was to install Ubuntu Feisty Fawn rather than Kubuntu Fiesty Fawn.

Why Ubuntu could be updated successfully but not Kubuntu perplexes me, but that is what happened.

Any explanations most welcome.

TIA.

---

