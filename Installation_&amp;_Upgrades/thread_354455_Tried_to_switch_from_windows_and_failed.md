---
title: "Tried to switch from windows and failed"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by roofchop on 2007-02-06
I have wanted to make the switch from Windows XP MCE to Ubuntu & MythTV for a while, tonight I tried and it didn't work, help!

I started by following this site:
[http://parker1.co.uk/mythtv_ubuntu.php]("http://parker1.co.uk/mythtv_ubuntu.php")

I didn't make it very far.  I downloaded the Ubuntu Edgy CD, burned it onto CD, then boot to the CD, Installed Ubuntu (all defaults), the installation finished, prompted me to remove the CD, and then reboot.  Sounds right up until now.

When I tried to boot after installation I got the message "Error starting operating system" in white letters on the top left of the screen. What did I do wrong? Mobo? SATA HD?  

I tried the whole process again, but had the same result.

TIA

---

### Post by kvonb on 2007-02-06
I may be wrong, but that doesn't sound like a Linux error message!  If you had Windows on the machine before, it might be the boot loader still left over from that.

IF you are using ONLY Ubuntu on the one hard disk, maybe clean the disk before re-installing, ie kill the boot sector!

There is a way to do this from the Ubuntu CD, I just don't know it off hand, and I'd hate to give you the wrong info :/.

If there is any more info given, please post it here.

Regards, Kev :)

---

### Post by kvonb on 2007-02-06
Another thought:

Maybe the hard disk isn't included in the boot chain!

Go into your BIOS (see your mainboard manual for help) and make sure that  you're hard disk is in the boot list, some mainboards have a built in menu so that you can boot from different devices, mine is F12 and I can select CD/HD1/Hd1/Floppy etc'.

---

### Post by roofchop on 2007-02-06
Good idea, I should have thought of that.  My Mobo sometimes "forgets" which is the primary HD.  In the past when that has happend I think get a slightly different error message.

---

### Post by kvonb on 2007-02-06
> **roofchop said:**
> Good idea, I should have thought of that.  My Mobo sometimes "forgets" which is the primary HD.  In the past when that has happend I think get a slightly different error message.

No worries, I do the same thing!

Also, I just noticed that you have a Seagate AND a WD, I'm not sure with SATA as I don't use it, but I have had different drives not working too well with each other, this is on IDE, but just a thought.

Maybe the 2nd drive is trying to boot instead of the first, I would suggest removing the unused drive and try that :).

---

### Post by roofchop on 2007-02-06
Onto my fourth try with still no luck.  This time I tried to go dual boot, on my Seagate 120Gb SATA drive.  I have Windows MCE on 20Gb, and left the other 100Gb empty, and installed Ubuntu from the CD.  When I restarted, it went through POST and then the screen went blank except for a white flashing underscore in the top right corner.  I checked the BIOS for boot order, and it is booting from the right drive, but again no luck.  I can't even get back to windows.  :confused:

---

### Post by roofchop on 2007-02-06
I just tried deleting all the Ubuntu partitons and it still won't boot back into Windows.  Why can't I get this to work.:confused:

---

### Post by roofchop on 2007-02-06
OK, some success but the wrong way.  I went back into the partition manager from the Ubuntu live CD, this time I actually deleted the 3 partitions Ubuntu created, and I also checked the boot flag for the remaining 20Gb windows partiion.  Now it will boot into windows normally.  Now I have 20Gb for windows and 100Gb unpartitioned space.  How do I put Ubuntu on this unpartitioned space?  I tried to just install off the live CD, and I couldn't get either operating system to work.  Was checking that boot flag important?  Do I have to do something similar?  I have read about boot manager style programs, should I go with one of these?  :confused:

---

### Post by kvonb on 2007-02-07
As part of the install process, Ubuntu will install "grub" which you would want to place in the bootsector of your Windows partition.  This should then pick up the Windows partition and add it to it's boot menu.

It's been ages since I installed Ubuntu, so I can't remember the exact steps, but somewhere it will ask where you want to install the bootloader, that is the critical part, where you write it to!

Your disk structure should look something like this:

sda   (your entire physical hard disk)
sda1 (your NTFS Windows partition)
sda2 (your Ubuntu / partition)
sda3 (your Ubuntu SWAP partition)

in this example, sda1 would be set as bootable (standard Windows), make sure that you install GRUB on there, don't change the bootable flag, just leave it as it is, ie the Win partition should be bootable.

If it goes wrong, just boot from your Windows CD and select recovery mode, then run "fixmbr" or "fixboot" or the old "fdisk /mbr" to get it all back to original state!

Hope that helps :).

---

