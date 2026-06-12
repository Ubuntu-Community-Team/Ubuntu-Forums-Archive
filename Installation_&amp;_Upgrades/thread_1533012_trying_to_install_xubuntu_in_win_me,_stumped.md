---
title: "trying to install xubuntu in win me, stumped"
date: 2010-07-17
forum: Installation &amp; Upgrades
---

### Post by matfox on 2010-07-17
Hi everyone, my first post here, just dipping toes in ubuntu waters, & I like the temp so far,  but

I've been trying to get xubuntu (or perhaps dsl, whatever turns out to work best/lightest) onto an old Sony Vaio laptop running Win Me, without reinstalling Win operating system. Ultimately I want a dual-boot, so I can get to the old OS, but use the linux for other purposes. (Again, preferably I don't want to have to reinstall the Win OS, if I can avoid it.)

Wubi won't work, as I've discovered. Grrr. (Why???) Fine. Just one more proof that Microsoft was at a height of stupidity with Win Me.

So I've got a smallish overall HD, partitioned into a C and D, and I've been trying to add a partition to my D drive. I've tried a few utilities, but no dice yet. 

Parted Magic seemed / seems like the best bet, but it always stalls on booting kernel from live CD. I'm pretty sure the CD-Rom is failing somehow, since that was one piece of the machine that had occasional troubles. 

Is there anything else I can use/try to run from within Windows to add a partition space to my D drive, onto which I can then install xubuntu in a dual-boot config?

Any help would be greatly appreciated. Thanks!

---

### Post by snowpine on 2010-07-17
The Xubuntu installer has a built-in partitioning tool. No need to pre-partition your drive.

What are the hardware specs of the computer? Do they meet or exceed the minimum system requirements for Xubuntu?

[https://help.ubuntu.com/community/Installation/SystemRequirements#Lightweight%20GUI%20alternative%20%28Xubuntu%29](https://help.ubuntu.com/community/Installation/SystemRequirements#Lightweight%20GUI%20alternative%20%28Xubuntu%29)

---

### Post by matfox on 2010-07-17
Hi, thanks for helping.

It has 192mb ram I think, and at least 3gigs free on the d drive, so I'm right at minimums (I might be able to grub around and add some ram eventually, though sony has ram chips with proprietary slotting - grr). 

So how do I use the built in partitioner? load with livecd... go from there?

(I've only ever used wubi, which is very non-threatening)

edit: sorry, some stupid questions in there. I'll read up on the link you posted, then reply if needed; though feel free to jump in again if you get the notion. thanks

3rd thought edit: actually, there's a lot of trees in that forest, and I easily get lost in command line lingo. I just want a light linux up and running without much fuss, to (try to) serve up some media at home (and feel good about going open source). So any extra help from anyone, straight and simple, would be super duper. Thanks.

---

### Post by matfox on 2010-07-17
Screw it, I just went nuclear instead, should solve everything: upgrading the ME to XP, so I can use wubi (and anything else I might like to try).

Thanks everyone. I look forward to interacting with questions etc about ubuntu once I get this system dedicated to it!

---

### Post by oldos2er on 2010-07-17
> **matfox said:**
> It has 192mb ram I think, and at least 3gigs free on the d drive, so I'm right at minimums 

 Wubi requires a minimum of 384MB RAM and 5GB hard disk space. [http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by matfox on 2010-07-17
You know you're right, Ann in Cheyenne. But xubuntu only requires 256 ram and is known to install with less. I went ahead and tried it, since I had nothing to lose, and it ALMOST worked--wubi ran, downloaded iso, installed .... slowly.... rebooted, the dual boot was there, ready to go...but the OS itself would not in the end fully boot. I tried three times, but it stalled out. I am suspecting some other underlying hardware problems are there, but since I'm not that savvy, I'm just going another route, like dsl or puppy--or xubuntu through another install method. Now that I have xp on and going, all the myriad problems that I was encountering with WinME disappear (or at least are greatly mitigated).

Thanks!

---

