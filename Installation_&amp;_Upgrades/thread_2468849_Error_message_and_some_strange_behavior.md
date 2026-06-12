---
title: "Error message and some strange behavior"
date: 2021-11-11
forum: Installation &amp; Upgrades
---

### Post by reut2 on 2021-11-11
I have an alert message[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289454&stc=1[/IMG]
When I run apt --fix-broken install as suggested this si what I get:

> reuven@reuven-OptiPlex-9020:~$ sudo apt --fix-broken install

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libguvcview-2.0-2 libllvm11 libllvm11:i386 linux-headers-5.4.0-88 linux-headers-5.4.0-88-generic linux-image-5.4.0-88-generic
  linux-modules-5.4.0-88-generic linux-modules-extra-5.4.0-88-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libguvcview-2.0-0
The following NEW packages will be installed:
  libguvcview-2.0-0
0 upgraded, 1 newly installed, 0 to remove and 21 not upgraded.
1 not fully installed or removed.
Need to get 0 B/120 kB of archives.
After this operation, 364 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 277440 files and directories currently installed.)
Preparing to unpack .../libguvcview-2.0-0_2.0.7+ubuntu2~ppa1+1444-0ubuntu1~202110272153~ubuntu20.04.1_amd64.deb ...
Unpacking libguvcview-2.0-0:amd64 (2.0.7+ubuntu2~ppa1+1444-0ubuntu1~202110272153~ubuntu20.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/libguvcview-2.0-0_2.0.7+ubuntu2~ppa1+1444-0ubuntu1~202110272153~ubuntu20.04.1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libgviewaudio-2.0.so.2.0.0', which is also in package libguvcview-2.0-2:amd64 2.0.6+debian-1build1
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libguvcview-2.0-0_2.0.7+ubuntu2~ppa1+1444-0ubuntu1~202110272153~ubuntu20.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any suggestions as to how to fix this?

---

### Post by deadflowr on 2021-11-12
The problem is you added the guvcview ppa which has a libguvcview dependency conflict with an existing package.
As it want to install a  package of a lower value than the package already installed.
Luckily, though, it seems that the original libguvcview package is listed as autoremove--able
so maybe try
```
sudo apt autoremove
```
then see if it rights itself.

If that does nothing, perhaps look over this thread: [https://forums.linuxmint.com/viewtopic.php?t=300818]("https://forums.linuxmint.com/viewtopic.php?t=300818")
As it deals with the same exact problem.

---

### Post by agvantibo on 2021-11-12
Try: sudo apt reinstall libguvcview-2.0-2 libguvcview-2.0-0; sudo apt autopurge libguvcview-2.0-2 libguvcview-2.0-0; sudo apt autopurge; sudo apt autoclean;
This will:
1. Reinstall packages to get them all to a consistent state.
2. Try to safely remove them.

---

### Post by ActionParsnip on 2021-11-12
What is the output of
```

apt-cache policy libguvcview

```
Looks like a PPA. In which case you should contact the PPA maintainer to inform

---

### Post by reut2 on 2021-11-13
When I follow your suggestion this is what I get:
> reuven@reuven-OptiPlex-9020:~$ sudo apt autoremove
[sudo] password for reuven: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 guvcview : Depends: libguvcview-2.0-0 but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).



---

### Post by reut2 on 2021-11-13
This is the output from your suggestion:
> reuven@reuven-OptiPlex-9020:~$ sudo apt reinstall libguvcview-2.0-2 libguvcview-2.0-0; sudo apt autopurge libguvcview-2.0-2 libguvcview-2.0-0; sudo apt autopurge; sudo apt autoclean;
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libllvm11 libllvm11:i386 linux-headers-5.4.0-88
  linux-headers-5.4.0-88-generic linux-image-5.4.0-88-generic
  linux-modules-5.4.0-88-generic linux-modules-extra-5.4.0-88-generic
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  libguvcview-2.0-0
0 upgraded, 1 newly installed, 1 reinstalled, 0 to remove and 21 not upgraded.
1 not fully installed or removed.
Need to get 110 kB/230 kB of archives.
After this operation, 364 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal/universe amd64 libguvcview-2.0-2 amd64 2.0.6+debian-1build1 [110 kB]
Fetched 110 kB in 0s (436 kB/s)            
(Reading database ... 277440 files and directories currently installed.)
Preparing to unpack .../libguvcview-2.0-0_2.0.7+ubuntu2~ppa1+1444-0ubuntu1~20211
0272153~ubuntu20.04.1_amd64.deb ...
Unpacking libguvcview-2.0-0:amd64 (2.0.7+ubuntu2~ppa1+1444-0ubuntu1~202110272153
~ubuntu20.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/libguvcview-2.0-0_2.0.7+u
buntu2~ppa1+1444-0ubuntu1~202110272153~ubuntu20.04.1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libgviewaudio-2.0.so.2.0.0', whi
ch is also in package libguvcview-2.0-2:amd64 2.0.6+debian-1build1
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Preparing to unpack .../libguvcview-2.0-2_2.0.6+debian-1build1_amd64.deb ...
Unpacking libguvcview-2.0-2:amd64 (2.0.6+debian-1build1) over (2.0.6+debian-1bui
ld1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libguvcview-2.0-0_2.0.7+ubuntu2~ppa1+1444-0ubuntu1~2021
10272153~ubuntu20.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'libguvcview-2.0-0' is not installed, so not removed
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 guvcview : Depends: libguvcview-2.0-0 but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 guvcview : Depends: libguvcview-2.0-0 but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del linux-firmware 1.187.19 [110 MB]



---

### Post by reut2 on 2021-11-13
output of 
apt-cache policy libguvcview
> apt-cache policy libguvcview

---

### Post by reut2 on 2021-11-13
Thank you!
I followed the suggestion in the linuxmint forum, and the problem seems to have been resolved.

---

