---
title: "Dual boot wind0ws 7 and ubuntu 9.10"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by nerdtron on 2009-12-16
Hello everyone!
I'm currently running windows 7 on my newly formatted PC.
Win7 is installed on a SATA hard disk and I also have SATA dvd drive.
I have an extra 80Gb hard drive connected via IDE and i want to install Ubuntu Karmic on it.
Can somebody please guide me on how to properly install it?
Its my 1st time to try and I'm worried to be unable to boot 7 if something goes wrong.
Any help will be appreciated. Thank you very much!

---

### Post by presence1960 on 2009-12-16
> **nerdtron said:**
> Hello everyone!
I'm currently running windows 7 on my newly formatted PC.
Win7 is installed on a SATA hard disk and I also have SATA dvd drive.
I have an extra 80Gb hard drive connected via IDE and i want to install Ubuntu Karmic on it.
Can somebody please guide me on how to properly install it?
Its my 1st time to try and I'm worried to be unable to boot 7 if something goes wrong.
Any help will be appreciated. Thank you very much!

Make the IDE disk first hard disk to boot in BIOS, then boot the Live CD and install Ubuntu to the IDE disk. When you get to the Ready to install window of the installation process click the advanced button and choose /dev/sdx where x = your IDE disk. This will put GRUB on MBR of IDE disk so when you boot GRUB will take over and give you choice of Ubuntu or Windows.

Another advantage of this setup is that by putting GRUB on the mBR of IDE and having that boot first your windows bootloader on MBR of SATA disk remains untouched.

---

### Post by raymondh on 2009-12-16
> **nerdtron said:**
> Hello everyone!
I'm currently running windows 7 on my newly formatted PC.
Win7 is installed on a SATA hard disk and I also have SATA dvd drive.
I have an extra 80Gb hard drive connected via IDE and i want to install Ubuntu Karmic on it.
Can somebody please guide me on how to properly install it?
Its my 1st time to try and I'm worried to be unable to boot 7 if something goes wrong.
Any help will be appreciated. Thank you very much!



EDIT : just saw presence1960's post.  That is a good way to install and boot ubuntu.

---

### Post by maxkam on 2009-12-16
Not to rain on your parade, but I am having a similar problem.  I have an old work station (HP xw 6000) with dual Xenon processors and 2 seperate IDE HDD's.  One has Karmic and the other has Windows7 (another to be added later for Snow Leopard).  Has anyone tried a dual boot.  I tried setting the bios to configure dual boot, but I don't think that option is supported due to the age of the machine.  When both HDD's are connected, only 7 boots.  Please advise.

---

### Post by presence1960 on 2009-12-16
> **maxkam said:**
> Not to rain on your parade, but I am having a similar problem.  I have an old work station (HP xw 6000) with dual Xenon processors and 2 seperate IDE HDD's.  One has Karmic and the other has Windows7 (another to be added later for Snow Leopard).  Has anyone tried a dual boot.  I tried setting the bios to configure dual boot, but I don't think that option is supported due to the age of the machine.  When both HDD's are connected, only 7 boots.  Please advise.

Try switching the boot order of the disks in BIOS, if that is not possible you will have to open your case and switch the jumper settings or if you have a master/slave cable select connection from the mobo to the disks switch the connections.

The problem is that the disk with windows is booting, the disk with Ubuntu has GRUB on the MBR- that is the disk you want to boot first.

**Next time please start your own thread. It becomes very difficult to help more than one person in the same thread. If you need more help with this create a thread then kindly leave a link to it on this thread. Thanks for the cooperation.**

---

### Post by nerdtron on 2009-12-16
Wow! Thanks! I got the point!
I'm going to try it now...I'll let you know how it comes!

---

### Post by presence1960 on 2009-12-16
> **nerdtron said:**
> Wow! Thanks! I got the point!
I'm going to try it now...I'll let you know how it comes!

Any question/problems post back.

---

### Post by nerdtron on 2009-12-17
I tried going to the BIOS to make the IDE the 1st boot drive but somehow it doesn't let me choose it.
My 1st boot device is the dvd drive (it's ok) but the 2nd boot device is the SATA drive..I can't change it. I don't know why....Is there something I'm missing?

---

### Post by presence1960 on 2009-12-17
> **nerdtron said:**
> I tried going to the BIOS to make the IDE the 1st boot drive but somehow it doesn't let me choose it.
My 1st boot device is the dvd drive (it's ok) but the 2nd boot device is the SATA drive..I can't change it. I don't know why....Is there something I'm missing?

Refer to your computer documentation or the manufacturer's website for your manual. On my BIOS I have to highlight the disk and click + or - to change that disk's position in the boot order. + will move it up in the order and - will move it down in the order. There has to be a way to change the boot order. You are going to have to do the legwork of finding the info on how to change the boot order for your machine.

---

### Post by nerdtron on 2009-12-24
Finally! I installed karmic successfully alongside windows 7!
Thank you for all your help! :-)

---

### Post by raymondh on 2009-12-24
> **nerdtron said:**
> Finally! I installed karmic successfully alongside windows 7!
Thank you for all your help! :-)

Congratulations and well done.

Maligayang pasko at manigong bagong taon :)

Regards,

---

