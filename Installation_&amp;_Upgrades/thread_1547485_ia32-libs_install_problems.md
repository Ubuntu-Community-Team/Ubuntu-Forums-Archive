---
title: "ia32-libs install problems"
date: 2010-08-06
forum: Installation &amp; Upgrades
---

### Post by BillyJoeKyle on 2010-08-06
hello im new to the forum and fairly new to the linux OS. i have used Ubuntu 9.10 some and loved it and ive recently upgraded to 10.04 but seem to have nothing but problems. anyways the problem ive had it with the ia32-libs package refusing to install. ive been searching the forums and i have tried a bunch of stuff but nothing seems to be working so i thought i start a thread and see if anybody had any ideas for me.

so when i type this in terminal: sudo apt-get update && sudo apt-get install ia32-libs

everything runs okay then when it gets to the install part this comes out:
The following NEW packages will be installed:
  ia32-libs
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/36.6MB of archives.
After this operation, 159MB of additional disk space will be used.
(Reading database ... 158199 files and directories currently installed.)
Unpacking ia32-libs (from .../ia32-libs_2.7ubuntu26_amd64.deb) ...
lzma: Decoder error
dpkg: error processing /var/cache/apt/archives/ia32-libs_2.7ubuntu26_amd64.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess <decompress> returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_2.7ubuntu26_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

this is the linux im running if that helps: uname -a
Linux ubuntu 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux

any help would be amazing...thanks

---

### Post by oldos2er on 2010-08-06
```
sudo rm /var/cache/apt/archives/ia32-libs_2.7ubuntu26_amd64.deb
``` then retry sudo apt-get install ia32-libs.

---

### Post by BillyJoeKyle on 2010-08-06
It worked!!!!

thank you very much!

---

### Post by jouzts on 2010-08-10
I have a similar error message, but apparently a different cause.

My error message:
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  ia32-libs
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/36.6MB of archives.
After this operation, 20.5kB of additional disk space will be used.
Do you want to continue [Y/n]?
(Reading database ... 252313 files and directories currently installed.)
Preparing to replace ia32-libs 2.7ubuntu25 (using .../ia32-libs_2.7ubuntu26_amd64.deb) ...
Unpacking replacement ia32-libs ...
dpkg: error processing /var/cache/apt/archives/ia32-libs_2.7ubuntu26_amd64.deb (--unpack):
 trying to overwrite '/usr/lib32/libGL.so', which is also in package nvidia-glx-190 0:190.53-0ubuntu5
Processing triggers for libglib2.0-0 ...
Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_2.7ubuntu26_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Unfortunately "sudo rm /var/cache/apt/archives/ia32-libs_2.7ubuntu26_amd64.deb" does not remedy the problem. Judging from my error message, I should remove my proprietary nvidia driver, do the upgrade and replace the nvidia driver. But what if nvidia won't re-install? That would be a worse situation than I am in now since this is a MythTV frontend box. 

Any thoughts?

Thanks, John

---

### Post by locosway on 2010-08-12
I'm having the same issue. After removing the package I tried to update again and it still failed.


```
greg@moniker:/var/cache/apt/archives$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  ia32-libs
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 36.6MB of archives.
After this operation, 20.5kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe ia32-libs 2.7ubuntu26 [36.6MB]
Fetched 36.6MB in 2min 3s (297kB/s)                                                                                                                                             
(Reading database ... 330025 files and directories currently installed.)
Preparing to replace ia32-libs 2.7ubuntu25 (using .../ia32-libs_2.7ubuntu26_amd64.deb) ...
Unpacking replacement ia32-libs ...
dpkg: error processing /var/cache/apt/archives/ia32-libs_2.7ubuntu26_amd64.deb (--unpack):
 unable to stat `./lib32/udev' (which I was about to install): Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_2.7ubuntu26_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
greg@moniker:/var/cache/apt/archives$ 
```

This has been happening for weeks, and the only thing I can think of is the package is broken.

---

