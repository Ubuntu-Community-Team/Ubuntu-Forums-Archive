---
title: "GRUB Expert needed!"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by jesusfreak107 on 2008-05-02
I have posted a lot of posts, trying to solve this problem, and have not come to a solution.  Therefore, I want an expert to answer this question, and not someone who thinks one of their ideas might work.  Preferably an Admin, but any expert is welcome.  I have a simple question that nobody seems to be able to do.  I need to boot an iso file, via grub, off of a USB stick (actually a SD adapter), on a computer running Windows 98SE, with one 10GB HDD, all one partition.  I need the exact lines of code that will accomplish this.  not random ideas.  code. I am running GRUB, and GRUB4DOS, I can use either.

---

### Post by dstew on 2008-05-02
I can help you. What you want to do is to be able to boot a system that is on your USB SD card. But, Charlie is old and cannot boot a USB stick. Probably its BIOS would not even see it. If this is the case, you cannot use grub to boot it, because grub relies on the BIOS to enumerate drives. Also, grub does not have the capacity to boot .iso's. It loads and boots kernels out of filesystems.

There is something you can do, but you use the syslinux program. This program runs under DOS or Windows, and can "boot" a USB stick. It is used as a way to install Ubuntu onto computers with no CD, no bootable USB, but USB access. It uses the DOS or Windows system to recognize and access the USB stick, because the BIOS cannot.

Here is a [Wiki page]("https://help.ubuntu.com/community/Installation/FromUSBStick") that discusses the use of syslinux to install Ubuntu FROM a USB stick (using as you would a Live CD). This is different from installing Ubuntu ON a USB stick, and people get the two confused. I think you want to install FROM a USB stick, and make your old laptop a dual-boot powerhouse ;-)

You will have problems, though, because you have too little memory to run the Live CD .iso. You might have to try the Alternate Install CD, which I think can run on less. You should also consider installing Xubuntu unless you can put more memory in there.

---

### Post by jesusfreak107 on 2008-05-02
I am using the Xubuntu Iso already.  Thanks for the link!  I had heard about syslinux but did not really know how it worked, and how to use it.  Thanks a lot!  I'll try this and reply back to this post probably Sunday, I am going to be out of town on a hiking trip tomorrow.

---

### Post by jesusfreak107 on 2008-05-04
Okay, little problem.  I tried putting it on the USB device with my main Linux installation.  I could not boot off of it, but I do not know if that was my fault or not.  However, I decided thatI should do it on Windows, just to make sure that it was compatible, especially with my outdated OS/Hardware .  I downloaded the windows version, and found instructions.  I downloaded the .zip file, and extracted it.  I put the syslinux.com in C:\WINDOWS.  I tried to use the command to install it on the USB device (E:\).  As you can see below, it did not work.  I tried different variants of the command I was given.  I tried using the command via the original location, where I extracted it, and the default C:\WINDOWS directory, and the C: drive, relocating it to each location.  (I am sorry if I have made a stupid mistake here, I am a Linux guy, not a DOS guy, I have NO experience with it.)  here is the error, showing the different variants I used.

> 
C:\WINDOWS>cd C:\

C:\>syslinux -s -m E:\
Usage: syslinux [-sfmar][-d directory] <drive>: [bootsecfile]

C:\>syslinux -s -m E:
syslinux: sector read error

C:\>syslinux -s E:
syslinux: sector read error

C:\>syslinux E:
syslinux: sector read error

C:\>syslinux -a E:
syslinux: sector read error

C:\>syslinux.com -a E:
syslinux: sector read error

C:\>syslinux A:
syslinux: sector read error

C:\>


Any ideas?

---

### Post by janz84 on 2008-05-04
Also need a grub expert for a different situation:

I have 3 sata disks: sda sdb sdc

sda has xp
sdb has vista
sdc has linux

How should my menu.lst file look to boot all the above and default sdc?

---

### Post by dstew on 2008-05-04
To Jesusfreak: Does the USB drive have a FAT16 format? If it does not, format it first. If it has an ext3 format, Windows cannot write to it. Make sure it has a Windows format.

Then, are you sure the USB drive is E: ? Sometimes it is another letter. Check in My Computer, and see what the drive designation is. If it does not appear in My Computer, that is a sign it is not formatted for Windows. It has to appear in My Computer in order to be accessible to syslinux.

---

### Post by jesusfreak107 on 2008-05-04
> **dstew said:**
> To Jesusfreak: Does the USB drive have a FAT16 format? If it does not, format it first. If it has an ext3 format, Windows cannot write to it. Make sure it has a Windows format.

Then, are you sure the USB drive is E: ? Sometimes it is another letter. Check in My Computer, and see what the drive designation is. If it does not appear in My Computer, that is a sign it is not formatted for Windows. It has to appear in My Computer in order to be accessible to syslinux.
Yes, it is E.  No, it is not FAT16.  It is FAT32.  Should I reformat it? 

Oh, by the way, if it matters any, it is a 2GB KINGSTON SD/USB adapter, partitioned with one 900-ishMB EXT3, one 760MB FAT32 (the E: drive), and the rest as EXT3 SWAP, paritioned with the idea of possibly running Linux off the drive itself.

---

### Post by jesusfreak107 on 2008-05-05
Reformatted to FAT16.  Will try it tomorrow, going to bed now.  Any ides before I start?

---

### Post by jesusfreak107 on 2008-05-05
Okay, tried with FAT16. Got the following problem when using isostick.sh in Linux:
> ./isotostick.sh [--reset-mbr] [--noverify] <isopath> <usbstick device>
I entered exactly what they said in the manual.
Any ideas?  I am on Summer Break now, i have more time to deal with the problem.

I got that script from the manual you gave me in your first post.

---

### Post by dstew on 2008-05-05
If you entered *exactly* what was in the manual you made a mistake, because you need to substitute the correct linux device name for /dev/sdX1 that is in the command. Also, the command assumes that the .iso is in the current directory. Was this true?

---

### Post by jesusfreak107 on 2008-05-05
I know that that error means that it was not used correctly.  Could you take a look at the code on the [manual]("https://help.ubuntu.com/community/Installation/FromUSBStick"), and see what was wrong with it?

---

### Post by jesusfreak107 on 2008-05-05
no, I modified it to fit my drive.  Sorry I forgot to mention that.  I changed it to SDA1, which was my drive

---

### Post by dstew on 2008-05-05
Just to be sure, I would like you to navigate to the directory that contains the isotostick.sh file, and do```
ls -l
```and```
sudo fdisk -l
```. This will check that the .iso and the isotostick script are in the same directory, that the script has the correct permissions, and will also confirm the Linux name of your USB stick partition that you want the .iso to be installed into.

---

### Post by jesusfreak107 on 2008-05-05
oops.  it was SDB1.  haha.  Okay, I installed it!  immediately after I installed it, I unmounted it and tried it on the lappy.  it did not work.  were there any more steps?

---

### Post by jesusfreak107 on 2008-05-05
At the beginning of the manual, it says
> This pages describes how to install Ubuntu by copying the contents of the installation CD to an USB drive such as a memory stick (or flash drive) and making the USB stick bootable. This is handy for machines like ultra portable notebooks that do not have a CD drive but can boot from USB media.
The lappy cannot boot from a USB device.  Is this possible using a flopppy?

---

### Post by jesusfreak107 on 2008-05-05
correction:  I know it's possible.  any ideas how?  I've never configured a floppy before, I became a geek after they were almost obsolete.

---

### Post by dstew on 2008-05-05
The [Smart BootManager]("https://help.ubuntu.com/community/SmartBootManager") can run from a floppy and boot a non-bootable CD-ROM. It can probably also boot a USB drive.

EDIT: But maybe not. I see that it cannot boot a USB-CD-ROM drive.

EDIT again: It might be necessary to use an operating system to recognize the USB in your computer, because the BIOS is old, and may have no USB support at all. If you want to try something that will work for sure, you can install a [small Debian system]("http://http://www.debian.org/distrib/netinst") from 4 or 5 floppies. Once that is in, you might be able to "bootstrap" a full system into the laptop.

---

### Post by jesusfreak107 on 2008-05-07
No, SBM did not work (I never saw your edits.).  However, I finally just gave up on Ubuntu.  I used a WakePup floppy to install the latest Puppy Linux version on it, and it is working better than I think Xubuntu would have, performance-wise.  While it is not as full-fledged of an OS as Ubuntu, it has improved greatly from the last version that I had used, and I am quite pleased with it.  Thank you for your help, dstew.  Even though I never managed to boot ubuntu, I learned a lot about GRUB, floppies, and hardware.  Thanks.  Screenshots of my Puppy below.
:guitar::guitar::guitar::guitar::guitar:

---

### Post by jesusfreak107 on 2008-05-07
...how do I mark this thread solved?...

---

### Post by dstew on 2008-05-07
Thread tools, "Mark as Solved".

---

### Post by jesusfreak107 on 2008-05-07
> **dstew said:**
> Thread tools, "Mark as Solved".
it is not on there.  There is:

Show Printable Version
E-mail This Page
subscribe to this thread
add a poll to this thread

???

---

### Post by dstew on 2008-05-07
Ha! The selection disappeared when the forum format was changed. See [this thread]("http://ubuntuforums.org/showthread.php?p=4805983"). You can edit the title of your thread and put [SOLVED] at the front. Best wishes.

---

### Post by jesusfreak107 on 2008-05-07
I cannot seem to figure out how to do that, either.

---

