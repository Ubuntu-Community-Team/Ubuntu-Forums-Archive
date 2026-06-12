---
title: "Need Help w/ Grub on Two HDs"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by immaculance on 2010-01-29
I have an existing Ubunto 9.10 install sitting on a 500 GB SATA drive that was sitting in my second SATA port.

I'm trying to swap the internal HD  out to a new system that has a 500 GB SATA drive with Windows 7 on it as the primary drive, in SATA port 0.

When I configure BIOS to boot from my Ubuntu drive, I just get a flashing cursor on the screen and no Grub bootloader like I was before.

Does this mean Grub isn't on my Ubuntu drive?

Should I install grub on both my Ubuntu drive's MBR AND my primary Windows 7 drive's MBR, or only one of the other.  The instructions I've been reading don't specify which drive to reinstall Grub on and which drive I should boot from, so I'm confused.

How do I get it so that Grub acknowledges my Windows 7 install on the primary drive?

HELP!?

---

### Post by audiomick on 2010-01-29
Hallo.
Just to be clear about things:
you have taken a drive with an Ubuntu install out of one machine and put it into another that has a drive with a win7 install already in it.
Is this correct?

This sounds like I wont be able to fix it, but I am sure it can be fixed. I think some more info will be helpful to those who know more about this.

Go here
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
and follow the instructions.

You will need a Live CD; you can't boot into your Linux install right now, can you?

Carry out the procedure with the drives plugged in the way you want to have them installed.

Post the result back here.

The script reports info about what is on which disk. It should detect whether you have a grub, or remains of one, anywhere on the drives, and which system is installed where.

---

### Post by darkod on 2010-01-30
If I understood you correctly, you currently have two disk system, and you want to move you ubuntu disk to another system with win7 disk already in it. And you can't boot ubuntu.

It seems you think that grub2 is on the ubuntu disk while it might be on your other disk in the current system. That would be the only reason that you are not seeing grub2 after moving the disk to another system.

To make sure what we are talking about, run the script as suggested, either in your old system or in the new system, and we can take it from there.

---

### Post by tachuela on 2010-01-30
Take a good red at this link:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by presence1960 on 2010-01-30
run the boot info script as audiomick suggested. Just in case:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by immaculance on 2010-01-30
Thanks everyone for your feedback.  My apologies for not being clear on my problem, but most of you got it right...  I'm trying to take an HD with just Ubuntu on it from a box with two HDs on it (the second with WinXP) and place it into a different box as the second HD with an existing HD that now has Win7 on it.

I consulted the Grub2 file in the Ubuntu Community Documentation ([https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) from LiveCD) and it helped me to reinstall Grub2 onto the master boot record of my **primary HD, which has windows 7 on it.**  I actually reinstalled Grub2 on both HDs just to be safe and upon restart everything was peachy and I'm back up and running with Grub, Ubuntu 9.10 on my second HD, and Windows 7 on my primary HD without issues.

Since I have the Win7 HD setup as the primary boot device, I needed Grub on it's MBR, since grub wasn't on my Ubuntu drive, which is why I got nothing when setting it as the primary boot device.  I probably could have just set the second HD with Ubuntu up with Grub and then set it as the primary boot device, but whatever.

I'm good to go and issue resolved.  My apologies for the un-thorough panic post.  Thanks again to all those who took the time to read and reply!

---

### Post by oldfred on 2010-01-30
It still would be best to have grub on the drive with the Ubuntu install. And set that drive in BIOS to boot first. You also may have a 10-20 delay in the grub menu coming up as there is a minor bug if grub is on one drive and Ubuntu on another.

I would also set the windows drive first in BIOS temporarily and run the windows repair so that drive can boot on its  own, if you ever wanted to revert to that or if the Ubuntu drive had issues.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

