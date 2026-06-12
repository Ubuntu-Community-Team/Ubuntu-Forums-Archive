---
title: "Odd problems with partition utility and install"
date: 2006-10-11
forum: Installation &amp; Upgrades
---

### Post by jaden-excalibur on 2006-10-11
Well, first I'd like to say that I'm new to Linux (except for my brief stint with the FreeSpire live cd, which would not run. *sigh*), and am in need of a guide in some pretty odd and disturbing problems with the part utility.

You see, I tried to use the partitioning utility to resize an NTFS part, and it did about half its job... the 20GB I removed are gone from the part, but their not back on the HDD either! Neither is my HDD listed as 250GB, but 232GB!!! Now, using the live cd for FreeSpire, I managed to get access to GpartEd and did all the required work that way (never saw my 20GB again...). I used 
"chkdsk /f" command in windows to verify my HDD at startup like GpartEd told me to do (still no 20GB), and then proceeded with the install of Ubuntu! WOW, everything worked just great, I had my root ext2, my swap, and I was installing in minutes.

...Boom, it blows up on me. It failed to write the packages to disk, and wouldn't do anything past that without a complete failure and loss of composure.. giving error code 1. Now i'm two OS's in the gutter and my MRB for windows is gone due to the FreeSpire install attempt..(sigh).

So now im here, hoping some Linux genius can save my pc from the curse that is microsoft.](*,)

My stats are...:
-HP media center pc
-dual dvd rom/ram drives
-AMD Athlon 64 X2 dual core 4200+
-1GB dual channel DDR2 RAM
-250GB SATA SAMSUNG HDD
-ATI X300-700

     -Thank you in advance

---

### Post by gn2 on 2006-10-11
If it's possible to add a second hard drive, you could try this option:

[http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)
.

---

### Post by jaden-excalibur on 2006-10-11
> **gn2 said:**
> If it's possible to add a second hard drive, you could try this option:

[http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)
.

Thank you for the tip.. too bad my MRB is already skewered into bits. But my HP media center pc does have a semi external usb HDD mount (its kindof a cosy plug in). So its not impossible.... I'll consider it! But if you can help with restoring the windows MRB untill thats ruled out, it'd be appreciated. Actualy, would that be solved by using the sys restore OS and reverting to last week?

THNX!

---

### Post by gn2 on 2006-10-11
> **jaden-excalibur said:**
> Thank you for the tip.. too bad my MRB is already skewered into bits. But my HP media center pc does have a semi external usb HDD mount (its kindof a cosy plug in). So its not impossible.... I'll consider it! But if you can help with restoring the windows MRB untill thats ruled out, it'd be appreciated. Actualy, would that be solved by using the sys restore OS and reverting to last week?

THNX!

System restore won't help, you need to use the Windows install CD, boot from it, select recovery mode and run the command fixmbr.

If you're getting Windows to boot at all then I would advise leaving things as they are.

Installing Ubuntu on a USB drive is a headache, PCLinuxOS is a much better bet for this option, because it has a GUI installer, draklive which will do it easily for you from start to finish.
.

---

### Post by jaden-excalibur on 2006-10-11
This is unfortunate... those bastards at Future Shop jiped me of my Windows cd, the policy is that if its got a backup OS then they can keep the thing..?!?! I've known that this would be a problem.. AHHHHHHH!!!!!!....ok. calm down.. I can still use my dads XP cd to call the function...(*sigh*)..

Why is it that when I try to improve on my machine, the unthinkable happens? I'm stuck without FreeSpire untill the newer kernel is introduced in version 1.1... in January or later. The OS is not compatible with my SATA drive, same with many others, it just jams at the USB detection phase. Thats another thing I was hoping to get help with here, I know that Ubuntu's community is experienced and top notch. AND, there is still the issue with my missing 20GB of space (which I know is of course still there), and figuring out how get it back. I think that this is causing problems with the install.

Also, I was incorrect with the reference to the USB external mount, it seems to be some other connection, as I can't see very well into the opening.

Thanks again.

---

### Post by jaden-excalibur on 2006-10-11
You see, I was hoping to set up a triple boot between CrapSoft XP and FreeSpire, then set up Ubuntu afterwards (I heard freespire was easier to install.. so much for that!). I am very worried that my HP machine will never see a penguin for the rest of its unnatural lifespan...

---

### Post by Sef on 2006-10-11
> You see, I tried to use the partitioning utility to resize an NTFS part, and it did about half its job... the 20GB I removed are gone from the part, but their not back on the HDD either! Neither is my HDD listed as 250GB, but 232GB!!! Now, using the live cd for FreeSpire, I managed to get access to GpartEd and did all the required work that way (never saw my 20GB again...). I used
"chkdsk /f" command in windows to verify my HDD at startup like GpartEd told me to do (still no 20GB), and then proceeded with the install of Ubuntu! WOW, everything worked just great, I had my root ext2, my swap, and I was installing in minutes.


Try [GParted]("http://gparted.sourceforge.net/") to resolve your problem.

> ...Boom, it blows up on me. It failed to write the packages to disk, and wouldn't do anything past that without a complete failure and loss of composure.. giving error code 1. Now i'm two OS's in the gutter and my MRB for windows is gone due to the FreeSpire install attempt..(sigh).


Here is how to [Reinstall GRUB.]("https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28GRUB%29")

---

### Post by jaden-excalibur on 2006-10-11
Well, thats a good link. Too bad I don't have a demo cd, I only got the actual install cd (unless they are one and the same, in which case I'm lost..). Is there a specific ISO for the live CD? If so, where can I find it? I'd love to get it anyway, just to see how it all works in Ubuntu.:)

---

