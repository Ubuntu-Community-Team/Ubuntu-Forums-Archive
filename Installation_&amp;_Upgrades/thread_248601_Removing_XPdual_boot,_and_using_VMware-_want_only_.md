---
title: "Removing XP/dual boot, and using VMware- want only Ubuntu partition..?"
date: 2006-09-01
forum: Installation &amp; Upgrades
---

### Post by kendals on 2006-09-01
Heya guys.

I'm so in love with Ubuntu, and now I have WinXP working in VMWare, so my question is this:

XP takes up the first partition on my HDD (or first bunch of blocks/cylinders, etc.)- it has 47 of 60b in it's partition, whilst Ubuntu has a root partition taking 11gb, and a swap taking the last 1gb.

I also have Grub installed as my boot loader. What I want to do is this:

1. Remove the Windows partition, after backing up all the files I want.
2. Get Ubuntu root partition to take up ALL of the 45gb form XP partition.
3. Remove Grub so that it just boots straight into Ubuntu without needing to waste time at the Grub screen/load stuff.

After that, I'll set all my XP stuff up in VMware Server which is running nicely.

So, could someone please let me know how I do step 1-3? I know I can use Gpart, but will it let me simply SHIFT the Ubuntu partition to the start of the HDD, and then extend to the whole 59gb?

Finally, with just Ubuntu on the HDD, will I need Grub to load it, or does it have it's own thing?

Thanks! :KS :confused:

---

### Post by x64Jimbo on 2006-09-01
You'd be better off saving your entire partition out to a backup medium and then reformatting your main drive to use the whole space, then copying all the files back and reinstalling grub.

---

### Post by kendals on 2006-09-01
I thought about that, but using that Simple Backup software, to keep programs that are installed, and set up, etc., (i.e. Network manager, VMWare Server, etc.), will those all be backed up properly? How do I know all the files necessary for this software will be backed up?

---

### Post by x64Jimbo on 2006-09-03
I would not trust a piece of software to do the job for you unless that software runs on a livecd that you boot when you want to back up your system. Really, you should copy everything over to a backup medium from a livecd so that you can be sure that you get it all.

---

