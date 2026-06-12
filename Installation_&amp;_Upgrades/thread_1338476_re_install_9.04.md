---
title: "re install 9.04"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by stp1974 on 2009-11-26
hello everyone.... i am very confused here.

i recently installed ubuntu 9.04 from vista on my laptop using a dvd i burned the iso too.  i have played around with it a bit and now want to re install a fresh 9.04 on the same laptop and start from scratch with some of the things i have learned.

i put the same dvd in to drive, and restart.... no boot from cd... again...no boot from cd.

i went into grub and i see no option for boot from cd.  why does everything with linux have to be a huge project!! :P

arghhhhhhhhhh lol

---

### Post by phillw on 2009-11-26
Hi

Step 1)  Boot of the CD
2) Install Ubuntu - as you've already had a ubuntu install - so, just tell it where you want it.
3) ...... There isn't a step 3

I don't think that's too hard an 'issue' ;)

If you're at all unsure of the partition (area) of your hard disk, pop back the result of 

```
sudo fdisk -l

```and one of the guys and gals here will let you know. (I'll be kicking around somewhere if you get stuck, as well)


/edit  If you can't boot from the CD - check your BIOS is set to having the cd/dvd drive as the 1st boot device

Regards,

Phill.

---

### Post by stp1974 on 2009-11-26
i agree it should not be hard.... problem is. the computer is not booting off the cd anymore.  it did the first time i installed 9.04.  

is there something special i have to do to get the computer to boot from the cd now that i already have 9.04 installed?

thanks

---

### Post by audiomick on 2009-11-26
Like Phil said, you should go into BIOS and make sure it is set to look for a bootable system on the CD before any of the HD's

---

### Post by phillw on 2009-11-26
> **stp1974 said:**
> i agree it should not be hard.... problem is. the computer is not booting off the cd anymore.  it did the first time i installed 9.04.  

is there something special i have to do to get the computer to boot from the cd now that i already have 9.04 installed?

thanks

Probable cause == BIOS booting order
Possible cause == damaged CD 

If you have checked your BIOS boot priority, then it is check the CD time -->  [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Working CD is essential - Damaged CD will have you chasing your self around and round in circles.

Phill.

---

### Post by stp1974 on 2009-11-26
ok.. i looked for bios menu when rebooting.  it does not show up anymore.  when i boot the computer it goes straight to something called "grub" and then on to the ubuntu log in page.  it completely skips anywhere to enter the bios???  

this may seem simple to some of you power users.... i am not one of them :(

thanks

---

### Post by phillw on 2009-11-26
> **stp1974 said:**
> ok.. i looked for bios menu when rebooting.  it does not show up anymore.  when i boot the computer it goes straight to something called "grub" and then on to the ubuntu log in page.  it completely skips anywhere to enter the bios???  

this may seem simple to some of you power users.... i am not one of them :(

thanks


Kicking in the bios is done before ANY operating system is actioned. It is part of the POST checking that computers do. If you tell me your make / model computer I'll tell you what button to press - it's usually ESCape key, F2 key of F11 key.

The message to go into bios is pretty quick - so keep your wits about you when you boot :D

Phill.

---

### Post by phillw on 2009-11-26
>  this may seem simple to some of you power users.... i am not one of them :sad:

None of us are power users, you will, however, find people on this forum who well remember being a 'noobie'  We all were, and in many ways still are.

I always offer 1-2-1 support for when people get 'stuck' - My buddy list on AIM/AOL IM is constantly growing :p

Stay calm, don't get stressed - that answer is out there. Altering the mind-set from win or mac to ubuntu takes a little time. To cheer you up have a read through this --> [http://linuxgazette.net/issue45/orr.html](http://linuxgazette.net/issue45/orr.html)

When you find it funny, you'll know you're a Linux user ;-)

Regards,

Phill.

---

