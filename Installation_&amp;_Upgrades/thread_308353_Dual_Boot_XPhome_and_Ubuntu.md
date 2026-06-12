---
title: "Dual Boot XPhome and Ubuntu"
date: 2006-11-27
forum: Installation &amp; Upgrades
---

### Post by Donut417 on 2006-11-27
Well basically I have a 200GB Hard disk with XP home on it. I have an 80Gig hard disk with nothing at all on it. I want to place Ubuntu on the 80Gig Hard disk and dual boot with XP. The only reason I don't want to install Ubuntu on the 200Gig is because I don't have an XP cd and cant afford one, so I cant mess up my current install.

---

### Post by confused57 on 2006-11-28
You might want to read over this "howto", as a possible option of setting up a dualboot:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by galilite on 2006-11-28
You are a very wise person, Donut. 

I just wish I checked all this stuff before I installed Ubuntu and my XP boot record was screwed up by GRUB ](*,) . On the positive side, however, I learned many new things.

In any case, two most important things to remember:

1. Don't panic, if you can't boot, in most cases your files are still intact.
2. Use Linux recovery tools rather than Windows - the latter has this nasty perception that it is alone in the universe. While I tweaked GRUB, everything was there, but after I ran FIXBOOT, the HD became a toast.

There are two ways to dual-boot:
* Install GRUB on the main boot record (MBR) and managing everything from there - should work in theory. I recommend **not** to do this as I see from the forums many people ending up with UNMOUNTABLE_BOOT_VOLUME error or similar nasties. Unfortunately, [COLOR="Red"]this is the default so watch out!!![/COLOR]. If any of the unlucky people come across this thread, you might want to read this:
[http://josephhall.org/grub_install_hda1.html](http://josephhall.org/grub_install_hda1.html)
* Tweak Windows boot loader to point to the Linux partition and continue to boot from there. I believe, this is the safest option although it takes slight effort to a newbie.

---

### Post by Donut417 on 2006-11-28
Well I noticed from reading that If my BIOS supports it and I think it does I could set it up so I could bring up a boot menu and choose the dirve that way. That seems to be a lot easyer then messing with the MBR. Like I stated I dont have a XP disk. HP gives me a recovery partion on my master hard disk, so I can mess that one up. But like I said if I can do it the esay way that good. 


On a secondary note, how good is ubuntu's support when it comes to linksys wireless adapters?
Also, Im running PC3200 and PC2700 DDR, why? Well HP being retarted as they are put on my case pc2700 however they put pc3200 in by mistake. Im not complaining. However I did install some pc2700 too for extra ram, as a temporay ram. I checked benchmarks and it made my machine better, is this going to affect the way ubuntu runs?

---

