---
title: "Problem installing Ubuntu with WIN XP."
date: 2010-09-21
forum: Installation &amp; Upgrades
---

### Post by carlitos_30 on 2010-09-21
Hello:

 Im pretty noob with Linux. I have  a PC with 2 hard disks. In one hard disk i have WINDOWS XP installed. In the other hard disk I installed Ubuntu. This hard disk has 2 partitions. I installed ubuntu in one of these partitions ( I put in that partition the "/" character). Ubuntu is running fine now, but when I tried to load WIN XP I couldnt start it . Appears an error: " MBR ERROR 3, try load from floppy". I made some research and one possible solution is to apply the FIXMBR command from Windows Console. But if I do this I fear that Linux wont work anymore. What does that error mean? How do I fix it?

---

### Post by Mark Phelps on 2010-09-22
If you really have two physical drives and you made the mistake of installing GRUB to the XP drive, then yes, restoring the XP MBR to that drive will wipe out GRUB.

But ... that's what I recommend you do.

Then, disconnect the XP drive, leaving the Ubuntu drive connected, and reinstall GRUB to THAT drive using the instructions in Section 11 of the link below:

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

After that, reconnect the XP drive but continue to boot from the Ubuntu drive, open a terminal, and enter "sudo update-grub".  This will regenerate the GRUB menu and add an entry for XP.

When you reboot, you should be presented a GRUB menu with entries for XP and Ubuntu.

---

