---
title: "Ubuntu upgrade to 14.04 put Grub on Windows Disk - how do I rebuild the MBR?"
date: 2014-04-28
forum: Installation &amp; Upgrades
---

### Post by Subdla on 2014-04-28
I upgraded to Ubuntu 14.04.
This destroyed the Grub on my Ubuntu disk - using Bios to boot to this disk resulted in Grub rescue>.
The upgrade put the Grub boot on my Windows XP disk.
I booted to Ubuntu and installed the Boot-Repair application.
I used Boot Repair to re-create the Grub on my Ubuntu disk.
    - On the main menu I selected Reinstall Grub and unhide menu - the default
    - I used advanced options
    - I selected the Ubuntu disk as the boot disk.
    - I placed the Grub into the Ubuntu disk.
    - this appeared to work - I can now select the Ubuntu disk from my Bios and then boot to it.
- (There was some error which I allowed to be reported - but it did not seem to cause any problems)

I now want to repair the MBR on my Windows XP boot disk so it does not go through Grub to boot.
    - Do I select repair the boot of the computer and select the drive - then apply?
    - Will it only do that and not execute the other options?

From the main Boot-Repair screen I created a boot info summary.

[http://paste2.org/E3amws3E](http://paste2.org/E3amws3E)

---

### Post by pfeiffep on 2014-04-28
[This]("https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader") might help

---

### Post by oldfred on 2014-04-28
+1 on pfeiffep's link

I do not like Boot-Repairs auto fix when you have more than one hard drive. It just installs grub to every MBR. It may be so a user does not have to go into BIOS to change to boot Ubuntu drive with grub in the MBR.
With different installs in didfferent drives you do want each install to have its boot loader in that drive's MBR.
You can use Boot-Repair's advanced option and choose system and choose drive to update its MBR with that system's boot.

---

### Post by Subdla on 2014-04-28
Thanks.  I had to repair my W7 laptop a couple years ago in the same way after updating Ubuntu.  I used the Windows 7 disk and selected repair, etc.  The tutorial is what I was looking for.  I am sure that will work.  I do not trust the Boot-Repair to update the MBR.  I tried that a couple of years ago and it did not rebuild the MBR on my W7 OS.

---

### Post by pfeiffep on 2014-04-28
If this solves your problem [please mark thread 'solved']("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

