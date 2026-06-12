---
title: "Errors when trying to fix FGLRX"
date: 2010-06-27
forum: Installation &amp; Upgrades
---

### Post by bronxbomberz41 on 2010-06-27
A few weeks ago either after the upgrade to 10.04 or on a subsequent system update I have been having problems.  I have not been able to use Compiz Desktop Effects and playing videos in full screen is awful slow and choppy.  I have tried numerous things to try and fix this and now at this point whenever i try anything through the terminal I get the following error.

```
brian@brian-laptop:~$ sudo apt-get -f purge xorg-driver-fglrx fglrx fglrx-amdcccle fglrx-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xorg-driver-fglrx is not installed, so not removed
Package fglrx-amdcccle is not installed, so not removed
Package fglrx-kernel-source is not installed, so not removed
The following packages will be REMOVED:
  fglrx
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 101MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 224121 files and directories currently installed.)
Removing fglrx ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--remove):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for ureadahead ...
Errors were encountered while processing:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It is also showing as a package marked for removal in Synaptic but it his an error every time I try to remove it.

---

### Post by dino99 on 2010-06-27
add this ppa to synaptic repo and update

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by bronxbomberz41 on 2010-06-27
Thanks but it doesn't look like its working.  I tried it and its timing out.  Here is what I was inputting in case i did anything wrong, along with the output in the terminal.

```
brian@brian-laptop:~$ sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 643DC6BD56580CEB1AB4A9F63B22AB97AF1CDFA9
gpg: requesting key AF1CDFA9 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

```

---

### Post by bronxbomberz41 on 2010-06-27
I also tried to manually add the ppa via the software sources and I got the following error (screenshot because for some reason it wouldn't let me copy the text)

---

### Post by bronxbomberz41 on 2010-06-28
Bump

---

### Post by bronxbomberz41 on 2010-06-30
My update manager and synaptic are not working properly and I can't perform updates through the terminal anymore.  I'm kinda stuck here if anyone can help.  Don't want to have to do a fresh re-install (which I've had to do pretty much every time I upgrade to the latest distro through the upgrade channels)

---

