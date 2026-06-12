---
title: "Ubuntu hates me"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by fbaerkir on 2008-04-29
I've tried everything I can think of to install Ubuntu, and nothing works. I tried using dmraid to get it to share my RAID with Vista, with no luck. I tried adding a separate HD, but installing on that disabled my Windows MBR. I tried manually editing Grub, with no luck. I tried telling Grub not to alter other drives, but it stilled altered my Windows mbr. I also tried putting Grub on a floppy; that didn't work, either. Nor did editing Grub on that floppy.
Finally, I tried just using Wubi. Of course, no dice.
Using Wubi, I'm trying to put the files on a separate partition that's not part of my RAID. It looks like it installs OK, but when I select Ubuntu to boot, it fails.
I get the following message:
file:\ubuntu\winboot\wubildr.mbr
Status: 0x000000e
Selected entry could not be located because the application is missing or corrupt
I've looked around on the forums and see no solutions to this.
Does anyone know of any way, using RAID5, a separate HD, or Wubi, that I can get Ubuntu up and running?

---

### Post by eldragon on 2008-04-29
what i did when i was learning is:
i removed my windows HDD, installed ubuntu on my extra hdd, and then chose which to boot pressing f8 (motherboard POST) and picking boot device through bios. this might not be doable on all haradware.


PS. im still learning :D

---

### Post by fbaerkir on 2008-04-29
I was hoping to do something like that. But my BIOS doesn't recognize the Ubuntu HD, apparently because part of Grub goes to the other HDs. I'm leery of actually unplugging the Windows drives because it's a RAID, and I don't want to break it.

---

### Post by acelin on 2008-04-29
Dont worry it hates you too :D jkjk

---

### Post by thomasyo on 2008-04-29
In reference to the removing of hard drives, what is the master/slave set up of the individual drives?

I run a 40 gig as a slave to my 120 gig master but would love to use the 40 gig for ubuntu and i am having alot of trouble installing 7.1.

---

### Post by thomasyo on 2008-04-30
> **thomasyo said:**
> In reference to the removing of hard drives, what is the master/slave set up of the individual drives?

I run a 40 gig as a slave to my 120 gig master but would love to use the 40 gig for ubuntu and i am having alot of trouble installing 7.1.

i run XP from my 120 and am looking to dual boot

---

### Post by fbaerkir on 2008-04-30
The RAID is composed of four SATA drives, so there's no master/slave option. The separate drive I'm trying to get Ubuntu onto is an IDE, but the only one. I have the jumpers set to master.

---

