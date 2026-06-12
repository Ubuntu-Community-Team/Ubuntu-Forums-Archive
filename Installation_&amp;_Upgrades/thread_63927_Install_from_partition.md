---
title: "Install from partition?"
date: 2005-09-09
forum: Installation &amp; Upgrades
---

### Post by Richard Rowlands on 2005-09-09
Hi folks,

I have an Ubuntu installation CD (5.04) and wish to install it on an old laptop I have.  Unfortunately I have no network card (which rules out the HowTo on installing without burning a CD) or CD drive on the laptop, just an internal hard drive and a floppy disk drive.  I can transfer files from my desktop machine (with a CD drive) over a parallel laplink cable onto a partition on the laptop's hard drive.  I also have a working floppy drive on the laptop.

Is there any way I can do an install from a partition on the laptop's hard drive?  Has anybody succeeded in doing something similar to this?  I would really like to try this distribution but am stumped as to how I might go about installing without a CD or network card.  Any advice or tips would be warmly welcomed.

Best regards, Richard.

---

### Post by saikee on 2005-09-09
Not much a solution but if I were you I would remove the hdd, get a 2.5" to 3.5" hdd adaptor, put it on a PC with a CD drive and install Ubuntu on it.  

Then I remove the hdd and put it back into the laptop.  It should work out.

---

### Post by Richard Rowlands on 2005-09-10
Well, I'm now writing this from a working Ubuntu Linux installation on my old Thinkpad 770 over a wireless internet connection!  What an amazing distribution!  Having tried RedHat, SuSE, Mandrake this is by far the best.  For a long time I've been feeling that Linux distributions have been moving in the wrong direction, becoming more and more bloated.  Ubuntu is what I have always wanted from a Linux distribution.  (Would love to see some floppy install images to kick off either a USB, hard disk, installation though!).

Anyway, how I solved my problem was by borrowing an external USB CD drive.  I was unable to boot from this device so I created a DOS boot disk that supported USB CD drives.  If anyone needs to do the same, the lines from my CONFIG.SYS file are shown below.  The corresponding files were found online (Google).


DEVICEHIGH=A:\USBASPI.SYS /v/w
DEVICEHIGH=A:\DI1000DD.SYS
DEVICEHIGH=A:\USBCD.SYS /D:USBCD001


Using FDISK.EXE I then created a small partition on my hard disk and formatted it as a FAT16 volume.  I copied the vmlinuz file (the kernel) and initrd.gz file (initial RAM disk) from the Ubuntu installation CD (both files were in the \INSTALL directory) to the root directory of the newly formatted C: drive.  I then used GRUB for DOS to boot from these files by creating a directory C:\BOOT\GRUB and copying the files GRUB.EXE and MENU.LST there.

I believe I setup the MENU.LST file as follows :-


timeout 0
default 0

title Ubuntu Install
rootnoverify (hd0,0)
kernel /vmlinuz vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
initrd /initrd.gz


After typing GRUB at the DOS prompt and selecting Ubuntu Install, the installation started from the hard disk and once the Linux kernel had loaded installation continued from the USB CD drive, Linux accessing it directly this time.

During installation I selected to erase the hard disk handing the entire drive over to Linux.

Once the install had finished I then turned my attention to getting my Belkin 54g USB adapter working.  When I have time I will submit a post explaining what I did as I found I had to refer to numerous different sources to get this adapter to work.  The bottom line is that the rt2570 native Linux driver can be made to work with the Belkin 54g USB adapter F5D7050uk on Ubuntu quite easily, and it rocks!

Regards, Richard

PS: Really love this distribution!!

---

### Post by pbmax on 2005-09-10
I'm going to take this a step farther, and I know... hmm, nothing about linux.

Ubuntu was recommended to me and I have an old laptop that isn't used so I thought I'd install it.  problem is the old hard drive clicks and thumps and makes me think unhappy thoughts about it.  So I got a new one.  How do I get ubuntu onto this new HD?

I have an external USB 3.5 and external cdrom.  The only way I can get the computer to boot even to the BIOS screen is to use an external USB adapter for the HDD. Then I can get it to boot.  It will still boot and run off the old HDD, but will not ever read the new one (toshiba 40g).  It always freezes at "autodetecting IDE devices" if I have the HDD installed and boot.

Right now I am just installing 5.10 (the new pre release) onto the old HDD. erasing and letting the installer hadle it all.  Don't know if it works yet or not. I'll let you know

The new HDD will read off the USB connection on the old computer and my current  XP laptop, so it's not the drive that's bad. It's me.

so the questions:
How can I get the computer to recognize the new HDD when installed?
Is there another option to get UBUNTU onto the new HDD
Should I try with 5.04 instead?

thanks
pb

---

