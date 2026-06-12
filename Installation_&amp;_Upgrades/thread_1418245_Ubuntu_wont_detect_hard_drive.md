---
title: "Ubuntu wont detect hard drive"
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by SSStylish on 2010-02-28
[LEFT][SIZE=2]Hello,
I recently got the ubuntu 9.10 cd desktop-i386 (i ordered it from canonical) and i tried to install it , but when i came to step 4 (to pratition the HDD) it doesent recognize my hard drive (3 partitions : 15 gb ext4, 37gb ntfs , 25 gb ntfs). I run Windows XP on one partition without problem. [/SIZE][SIZE=2]I reserved that ext4 for karmic. Also i booted up the live cd  to try smth in the terminal...i tried with sudo apt-get -y remove dmraid but still doesnt work.Also when i looked into Places menu the HDD partitions were not there.Also i dont know why but if i dont select  ACPI=OFF, ofter booting up  desktop freezes after 10 sec...when i select ACPI=OFF it runs great. And when i select ACPI=OFF and NOLAPIC from the F6 boot menu , ubuntu detects my hard drive in places menu and instalation menu,but after 15-20 sec the screen freezes and i must restart :( .I dont think it's the cd because when i teseted the live cd at my friends computer it detects their HDD, even without NOLAPIC ! I dont know what to do and i really need Ubuntu. Do i need to upgrade my BIOS or what ? PLS HELP ![/SIZE]
[/LEFT]

---

### Post by raymondh on 2010-02-28
Just a hunch .....

those 3 partitions you mentioned, are they all primary and is there any recovery partition that you may not have mentioned?

What I'm leading at is that I seem to recall a thread wherein karmic will not insist on installing when the max partition limit has been reached.

If this hunch is right, try deleting the ext4 partition, keeping it unallocated and then see if the liveCD will recognize.  If so, then just install in largest unallocated space.

Also ... why the command ***sudo apt-get -y remove dmrai***d instead of ***sudo apt-get remove dmraid***?

Raymond

---

### Post by SSStylish on 2010-04-08
I updated my bios and it worked.Ubuntu now works :)

---

