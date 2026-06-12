---
title: "Do I need to rollback upgrades? if so, how do i do so?"
date: 2021-02-13
forum: Installation &amp; Upgrades
---

### Post by wolfe23 on 2021-02-13
Hello,
   I''m running Ubuntu 20.04LTS on a dual boot system (Windows 10 that i rarely use)... that i have been using for quite some time (back to at least Ubuntu 12-14 or so), and haven't really had too many issues with... a few here and there, that i've been walked through via ubuntu help groups.

  So here is my problem, at some point in allowing automatic upgrades there must have been a glitch, tho i'm not sure how it happened. If i just allow a default boot, i'm unable to access my wireless network, or a few different options under settings. I can't even shutdown via ""power off".  In order to get a working system, i have to select advanced options in Grub, and select Linux 5.4.0.54 (i'm assuming that is the kernel version, please correct me if i'm mistaken)... the latest available on my system in that menu is 5.4.0.62 (i've also stopped allowing updates to happen, tho i allowed a few after i noticed the issue initially).

  I'm assuming i might need to rollback the updates, and then update again??

  Tho i don't often have time to explore as much as i'd like to, i'm actually running linux with the idea of learning more about it (well ,and the fact i'm not a fan of windows as well). i'm comfortable using terminal, and have installed software both in the gui program "software" and via apt-get install.

So i'm hoping to get help with both what to do, and why i'm doing it at the same time. If there is any other data needed, or any actions i need to perform, then please let me know.

  Your time, attention and help is much appreciated.
-bw

---

### Post by wolfe23 on 2021-02-13
okay... going off an askubuntu thread... i did this:

```
wolfe23@Eris23:~$ dpkg --list | egrep -i --color 'linux-image|linux-headers|linux-modules' | awk '{ print $2 }'
linux-headers-5.4.0-59
linux-headers-5.4.0-59-generic
linux-headers-5.4.0-60
linux-headers-5.4.0-60-generic
linux-headers-5.4.0-62
linux-headers-5.4.0-62-generic
linux-headers-generic
linux-image-4.15.0-20-generic
linux-image-4.15.0-23-generic
linux-image-4.15.0-24-generic
linux-image-4.15.0-29-generic
linux-image-4.15.0-30-generic
linux-image-4.15.0-32-generic
linux-image-4.15.0-33-generic
linux-image-4.15.0-34-generic
linux-image-4.15.0-36-generic
linux-image-4.15.0-38-generic
linux-image-4.15.0-39-generic
linux-image-4.15.0-42-generic
linux-image-4.15.0-43-generic
linux-image-4.15.0-44-generic
linux-image-4.15.0-45-generic
linux-image-4.15.0-46-generic
linux-image-4.15.0-47-generic
linux-image-4.15.0-48-generic
linux-image-4.15.0-50-generic
linux-image-4.15.0-51-generic
linux-image-4.15.0-52-generic
linux-image-4.15.0-54-generic
linux-image-4.15.0-55-generic
linux-image-4.15.0-70-generic
linux-image-5.0.0-36-generic
linux-image-5.3.0-23-generic
linux-image-5.3.0-24-generic
linux-image-5.3.0-26-generic
linux-image-5.3.0-29-generic
linux-image-5.3.0-40-generic
linux-image-5.3.0-42-generic
linux-image-5.3.0-45-generic
linux-image-5.3.0-46-generic
linux-image-5.3.0-51-generic
linux-image-5.4.0-29-generic
linux-image-5.4.0-31-generic
linux-image-5.4.0-33-generic
linux-image-5.4.0-37-generic
linux-image-5.4.0-39-generic
linux-image-5.4.0-40-generic
linux-image-5.4.0-42-generic
linux-image-5.4.0-45-generic
linux-image-5.4.0-47-generic
linux-image-5.4.0-48-generic
linux-image-5.4.0-51-generic
linux-image-5.4.0-52-generic
linux-image-5.4.0-53-generic
linux-image-5.4.0-54-generic
linux-image-5.4.0-56-generic
linux-image-5.4.0-58-generic
linux-image-5.4.0-59-generic
linux-image-5.4.0-60-generic
linux-image-5.4.0-62-generic
linux-image-generic
linux-modules-4.15.0-20-generic
linux-modules-4.15.0-23-generic
linux-modules-4.15.0-24-generic
linux-modules-4.15.0-29-generic
linux-modules-4.15.0-30-generic
linux-modules-4.15.0-32-generic
linux-modules-4.15.0-33-generic
linux-modules-4.15.0-34-generic
linux-modules-4.15.0-36-generic
linux-modules-4.15.0-38-generic
linux-modules-4.15.0-39-generic
linux-modules-4.15.0-42-generic
linux-modules-4.15.0-43-generic
linux-modules-4.15.0-44-generic
linux-modules-4.15.0-45-generic
linux-modules-4.15.0-46-generic
linux-modules-4.15.0-47-generic
linux-modules-4.15.0-48-generic
linux-modules-4.15.0-50-generic
linux-modules-4.15.0-51-generic
linux-modules-4.15.0-52-generic
linux-modules-4.15.0-54-generic
linux-modules-4.15.0-55-generic
linux-modules-4.15.0-70-generic
linux-modules-5.0.0-36-generic
linux-modules-5.3.0-23-generic
linux-modules-5.3.0-24-generic
linux-modules-5.3.0-26-generic
linux-modules-5.3.0-29-generic
linux-modules-5.3.0-40-generic
linux-modules-5.3.0-42-generic
linux-modules-5.3.0-45-generic
linux-modules-5.3.0-46-generic
linux-modules-5.3.0-51-generic
linux-modules-5.4.0-29-generic
linux-modules-5.4.0-31-generic
linux-modules-5.4.0-33-generic
linux-modules-5.4.0-37-generic
linux-modules-5.4.0-39-generic
linux-modules-5.4.0-40-generic
linux-modules-5.4.0-42-generic
linux-modules-5.4.0-45-generic
linux-modules-5.4.0-47-generic
linux-modules-5.4.0-48-generic
linux-modules-5.4.0-51-generic
linux-modules-5.4.0-52-generic
linux-modules-5.4.0-53-generic
linux-modules-5.4.0-54-generic
linux-modules-5.4.0-56-generic
linux-modules-5.4.0-58-generic
linux-modules-5.4.0-59-generic
linux-modules-5.4.0-60-generic
linux-modules-5.4.0-62-generic
linux-modules-extra-4.15.0-20-generic
linux-modules-extra-4.15.0-23-generic
linux-modules-extra-4.15.0-24-generic
linux-modules-extra-4.15.0-29-generic
linux-modules-extra-4.15.0-30-generic
linux-modules-extra-4.15.0-32-generic
linux-modules-extra-4.15.0-33-generic
linux-modules-extra-4.15.0-34-generic
linux-modules-extra-4.15.0-36-generic
linux-modules-extra-4.15.0-38-generic
linux-modules-extra-4.15.0-39-generic
linux-modules-extra-4.15.0-42-generic
linux-modules-extra-4.15.0-43-generic
linux-modules-extra-4.15.0-44-generic
linux-modules-extra-4.15.0-45-generic
linux-modules-extra-4.15.0-46-generic
linux-modules-extra-4.15.0-47-generic
linux-modules-extra-4.15.0-48-generic
linux-modules-extra-4.15.0-50-generic
linux-modules-extra-4.15.0-51-generic
linux-modules-extra-4.15.0-52-generic
linux-modules-extra-4.15.0-54-generic
linux-modules-extra-4.15.0-55-generic
linux-modules-extra-4.15.0-70-generic
linux-modules-extra-5.0.0-36-generic
linux-modules-extra-5.3.0-23-generic
linux-modules-extra-5.3.0-24-generic
linux-modules-extra-5.3.0-26-generic
linux-modules-extra-5.3.0-29-generic
linux-modules-extra-5.3.0-40-generic
linux-modules-extra-5.3.0-42-generic
linux-modules-extra-5.3.0-45-generic
linux-modules-extra-5.3.0-46-generic
linux-modules-extra-5.3.0-51-generic
linux-modules-extra-5.4.0-29-generic
linux-modules-extra-5.4.0-31-generic
linux-modules-extra-5.4.0-33-generic
linux-modules-extra-5.4.0-37-generic
linux-modules-extra-5.4.0-39-generic
linux-modules-extra-5.4.0-40-generic
linux-modules-extra-5.4.0-42-generic
linux-modules-extra-5.4.0-45-generic
linux-modules-extra-5.4.0-47-generic
linux-modules-extra-5.4.0-48-generic
linux-modules-extra-5.4.0-51-generic
linux-modules-extra-5.4.0-52-generic
linux-modules-extra-5.4.0-53-generic
linux-modules-extra-5.4.0-54-generic
linux-modules-extra-5.4.0-56-generic
linux-modules-extra-5.4.0-58-generic
linux-modules-extra-5.4.0-59-generic
linux-modules-extra-5.4.0-60-generic
linux-modules-extra-5.4.0-62-generic


```
i guess i'm gonna try to "sudo apt purge" most of the kernels back to 5.4.0-54...  then try upgrading again.... after i do some backing up first.

---

### Post by Impavidus on 2021-02-14
There's something in the new kernels that doesn't work well with your system. Wifi problems are relatively common, your other problems sound weird. New kernels are pulled in when the kernel metapackage is upgraded. There's no undo for this upgrade, but that doesn't matter, as it's a metapackage anyway. Old kernels get removed later. As you have seen, kernel 5.4.0-54 is still on your system.

The output in your second post isn't very useful, as it lists many kernels that have been removed. Better look at this:```
dpkg --list 'linux-*' | grep -v '^rc \|^un '
```
Keep the last known working kernel (5.4.0-54), keep the metapackages (those with no version number in their name) and keep the kernels on which the metapackages depend (as their removal would force removal of the metapackage). You need the metapackage to pull in the new kernels, in one of which this issue will hopefully be fixed. Don't allow automatic removal of old packages

Seach bug reports. Maybe somebody has already reported your issue.

---

### Post by wolfe23 on 2021-02-15
Code:
```
wolfe23@Eris23:~$ dpkg --list 'linux-*' | grep -v '^rc \|^un '
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                   Version              Architecture Description
+++-======================================-====================-============-===============================================================
ii  linux-base                             4.5ubuntu3.1         all          Linux image base package
ii  linux-firmware                         1.187.7              all          Firmware for Linux kernel drivers
ii  linux-generic                          5.4.0.62.65          amd64        Complete Generic Linux kernel and headers
ii  linux-headers-5.4.0-59                 5.4.0-59.65          all          Header files related to Linux kernel version 5.4.0
ii   linux-headers-5.4.0-59-generic         5.4.0-59.65           amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-60                 5.4.0-60.67          all          Header files related to Linux kernel version 5.4.0
ii   linux-headers-5.4.0-60-generic         5.4.0-60.67           amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-62                 5.4.0-62.70          all          Header files related to Linux kernel version 5.4.0
ii   linux-headers-5.4.0-62-generic         5.4.0-62.70           amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                  5.4.0.62.65          amd64        Generic Linux kernel headers
ii  linux-image-5.4.0-54-generic           5.4.0-54.60          amd64        Signed kernel image generic
ii  linux-image-5.4.0-59-generic           5.4.0-59.65          amd64        Signed kernel image generic
ii  linux-image-5.4.0-60-generic           5.4.0-60.67          amd64        Signed kernel image generic
ii  linux-image-5.4.0-62-generic           5.4.0-62.70          amd64        Signed kernel image generic
ii  linux-image-generic                    5.4.0.62.65          amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                   5.4.0-62.70          amd64        Linux Kernel Headers for development
ii   linux-modules-5.4.0-54-generic         5.4.0-54.60           amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86  SMP
ii  linux-modules-5.4.0-59-generic         5.4.0-59.65           amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86  SMP
ii  linux-modules-5.4.0-60-generic         5.4.0-60.67           amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86  SMP
ii  linux-modules-5.4.0-62-generic         5.4.0-62.70           amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86  SMP
ii  linux-modules-extra-5.4.0-54-generic   5.4.0-54.60           amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86  SMP
ii  linux-modules-extra-5.4.0-59-generic   5.4.0-59.65           amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86  SMP
ii  linux-modules-extra-5.4.0-60-generic   5.4.0-60.67           amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86  SMP
ii  linux-modules-extra-5.4.0-62-generic   5.4.0-62.70           amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86  SMP
ii  linux-sound-base                       1.0.25+dfsg-0ubuntu5 all          base package for ALSA and OSS sound systems
wolfe23@Eris23:~$ 
```


so... assuming zz= (59,60,62)
i should sudo apt purge:
linux-headers-5.4.0-zz  
linux-headers-5.4.0-zz-generic
linux-image-5.4.0-zz-generic
linux-modules-5.4.0-zz-generic  and
linux-modules-extra-5.4.0-zz-generic

is that correct? and basically keep everything else?
then should i basically sudo apt upgrade? or what should i do afterwards to get back to the current kernel distribution?

also,  is there anywhere (logs) i should be checking for error reports  beforehand? maybe to understand what went wrong, and perhaps check that  it doesn't glitch again?
oh... and where do i check bug reports online?

thanx so much for your help @Impavidus.```

```

---

### Post by Impavidus on 2021-02-16
Remove 59 and 60. They are broken (you say, I can't see from the output) and old. Keep 54 (it works). Removal of 62 will trigger removal of the kernel metapackage. You need that kernel metapackage to get automatic upgrades, so even they currently don't work, you want them back later when this has been fixed.

Nothing went wrong during installation of your packages and nothing will be fixed by reinstalling them. The problem is a bug in kernels 56 and later.

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
Note that I only encountered very few bugs myself and in all cases they were already known and being worked on.

---

### Post by TheFu on 2021-02-16
```
sudo apt purge linux-image-4.15*
```
will remove all the 4.15 line of kernels.  Probably want to remove the 
linux-modules-4.15* and linux-headers-4.15* too.

Wildcards are handy.

I'd keep no more than 3 kernels around.  If you patch and a new 4.15 kernel gets installed, then the metapackage for that needs to be removed too ... and the newly installed 4.15 kernel, headers, and modules too.

Purge will remove the 'rc' cruft that gets reported by APT/dpkg.  I've had to manually remove some files in /etc/modules/... under unwanted kernels too.

As for rollbacks .... we call those "backups." Always a good idea to have at least weekly, if not daily, backups. Make them versioned to have better options when bad things happen, faster backups, and gain so much more storage efficiency for each version in any modern backup tool.

---

