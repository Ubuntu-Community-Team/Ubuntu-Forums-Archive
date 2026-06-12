---
title: "Install hangs on 10.10"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by evilnone on 2011-01-07
I am trying to install a fresh install of Ubuntu 10.10 i386 on to an ASUS N70sv laptop.  When I tried booting from the CD it just hangs with a blinking curser.  I tried using a USB flash for install and it gets stuck on "Registered Taskstats Version 1" when I try to install or try to run from USB Drive.  Does anyone know of anything that could be the cause?

---

### Post by evilnone on 2011-01-07
I just wanted to add that this laptop just was returned from RMA and I currently have the same laptop model (they were both ordered at the same time) with Ubuntu 10.10 installed on mine without having an issues.

---

### Post by Bucky Ball on 2011-01-07
Can you get to a desktop by booting from the LiveCD without any issues?

What kernel is the working machine using? The latest kernel for 10.10 (2.6.35-24) is problematic right now and if you downloaded the ISO recently and that is what you are using that could be your problem. The Ubiquity installer seems a bit screwed. ;)

What you could try is downloading the 'alternate' ISO rather than the Desktop image. It is text based but exactly the same without the pretty graphics.

---

### Post by evilnone on 2011-01-07
No, it hangs on the install CD as well.

Edit: I also have tried the 64bit as well with the same results

---

### Post by Bucky Ball on 2011-01-07
Try the alternate as suggested in my last post. Just edited it.

---

### Post by evilnone on 2011-01-07
ok will try the alternative, will report back

---

### Post by evilnone on 2011-01-07
after trying the alternative disc it hangs on a blank screen.  Still freezing.

---

### Post by Bucky Ball on 2011-01-07
Download 10.04 LTS, burn a CD, and see if that has the same issues.

Latest is NOT always the greatest and the current kernel used by 10.10, 2.6.35-24, is problematic on some machines at the moment. Specifically the Ubiquity installer and problems with some Broadcom wireless cards. ;)

---

### Post by m_e_71 on 2011-02-04
The issue seems to be related to ASUS laptops:

[http://ubuntuforums.org/showthread.php?p=10331672#post10331672](http://ubuntuforums.org/showthread.php?p=10331672#post10331672)

---

### Post by VeRychard on 2012-04-17
I SOLVED IT!!!!!

If you have an Asus laptop like me, or you have this option in BIOS CHECK IT!!!!!

Go to bios >
Security> I / O interface Security> [COLOR=red]"New interface card"[/COLOR] or so. SET IT TO LOCKED!!! 

After that everything went fine for me ^^

Booted properly

Hope it helps :)

---

### Post by Bucky Ball on 2012-04-17
Please mark thread as 'Solved' from Thread Tools and this will help others. ;)

---

### Post by oldos2er on 2012-04-17
Closed, necromancy.

---

