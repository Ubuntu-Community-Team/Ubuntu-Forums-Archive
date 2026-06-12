---
title: "Feisty install problems, error 15"
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by Evegan on 2007-06-07
So I loaded up the Cd and installed everything, but once I rebooted the computer I got this error message:

--Grub loading, please wait
--Error 15

What did I do wrong? It won't move past this point. Nor will it load up my old Hoary. At the moment I'm running this from the Live CD. 

Any ideas?

Thanks
Evan

---

### Post by Evegan on 2007-06-07
Also, when I first tried to install Feisty I was told that "no file directory" could be found. The last time I tried everything went through fine, except the error 15 message. 

Evan

---

### Post by autocrosser on 2007-06-07
I've had that problem a couple of times--when grub updated & "found" the wrong drive to boot from. Fire up a LiveCD & mount your install--goto /boot/grub/menu.lst & look to see what it's trying to boot root from. Chances are that if you boot from hd0,1--you'll find it says hd1,0. Edit for your correct boot location & try a reboot.....

---

### Post by confused57 on 2007-06-07
Here's how to mount your root partition with the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

Here's a description of grub error 15 & possible solutions:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#15](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#15)

You might want to burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it's a small download(5-7Mb) & may be able to boot your Ubuntu or Windows

---

### Post by Evegan on 2007-06-07
#1 - how do I get to a terminal from the Live CD? -- nevermind, just saw it, duh.

#2 - I opened up the Partition Manager and it looks like this:

/dev/sda1    ext3           36.56GiB       2.69GiB   33.87GiB   boot
/dev/sda2    extended    721.67MiB
   /dve/sda5 linux-swap  721.64MiB

I'm assuming that the sda1 is the Hard Drive?


Does all this mean something?

Evan

---

### Post by confused57 on 2007-06-07
> **Evegan said:**
> #1 - how do I get to a terminal from the Live CD? -- nevermind, just saw it, duh.

#2 - I opened up the Partition Manager and it looks like this:

/dev/sda1    ext3           36.56GiB       2.69GiB   33.87GiB   boot
/dev/sda2    extended    721.67MiB
   /dve/sda5 linux-swap  721.64MiB

I'm assuming that the sda1 is the Hard Drive?


Does all this mean something?

Evan
IF you have internet access when you boot the live cd, copy & paste the output of:
```
sudo fdisk -l
```
the -l is a small "L"

If you don't have internet access, you need to mount your root partition in the live cd, from a terminal:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
gedit /media/ubuntu/boot/grub/menu.lst
```
post the line that begins with root in your OS boot entries & the root entry in your kernel line(copy & paste, if you have internet access in the live cd).

---

### Post by Evegan on 2007-06-08
sudo fdisk -l got me this:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4773    38339091   83  Linux
/dev/sda2            4774        4865      738990    5  Extended
/dev/sda5            4774        4865      738958+  82  Linux swap / Solaris

-------------------------------------------------------------------------
Next:

ubuntu@ubuntu:~$ sudo mkdir /media/ubuntu
mkdir: cannot create directory `/media/ubuntu': File exists
ubuntu@ubuntu:~$ sudo mount -t est3 /dev/sda1 /media/ubuntu
mount: unknown filesystem type 'est3'
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 /media/ubuntu
mount: /dev/sda1 already mounted or /media/ubuntu busy
mount: according to mtab, /dev/sda1 is already mounted on /media/ubuntu
ubuntu@ubuntu:~$ gedit /media/ubuntu/boot/grub/menu.lst

Nothing happens at this point, it just pops up the "ubuntu@ubuntu:~$" line and that's it.

Also, how do I burn the Super Grub to CD if I'm running off the Live CD right now?

Evan

---

### Post by Evegan on 2007-06-08
I'm going to try and set up the install manually once I get home tonight. We'll see if that works out. Otherwise, I downloaded and burned a copy of the Super Grub disk. Once I get Ubuntu up, hopefully, how do I figure out what is missing and what needs to be fixed?

Thanks for all the help.

Evan

---

### Post by Evegan on 2007-06-09
OK, more help please. I burned a copy of the Super Grub Disk but still wasn't able to boot ubuntu. From the Live CD, in terminal, I ran "ls /boot" and it got this:

[I]ubuntu@ubuntu:~$ ls /boot
abi-2.6.20-15-generic             memtest86+.bin
config-2.6.20-15-generic          System.map-2.6.20-15-generic
initrd.img-2.6.20-15-generic.bak  vmlinuz-2.6.20-15-generic[/I]

From the Super Grub page I realized the "vmlinuz-2.6.20-15-generic" should be **vmlinux** rather than **vmlinuz**. So how do I fix this typo? Could this be causing my boot problems? The grub pages says to:

[I]"Boot with Super Grub Disk instead, and then with your operating system running you can check your file and correct your menu entry for Linux.
Open your menu.lst file with 'sudo gedit /boot/grub/menu.lst', if you are using Ubuntu Linux.
Use the command 'ls /boot' to check for the correct name for your Linux kernel and initrd.img.
Copy the correct name from the terminal output to the text file and paste it to avoid typos. Don't forget to save the changes in your menu.lst file before your close it."[/I] 

But since I'm still unable to get ubuntu up and running is there anyway to fix this error in the Live CD?

Also, if I enter "ls /grub" it says *"no file such file or directory"*

I'm doing something wrong here, but I don't know what it is.

Evan

---

### Post by Evegan on 2007-06-09
Using the SGD, I tried to boot linux/gnu directly and it returned this to me:

[I]set out_file=/vmlinuz
back
set kernel_device=(hd0,0)
set kernel_file=vmlinuz
set kernel_bug=sd
set kernel_end=a1
set choose_title="choose initrd"
selectfile /boot/initrd.img /initrd.img
Error 15: file not found
Press any key to continue[/I]

So, I went back and selected "Fix boot of linux/gnu" and got this:

[I]selectfile /grub/stage1/boot/grub/stage1
Error 15: file not found
Booting "NOT lucky"

pause SGD has **NOT** succeeded :(
SGD has **NOT** succeeded :([/I]

Again, something has gone wrong with my install and I don't know how to fix it. Please help.

Evan

---

### Post by confused57 on 2007-06-09
Boot up the live cd, open a terminal & see what the output of this is:
```
sudo grub
find /boot/grub/stage1
```

type "quit", with quotes to exit the grub prompt

---

### Post by Evegan on 2007-06-09
I did that, returned that it could not be found/did not exist.

I went through some steps I found to install grub from a live CD but that failed as well.

Any ideas?

I also posted that there is a typo in the vmlinux line (see above post). Could that be keeping the OS from booting? If so, how can I change it if I can only access the live cd?

Evan

---

### Post by confused57 on 2007-06-09
> **Evegan said:**
> I did that, returned that it could not be found/did not exist.

I went through some steps I found to install grub from a live CD but that failed as well.

Any ideas?

I also posted that there is a typo in the vmlinux line (see above post). Could that be keeping the OS from booting? If so, how can I change it if I can only access the live cd?

Evan
It seems for some reason, grub isn't installing correctly.  When you did "ls /boot", it was showing the kernel in the live cd, and it should be vmlinuz.

Try mounting your Ubuntu linux root partition again, using the live cd...once you have it mounted, then open nautilus, click on filesystem, open your boot directory, then open grub directory...see if there is a menu.lst file in the grub directory.


Added:  You might want to try using the alternate install cd, if you have access to another pc that you can download & burn a copy...might be a waste of time, I don't know for sure.

You might try using the grub CLI to investigate your computer, type sudo grub in a terminal, then follow these instructions:
[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_get_GRUBs_Command_Line_to_investigate_a_computer](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_get_GRUBs_Command_Line_to_investigate_a_computer)

Read further down in this link about chrooting into your root partition(sda1):
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
might be worth a try...if the instructions don't work, as described, once you're chrooted into your root partition, try:
```
sudo grub-install /dev/sda
```

---

### Post by Evegan on 2007-06-09
So it should say "vmlinuz," OK. 

Just so I'm clear could you explain how to re-mount the linux root partition? Do I do this from the *"Install"* wizard thing or should I be doing this via a terminal?

Side note - do you wanna come to greensboro and get paid to put this on my computer? 

Thanks

Evan

---

### Post by confused57 on 2007-06-09
> **Evegan said:**
> So it should say "vmlinuz," OK. 

Just so I'm clear could you explain how to re-mount the linux root partition? Do I do this from the *"Install"* wizard thing or should I be doing this via a terminal?

Side note - do you wanna come to greensboro and get paid to put this on my computer? 

Thanks

Evan
Greensboro, I didn't notice that, about 35 miles away. 
 I've edited & added a little more to my last reply...you might want to try the last suggestion I mentioned about chrooting into your root partition...be sure to type the entries exactly(case-sensitive, spaces,etc) as they're listed, if you can't copy & paste...I'll be on & off the forum today, I'll help as much my limited knowledge allows.

---

### Post by Evegan on 2007-06-09
Thanks, I'm at work till 4 or 5 so I don't have access to my computer at the moment. I'll try those suggestions this evening.

Evan

---

### Post by Evegan on 2007-06-09
Tried the sudo grub-install, here's what it returned:

[I]ubuntu@ubuntu:~$ sudo mkdir /mnt/root
mkdir: cannot create directory `/mnt/root': File exists
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 /mnt/root
mount: /dev/sda1 already mounted or /mnt/root busy
mount: according to mtab, /dev/sda1 is already mounted on /mnt/root
ubuntu@ubuntu:~$ sudo mount -t proc none /mnt/root/proc
mount: none already mounted or /mnt/root/proc busy
mount: according to mtab, none is already mounted on /mnt/root/proc
ubuntu@ubuntu:~$ sudo chroot /mnt/root /bin/bash
root@ubuntu:/# sudo mount -t ext3 /dev/sda1 /boot
root@ubuntu:/# sudo grub-install dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Format of install_device not recognized.
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-shell=FILE       use FILE as the grub shell
  --no-floppy             do not probe any floppy drive
  --force-lba             force GRUB to use LBA mode even for a buggy
                          BIOS
  --recheck               probe a device map even if it already exists

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into the DIR/boot directory specfied by
--root-directory, and uses the grub shell to install grub into the boot
sector.

Report bugs to <bug-grub@gnu.org>.
root@ubuntu:/# 

[/I]

I'm still messing with it so we'll see what happens.

Evan

---

### Post by Evegan on 2007-06-09
When I open up the file browser I see several "places":

ubuntu, desktop, filesystem, floppy drive and /mnt/root.

If I go into *filesystem -> boot* there is no grub. If I go into */mnt/root -> boot -> grub* all I see is device.map.

---

### Post by confused57 on 2007-06-09
I'm not sure if it'll make a difference, but you entered:
> root@ubuntu:/# sudo grub-install dev/sda

try this:

```
root@ubuntu:/#sudo grub-install /dev/sda
```

notice the / in front of dev...the / represents the root filesystem in the path to install grub...fingers crossed.
You probably don't need sudo, since you've chrooted into your install.

If the "grub-install" doesn't work, which it may not since it doesn't appear grub installed completely, and you have internet access in your chrooted environment, you could try reinstalling grub:
```
apt-get install grub
```
I don't think you need to use sudo.

There may possibly be a bug with your hardware and the Feisty installer, you might want to try Dapper, which will be supported for 2 more years...if you're unable to get a copy, PM me and I'll mail you one.

---

### Post by Evegan on 2007-06-09
[I]ubuntu@ubuntu:~$ sudo chroot /mnt/root /bin/bash
root@ubuntu:/# sudo grub-install /dev/sda
The file /boot/grub/stage1 not read correctly.
root@ubuntu:/# apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grub is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:/# 
[/I]

Grrrr. I've already downloaded and burned a copy of Feisty, I get the same problem with both my copy and the one I ordered.

Would manually setting up the partitions help? If so, how do I do it?

Evan

---

### Post by confused57 on 2007-06-09
With the problems you're having with your current install, I believe reinstalling would be a good idea...use the cd that you ordered.  I always use the alternate cd, but I'll try to walk you through how you might manually partition & install with the live cd.
When you get to the partitioning selection...choose "manual partitioning"...first you should be able to delete the partitions that you have, in gparted.
What I think you ought to try, since the installation hasn't worked for you is to set up a separate /boot partition.

I belive what you do is click on the unallocated space & select new partition...move the slider to 100 Mb for the new partition, select the mountpoint as /boot, format as ext2, select primary partition.

Then click again in the remaining unallocated space, new partition...move the slider to create your / partition, all but approx 1 Gb(which you will use for your swap), select the mountpoint as / , format as ext3, select primary partition.

Then create your swap partition on the remaining 1 Gb, mountpoint is swap, format as swap, select logical partition(or extended).

I don't install with the live cd, so the actual steps will be slightly different from what I've described, but you should be able to get the idea of what you need to do.

When the installer reaches the grub installation stage, click on the "Advanced" button...type in /dev/sda as the location to install grub...or however gparted designated your hard drive, should be sda.

This may not work...the separate /boot partition may not make a difference, but it's worth a try.

---

### Post by Evegan on 2007-06-09
I can't get past the partition section, no matter what I do it always says 

*No root file system is defined*

When I select the remaining portion, *use as* swap, it won't let me select a mount point.

---

### Post by confused57 on 2007-06-10
> **Evegan said:**
> I can't get past the partition section, no matter what I do it always says 

*No root file system is defined*

When I select the remaining portion, *use as* swap, it won't let me select a mount point.
I don't think you need to select a mountpoint for swap.  If you did select / as the root partition mountpoint(not /root), then it could possibly be this bug that was seen in the Edgy installer:

[http://ubuntuforums.org/showpost.php?p=1700787&postcount=29](http://ubuntuforums.org/showpost.php?p=1700787&postcount=29)

I haven't heard of this bug in Feisty, but it might be worth trying the "fix" mentioned  in the thread for Edgy.

---

### Post by Evegan on 2007-06-10
Dear god, it works! Manual set-up was the trick!! Needless to say I'm excited and eternally in your debt. Thank so much for all the help.

My only problem now is that the screen is pushed 1/3 of the way to the right. Meaning, there's about 2 inches of black space on the left of the screen. Any idea how to fix this?

Evan

---

### Post by confused57 on 2007-06-10
> **Evegan said:**
> Dear god, it works! Manual set-up was the trick!! Needless to say I'm excited and eternally in your debt. Thank so much for all the help.

My only problem now is that the screen is pushed 1/3 of the way to the right. Meaning, there's about 2 inches of black space on the left of the screen. Any idea how to fix this?

Evan
Good job getting it working, saved me a trip to Greensboro...  

Your screen problem might just be that your monitor needs adjustment...you probably just need to adjust it manually...there should be buttons on the front for this.

Glad to have helped.

Jim

---

### Post by Evegan on 2007-06-10
I hit the auto/set button and that fixed it. It didn't work while using the livecd for some reason so I thought it might not work after either.

Again, thanks for the help and patience.

Evan

---

