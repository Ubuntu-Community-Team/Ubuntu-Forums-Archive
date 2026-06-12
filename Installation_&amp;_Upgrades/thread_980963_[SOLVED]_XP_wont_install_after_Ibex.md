---
title: "[SOLVED] XP wont install after Ibex"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by Valpskott on 2008-11-13
Ok, here is the story... I thought I'd get rid of XP and switch to Ubuntu, but just in case I needed to run some Windows software, I thought it would be nice to install Vista as well and setup a Dual Boot.

So, I began with installing Vista on (hd0,0), then I installed Ubuntu 8.10 on(hd0,2)... Both OS's booted just fine but I had problems with installing proper GFX-drivers for Vista and I also had problems with Vista activation, so I decided to format that partition and install XP to it.

During XP install, after the first reboot, it wont continue with install, and it didn't boot from any other partition. So I booted from 8.10 live cd, restored Grub, now Ubuntu works fine, but I still can't continue with install of XP. So I downloaded TinyXP rev.9, burned it to a CD, booted from that CD, reformatted (hd0,0), and continued with install of XP, after first reboot(during install) the installation won't continue(just as with the other XP install attempt).

I've installed XP maybe 20 times in my lifetime, maybe 4-5 on this computer alone, so I know it should work, and I know how to do it(except for right now, that is).

---

### Post by lifestream on 2008-11-13
I might be wrong, and I do realize you know what you are doing.
But I could swear I read somewhere that you must install XP first, then Ubuntu, because XP is picky about the hard drive setup. Shame.

(Not sure, because I haven't used windows in years, but I believe that's correct)


Hmmm you say "it won't continue the install" but you don't explain why. Does it give an error message? If so, what?
Does it quit on you? Does it crash? Does it keep rebooting the PC? What happens? Does it cancel? Why, does it say why?

---

### Post by Valpskott on 2008-11-13
Well, it stopped at "Starting Up ..." or something like that(before going to graphical part of installation), and nothing happens. But I thought about it and relized it could be some issue with going from Vista to XP, so I googled it and found a solution. It had to do with the NTFS partitioning beeing somewhat diffrent done in Vista, and with some motherboards it just goes wrong when one goes back to XP from Vista.

I've also read that one should install Windows before Ubuntu, which I tried, but after setting up Ubuntu with fonts, graphic drivers, themes, software, compiz fusion settings etc, I would like to avoid reinstalling Ubuntu.

My solution was to delete the partition and then adding it again. So, problem solved, but anyway, thanks for showing interest :)

---

### Post by Valpskott on 2008-11-14
For more info and solution, read

[http://support.microsoft.com/kb/931760](http://support.microsoft.com/kb/931760)

---

