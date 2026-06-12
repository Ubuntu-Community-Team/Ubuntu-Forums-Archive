---
title: "Live CD won't run"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by Minty :) on 2010-04-04
Hello

I have a **Ubuntu, Kubuntu 9.10 live CD which i know work** because i have installed on my other computer, (hp pavillion ze2000), and also **linux mint 8 and openSUSE 11.2, which also run/work.** **However when i put them in my current computer and restart, the computer simply ignores them and carries on with vista.** I have been testing out the live CD's on VirtualBox and on my second computer and they look pretty nifty :) But the computer just ignores them as if they wern't there :(

Spefications :

Hp Pavillion dv6 notebook PC
Windows Vista service pack 2
AMD athlon X2 Dual Core
2.00 GB RAM
32 bit
X86-based PC

Thanks in advance ;)

---

### Post by byStanderone on 2010-04-04
...have you chech the cmos setting on that particula computer in question, is it set to boot from the cd drive  first?

---

### Post by Minty :) on 2010-04-04
> **byStanderone said:**
> ...have you chech the cmos setting on that particula computer in question, is it set to boot from the cd drive  first?

:O

Whats CMOS ?
And how would i change it ?

Thanks for the responce

---

### Post by akakingess on 2010-04-04
> **Minty :) said:**
> :O

Whats CMOS ?
And how would i change it ?

Thanks for the responce

The other poster is referring to your BIOS settings on the computer you are trying to boot from the live CD right now. Usually, when you first turn on the computer you will see the BIOS screen with some choices (usually F12, F10, ESC, (depends on the BIOS)), so you need to press the proper button and get into your computers BIOS settings and make sure the boot order is correct, or at least that it looks for a bootable CD as #1, then moves on to the hard drive. That way, when the BIOS is looking for what to boot from, it will check the CD-ROM drive first and if it is bootable such as a Live CD, it will boot from it, and if there is not a bootable CD in the drive, it just moves on to the next option. Also, there may be an option to boot from USB as well, and you may want to put that up near the top of the list if you start doing what I am, which is dual-booting, and occasionally booting from a USB stick (sorry to go off on a tangent), hope this info helps and if you have more questions let us know :)

---

### Post by Minty :) on 2010-04-04
> **akakingess said:**
> The other poster is referring to your BIOS settings on the computer you are trying to boot from the live CD right now. Usually, when you first turn on the computer you will see the BIOS screen with some choices (usually F12, F10, ESC, (depends on the BIOS)), so you need to press the proper button and get into your computers BIOS settings and make sure the boot order is correct, or at least that it looks for a bootable CD as #1, then moves on to the hard drive. That way, when the BIOS is looking for what to boot from, it will check the CD-ROM drive first and if it is bootable such as a Live CD, it will boot from it, and if there is not a bootable CD in the drive, it just moves on to the next option. Also, there may be an option to boot from USB as well, and you may want to put that up near the top of the list if you start doing what I am, which is dual-booting, and occasionally booting from a USB stick (sorry to go off on a tangent), hope this info helps and if you have more questions let us know :)

Thanks alot :)

They said you guys were good !

I also looked at this [http://answers.yahoo.com/question/index?qid=20080216214457AAykvTq](http://answers.yahoo.com/question/index?qid=20080216214457AAykvTq) and you guys have really cleared up alot of things for me :p

---

### Post by akakingess on 2010-04-04
> **Minty :) said:**
> Thanks alot :)

They said you guys were good !

I also looked at this [http://answers.yahoo.com/question/index?qid=20080216214457AAykvTq](http://answers.yahoo.com/question/index?qid=20080216214457AAykvTq) and you guys have really cleared up alot of things for me :p

That's what I love about this community, friendly, and plenty of different knowledge levels, I am still a novice and just read these forums to learn and I have learned plenty. Just one more note if you don't mind, if you have gotten your issue resolved, please go to the top of this thread and under thread tools you should have an option to mark this thread as "solved", that way others don't NEED to look at it to see if they are needed, but they can still look at it and add more input. Just a way to sort out those threads that are solved and those that still need assistance. Welcome to the community and have fun learning (I certainly have)  :)

---

### Post by byStanderone on 2010-04-04
...akakingess, my thanks as well.

---

