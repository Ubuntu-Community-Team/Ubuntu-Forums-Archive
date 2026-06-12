---
title: "freeing up disk space &amp; follow-up"
date: 2015-02-25
forum: Installation &amp; Upgrades
---

### Post by David2009 on 2015-02-25
Bottom Line Up Front: Updating worked, but what did I do?

Hello.  I have been using Ubuntu 14.04 LTS for a couple of months.

I used the Updater program today, and got the following message:
 
The upgrade needs a total of 79.9 M free space on disk '/boot'. Please free at least an additional 9,311 k of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

I went to a terminal window and ran the sudo apt-get clean.  Next I returned to the Updater, and got the same error message.

So, I kept reading in various posts, and found a lady who suggested that a particular command helps out lots of people.  So, I ran the suggested command:
 
sudo apt-get autoremove –purge

I returned to the Updater, ran it, and it looks like the "purge" command worked, since I was able to install the updates.  

- Can someone tell me what I did to the computer with these commands? 
- I have 310 GB on my hard drive, with 6 GB used.
- I "right clicked" on Computer, and 6 GB of the pie is in blue, there is another section in grey, and the majority is in white.  Is the grey section the OS?

Thank you for your help.

David

---

### Post by JKyleOKC on 2015-02-25
Your "sudo apt-get autoremove &#8211;purge" command removed all packages that were no longer needed, and also their configuration files. Without the "--purge" argument, it would have removed the packages but left the configuration files in place for possible future use.

The most usual cause of your original problem is having too many outdated copies of the kernel itself in the /boot directory; "autoremove" doesn't affect these so they are probably still there. Post the result of "ls -l /boot" here and we can tell you how to get rid of those as well. You only need two copies -- the current kernel and the one immediately prior to it -- on the drive; the rest can go away.

Hope this helps!

---

### Post by ajgreeny on 2015-02-25
It sounds as if you have a separate /boot partition which was filled with old kernels which were then removed by the autoremove command.

Do you run an encrypted system or use LVM partitions?  If not a separate /boot partition is not needed and causes this type of problem too often.  It is too late to do much now but next time you install Ubuntu leave /boot in the root partition, unless using encryption or LVM, when /boot is made for you.

Let's see the output of **df -hT** in terminal please which will show the partitions and their space usage.

---

### Post by David2009 on 2015-02-25
Jim,

Thank you for the quick reply.  I ran the ls -l/boot, and here are the results:

total 153148
-rw-r--r-- 1 root root  1164720 Dec  8 14:28 abi-3.13.0-43-generic
-rw-r--r-- 1 root root  1164720 Dec 15 19:17 abi-3.13.0-44-generic
-rw-r--r-- 1 root root  1164967 Jan 13 14:12 abi-3.13.0-45-generic
-rw-r--r-- 1 root root  1164852 Feb 10 10:00 abi-3.13.0-46-generic
-rw-r--r-- 1 root root   165745 Dec  8 14:28 config-3.13.0-43-generic
-rw-r--r-- 1 root root   165748 Dec 15 19:17 config-3.13.0-44-generic
-rw-r--r-- 1 root root   165748 Jan 13 14:12 config-3.13.0-45-generic
-rw-r--r-- 1 root root   165748 Feb 10 10:00 config-3.13.0-46-generic
drwxr-xr-x 5 root root     1024 Feb 25 08:58 grub
-rw-r--r-- 1 root root 28366487 Dec 31 09:30 initrd.img-3.13.0-43-generic
-rw-r--r-- 1 root root 28368342 Jan 15 07:03 initrd.img-3.13.0-44-generic
-rw-r--r-- 1 root root 28375918 Feb 21 14:07 initrd.img-3.13.0-45-generic
-rw-r--r-- 1 root root 28382877 Feb 25 08:57 initrd.img-3.13.0-46-generic
drwx------ 2 root root    12288 Dec 31 08:49 lost+found
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  3388760 Dec  8 14:28 System.map-3.13.0-43-generic
-rw------- 1 root root  3388834 Dec 15 19:17 System.map-3.13.0-44-generic
-rw------- 1 root root  3389258 Jan 13 14:12 System.map-3.13.0-45-generic
-rw------- 1 root root  3389458 Feb 10 10:00 System.map-3.13.0-46-generic
-rw------- 1 root root  5814080 Dec  8 14:28 vmlinuz-3.13.0-43-generic
-rw------- 1 root root  5814496 Dec 15 19:17 vmlinuz-3.13.0-44-generic
-rw------- 1 root root  5814112 Jan 13 14:12 vmlinuz-3.13.0-45-generic
-rw------- 1 root root  5814528 Feb 10 10:00 vmlinuz-3.13.0-46-generic

---

### Post by David2009 on 2015-02-25
When I did the original installation of Ubuntu I did use the encryption option.  Did not know what it would do for me, but it sounds like a good option.

Here are the results from df -hT:

Filesystem                  Type      Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root ext4      290G  5.7G  269G   3% /
none                        tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
udev                        devtmpfs  2.0G  4.0K  2.0G   1% /dev
tmpfs                       tmpfs     396M  1.1M  395M   1% /run
none                        tmpfs     5.0M     0  5.0M   0% /run/lock
none                        tmpfs     2.0G  192K  2.0G   1% /run/shm
none                        tmpfs     100M   32K  100M   1% /run/user
/dev/sda1                   ext2      236M  156M   68M  70% /boot
/home/david/.Private        ecryptfs  290G  5.7G  269G   3% /home/david

---

### Post by dino99 on 2015-02-25
hello David
usually you only need 2 kernels installed: the latest pushed by "upgrade" script, and the previous good one (in case of trouble with the latest)

but also clean the system to get it running smoothly:
- sudo apt-get clean
- sudo apt-get autoclean
- sudo apt-get autoremove

you also can wipe the "orphans" with "gtkorphan" (if you run gnome or unity) and/or "bleachbit" (install "synaptic" and see the package description); "localepurge" can be usefull to remove all the languages you dont care about; "ubuntu-desktop" can also be safely removed, to let you uninstall some apps you never use ):P

---

### Post by Bashing-om on 2015-02-25
David2009; Hi !

You are the victim of this condition:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093)
/boot created to small.

You are encouraged to add your voice to the report.
In the meantime, did "autoremove" not free up some space ? Since 13.10 release 'autoremove' has been revamped to also remove old kernels.
If the package manager (autoremove) does not have the operating head room, we will have to give the package manager a helping hand. We can do that.
```

dpkg -l | grep linux-

```
to see what there is yet to be done.

[INDENT][INDENT]regretful this situation arises
[INDENT][INDENT][INDENT]the good news is that is is fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by JKyleOKC on 2015-02-25
> **David2009 said:**
> Jim,

Thank you for the quick reply.  I ran the ls -l/boot, and here are the results:

total 153148
[B]-rw-r--r-- 1 root root  1164720 Dec  8 14:28 abi-3.13.0-43-generic
-rw-r--r-- 1 root root  1164720 Dec 15 19:17 abi-3.13.0-44-generic
[/B]-rw-r--r-- 1 root root  1164967 Jan 13 14:12 abi-3.13.0-45-generic
-rw-r--r-- 1 root root  1164852 Feb 10 10:00 abi-3.13.0-46-generic
[B]-rw-r--r-- 1 root root   165745 Dec  8 14:28 config-3.13.0-43-generic
-rw-r--r-- 1 root root   165748 Dec 15 19:17 config-3.13.0-44-generic[/B]
-rw-r--r-- 1 root root   165748 Jan 13 14:12 config-3.13.0-45-generic
-rw-r--r-- 1 root root   165748 Feb 10 10:00 config-3.13.0-46-generic
drwxr-xr-x 5 root root     1024 Feb 25 08:58 grub
[B]-rw-r--r-- 1 root root 28366487 Dec 31 09:30 initrd.img-3.13.0-43-generic
-rw-r--r-- 1 root root 28368342 Jan 15 07:03 initrd.img-3.13.0-44-generic
[/B]-rw-r--r-- 1 root root 28375918 Feb 21 14:07 initrd.img-3.13.0-45-generic
-rw-r--r-- 1 root root 28382877 Feb 25 08:57 initrd.img-3.13.0-46-generic
drwx------ 2 root root    12288 Dec 31 08:49 lost+found
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
[B]-rw------- 1 root root  3388760 Dec  8 14:28 System.map-3.13.0-43-generic
-rw------- 1 root root  3388834 Dec 15 19:17 System.map-3.13.0-44-generic
[/B]-rw------- 1 root root  3389258 Jan 13 14:12 System.map-3.13.0-45-generic
-rw------- 1 root root  3389458 Feb 10 10:00 System.map-3.13.0-46-generic
[B]-rw------- 1 root root  5814080 Dec  8 14:28 vmlinuz-3.13.0-43-generic
-rw------- 1 root root  5814496 Dec 15 19:17 vmlinuz-3.13.0-44-generic
[/B]-rw------- 1 root root  5814112 Jan 13 14:12 vmlinuz-3.13.0-45-generic
-rw------- 1 root root  5814528 Feb 10 10:00 vmlinuz-3.13.0-46-genericAs others have noted, you have surplus kjernels in the /boot directory. You can delete all of those that I've marked by boldface in the quote above and make plenty of space for future updates.

I use a third-party tweaking package that can handle such matters automagically, but I'm not sure that it works with all the latest versions. Others have mentioned "bleachbit" which can do the job, but be very cautious about its use and make sure that it doesn't remove anything essential. I've seen a number of problems mentioned in the forums here but have never used it myself.

Any time a kernel gets updated, you should repeat this exercise and make sure that you keep only the two most recent versions. The newest, of course, is the reason for the update, and the previous one is for emergencies if the newer one fails to work properly for you. Only once in the past seven years have I needed to fall back to an older kernel, but that time it saved me from having to do a full re-install!

---

### Post by JKyleOKC on 2015-02-25
> **David2009 said:**
> When I did the original installation of Ubuntu I did use the encryption option.  Did not know what it would do for me, but it sounds like a good option.If you're as paranoid as most of us who have been around are, about invasion of privacy, then the encryption is indeed a good option. However, it can make recovery from any sort of major disaster almost impossible, because any damage to the encryption software itself can result in total loss of **all** of your data -- photos, movies, music, email, everything! Bottom line: since you chose to encrypt, be sure to back up **everything** that you want to keep forever, and put it onto a separate drive if not a totally separate computer. Do this every time your irreplaceable data changes. Even though I'm not encrypting anything here, I do back up my email files every three days, and have all my photos stored on three different machines. At one time I used a commercial off-site backup service, but that finally got too slow to keep up with the size of my photo files...

---

### Post by David2009 on 2015-02-25
I gave those three SUDOs a try:
 
- sudo apt-get clean
- sudo apt-get autoclean
- sudo apt-get autoremove

david@david-Satellite-A305:~$ - sudo apt-get clean
-: command not found
david@david-Satellite-A305:~$ - sudo apt-get autoclean
-: command not found
david@david-Satellite-A305:~$ - sudo apt-get autoremove
-: command not found

I'll have to read up on the bleachbit & localepurge.  I may have some time tomorrow.  

Thank you for your help!

David

---

### Post by David2009 on 2015-02-25
I clicked on the link, and read many of the comments.  I really don't think I know enough to add my voice.  

Yes, autoremove did free up enough space for the latest updates.  That was great news!

Is there another step to take?

I just ran "dpkg -l | grep linux-".  Here's the output:
 
ii  linux-firmware                                        1.127.11                                            all          Firmware for Linux kernel drivers
ii  linux-generic                                         3.13.0.46.53                                        amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-43                               3.13.0-43.72                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-43-generic                       3.13.0-43.72                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-44                               3.13.0-44.73                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-44-generic                       3.13.0-44.73                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-45                               3.13.0-45.74                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-45-generic                       3.13.0-45.74                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-46                               3.13.0-46.75                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-46-generic                       3.13.0-46.75                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.46.53                                        amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-43-generic                         3.13.0-43.72                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-44-generic                         3.13.0-44.73                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-45-generic                         3.13.0-45.74                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-46-generic                         3.13.0-46.75                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-43-generic                   3.13.0-43.72                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-44-generic                   3.13.0-44.73                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-45-generic                   3.13.0-45.74                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-46-generic                   3.13.0-46.75                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                   3.13.0.46.53                                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-46.75                                        amd64        Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies

---

### Post by David2009 on 2015-02-25
Hi, Jim.

How do I edit the file (and which file) to delete the old kernals?  

How frequently are new versions pushed?

Thank you.

David

---

### Post by David2009 on 2015-02-25
> **JKyleOKC said:**
> 
I use a third-party tweaking package that can handle such matters automagically, but I'm not sure that it works with all the latest versions. Others have mentioned "bleachbit" which can do the job, but be very cautious about its use and make sure that it doesn't remove anything essential. I've seen a number of problems mentioned in the forums here but have never used it myself.



I just installed BLEACHBIT, but was unsure of how to configure it before running the program.  So, I'll look around tomorrow to see options for its configuration.

Thank you.

David

---

### Post by mörgæs on 2015-02-26
> **David2009 said:**
> I gave those three SUDOs a try:
 
- sudo apt-get clean
- sudo apt-get autoclean
- sudo apt-get autoremove

david@david-Satellite-A305:~$ - sudo apt-get clean
-: command not found
david@david-Satellite-A305:~$ - sudo apt-get autoclean
-: command not found
david@david-Satellite-A305:~$ - sudo apt-get autoremove
-: command not found

I'll have to read up on the bleachbit & localepurge.  I may have some time tomorrow.  

Thank you for your help!

David

There is no dash in front of the commands.
When posting terminal output please use CODE tags.

---

### Post by David2009 on 2015-02-26
Thank you for the reply.  I ran the sudo commands without the dash in front.

Here is what I got for output:
 
david@david-Satellite-A305:~$ sudo apt-get clean
david@david-Satellite-A305:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
david@david-Satellite-A305:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
david@david-Satellite-A305:~$ 

Is there something else I need to do, especially in reference to the 13 not upgraded?

Thank you.

David

---

### Post by spronkc on 2015-02-26
I am getting the same results as David using the same commands.  I get a message I cannot update as I have only 59 Meg of disk space, and I need 81 Meg.

The sudo apt-get clean and the other variations does nothing to free up the disc space.

---

### Post by David2009 on 2015-02-26
The autoremove command did remove enough space, and I was able to put on the updates yesterday.
 
sudo apt-get autoremove &#8211;purge

Good luck!

David

---

### Post by Bashing-om on 2015-02-26
@David2009; Hey ;

Look'n better .
this:
> 
 0 to remove and 13 not upgraded.

says in effect to run:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
As 'apt-get install' only updates installed packages and will not install new stuff; 'dist-upgrade' will take care of the new packages install. ( has no relation to a release-upgrade).

@spronkc; Hello;

Maybe you are running 12.04 ? The ability of 'autoremove' has not been backported to support the older release.
What returns:
```

lsb-release -a
uname -r
dpkg -l | grep linux-

```
To indicate what we can do and what there is to do,

[INDENT][INDENT]ain't nothing but things
[/INDENT][/INDENT]

---

### Post by spronkc on 2015-02-26
I found a link in Launchpad.  Sent me to this thread which has been marked as "Solved".

[http://ubuntuforums.org/showthread.php?t=2240240](http://ubuntuforums.org/showthread.php?t=2240240)

The command that worked for me was 


sudo apt-get dist-upgrade

There were a few errors along the way, but in the end I am properly updated.

---

### Post by spronkc on 2015-02-26
cornelis@cornelis-OptiPlex-755:~$ df -hTFilesystem                  Type      Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root ext4      145G   11G  127G   8% /
none                        tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
udev                        devtmpfs  1.5G  4.0K  1.5G   1% /dev
tmpfs                       tmpfs     297M  1.2M  296M   1% /run
none                        tmpfs     5.0M     0  5.0M   0% /run/lock
none                        tmpfs     1.5G   16M  1.5G   2% /run/shm
none                        tmpfs     100M   48K  100M   1% /run/user
/dev/sda1                   ext2      236M  208M   16M  94% /boot
/home/cornelis/.Private     ecryptfs  145G   11G  127G   8% /home/cornelis

I am concerned about the ext2 memory being 94% full.

I was also surprised to use the dist-upgrade command.  It seemed to have done the job as a sort of work around.

---

### Post by Bashing-om on 2015-02-26
@spronkc; well ;

see:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093)
and add your voice to the report.
This:
> 
/dev/sda1 ext2 236M 208M 16M 94% /boot

with only 16M available says you have not done enough- it takes +120Mb of space per kernel -, I bet there are still old kernels residing on the system.

As noted above, 'dist-upgrade' has done nothing to resolve the underlying problem of removing old kernels to gain back the space in /boot.
IF "apt-get autoremove" does not have the operating head room, then will not function, then one must resort to an application of 'dpkg' to remove the superfluous kernels.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by spronkc on 2015-02-26
Found another thread.  Gives a rather complex command, but using the copy and paste, I got my boot memory from 94% down to 38%.

It was suggested that I will need to run this comment periodically to free up enough boot space to allow updates into the small memory allocated to it.

[http://ubuntuforums.org/showthread.php?t=2256490&highlight=resize+boot+partition](http://ubuntuforums.org/showthread.php?t=2256490&highlight=resize+boot+partition)

---

### Post by Bashing-om on 2015-02-26
@spronkc; Good deal.

Yepper, will have to keep an eye on /boot.

> **spronkc said:**
> Found another thread.  Gives a rather complex command, but using the copy and paste, I got my boot memory from 94% down to 38%.

It was suggested that I will need to run this comment periodically to free up enough boot space to allow updates into the small memory allocated to it.

[http://ubuntuforums.org/showthread.php?t=2256490&highlight=resize+boot+partition](http://ubuntuforums.org/showthread.php?t=2256490&highlight=resize+boot+partition)

IF you are running 14.04 and above, 'autoremove' at a timely time will take care of those old kernels. 

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

