---
title: "EVERY Kernel Update Renames My Drives!"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by OzzyFrank on 2007-06-19
OK, this is just a tad annoying, and for me easily fixed, but for newbies it might seem a lot worse. First off, when I installed Edgy as a newbie, I got used to my drives being "hda" etc, and saw mention in forums of people with SATA drives having drives called "sda" etc. When I was forced to do a fresh install of Feisty as my Edgy drive was dying, I noticed my drives were all called "sda" etc. I thought, OK, I have IDE drives, but no big deal... maybe with Feisty all drives start with an "s". Somewhere in my system i saw mention of my drives being referred to as SCSI,  and of course they're neither SCSI nor SATA.

Anyway, after the first kernel update after the release of Feisty I noticed all my drives that are mounted in fstab were not being mounted. Or should I say, they were available in Computer, but the system automounted way where you have RO access after password. Fstab hadn't changed... but then soon realised my drives names or addresses had! They had been changed to "hda" etc, which is what I was used to with Edgy, so just edited fstab and hoped that was it.

Now, after updating the kernel again yesterday, I rebooted and wasn't a bit surprised to see my drive icons missing from the desktop again... and yes, the drives are now "sda" etc.

Is this some joke we're playing on newbies that I wasn't aware of, hehe?? Likle I said, for me it is a fairly trivial thing - especially since none of this ever effected the actually Ubuntu partition, and it booted no matter what fstab referred to it as - but this could be seen as another reason for newbies not to stick with Ubuntu.

But while I say it is a fairly trivial thing, I would rather not have to edit fstab each time i update the kernel. Is there anything I can do to prevent this (besides have a backup copy of fstab for quick replacement)? Or is this some kind of bug or something?

---

### Post by hummingbird59 on 2007-06-19
I AM a newbie and this happened to me two days after I installed Feisty.  Talk about nerve rattling..... My solution: I went back to the 15 kernel and I don't do updates until someone can explain wtf that's about.

---

### Post by OzzyFrank on 2007-06-19
Well, if other newbies read this post, they'll know it ain' that bad, and is fixed simply enough by opening fstab and editing a few "h"s to "s"s or vice versa from the drive names (sudo gedit /etc/fstab). At least when this happens people can still access any attached drives with password in Computer. But yes, I figured it could be "nerve rattling" for newbies out there. Obviously this issue needs to be addressed. But for now, just boot the latest kernel (which you can still do) and edit fstab to get your other drives automounted your way.

---

### Post by hummingbird59 on 2007-06-19
Just FYI:  I deleted the kernel via synaptic and didn't do all that fstab stuff (couldn't or didn't want to figure it out - I don't know).  It appears to be gone from my boot menu and all of my new kernel probs disappeared so....

But no it really wasn't that bad - just really bad timing...

---

### Post by OzzyFrank on 2007-06-26
Still no takers, huh? Hehe...

Oh, and editing fstab is infinitely much easier than removing a kernel upate! It's just a text file, and you can change drive paths there, and of course turn **hda** into **sda** or vice versa. To edit fstab:

**sudo gedit /etc/fstab**

PS: My drives got renamed again yesterday. I am call this the "Ubuntu Musical Drives" feature.

---

