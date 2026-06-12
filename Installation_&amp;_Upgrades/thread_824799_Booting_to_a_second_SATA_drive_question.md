---
title: "Booting to a second SATA drive question"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by GreatSunJester on 2008-06-10
I have searched around the forums and google in general and did not find anything that seemed to fit, so if this has been answered to death already please post the link!

I have Vista on my main computer and would prefer not want to have anything touch the drive but vista (OK, I'll install GRUB there if it comes down to it). Paranoid?  Yes.
I have a second SATA drive bought specifically for Ubuntu.  I booted to the LiveCD, did my partitions of sdb (/ , /home and swap) and selected sdb as the location for the boot loader.  Once I restart my machine, select the second drive for boot, GRUB comes up and has the correct listing of boot possibilities (including booting back to the Vista install!) but when I select Ubuntu it cannot boot.
Unfortunately I am at work and can not get the exact messege to post here.
What am I missing, except the bravery to install GRUB to my first harddrive?  (bad experience a while ago with a screwed up MBR and XP, Vista just makes me feel less confident)

---

### Post by Pumalite on 2008-06-10
Best thing you can do is install Grub to your first drive (Vista). You'll have dual boot:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by GreatSunJester on 2008-06-10
Got it -- posting from FF in Ubuntu on my machine.  Took a guess and looked at menu.lst
The installer had set the Ubuntu disk as (HD1,0) and the Vista disk as (HD0,0) -- exactly what it should have done IF grub was being installed on the first drive.  Since I am telling my BIOS boot to the second drive first, the boot loader wants to treat it like it was the primary drive.  I swapped the drive assignments so Ubuntu is (HD0,0).
Booted perfectly.  Downloading updates now.  Of course, in my paranoia I will let the machine do a default boot back into Vista just to be sure.....

EDIT
Perfect .. updates completed (re-edited menu.lst after I let the updater work it's magic!) and computer rebooted following it's BIOS default and VISTA loaded normally.... totally oblivious to the danger lurking just millimeters away inside the case.

---

### Post by Lostincyberspace on 2008-06-10
I have a similar problem when I install it I tell it to install on (hd0) since I have 2 hard drives one on a controller card (which is not bootable), one on the mother board (which is). the problem comes in where sometimes it will choose the one on the controller card to write to the mbr and sometimes it will write to the other one but has it as sdb instead of sda so it wont boot and drives me crazy. do you have any advice?

---

### Post by Pumalite on 2008-06-11
You have to edit menu.lst reflecting the changes or change the HD boot order in BIOS. If you have a mix of IDE and SATA; Ubuntu will probably try to boot the IDE first. The solution is to have both OS's in the first drive and keep the second for storage or a separate /home for Ubuntu:
[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)
[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213639](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213639)

---

