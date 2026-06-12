---
title: "Dual booting Vista and Edgy, SATA, PATA drives not compatible"
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by markmaus on 2007-01-08
I've looked through the forums, but haven't found anything like my problem, so here goes:

Here's my setup;
sda1, M$ Vista (NTFS) Serial ATA drive
hda1, Edgy (ext3) (with Grub written to this MBR), Primary IDE Master Parallel ATA drive
DVD-RW Optical Drive set as Primary IDE Slave

My bios supports switching the hard drive boot order.
I install Vista on sda1, with sda set as the first boot drive, and everything is hunkydory, Vista boots up just fine.

I switch the first boot hard drive in the bios to hda and install Edgy and Edgy boots fine when booting hda as the first boot drive.
When I select "Vista" from the Grub menu, it just reboots the machine, but that's ok.   I can live with toggling the boot drive order in the bios to switch operating systems.  (I've edited the /boot/grub/menu.lst file, adding mapping and all the usual tricks to no avail)

But here is the problem.  When I set the first boot hard drive back to sda in the bios and Vista boots, the OS pauses for a minute (I think that it is destroying grub) before booting into Vista.  Vista works fine once booted.

Then I switch the bios drive order back to hda for the first boot drive and try to boot Edgy, and all that I get is a command prompt.  (Not a Grub prompt, but a different type of prompt)

I've reinstalled Edgy three times.  It runs great until I use Vista.  Then I can no longer boot Edgy.  Maybe I have the wrong combination of PATA, SATA drives working here, or maybe Vista is programmed for a search and destroy mission to kill Grub.  Any insight to this problem or recommendation to get Vista and Edgy to play nice together would be appreciated.

I also tried to load Grub to the MBR on sda (the Vista drive).  That basically nuked the Windoz boot loader and wouldn't boot Edgy or Vista and "fixmbr" from a windoz boot disk is no longer an option in Vista.  The Vista disk doesn't seem to have a recovery console.  So I had to reinstall Vista.
Thanks,

---

### Post by ukrudl3r on 2007-01-08
> **markmaus said:**
> ...and "fixmbr" from a windoz boot disk is no longer an option in Vista...

No help here, but can I just say OMG!!!!!!  I don't know how many times fixmbr saved my installation from a messed up GRUB.  Not good to hear.

---

### Post by yager on 2007-01-08
Check out this link to see if it is any help.

[http://www.pro-networks.org/forum/about78184.html](http://www.pro-networks.org/forum/about78184.html)

hand it to M$ to act as if they are the only system allowed on your, or should I say their box that they let you borrow.

There were some comments about BitLocker which is a new security feature in Windows that basically hoses dual booting by encrypting the drive at the hardware level.  You may want to look into that.

I remembered reading that there was a way to add multiple OSes through M$ bootloader.  Refer to this link to see if there is any similarity to XP or earlier and may be an option.
[http://jaeger.morpheus.net/linux/ntldr.php](http://jaeger.morpheus.net/linux/ntldr.php)
It uses LILO as the example, but you should be able to replicate the image of a GRUB mbr to feed to the NTLDR program that belongs to Vista.

---

### Post by markmaus on 2007-01-09
thanks for the links Yager.  I'll check them out tonight.  Something wierd is definately going on here.  If i figure it out, I'll post a solution.

---

### Post by markmaus on 2007-01-11
I got it straightened out.  The solution is to use only one hard drive with grub on a floppy.  So I put Vista on the first partition of a 120 GB Sata drive, Edgy on the second partition and grub on a boot floppy.  (I had to use the Alternate Edgy install disk to write grub to a floppy)  Now Vist boots from the MBR and Edgy boots from the floppy.  Interesting enough the grub floppy has a boot line for Vista, but it doesn't work.  

I still have the problem of Edgy not booting when I install a second hard drive (either a SATA drive or a PATA drive).  With a second drive connected I get the same old error something like this:

BusyBox V.1.00 built in shell (ash)
/bin/sh: can't access tty; job control turned off

Which kind of sucks, because I need about 80 GB of space for my audio/video library and I only have 50 GB available.  So I'll probably go through the entire reinstall of both OSs on a 320 GB SATA drive that I just bought.  I've looked through the forums for a solution to the "Job control turned off" problem.  But all posts that mention it list a DEAD LINK as the solution.  If anyone knows how to fix this, please reply with the solution.
Thanks,

---

