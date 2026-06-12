---
title: "How to dual boot Ubuntu and Windows XP without changing the Windows MBR"
date: 2005-08-13
forum: Installation &amp; Upgrades
---

### Post by celticmonkey on 2005-08-13
*How to dual boot Windows and linux without changing the Windows Master Boot Record:*

(I'm assuming you've read other FAQs on how to install linux to your partition of choice.)

When installing ubuntu, install the boot loader (GRUB) to a floppy disk instead of the MBR. ie. when prompted for grub location enter: /dev/fd0

Boot into ubuntu with the floppy. 

Open a terminal window.

Copy your bootloader from the floppy to a file called bootsect.lnx with this command:
dd if=/dev/fd0 of=bootsect.lnx bs=512 count=1

Save that file somewhere that you can access from within Windows. ie a FAT partition, a USB drive, a floppy (but not your boot floppy!) Don't try saving it to an NTFS Windows XP partition from within linux. (Bad!)

Reboot into Windows. (hint: take the floppy out of the drive. Keep it somewhere as a rescue boot floppy.)

Copy bootsect.lnx from wherever you had stored it to c:\bootsect.lnx

Open a file called c:\boot.ini 
(It's normally a hidden read-only file, so you may have to change the folder and file options.)

After opening boot.ini add the following line to the end of it and save it:
c:\bootsect.lnx=”Linux”

Reboot your system. 

You will be prompted to boot either Windows or Linux and your MBR hasn't been changed at all! 

It's magic!

I use this setup to boot ubuntu from the third parition of my second hard drive, but I don't see why it wouldn't work with one partitioned drive as well. (I'd be interested to find out if it works with normally non-bootable USB devices that BIOS can't see as well, but I haven't tested that. Probably not.) As ubuntu is on a second drive I haven't really made any changes to my Windows partition at all! Risk free.

(If you do screw up your MBR and can't get into Windows try booting your Windows rescue CD and then type 'fdisk /mbr' to restore it. If you already have ubuntu installed I think you can make a boot floppy this way, but I"m not 100% certain: In a console, type grub-intall /dev/fd0.)

James.

---

### Post by Copter on 2005-08-13
sounds nice :). i would try this but my computer doesnt have floppy drive :(. i think it should be put in tips&tricks howto section.

copter :]

---

### Post by mailmaldi on 2005-08-13
> 
When installing ubuntu, install the boot loader (GRUB) to a floppy disk instead of the MBR. ie. when prompted for grub location enter: /dev/fd0


in normal installation i dont get this option where to install......

wat do i do to get such options???

boot: custom??

or 

boot:expert ???

---

### Post by celticmonkey on 2005-08-13
Hmmm... I'll have to repeat the process to find out, but as I remember it, I was asked where to install GRUB after I had selected the partition I wanted to use for ubuntu and installed there.

If you have made a second partition for ubuntu and not overwritten you windows parition the installer should detect two operating systems and ask you where to install the boot loader. The default is the MBR on the primary drive.

From the ubuntu install guide wiki ([https://wiki.ubuntu.com/Installation/I386):](https://wiki.ubuntu.com/Installation/I386):)
"If the installer detects other operating systems on your computer, it will add them to the boot menu"

---

### Post by pkoufalas on 2005-08-21
Interesting solution.

FYI I'm using grubinstall,

[www.geocities.com/lode_leroy/grubinstall/](www.geocities.com/lode_leroy/grubinstall/)

I found out about it when installing Knoppix to my HDD,

[http://www.knoppix.net/forum/viewtopic.php?p=57198](http://www.knoppix.net/forum/viewtopic.php?p=57198)

I've found it to be quite good. The only frustating issue I had was grubinstall failing to locate the menu.lst file: It couldn't see it when menu.lst was on my windows partition, but I succesfully put it into my (Ubuntu) linux partition instead.

---

### Post by redfox on 2005-08-22
So the niftiness of this resides in being able to delete that line, the linux partition, and then everything will pre-linux again?

I wish I would have known about boot.ini a few days ago :grin: .

---

### Post by TreeFrog on 2005-08-28
I got the strange problem again. Like I get the short straw.

My system is an AMD64 with 3 SATA drives and two quite old IDE drives.
XP is on one SATA drive
Suse is on another SATA drive
and I have (as per this guide) put Ubuntu i386  on the third SATA drive. All drives were plugged in at the time so all the entries in grub should be good.

XP is there the longest and works fine with all drives
 
Suse was installed without any other drives plugged in but works fine when selected in the BIOS boot menue. have not sorted out mounting the other drives.

Ubuntu will boot from the floppy (as per this guide) but not from the file put on the C;\ of XP

After selecting the Linux option in the boot options I get the text "GRUB" in the top left of the screen and that is it.. nothing else.. reboot with floppy and it is cool. 

Why Why Why. ](*,) 

or more productivly how do I solve it. ??

Any ideas!

---

### Post by TreeFrog on 2005-08-28
a question. 
can I simplify the grub stuff right down so the variables are less. so I can rule out grub or find out where it is having problems.

What is the most simple grub file I can use.

---

### Post by shakyone on 2006-07-27
Celtic Monkey,

     Have you figured out a way to make this work when installing Ubuntu 6.06.  I have Windows XP on one drive, and Ubuntu on another (installed with XP drive removed) and your solution sounds great, except I, like one of your other replies, did not get the option to install grub somewhere specific.  I like your solution, it looks like the most painless one, I just missed that one option and how to overcome it.

---

