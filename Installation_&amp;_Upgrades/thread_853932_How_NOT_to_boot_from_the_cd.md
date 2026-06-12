---
title: "How NOT to boot from the cd?"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by SalmonBoy11 on 2008-07-09
Hi, I just installed ubuntu 8.04 for the first time. Once I finished installing it, the program prompted me to restart, so I did. And now that I'm trying to reboot and log into my ubuntu system on my hard drive, It still thinks I'm trying to boot from the cd. "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER" comes up. when I put the cd in and try to boot from the cd it starts right up. I want to boot from my hard drive, so any help you guys could offer me would be very useful. Thanks in advance.

P.S. I don't know anything about the system specs, cause I got this computer at a garage sale. What I do know is that it used to be a windows XP before I formatted the hard drive, and that it can run ubuntu 8.04 off the cd flawlessly.

P.S.S. Changing the boot order so that my Hard Drive is frist on the list doesn't change anything either.

---

### Post by iaculallad on 2008-07-09
EDIT: Do you have 2 or more physical drives installed on your system?

OR

Try to boot using your liveCD and on the terminal:

```
fdisk -l
```

and post whatever displays

---

### Post by SalmonBoy11 on 2008-07-09
Nope

also, when I boot from the cd and choose the option that says to boot from first hard disk it says:

Booting from local disk...
isolinux: Disk error 01, AX = 0201, drive 80

Boot failed: press a key to retry...

edit: I don't quite know what you mean, livecd as in the ubuntu 8.04 installation disk?

---

### Post by iaculallad on 2008-07-09
> **SalmonBoy11 said:**
> Nope

also, when I boot from the cd and choose the option that says to boot from first hard disk it says:

Booting from local disk...
isolinux: Disk error 01, AX = 0201, drive 80

Boot failed: press a key to retry...

edit: I don't quite know what you mean, livecd as in the ubuntu 8.04 installation disk?

Yes, try to boot using the LiveCD and post whatever displays when you issue the command below on the terminal.

```
fdisk -l
```

---

### Post by SalmonBoy11 on 2008-07-09
What terminal? (Sorry if I'm being stupid :()

---

### Post by iaculallad on 2008-07-09
> **SalmonBoy11 said:**
> What terminal? (Sorry if I'm being stupid :()

A quote from this [thread]("http://ubuntuforums.org/showthread.php?t=622850") (having the same problem as yours):

> MOST IMPORTANT!!!!! Make sure the IDE cables are connected correctly as if they were CS (Cable Select) - the HDD is closest to the motherboard & CD/DVD is at the end - it didn't matter to the system whether or not the components were jumpered master/slave

---

### Post by SalmonBoy11 on 2008-07-09
Ok, the cables were wrong, I rearranged the cd and hd in the cable and it worked. Thanks a ton for bein so patient!

---

