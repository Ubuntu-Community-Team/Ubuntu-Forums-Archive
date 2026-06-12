---
title: "Installing Ubuntu in a triple boot system"
date: 2011-01-22
forum: Installation &amp; Upgrades
---

### Post by Thandroo on 2011-01-22
Hi all,

Run into some issues installing Ubuntu. I have Windows XP and Windows 7 as 2 partitions on one drive. I have one other drive that I have partitioned in Windows and have allocated 16GB for Ubuntu.

Upon trying to install Ubuntu onto the newly created partition, I get an error telling me that no root file system is defined

What am I doing wrong?

Some help here please!

---

### Post by oldfred on 2011-01-22
welcome to the forums.

You have to define two partitions for a normal Ubuntu install. One is  / (root) and the other is swap. 

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Some examples of installs with screens showing how it works.

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)


Some examples of installs and issues:
Issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

### Post by Thandroo on 2011-01-22
Hi Oldfred,

thanks for replying.

I'm going to partition the drive in Windows (3 partitions as advised - 12GB, 2GB, 2GB)

I have 3GB RAM, so any real need for swap?

---

### Post by oldfred on 2011-01-22
DO NOT use windows to partition. It will convert to SFS, a windows logical partition scheme that is not compatible with anything and cannot be undone.

Use gparted to create partitions. Windows does not know about Linux partitions and cannot create them anyway. Gparted is on the Ubuntu liveCD or can be downloaded as its own liveCD.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by Thandroo on 2011-01-22
Ah - becoming slightly clearer now. Will try that and get back to you.

Thanks in the meantime

---

### Post by Thandroo on 2011-01-22
Not enjoying this at all!

here's what I have in "allocate drive space":

Device            Type    Mount Point                            Size           Used
/dev/sda
    /dev/sda1    ntfs                                                    23451 MB (21312 MB used)
    /dev/sda2    ext2     /boot                                      10504 MB (188 MB used)
    /dev/sda5    ext3     /home                                     6062  MB (241 MB used)


I'm missing something simple here as I get same error.

Added help please

---

### Post by wilee-nilee on 2011-01-22
Boot the Ubuntu live cd and go to system-admin-gparted, open gparted and post a screen shot of it.

---

### Post by Sylslay on 2011-01-22
Well.
Use live cd.
Delete partitons, (only at space dedicated for linux)

Run installer.
Make ext4 about 15GB mounted at:   /
Make 1GB swap parition, 

When installing grub2 at the end , choose MBR of hd[X] or sd[X] partion for alloceate grub installation.

Where X colud be: a,b,c,..

If You like use hibernate under linux use 2 GB swap partion.
My laptop has 1gb ram and 1gb swap. but newer notice swap to be  used on it.
Swap is usefull when system has 512 RAM or less.

---

### Post by wilee-nilee on 2011-01-22
> **Sylslay said:**
> Well.
Use live cd.
Delete partitons, (only at space dedicated for linux)

Run installer.
Make ext4 about 15GB mounetd at /
Make 1GB swap parition, 

When installing grub2 at the end , choose MBR of hd[X] or sd[X] partion for alloceate grub installation.

Where X colud be: a,b,c,..

If You like use hibernate under linux use 2 GB swap partion.
My laptop has 1gb ram and 1gb swap. but newer notice swap to be  used on it.
Swap is usefull when system has 512 RAM or less.

The portion where grub is pointed to the MBR is in the custom partitioning section. The description they have looks a little off, they have XP and W7 there should be 2 NTFS partitions, at the least.

---

### Post by oldfred on 2011-01-22
You also do not need a separate /boot unless you have an old system, RAID or LVM which are advanced installs. In fact a separate /boot makes any repairs more difficult. Standard desktops need just / (root) & swap, but I always suggest a separate /home, but even that is more advanced.

---

### Post by Thandroo on 2011-01-23
Really struggling here. I have all the above in place, but the install keeps failing. I've redone the install disc three times and it keeps failing. Finally downloaded the AMD64 version and it will not go further than the UBUBTU logo screen and shows the following:
 
>  
BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.
 
(initranfs) mount: mounting /dev/loop0 on /filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs
udevd[143]: worker [287] unexpectedly returned with status 0x100
 
udevd[143]: worker [287] failed while handling '/devices/virtual/block/loop0'

 
This is driving me insane - not a great start when I'm considering migrating from Windows.
 
I've also tried booting from my USB stick, but does not work (used the USB installer)
 
Any help please guys?

---

### Post by Thandroo on 2011-01-23
Would it help if I posted my system specs?

CPU - AMD Athlon II x4 630 2.8 GHz
MEM - 3GB DDR2-RAM 667MHz (PC2-5300)
MOBO - GIGABYTE GA-MA770-UD3 mobo
PSU - Corsair TX 650W PSU
GFX - Radeon HD5670 512Mb (1.5GB Vista/7) PCI-e
40 GB Seagate Barracuda IDE HD - Partitioned for using Ubuntu (25GB used for windows storage)
250GB Western Digital SATA HD
250GB Western Digital SATA HD
150GB Hitachi SATA HD - Partition x3 (XP/ Win 7/ Storage)

16x Sony DVD +/- RW Dual Layer

XP Pro SP3/Windows 7 Ultimate

---

### Post by oldfred on 2011-01-23
If you are having issues with the 64bit installer, I would stay with the 32bit. Not sure about your processor on whether it is 64bit or not, but if it is either should work.

Have you been able to run the CD in the liveCD mode to make sure your system works ok? Have to run the check CD for errors?

In post #6 you showed partitions with a /boot and no / (root). You have to have root.

Did you go thru Herman's install on second (or more) drive, as it shows each screen and what you have to do.

---

### Post by Thandroo on 2011-01-23
In the Live CD environment, I used the CD check utility and it reports "The file integrity check could not be performed" and some text about not having permissions
 
I'm losing faith with this quite rapidly - hope you can help!

---

### Post by Thandroo on 2011-01-23
Yes, I successfully used the method to create root; home; swap. When the installation gets to the user input screens (location; password; keyboard language, etc) that's when it fails.

---

### Post by Thandroo on 2011-01-23
Just trying again and it is copying files - up to around 50 %. A record so far I think!! Will update soon

---

### Post by Thandroo on 2011-01-23
AAAAAARRRRGH!!!
 
Copyimg files - OK!!
 
Scanning CD-ROM - apt configuration problem "An attempt to configure apt to install additional packages from the CD failed"
 
 
So close and yet so far!!

---

### Post by oldfred on 2011-01-23
The first issue you had may have been because the current installer will not let you have caps in your name on the set name &  password screen.

Have not seen the apt install error. Still seems like some sort of CD burning issue. 

I stopped using CDs a year or two ago and just use a no name flash drive that I boot with grub and loop mount the ISO. Setting it up is more advanced but once done it is easier to use. Some do have issues with the standard USB flash drive creator.

---

### Post by Thandroo on 2011-01-23
Setting up USB drive using universal USB installer. Will try that then your suggestion of caps in username (or not as the case may be!).

Will let you know

---

### Post by Thandroo on 2011-01-25
okay. We're rolling!! Burned the ISO to DVD and it installed without a problem. A few tweaks with EasyBCD and it's sorted. Going to have a good play around.

I don't quite understand why the CD-R discs weren't working - they are Memorex branded ones. DVD-R are also Memorex branded. Bug maybe or what?

thanks to all for their input

---

