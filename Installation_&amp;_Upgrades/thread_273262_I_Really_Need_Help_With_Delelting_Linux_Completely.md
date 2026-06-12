---
title: "I Really Need Help With Delelting Linux Completely And Installing Windows Xp.."
date: 2006-10-07
forum: Installation &amp; Upgrades
---

### Post by Da1nonly89 on 2006-10-07
I WANT TO DELETE LINUX FROM MY COMPUTER AND INSTALL WINDOWS XP FROM A RE-INSTALL CD....I AM COMPLETELY LOST....I DONT EVEN KNOW HOW TO PARTITION AT ALLL...I NEEED HELPP...SOME1 PLEASE!!!!!!!!1:eek:

---

### Post by louieb on 2006-10-07
No need to shout. What happens when you put you windows CD in and tell it to install?

---

### Post by Da1nonly89 on 2006-10-07
When i insert the cd..i click on the cd rom drive...then i click on setup.exe.. this asks me if i want to install windows..i click on the install button...then a error message comes up saying that it had encountered a problem and that i need to rerun setup...it weird...do i need to partition or w/e???i dont even know what partitioning is...well if you can please help!!

---

### Post by brt on 2006-10-07
i think you should: 

* insert CD
* reboot computer
* make sure (in the bios) that it boots from CD into the installer

---

### Post by Da1nonly89 on 2006-10-07
how do i make sure (in the bios) that it botts from CD into the installer?

---

### Post by brt on 2006-10-07
if your computer starts, in the very first beginning, depending on your bios you have to press a key, mostly <del>. then you're entering the BIOS.
now look for your boot-options/priority and make sure that it first boots from CDROM, and 2nd from Harddisk. You should be very carefull with what you are changing in the bios, as it can make your computer unbootable.

---

### Post by Da1nonly89 on 2006-10-07
ok...when my comp..starts i have to press esc...it then gives me different modes i think...im going to go try this and message u back ok if it doesn't work...

---

### Post by brt on 2006-10-07
sometimes i would really love to act like the BOFH ;)

---

### Post by Da1nonly89 on 2006-10-07
okay im at the partition screen..it asks me 

if i want to install windows xp on selected, press ENTER

to create a partition in the unpartitioned, press C

to delete the selected partion, press D.

which one should i pick?

---

### Post by Da1nonly89 on 2006-10-07
partition1...has 18363 MB of free space..
partition2...has 706 MB of free space..

should i delete them both??

if i want to run both linux and windows what do i do??

---

### Post by doobit on 2006-10-07
> **Da1nonly89 said:**
> partition1...has 18363 MB of free space..
partition2...has 706 MB of free space..

should i delete them both??

if i want to run both linux and windows what do i do??

Please read [this]("http://www.ehomeupgrade.com/entry/2622/how-to_dual-boot_ubuntu") installation guide.

---

### Post by crokett on 2006-10-07
> **Da1nonly89 said:**
> partition1...has 18363 MB of free space..
partition2...has 706 MB of free space..

should i delete them both??

if i want to run both linux and windows what do i do??

Since you need separate partitions for Linx and Windows, if you want to run both you really don;t have a choice except to delete your 18363 MB partition and create 2 smaller ones.  Neither OS will install in 706MB.

---

### Post by doobit on 2006-10-07
If you really want to have a dual boot with Windows XP and Linux, then you should delete both, create three or four new ones, like crokett said. You need 3.5 MB for Ubuntu's system files, twice your RAM size for a swap file (if you have a gig of RAM, then you may not need this) and I recommend a separate /home partition as well. The partition that Windows is on needs to be the first Primary one, the rest can be logicals. After you create them, format the Primary partition an NTFS using your Windows XP CD. Leave the rest alone for now.

---

### Post by brt on 2006-10-16
:)

---

