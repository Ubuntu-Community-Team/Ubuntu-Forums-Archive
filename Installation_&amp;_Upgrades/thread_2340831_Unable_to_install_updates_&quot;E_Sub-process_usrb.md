---
title: "Unable to install updates: &quot;E: Sub-process /usr/bin/dpkg returned an error code (1)&quot;"
date: 2016-10-22
forum: Installation &amp; Upgrades
---

### Post by Seventh_Magpie on 2016-10-22
Hello everyone, 

I'm not an experienced user, to begin with. And now I've ran into  problem I cannot solve on my own. Hope somebody will help me. 

I'm running Xubuntu 14.04. 

Some time ago the warning appeared in my tray, the red circle with a "brick". Some updates were trying to get installed, but couldn't. I ran the suggested command [FONT=arial black]apt-get install -f[/FONT] and got the following: 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libreoffice-gtk linux-image-3.13.0-98-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libreoffice-common tzdata
Suggested packages:
  libreoffice-style-hicontrast libreoffice-style-oxygen libreoffice-style-sifr
The following packages will be upgraded:
  libreoffice-common tzdata
2 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
28 not fully installed or removed.
Need to get 0 B/22,7 MB of archives.
After this operation, 2 048 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Preconfiguring packages ...
(Reading database ... 1293038 files and directories currently installed.)
Preparing to unpack .../libreoffice-common_1%3a5.2.2-0ubuntu1~trusty0_all.deb ...
Unpacking libreoffice-common (1:5.2.2-0ubuntu1~trusty0) over (1:5.2.1~rc2-0ubuntu1~trusty0) ...
No apport report written because the error message indicates a disk full error
                                                                              dpkg: error processing archive /var/cache/apt/archives/libreoffice-common_1%3a5.2.2-0ubuntu1~trusty0_all.deb (--unpack):
 unable to create `/usr/lib/libreoffice/share/gallery/arrows/A62-Arrow-StripedBlue-Right.svg.dpkg-new' (while processing `./usr/lib/libreoffice/share/gallery/arrows/A62-Arrow-StripedBlue-Right.svg'): No space left on device
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
rmdir: failed to remove ‘/var/lib/libreoffice/share/prereg/’: No such file or directory
rmdir: failed to remove ‘/var/lib/libreoffice/share/’: No such file or directory
rmdir: failed to remove ‘/var/lib/libreoffice/program/’: No such file or directory
rmdir: failed to remove ‘/var/lib/libreoffice’: No such file or directory
rmdir: failed to remove ‘/var/lib/libreoffice’: No such file or directory
Preparing to unpack .../tzdata_2016g-0ubuntu0.14.04_all.deb ...
Unpacking tzdata (2016g-0ubuntu0.14.04) over (2016f-0ubuntu0.14.04) ...
No apport report written because the error message indicates a disk full error
                                                                              dpkg: error processing archive /var/cache/apt/archives/tzdata_2016g-0ubuntu0.14.04_all.deb (--unpack):
 unable to create `/usr/share/zoneinfo/right/Etc/GMT-6.dpkg-new' (while processing `./usr/share/zoneinfo/right/Etc/GMT-6'): No space left on device
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a5.2.2-0ubuntu1~trusty0_all.deb
 /var/cache/apt/archives/tzdata_2016g-0ubuntu0.14.04_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

[FONT=arial black]df -h[/FONT] gives me this: 

```
Filesystem      Size  Used Avail Use% Mounted on
udev            994M  8,0K  994M   1% /dev
tmpfs           201M  1,1M  200M   1% /run
/dev/sda5        20G   16G  3,4G  83% /
none            4,0K     0  4,0K   0% /sys/fs/cgroup
none            5,0M     0  5,0M   0% /run/lock
none           1003M  160K 1003M   1% /run/shm
none            100M   44K  100M   1% /run/user
/dev/sda7        47G   15G   30G  33% /home
/dev/sda3        50G  3,5G   47G   7% /media/data
```

[FONT=arial black]df -i[/FONT] gives me this:

```
Filesystem       Inodes   IUsed    IFree IUse% Mounted on
udev             214907     510   214397    1% /dev
tmpfs            219716     512   219204    1% /run
/dev/sda5       1310720 1309501     1219  100% /
none             219716       2   219714    1% /sys/fs/cgroup
none             219716       3   219713    1% /run/lock
none             219716       7   219709    1% /run/shm
none             219716      33   219683    1% /run/user
/dev/sda3      48849992    2695 48847297    1% /media/data
/dev/sda7       3088384   31379  3057005    2% /home
```

I suppose this line with 100% points to the cause. However, I don't know what to do about it. I've read a lot on this issue, people talk about removing old kernels from the boot partition, but I don't have the word "boot" after slash in the line with 100%... and I really am lost in all of this. Please assist.

---

### Post by oldos2er on 2016-10-22
Yes, it looks like you're out of inodes on your root partition. You could try some of the suggestions in this thread: [https://ubuntuforums.org/showthread.php?t=2325064](https://ubuntuforums.org/showthread.php?t=2325064)

---

### Post by Seventh_Magpie on 2016-10-22
Thank you for the link. Sadly, it doesn't clear things much for me. The topic starter there seems to know their way around Ubuntu, while my preferred keys are white and black. :) I don't even understand what he'd tried to do before he came to ask for advice. :)

I've done what Bashing-om first suggested: 

```
sudo apt-get autoclean 
sudo apt-get autoremove
sudo apt-get clean
```

I've done it before, and I've repeated it now. The first one and the third didn't give me any output, while the second one complained about unmet dependencies. This one I've already seen when I tried what the broken Package Manager suggested ([FONT=arial black]apt-get install -f[/FONT]).

By now I have a general idea about old kernels and headers taking up space. The question is what to do about it, preferably in a step-by-step fashion. :) I'm rather wary of Linux people saying things like "try removing some files", because that usually doesn't mean the usual way of point-and-click. :)

---

### Post by Bashing-om on 2016-10-22
Seventh_Magpiek Hey; 

From the error report:
> 
Unpacking tzdata (2016g-0ubuntu0.14.04) over (2016f-0ubuntu0.14.04) ...
No apport report written because the error message indicates a disk full error
                                                                              dpkg: error processing archive /var/cache/apt/archives/tzdata_2016g-0ubuntu0.14.04_all.deb (--unpack):
 unable to create `/usr/share/zoneinfo/right/Etc/GMT-6.dpkg-new' (while processing `./usr/share/zoneinfo/right/Etc/GMT-6'): No space left on device
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a5.2.2-0ubuntu1~trusty0_all.deb
 /var/cache/apt/archives/tzdata_2016g-0ubuntu0.14.04_all.deb

Let's take a gentler poke at it and see what bites back:
```

sudo apt install --reinstall tzdata 

```

Depending here is what we next do ( /libreoffice ) .

[INDENT][INDENT]keeping the package manager
[INDENT][INDENT][INDENT]satisfied
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Seventh_Magpie on 2016-10-23
Hello Bashing-om!

[FONT=arial black]sudo apt install --reinstall tzdata[/FONT] gives me the following: 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:5.2.2) but 1:5.2.1~rc2-0ubuntu1~trusty0 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by Bashing-om on 2016-10-23
Seventh_Magpie; K;

That looks promising .
Are we now looking at a version conflict ?
show:
```

apt-cache policy libreoffice
apt-cache policy libreoffice-common

```
seems now that there is a PPA involved here.
The system says :
> 
libreoffice-core : Depends: libreoffice-common (> 1:5.2.2) but 1:5.2.1~rc2-0ubuntu1~trusty0 is to be installed

where the system wants to install a earlier version than the package manager will permit.
And further, what is in the repository:
> 
sysop@1404mini:~$ apt list libreoffice-common
Listing... Done
libreoffice-common/trusty-updates,trusty-security 1:4.2.8-0ubuntu4 all
sysop@1404mini:~$


and this begs the question:
[INDENT][INDENT]which way did he go, George
[/INDENT][/INDENT]

---

### Post by Seventh_Magpie on 2016-10-23
My first thought at the very beginning was that something was wrong with the way LibreOffice was installed, as well. I don't remember the details and how I solved it back then, but I remember there were problems when upgrading from LO 4 to LO 5. 

However, there is still issue with disk space? Or is it a separate issue?

apt-cache policy libreoffice
```

libreoffice:
  Installed: 1:5.2.2-0ubuntu1~trusty0
  Candidate: 1:5.2.2-0ubuntu1~trusty0
  Version table:
 *** 1:5.2.2-0ubuntu1~trusty0 0
        500 [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/) trusty/main i386 Packages
        100 /var/lib/dpkg/status
     1:4.2.8-0ubuntu4 0
        500 [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) trusty-updates/universe i386 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/universe i386 Packages
     1:4.2.3~rc3-0ubuntu2 0
        500 [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) trusty/universe i386 Packages  
```


apt-cache policy libreoffice-common
```

libreoffice-common:
  Installed: 1:5.2.1~rc2-0ubuntu1~trusty0
  Candidate: 1:5.2.2-0ubuntu1~trusty0
  Version table:
     1:5.2.2-0ubuntu1~trusty0 0
        500 [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/) trusty/main i386 Packages
 *** 1:5.2.1~rc2-0ubuntu1~trusty0 0
        100 /var/lib/dpkg/status
     1:4.2.8-0ubuntu4 0
        500 [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) trusty-updates/main i386 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main i386 Packages
     1:4.2.3~rc3-0ubuntu2 0
        500 [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) trusty/main i386 Packages 
```

---

### Post by Bashing-om on 2016-10-23
Seventh_Magpiel Yeah ..

We do have separate issues here .
On the disk space issue we find out where all the space is taken up:
```

cd /
sudo du -sx * | sort -n

```
If you need to drill down further, use cd to move to a directory of interest then repeat the du command.
The results are in megabytes, (The "x" switch limits du to a single file system, in this case the root file system.)

And for libreoffice.
Why 32 bit install ? Is this a 32 bit system ?
show:
```

uname -a

```

And is there a reason why the supported repository version will not work for you ?
I would consider  ppa-purge and revert the PPA version to that of the repo .
What think you ?

[INDENT][INDENT]progress made
[INDENT][INDENT][INDENT]one step at the time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Seventh_Magpie on 2016-10-23
Yes, it's 32 bit system. It's a 10 year old Samsung NC 10 netbook. :) I use it mainly for writing and sometimes reading of piano magazines. 

This is what [FONT=arial black]uname -a[/FONT] gives me: 
Linux Soroca 3.13.0-96-generic #143-Ubuntu SMP Mon Aug 29 20:15:47 UTC 2016 i686 i686 i686 GNU/Linux

I don't think I understand you correctly where repositories are concerned. Is it not an official LibreOffice repository that I have? 

As for [FONT=arial black]du[/FONT], it seems to show me the content of Home. There is enough space as far as I can see. Maybe something else?

---

### Post by Bashing-om on 2016-10-23
Seventh_Magpie; Well ..

Ya got a partially installed libreoffice from the PPA  "ppa.launchpad.net/libreoffice/ppa/ubuntu/" .
You must decide if ya would rather not have the repo version .

the 'du' command is to (c)hange (d)irectory to /
so we look at the operating system rather than just /home .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by Seventh_Magpie on 2016-10-23
Hmm. LibreOffice doesn't look partially installed, as far as I can see. It works without issue. I cannot even uninstall it due to these unmet dependencies. :) What do you mean by "decide if ya would rather not have the repo version"? Are you saying that I have a newer version installed compared to one that is trying to install itself? How can that be? While it is quite possible that I've installed LO 5 manually, not via Software Center, that was quite some time ago. Like I said, there were some issues with upgrading from LO 4 to LO 5. I'd like to have the current version of LibreOffice, if that's possible. Although at this moment I don't even care all that much. This broken Package Manager is wearing me out. 

As for the disk usage, it gives me this: 
```

du: cannot access &#8216;proc/3449/task/3449/fd/4&#8217;: No such file or directory
du: cannot access &#8216;proc/3449/task/3449/fdinfo/4&#8217;: No such file or directory
du: cannot access &#8216;proc/3449/fd/4&#8217;: No such file or directory
du: cannot access &#8216;proc/3449/fdinfo/4&#8217;: No such file or directory
0 initrd.img
0 initrd.img.old
0 proc
0 sys
0 vmlinuz
0 vmlinuz.old
4 cdrom
4 dev
4 mnt
4 srv
8 media
16 lost+found
20 tmp
44 root
1128 run
9472 bin
12000 sbin
14808 etc
183088 opt
676856 var
1109304 boot
5781808 lib
7489160 usr
12622196 home 
```

---

### Post by Bashing-om on 2016-10-23
AgoSeventh_Magpie; Wellllll

Here is what a tightly managed system disk usage is:
```

sysop@1404mini:/$ sudo du -sx * | sort -n
du: cannot access ‘proc/1797/task/1797/fd/4’: No such file or directory
du: cannot access ‘proc/1797/task/1797/fdinfo/4’: No such file or directory
du: cannot access ‘proc/1797/fd/4’: No such file or directory
du: cannot access ‘proc/1797/fdinfo/4’: No such file or directory
0       forcefsdk
0       initrd.img
0       initrd.img.old
0       proc
0       sys
0       vmlinuz
0       vmlinuz.old
4       dev
4       lib64
4       srv
4       test
4       work
12      media
12      tmp
16      lost+found
32      mnt
776     run
1868    root
4984    grub
6492    etc
9464    sbin
9828    bin
104072  boot
173848  opt
711076  var
720240  home
728260  lib
1173552 usr
sysop@1404mini:/$

```

Note in your case that /boot is outlandish and /home is out of sight. Your /lib could use some looking after.
So, remove old kernels in /boot with the tools of the package management system, remove everything  in /home you do not need - things you do not access frequently go to a backup . For /lib .. applications you do not use need to be gone.

Now as to libfreoffice:
This:
> 
libreoffice:
  Installed: 1:5.2.2-0ubuntu1~trusty0
  Candidate: 1:5.2.2-0ubuntu1~trusty0
  Version table:
 *** 1:5.2.2-0ubuntu1~trusty0 0
        500 [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/) trusty/main i386 Packages

says you have version 1:5.2.2-0ubuntu1~trusty0 and it came from the libreoffice PPA.

and this:
> 
1:4.2.8-0ubuntu4 0
        500 [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) trusty-updates/universe i386 Packages

is the info in respect to what is in the ubuntu software repository.

Now when you have removed whatever you can from the system gaining the operational headroom, we see what we can do to fix the PPA libreoffice.

show:
```

dpkg -l | grep linux-

```
as a place to start the cleanup .

[INDENT][INDENT]maybe a long row to hoe here .
[/INDENT][/INDENT]

---

### Post by Seventh_Magpie on 2016-10-23
Okay, I see what you mean with LibreOffice. The old one needs to be gone, then. The one from LO official repository (LO 5) needs to stay. 

As for the disk usage, I can tell you that I've lived on 3 Gb of disk space on Win 95 from 1997 till 2004. :) I just didn't know that *ubuntu could so easily choke itself this way. I was told it was the most user friendly Linux, that a non-technical user like me could handle it without an issue. I didn't even do much with it, nothing risky or weird, except with LibreOffice, maybe. :) And now it turns out that the advertisement for the user friendly OS reflects reality in a Bach way. :D As in, it is easy to play any instrument - all you have to do is touch right keys at the right time. 

Well. Sorry for the rant. This is not directed at you. I really appreciate your help. Sorry. 

[FONT=arial black]pkg -l | grep linux-[/FONT] gives me this:

```

ii  linux-firmware                                              1.127.22                                all          Firmware for Linux kernel drivers
ii  linux-generic                                               3.13.0.96.104                           i386         Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-37                                     3.13.0-37.64                            all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-37-generic                             3.13.0-37.64                            i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-39                                     3.13.0-39.66                            all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-39-generic                             3.13.0-39.66                            i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-40                                     3.13.0-40.69                            all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-40-generic                             3.13.0-40.69                            i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-43                                     3.13.0-43.72                            all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-43-generic                             3.13.0-43.72                            i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-44                                     3.13.0-44.73                            all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-44-generic                             3.13.0-44.73                            i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-45                                     3.13.0-45.74                            all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-45-generic                             3.13.0-45.74                            i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-46                                     3.13.0-46.79                            all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-46-generic                             3.13.0-46.79                            i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-48                                     3.13.0-48.80                            all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-48-generic                             3.13.0-48.80                            i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-49                                     3.13.0-49.83                            all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49-generic                             3.13.0-49.83                            i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-51                                     3.13.0-51.84                            all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-51-generic                             3.13.0-51.84                            i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-52                                     3.13.0-52.86                            all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-52-generic                             3.13.0-52.86                            i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-53                                     3.13.0-53.89                            all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-53-generic                             3.13.0-53.89                            i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-54                                     3.13.0-54.91                            all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-54-generic                             3.13.0-54.91                            i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-55                                     3.13.0-55.94                            all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-55-generic                             3.13.0-55.94                            i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-57                                     3.13.0-57.95                            all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-57-generic                             3.13.0-57.95                            i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-58                                     3.13.0-58.97                            all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-58-generic                             3.13.0-58.97                            i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-59                                     3.13.0-59.98                            all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-59-generic                             3.13.0-59.98                            i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-61                                     3.13.0-61.100                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-61-generic                             3.13.0-61.100                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-62                                     3.13.0-62.102                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-62-generic                             3.13.0-62.102                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-63                                     3.13.0-63.103                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-63-generic                             3.13.0-63.103                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-65                                     3.13.0-65.106                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-65-generic                             3.13.0-65.106                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-66                                     3.13.0-66.108                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-66-generic                             3.13.0-66.108                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-67                                     3.13.0-67.110                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-67-generic                             3.13.0-67.110                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-68                                     3.13.0-68.111                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-68-generic                             3.13.0-68.111                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-71                                     3.13.0-71.114                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-71-generic                             3.13.0-71.114                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-74                                     3.13.0-74.118                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-74-generic                             3.13.0-74.118                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-76                                     3.13.0-76.120                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-76-generic                             3.13.0-76.120                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-77                                     3.13.0-77.121                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-77-generic                             3.13.0-77.121                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-79                                     3.13.0-79.123                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-79-generic                             3.13.0-79.123                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-83                                     3.13.0-83.127                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-83-generic                             3.13.0-83.127                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-85                                     3.13.0-85.129                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-85-generic                             3.13.0-85.129                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-86                                     3.13.0-86.131                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-86-generic                             3.13.0-86.131                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-87                                     3.13.0-87.133                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-87-generic                             3.13.0-87.133                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-88                                     3.13.0-88.135                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-88-generic                             3.13.0-88.135                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-91                                     3.13.0-91.138                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-91-generic                             3.13.0-91.138                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-92                                     3.13.0-92.139                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-92-generic                             3.13.0-92.139                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-93                                     3.13.0-93.140                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-93-generic                             3.13.0-93.140                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-95                                     3.13.0-95.142                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-95-generic                             3.13.0-95.142                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-96                                     3.13.0-96.143                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-96-generic                             3.13.0-96.143                           i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-generic                                       3.13.0.96.104                           i386         Generic Linux kernel headers
ii  linux-image-3.13.0-37-generic                               3.13.0-37.64                            i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-39-generic                               3.13.0-39.66                            i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-40-generic                               3.13.0-40.69                            i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-43-generic                               3.13.0-43.72                            i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-44-generic                               3.13.0-44.73                            i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-45-generic                               3.13.0-45.74                            i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-46-generic                               3.13.0-46.79                            i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-48-generic                               3.13.0-48.80                            i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-49-generic                               3.13.0-49.83                            i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-51-generic                               3.13.0-51.84                            i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-52-generic                               3.13.0-52.86                            i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-53-generic                               3.13.0-53.89                            i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-54-generic                               3.13.0-54.91                            i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-55-generic                               3.13.0-55.94                            i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-57-generic                               3.13.0-57.95                            i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-58-generic                               3.13.0-58.97                            i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-59-generic                               3.13.0-59.98                            i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-61-generic                               3.13.0-61.100                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-62-generic                               3.13.0-62.102                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-63-generic                               3.13.0-63.103                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-65-generic                               3.13.0-65.106                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-66-generic                               3.13.0-66.108                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-67-generic                               3.13.0-67.110                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-68-generic                               3.13.0-68.111                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-71-generic                               3.13.0-71.114                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-74-generic                               3.13.0-74.118                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-76-generic                               3.13.0-76.120                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-77-generic                               3.13.0-77.121                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-79-generic                               3.13.0-79.123                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-83-generic                               3.13.0-83.127                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-85-generic                               3.13.0-85.129                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-86-generic                               3.13.0-86.131                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-87-generic                               3.13.0-87.133                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-88-generic                               3.13.0-88.135                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-91-generic                               3.13.0-91.138                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-92-generic                               3.13.0-92.139                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-93-generic                               3.13.0-93.140                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-95-generic                               3.13.0-95.142                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-96-generic                               3.13.0-96.143                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
iU  linux-image-3.13.0-98-generic                               3.13.0-98.145                           i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic                         3.13.0-37.64                            i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic                         3.13.0-39.66                            i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-40-generic                         3.13.0-40.69                            i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-43-generic                         3.13.0-43.72                            i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-44-generic                         3.13.0-44.73                            i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-45-generic                         3.13.0-45.74                            i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-46-generic                         3.13.0-46.79                            i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-48-generic                         3.13.0-48.80                            i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-49-generic                         3.13.0-49.83                            i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-51-generic                         3.13.0-51.84                            i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-52-generic                         3.13.0-52.86                            i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-53-generic                         3.13.0-53.89                            i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-54-generic                         3.13.0-54.91                            i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-55-generic                         3.13.0-55.94                            i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-57-generic                         3.13.0-57.95                            i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-58-generic                         3.13.0-58.97                            i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-59-generic                         3.13.0-59.98                            i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-61-generic                         3.13.0-61.100                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-62-generic                         3.13.0-62.102                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-63-generic                         3.13.0-63.103                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-65-generic                         3.13.0-65.106                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-66-generic                         3.13.0-66.108                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-67-generic                         3.13.0-67.110                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-68-generic                         3.13.0-68.111                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-71-generic                         3.13.0-71.114                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-74-generic                         3.13.0-74.118                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-76-generic                         3.13.0-76.120                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-77-generic                         3.13.0-77.121                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-79-generic                         3.13.0-79.123                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-83-generic                         3.13.0-83.127                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-85-generic                         3.13.0-85.129                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-86-generic                         3.13.0-86.131                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-87-generic                         3.13.0-87.133                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-88-generic                         3.13.0-88.135                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-91-generic                         3.13.0-91.138                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-92-generic                         3.13.0-92.139                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-93-generic                         3.13.0-93.140                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-95-generic                         3.13.0-95.142                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-96-generic                         3.13.0-96.143                           i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-generic                                         3.13.0.96.104                           i386         Generic Linux kernel image
ii  linux-libc-dev:i386                                         3.13.0-96.143                           i386         Linux Kernel Headers for development
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu4                    all          base package for ALSA and OSS sound systems 
```

---

### Post by Bashing-om on 2016-10-23
Seventh_Magpie; Welp:

As a reference for how much space is required:
My tiny user space that works very well for my use case:
```

sysop@1404mini:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           396M  780K  395M   1% /run
/dev/sda1       4.7G  2.2G  2.3G  49% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs           2.0G   12K  2.0G   1% /tmp
none            5.0M     0  5.0M   0% /run/lock
none            2.0G   17M  2.0G   1% /run/shm
none            100M  8.0K  100M   1% /run/user
/dev/sda2       9.5G  729M  8.3G   8% /home
/dev/sda8       4.7G  705M  3.8G  16% /var
sysop@1404mini:~$

```

Now in any situation, ya try and put 12 pounds of sugar in a 10 pound bag ,, it ain't gonna fit .
In any OS there is always house cleaning to be done . In all my experience I have never seen a system requiring LESS maintenance and upkeep than that of 'buntu .

Kernels: The system will not decide for you what you want to keep ..  . Up until version 16.10. So we tell the system we do not want those old kernels ( and other orphaned files) .

what results:
```

sudo apt-get autoremove

```

Once we have the head room; we return to libreoffice .

[INDENT][INDENT]small steps still
[INDENT][INDENT][INDENT]get there
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Seventh_Magpie on 2016-10-24
Well. You know what needs to be done and how to do it. :) And I don't. I'm just your average user with average computer knowledge. Hence, I trust the OS to either automatically do what is needed or ask me for my decision. But it neither acts nor asks. :( I've had people screech at me that I haven't cleaned the system since 2014 when I first sought advice on another forum, as if I were a criminal or at least hopelessly stupid. But how were I to know? 
[FONT=arial black]
sudo apt-get autoremove[/FONT] still doesn't work. I've tried it before, I've tried it again. It still gives me this: 

```
 Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:5.2.2) but 1:5.2.1~rc2-0ubuntu1~trusty0 is installed
 tzdata-java : Depends: tzdata (= 2016h-0ubuntu0.14.04) but 2016f-0ubuntu0.14.04 is installed
E: Unmet dependencies. Try using -f. 
```

---

### Post by Bashing-om on 2016-10-24
Seventh_Magpie; Naw ..

Not to know is not a sin - none here were born knowing what we know. There is that process of learning and climbing up that ladder of learning.

As we can not move forward - easily; let's see if we can make the package manager happy .
Try:
```

sudo apt purge libreoffice-common
sudo apt install libreoffice-common

```
with the hope that we have enough head room for the package manager to work in .. and that the re-install picks version " 1:5.2.2-0ubuntu1~trusty0 " from the PPA rather than from the software repository.
Once the package manager is happy - in a consistent state - we return to cleaning up .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by ian-weisser on 2016-10-24
You consumed your inodes with kernel header packages (I stopped counting at 30), because you have the 'linux-headers-generic' metapackage installed.
Use apt to remove all but the current.
That will solve your inode problem and apt should begin to work without a bunch of errors.

Ubuntu does not come with kernel headers by default - you installed them.
Kernel headers are used for compiling your own kernels / modules / kpatch . If that sentence doesn't mean anything to you, then you don't need the headers.
If you don't know why you have kernel headers installed at all, then delete the current one too....and the 'linux-headers-generic' metapackage.
Obviously, if you installed the headers for a reason that you didn't understand or have forgotten, you will soon discover that reason when that something else breaks.

If you decide to keep a small number of headers, then make notes and mark your calendar to clean out those old headers once each year or so.

---

### Post by Seventh_Magpie on 2016-10-24
Hello, Ian 

Everything that's been installed has been installed on the OS cue. I sure am not technically savvy enough to install anything by myself. :)

Could you please advise how do I go about removing those headers?

---

### Post by Seventh_Magpie on 2016-10-24
Hello, Bashing-om 

Your suggestion concerning libreoffice-common didn't work. :( It refuses to purge it, still complains about dependencies. It seems like it has no breathing space at all. Or something.

---

### Post by ian-weisser on 2016-10-24
> **Seventh_Magpie said:**
> Everything that's been installed has been installed on the OS cue. I sure am not technically savvy enough to install anything by myself. :)
Oh, well. Perhaps it won't matter.

> **Seventh_Magpie said:**
> Could you please advise how do I go about removing those headers?
Open a terminal
```
sudo apt remove linux-headers-3.13.0-37 linux-headers-3.13.0-37-generic
```
Repeat for  -39, -40, -43, -44, and the rest of your list.

---

### Post by Seventh_Magpie on 2016-10-24
Thank you, Ian. 

I think I've broken something. :) 

I've removed some headers, and then tried [FONT=arial black]sudo apt -f install [/FONT]again. It worked, and the brick disappeared! LibreOffice seems to work, as well. At least, Writer starts, documents open and save. Shows me it's v. 5.2.2.2, which looks to be the latest released version according to LibreOffice website.

However, when I restated the computer, it gave me the default blue mouse wallpaper with wrong screen resolution, no USB ports and no wi-fi. I restarted it again (having read a lot in the last several days, I know by now about old kernels and why they might be needed :)) and selected the advanced boot option line in GRUB, where it allows to select the previous kernel. Kind of a recovery points system, this list? 

There I saw that the topmost kernel is called **3.13.0-98-generic**. However, when I compare it to my notes I've made of various terminal outputs, I see that just yesterday I had **3.13.0-96-generic**. When I select it, it loads with the same blue mouse standard wallpaper, but with correct screen resolution, and then changes to my custom wallpaper after I log in. All USB ports and wi-fi connections also become active. 

What did I do wrong? Did I somehow corrupt the latest kernel, which must have been in the queue to install when all this jam happened? Can it be fixed? Or removed? Now the OS doesn't want to load correctly via the first line in GRUB. I have to select my yesterday's **3.13.0-96-generic** manually to get to the working desktop. It's doable, of course, but now I have to actively participate in the boot process.

Thank you both guys in advance for your advice.

---

### Post by ian-weisser on 2016-10-24
Well, remember how you would find out what you needed kernel headers for?
I suppose you just discovered you need them for video drivers.
It's a kludgy solution, but some hardware makers are like that.

'removed some headers' is rather vague. Did you remove all?
Did you remove the -96 headers?
Did you remove the -98 headers?

Retain (or reinstall) the -98 headers, and then try:
```
sudo apt install --reinstall linux-image-3.13.0-98-generic
```
...and see if booting works any better.

---

### Post by Seventh_Magpie on 2016-10-24
It's a 10 year old netbook on Atom. I cannot afford a new one at the moment. That's partly the reason why I'm using Xubuntu. :) It's in dual boot with Windows XP, which is not supported anymore. Even Dropbox stopped working on it. And Xubuntu works good on this old machine, looks nice and has sliding panels that I love. :)

I didn't touch the 90-ies headers. In fact, I didn't touch anything above 50-ies. I'm wary of touching anything fresher than 2015. :)

ETA: No, reinstalling didn't help. It boots with wrong screen resolution and without USB ports and wi-fi.

---

### Post by Bashing-om on 2016-10-25
Seventh_Magpie; welp ....

Seems we will need the header files for the respective drivers to build ; in addition to the other problems.

So what now is the system's situation ?
What returns:
```

df -h
df -i
dpkg -l | grep linux-
apt-cache policy libreoffice
apt-cache policy libreoffice-common

```
to get a new idea of what we need to do .

[INDENT]still after all
[INDENT][INDENT][INDENT]a work in progress
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Seventh_Magpie on 2016-10-26
Hello Bashing-om! 

Sorry for being absent yesterday, real life interfered. 

So. Today a new update came via the now functioning Package Manager. It had a new kernel called 3.13.0-100-generic. I let it install itself, restarted the computer, and it's loaded correctly with this new kernel. Don't know what wrong was with the previous unlucky kernel, but it's fixed now. 

However, I'm back at square one concerning inodes. Everything that I've fought tooth and nail to free up has been eaten by the new update.

[FONT=arial black]df -h[/FONT]
```
Filesystem      Size  Used Avail Use% Mounted on
udev            994M  4,0K  994M   1% /dev
tmpfs           201M  1,1M  200M   1% /run
/dev/sda5        20G   15G  3,9G  80% /
none            4,0K     0  4,0K   0% /sys/fs/cgroup
none            5,0M     0  5,0M   0% /run/lock
none           1003M  152K 1003M   1% /run/shm
none            100M   36K  100M   1% /run/user
/dev/sda7        47G   13G   32G  28% /home
/dev/sda3        50G  3,5G   47G   7% /media/data
```

[FONT=arial black]df -i[/FONT]
```
Filesystem       Inodes   IUsed    IFree IUse% Mounted on
udev             214907     510   214397    1% /dev
tmpfs            219716     512   219204    1% /run
/dev/sda5       1310720 1309452     1268  100% /
none             219716       2   219714    1% /sys/fs/cgroup
none             219716       3   219713    1% /run/lock
none             219716       7   219709    1% /run/shm
none             219716      31   219685    1% /run/user
/dev/sda7       3088384   31214  3057170    2% /home
/dev/sda3      48849992    2695 48847297    1% /media/data 
```

The forum doesn't allow me to post complete output of [FONT=arial black]dpkg -l | grep linux[/FONT]-. I've saved it as a text file and put in Dropbox: [https://dl.dropboxusercontent.com/u/11756316/dpkg%20-l%20grep%20linux-.txt](https://dl.dropboxusercontent.com/u/11756316/dpkg%20-l%20grep%20linux-.txt)

[FONT=arial black]apt-cache policy libreoffice[/FONT]
```
libreoffice:
  Installed: 1:5.2.2-0ubuntu1~trusty0
  Candidate: 1:5.2.2-0ubuntu1~trusty0
  Version table:
 *** 1:5.2.2-0ubuntu1~trusty0 0
        500 [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/) trusty/main i386 Packages
        100 /var/lib/dpkg/status
     1:4.2.8-0ubuntu4 0
        500 [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) trusty-updates/universe i386 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/universe i386 Packages
     1:4.2.3~rc3-0ubuntu2 0
        500 [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) trusty/universe i386 Packages 
```

[FONT=arial black]apt-cache policy libreoffice-common[/FONT]
```
libreoffice-common:
  Installed: 1:5.2.2-0ubuntu1~trusty0
  Candidate: 1:5.2.2-0ubuntu1~trusty0
  Version table:
 *** 1:5.2.2-0ubuntu1~trusty0 0
        500 [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/) trusty/main i386 Packages
        100 /var/lib/dpkg/status
     1:4.2.8-0ubuntu4 0
        500 [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) trusty-updates/main i386 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main i386 Packages
     1:4.2.3~rc3-0ubuntu2 0
        500 [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) trusty/main i386 Packages 
```

---

### Post by Bashing-om on 2016-10-26
Seventh_Magpie; Well ....

libreoffice is now in a happy state .. no more worries there .

Let's see what we can do - easily -:
```

sudo apt-get autoremove

```
which I can accept will fail, mainly again no operating head room .. but worth the try for an easy way out .

[INDENT][INDENT]we try NOT to make it tougher
[/INDENT][/INDENT]

---

### Post by Seventh_Magpie on 2016-10-28
Hello Bashing-om! 

[FONT=arial black]sudo apt-get autoremove [/FONT]didn't fail. It Offered to remove libreoffice-gtk, which was used by the previous version of LO, and also offered to remove the previous [damaged] kernel. 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libreoffice-gtk linux-image-3.13.0-98-generic
0 upgraded, 0 newly installed, 2 to remove and 10 not upgraded.
After this operation, 33,2 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 1293020 files and directories currently installed.)
Removing libreoffice-gtk (1:5.2.2-0ubuntu1~trusty0) ...
Removing linux-image-3.13.0-98-generic (3.13.0-98.145) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-98-generic /boot/vmlinuz-3.13.0-98-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-98-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-98-generic /boot/vmlinuz-3.13.0-98-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-100-generic
Found initrd image: /boot/initrd.img-3.13.0-100-generic
Found linux image: /boot/vmlinuz-3.13.0-96-generic
Found initrd image: /boot/initrd.img-3.13.0-96-generic
Found linux image: /boot/vmlinuz-3.13.0-95-generic
Found initrd image: /boot/initrd.img-3.13.0-95-generic
Found linux image: /boot/vmlinuz-3.13.0-93-generic
Found initrd image: /boot/initrd.img-3.13.0-93-generic
Found linux image: /boot/vmlinuz-3.13.0-92-generic
Found initrd image: /boot/initrd.img-3.13.0-92-generic
Found linux image: /boot/vmlinuz-3.13.0-91-generic
Found initrd image: /boot/initrd.img-3.13.0-91-generic
Found linux image: /boot/vmlinuz-3.13.0-88-generic
Found initrd image: /boot/initrd.img-3.13.0-88-generic
Found linux image: /boot/vmlinuz-3.13.0-87-generic
Found initrd image: /boot/initrd.img-3.13.0-87-generic
Found linux image: /boot/vmlinuz-3.13.0-86-generic
Found initrd image: /boot/initrd.img-3.13.0-86-generic
Found linux image: /boot/vmlinuz-3.13.0-85-generic
Found initrd image: /boot/initrd.img-3.13.0-85-generic
Found linux image: /boot/vmlinuz-3.13.0-83-generic
Found initrd image: /boot/initrd.img-3.13.0-83-generic
Found linux image: /boot/vmlinuz-3.13.0-79-generic
Found initrd image: /boot/initrd.img-3.13.0-79-generic
Found linux image: /boot/vmlinuz-3.13.0-77-generic
Found initrd image: /boot/initrd.img-3.13.0-77-generic
Found linux image: /boot/vmlinuz-3.13.0-76-generic
Found initrd image: /boot/initrd.img-3.13.0-76-generic
Found linux image: /boot/vmlinuz-3.13.0-74-generic
Found initrd image: /boot/initrd.img-3.13.0-74-generic
Found linux image: /boot/vmlinuz-3.13.0-71-generic
Found initrd image: /boot/initrd.img-3.13.0-71-generic
Found linux image: /boot/vmlinuz-3.13.0-68-generic
Found initrd image: /boot/initrd.img-3.13.0-68-generic
Found linux image: /boot/vmlinuz-3.13.0-67-generic
Found initrd image: /boot/initrd.img-3.13.0-67-generic
Found linux image: /boot/vmlinuz-3.13.0-66-generic
Found initrd image: /boot/initrd.img-3.13.0-66-generic
Found linux image: /boot/vmlinuz-3.13.0-65-generic
Found initrd image: /boot/initrd.img-3.13.0-65-generic
Found linux image: /boot/vmlinuz-3.13.0-63-generic
Found initrd image: /boot/initrd.img-3.13.0-63-generic
Found linux image: /boot/vmlinuz-3.13.0-62-generic
Found initrd image: /boot/initrd.img-3.13.0-62-generic
Found linux image: /boot/vmlinuz-3.13.0-61-generic
Found initrd image: /boot/initrd.img-3.13.0-61-generic
Found linux image: /boot/vmlinuz-3.13.0-59-generic
Found initrd image: /boot/initrd.img-3.13.0-59-generic
Found linux image: /boot/vmlinuz-3.13.0-58-generic
Found initrd image: /boot/initrd.img-3.13.0-58-generic
Found linux image: /boot/vmlinuz-3.13.0-57-generic
Found initrd image: /boot/initrd.img-3.13.0-57-generic
Found linux image: /boot/vmlinuz-3.13.0-55-generic
Found initrd image: /boot/initrd.img-3.13.0-55-generic
Found linux image: /boot/vmlinuz-3.13.0-54-generic
Found initrd image: /boot/initrd.img-3.13.0-54-generic
Found linux image: /boot/vmlinuz-3.13.0-53-generic
Found initrd image: /boot/initrd.img-3.13.0-53-generic
Found linux image: /boot/vmlinuz-3.13.0-52-generic
Found initrd image: /boot/initrd.img-3.13.0-52-generic
Found linux image: /boot/vmlinuz-3.13.0-51-generic
Found initrd image: /boot/initrd.img-3.13.0-51-generic
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-48-generic
Found initrd image: /boot/initrd.img-3.13.0-48-generic
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda1
Found Microsoft Windows XP Home Edition RU on /dev/sda2
done
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
```

After I restarted the computer, I checked via [FONT=arial black]df -i[/FONT] and saw that the space on /dev/sda5 has increased slightly. Although it's still 100%. 

Also, after the restart the Package Manager informed me of lots of updates, including updates to LibreOffice. I'm afraid to install them now, to be honest. :)

---

### Post by ian-weisser on 2016-10-28
Keep removing obsolete kernel headers.
That's still the cause of your inode problems, which is in turn the cause of your upgrade failures.

---

### Post by Seventh_Magpie on 2016-10-28
I'm a bit afraid to remove anymore headers, following the previous issue with the kernel. Also, as far as I understand, there are several connected things: the header, the generic kernel image, the extra kernel image and something else. Is there maybe a way to take this whole bunch at once and remove it together? I don't think that kernels from 2014 will be needed anyway.

---

### Post by vasa1 on 2016-10-28
Would you mind posting the output of ```
dpkg -l | grep -i linux-
``` as an update to where you stand?

```
dpkg -l | grep -Ei 'linux-(g|h|i)'
```maybe cleaner.

And re.> Also, as far as I understand, there are several connected things: the header, the generic kernel image, the extra kernel image and something else. Is there maybe a way to take this whole bunch at once and remove it together?my last kernel update brought me```
linux-image-4.4.0-45-generic:amd64 (4.4.0-45.66, automatic), 
linux-headers-4.4.0-45:amd64 (4.4.0-45.66, automatic), 
linux-image-extra-4.4.0-45-generic:amd64 (4.4.0-45.66, automatic), 
linux-headers-4.4.0-45-generic:amd64 (4.4.0-45.66, automatic)

```so I'm guessing that's four kernel-related files each time.

---

### Post by ian-weisser on 2016-10-29
> **Seventh_Magpie said:**
> I'm a bit afraid to remove anymore headers, following the previous issue with the kernel.
That was most likely due to an install failure caused by your lack of available inodes, not due to the removal of ancient headers...which have no interaction with recent kernels.
Again, you will continue to suffer these problems until you remove all those old headers. They are the apparent cause of your lack of available inodes.

> **Seventh_Magpie said:**
> Is there maybe a way to take this whole bunch at once and remove it together? 
You already know how to tell apt to remove more than one package at at time. You have done it already. Simply remove all four packages at once....
```
sudo apt remove linux-headers-3.1.0-37 linux-headers-3.13.0-37-generic linux-image-generic-3.13.0-37 linux-image-extra-generic-3.13.0-37
```

---

### Post by Seventh_Magpie on 2016-11-02
Thank you, Ian. I've deleted several kernels with headers and some space has freed up. I'll proceed carefully.

---

