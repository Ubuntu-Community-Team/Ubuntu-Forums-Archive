---
title: "One install too many?"
date: 2010-09-07
forum: Installation &amp; Upgrades
---

### Post by M_Mynaardt on 2010-09-07
Hi!

I took a leap and made my desktop an all-Linux machine yesterday.  **However**, I had to have a go at it three times.  First two times; _nothing_ happened when I tried to reboot.  So, I tried the install for the third time and paid a bit more attention to the options.  And, behold!  I forgot I have two hard drives on my computer.  For whatever reason, the installation kept wanting to put the installation on the wrong drive.  No idea why.  But when I realized what was happening, I installed it on what should have been the default booting drive and it worked.

_However_...

My secondary drive is marked as a system disk.  What would happen if I reformatted that disk and get rid of that?  Would that make a mess of the install I have?  Meaning I'd have to do the install all over again?

Thanks in advance for any advice!

---

### Post by TNT1 on 2010-09-07
Can you login, and then use the disk utility to unmount the drive you want to format? If so, you can format it from inside your OS and you should be fine as far as your install goes.

---

### Post by 73ckn797 on 2010-09-07
You would need to go to System/Administration/Synaptic Package Manager and install "gparted" to format the other drive while in Ubuntu. You could also boot from the Live CD and Gparted is included with it.

---

### Post by M_Mynaardt on 2010-09-07
> **73ckn797 said:**
> You would need to go to System/Administration/Synaptic Package Manager and install "gparted" to format the other drive while in Ubuntu. You could also boot from the Live CD and Gparted is included with it.

Okay, thanks for that, I'll give it a go...

---

### Post by M_Mynaardt on 2010-09-07
> **TNT1 said:**
> Can you login, and then use the disk utility to unmount the drive you want to format? If so, you can format it from inside your OS and you should be fine as far as your install goes.

I was thinking of doing that; I just didn't want to hop right in doing something like that and then making a mess of it and having to reinstall all over again.

Sometimes simple fixes like that are more trouble than they're worth!

Mind you, if I did reinstall it wouldn't be that painful.  I've not had enough time to put stuff (data) on to the new installation, etcetera.  I also have a few days off work to get this all sorted out, thankfully...

---

### Post by M_Mynaardt on 2010-09-08
I started it from scratch again.  I've got Ubuntu and Mint (just because) running on the main hard drive and I've got the secondary drive cleaned up.  A bit of a chore, but it works now...

---

