---
title: "setting up dual booting on seperate drives?"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by TCMGO on 2011-03-04
[FONT=Times New Roman]I am using an Abit NF7-S V2 mobo to set up my dual boot system where each OS (XP & Ubuntu) will run on a totally separate HD (as opposed to both OS’s being set up on one HD).  Since they will be running as stand alone boot drives, how does one set it all up so that one can boot from one or the other?  I don’t see how I can do it from the bios.  How do I do it?[/FONT]
[FONT=Times New Roman][/FONT] 
[FONT=Times New Roman]Thanks[/FONT]
[FONT=Times New Roman][/FONT] 
[FONT=Times New Roman]TCMGO[/FONT]

---

### Post by the.drizzle on 2011-03-04
Simply put XP on one hd, say /dev/sda, and the Ubuntu install on /dev/sdb.  If you install XP first, Ubuntu will automatically configure GRUB to chainload your XP install as a bootup option, so all you have to do is make the drive containing the linux install the first boot device--this is done in the BIOS setup.

---

### Post by YesWeCan on 2011-03-04
The safest method is to install the OSes separately, the other drive being disconnected.
Once both are installed, connect both drives and configure the bios to boot first from the Ubuntu drive.
Once Ubntu has booted, run console command 'sudo update-grub'.
When you next reboot you will get a menu giving you choice of XP or Ubuntu.

---

