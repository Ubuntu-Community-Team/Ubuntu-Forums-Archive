---
title: "Disk read error! Press ctrl+alt+delete! Bad MBR! Can't boot from CD!"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by Eddievanzant on 2010-05-03
so I installed ubuntu in an attempt to begin my life as a hacker or programmer, unfortunately I've had some big problems.

I cut 25 gb from my XP partition and installed ubuntu 9 and since then, whenever I choose to load xp from grub, all I get is a flashing cursor. Ubuntu runs fine but I tried to use ms-sys to fix my MBR and it said it worked but now when I boot a get "a disk read error occurrd press ctrl alt delete to restart". So I couldn't even boot ubuntu

so I put the ubuntu disk in and reinstalled on the same 25 gb partition and it ran fine (xp still doesn't),  but I tried fixing the MBR again and this time, not only does xp and ubuntu not work, but my cd drive won't even boot the ubuntu or xp disc!

I'm finally at the point where I have no idea what to do. I do not believe that there is any hardware problem. I just think I've messed with my pc too much and I just need to format my drive and reinstall everything, but now my disk drive seems to not work either so crap.

I press esc when my pc is booting and select boot from cd, the screen says boot from cd, the cd spins for a few seconds, then it just goes to the hard drive and says disk read error press ctrl alt dlelet to restart.

If anyone can just help me get the cd drive working, I'm just going to format my drive.

Please help!

---

### Post by techunit on 2010-05-03
Ok well there was just another post someone posted looking for help on a similar issue...

First Try this:

```
sudo update-grub
```

This should do the trick if not look here:

[http://ubuntuforums.org/showthread.php?t=1471896](http://ubuntuforums.org/showthread.php?t=1471896)

---

### Post by Eddievanzant on 2010-05-04
Okay thanks I'll try that once I can but right now I can't even lget to grub or ubuntu and :KSmy cd drive still won't work. I put I the ubuntu disc, select to boot from cd, it says "Boot from CD :" for a second and then says "a disk read error occured press ctrl alt del to restart" so it's like it doesn't recognize that the disc is bootable or something. The same thing happens with the xp disc.

---

### Post by Eddievanzant on 2010-05-04
Does anyone have any idea why my cd won't boot?

---

