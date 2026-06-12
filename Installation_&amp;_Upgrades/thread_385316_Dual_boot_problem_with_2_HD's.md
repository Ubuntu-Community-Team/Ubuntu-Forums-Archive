---
title: "Dual boot problem with 2 HD's"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by adyhay on 2007-03-15
Hi, this is my first post to the ubuntu forums and I would be very grateful for any help with the following problem. I today added an extra HD to my PC. Installed XP to the master dive and then installed ubuntu to the slave drive. All seemed to go well until I booted the machine up and I got an error as GRUB loaded...... ERROR 21. I have successfully managed to do dual boots on a single HD with ubuntu, xubuntu and kubuntu. On one HD the Grub loader has always worked like a dream. I have no idea why it would not work with 2 hard drives. I did notice that my bios only showed the c drive as an option to boot from. Not sure if this makes any difference.....


Thanks   Adrian

Dell p4 geforce 4 512ram, ubuntu 6.10,

---

### Post by geirha on 2007-03-15
[QUOTE="http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors"]21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. [/QUOTE]

That's what the error means... perhaps the jumpers on the disks are wrong?

---

### Post by MichaelSM on 2007-03-23
Hi. I'm not too sure if this will help, but I was happy with my outcome. I have an old Celeron 1.7 PC, and it has two HDs installed. One is an 80 gig partitioned with Xandros and Window$ XP, the other a 40 gig with Ubuntu 6.10. 
With everything plugged in-and don't ask me about Master/Slave jumpers, because I think they're just as I had them when they worked alone- I just started it all up then hit F8 which got me into a part of BIOS with a window which allowed me to select either IDE 0 or IDE 1 as a first boot option. I must have picked the right one (sorry I can't be more exact as I am a newbie) because now when I power  up I get the Xandros multiple choice starter which lists the OS options available. I just use the down arrow to select the OS I want to use. or, since I have tons of stuff on Xandros, that OS starts automatically as default after about 30 seconds. 
It's conceivable that I just lucked in. I don't know if the Ubuntu 6.10, my preferred OS, would give a similar choice of OS if I'd selected the other IDE option in BIOS. And NO! I have zero interest in changing something which works. Um, sort of...this can all get a bit anal. 
Cheers, Mike.

---

### Post by zvacet on 2007-03-23
[http://ubuntuforums.org/showthread.php?t=275728&highlight=dual+boot]("http://ubuntuforums.org/showthread.php?t=275728&highlight=dual+boot")

---

