---
title: "GRUB install question"
date: 2007-03-01
forum: Installation &amp; Upgrades
---

### Post by nflp1999 on 2007-03-01
I have three HDs in my system.  I have XP on one as the master IDE, I have a second IDE and I just added a SATA for my LINUX trials.  I partitioned the drive into two separate partitions.  I installed MEPIS on one and I want to but Ubuntu on the second.  When I installed MEPIS I put GRUB on the root instead of the MBR.  This works really well since I use GAG as my boot loader.  I want to be able to do the same thing in the Ubuntu install.  How do I do that?  It prompts me for the GRUB install but has HD0 as the location.  I know what is not what I want since that is my XP drive.  I assume I want HD02 since that should be my SATA drive but do I need to tell it to install on the second partition so it doesn't mess with the MEPIS GRUB install?  I'm trying to keep everyone separate for now.  I will direct GAG to load Ubuntu from that menu.  So my main question is, where do I put GRUB to get this all to work?

---

### Post by angryfirelord on 2007-03-01
You'd have to take Grub's contents & make them work with GAG. GRUB would have to be installed on your /

Ubuntu's GRUB will find your OSs, including Windows & I've had no issues with it. You may want to use grub instead.

---

### Post by confused57 on 2007-03-01
> **nflp1999 said:**
> I have three HDs in my system.  I have XP on one as the master IDE, I have a second IDE and I just added a SATA for my LINUX trials.  I partitioned the drive into two separate partitions.  I installed MEPIS on one and I want to but Ubuntu on the second.  When I installed MEPIS I put GRUB on the root instead of the MBR.  This works really well since I use GAG as my boot loader.  I want to be able to do the same thing in the Ubuntu install.  How do I do that?  It prompts me for the GRUB install but has HD0 as the location.  I know what is not what I want since that is my XP drive.  I assume I want HD02 since that should be my SATA drive but do I need to tell it to install on the second partition so it doesn't mess with the MEPIS GRUB install?  I'm trying to keep everyone separate for now.  I will direct GAG to load Ubuntu from that menu.  So my main question is, where do I put GRUB to get this all to work?

Depending on the location of Ubuntu's root partition, you'd need to specify something like **/dev/sda2** to install grub there...the alternate install cd allows you to do this, I don't use the live cd installer...in the block with (hd0), can you just type in /dev/sdax(x being your root partition).

---

### Post by nflp1999 on 2007-03-01
Well, I got it all installed and working well.  Thanks for the help.  This was actually not bad at all.  I upgraded everything (except the video card) and it all works really well.:)

---

### Post by confused57 on 2007-03-01
> **nflp1999 said:**
> Well, I got it all installed and working well.  Thanks for the help.  This was actually not bad at all.  I upgraded everything (except the video card) and it all works really well.:)

Glad to hear everything went smoothly & you didn't have any problems, thanks for letting us know...

---

### Post by tnadenichek on 2007-03-03
so, did you end up installing grub to the root partition?

---

### Post by nflp1999 on 2007-03-04
yeah, I put it in root then told GAG where to load from.  Works like a charm.  I like GAG a lot.  Easy to use and customize.

---

