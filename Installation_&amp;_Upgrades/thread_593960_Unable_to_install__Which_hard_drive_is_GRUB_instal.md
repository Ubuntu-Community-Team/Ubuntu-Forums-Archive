---
title: "Unable to install?  Which hard drive is GRUB installed on?"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by nthwolf on 2007-10-27
Greetings all,

I have a box with 3 hard drives in it.  1-80GB (primary IDE), 1-120GB(secondary IDE) and 1-40GB(no idea).  I have windows installed on the 80GB which has 3 partitions.  The 120GB is used for storage.  I did have Ubuntu 6.x installed on the 40GB hard drive.

I tried installing Ubuntu 7.10 to the 40GB this morning but it failed about 40% through.  It said there was a cd/dvd or hard drive failure.

Before this I noticed that booting to windows kind of stalled.  My questions is this, "where is GRUB installed?"  I'm trying to figure out which hard drive died on me since I was able to boot from the cd/dvd drive.  

If GRUB was installed on the MBR of the windows drive then how to I uninstall GRUB to see if that drive still boots?

Any other suggestions would be appreciated.

Thank you.

Forgot to put in the post how things were installed on this box.  Windows was installed first then the 40GB hard drive was put in and Ubuntu was installed on that.  I just went with the default install options so I'm not really sure where GRUB was installed or anything.

---

### Post by louieb on 2007-10-27
IF you just let Ubuntu install GRUB as default. A pointer to it is installed in the MBR of the  1st boot drive. The GRUB program itself will be in the /boot/grub/  directory of the Ubuntu install. (program name is stage2).

Sounds like you need to change the MBR of the 1st boot drive  to point to the Windows boot loader. This link has  a few different ways of doing just that.  [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

### Post by nthwolf on 2007-10-27
can grub get corrupted even if it was working fine the last time i booted to ubuntu?

i threw in my windows cd and went to the recovery window and typed fixmbr and booted to windows fine.

think it might've been my hard drive that went bad?  it threw an error 15 at me when it was trying to load grub

kinda worried about installing ubuntu to the 40gb drive again because i don't want to spend all that time installing and making it look nice to have the hd crash on me.

---

### Post by louieb on 2007-10-27
Been using Linux about 20 months haven't heard of Grub getting corrupted. But have seen hard drives go bad. Go to the mfg website and get there diag utility. and check the drive out with that.  Won't assure that you  have a good drive but at least you'll know if its gone or going bad.  Most of the time a drive will give some warning before it refuses to do anything perhaps this is yours.

---

