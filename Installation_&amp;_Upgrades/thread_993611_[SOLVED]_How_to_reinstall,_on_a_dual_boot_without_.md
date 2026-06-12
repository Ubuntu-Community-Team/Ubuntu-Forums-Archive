---
title: "[SOLVED] How to reinstall, on a dual boot without effecting Grub?"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by -Outcast- on 2008-11-25
After upgrading to Ibex from Hardy and suffering tons of problems, the final straw came yesterday when Ubuntu locked my out telling me something about either out of disk space or cannot access account. 

I am dual booting with Vista, and have Grub set up the way I like it. 

Using the Live CD, what is the best way to get rid of this current installation and install a fresh one without upsetting Vista or my Grub, though if Grub needs to be redone, then fine. I just don't want to loose vista. 

Thanks

---

### Post by Shwefty on 2008-11-25
I had this problem too.  Upgraded Hardy to Intrepid, even gave the out of disk space error and everything...

Are you familiar with manual partitioning?  I have XP on a different partition and didn't want to delete it, so, I got the 8.10 LiveCD (or made one).  8.04 works just as well.  Either way, in the install, when the partitioner comes up, choose manual partitioning.  Format everything that's ext3, and reinstall Ubuntu on that space.  Leave the NTFS ALONE!!!!!  That's Vista.

You are reinstalling Grub when you do this, but as long as you check the md5sum and the cd for defects, you'll be fine.

---

### Post by Shwefty on 2008-11-25
Hmmm, maybe somebody else could tell you how not to lose Grub?

BUMP.

---

### Post by -Outcast- on 2008-11-26
Thanks for that. 

I did manual partitioning for the first install. It looks a bit different with Ibex. But I should be able to handle it if it's just wiping out the ext3 and installing there. 

My worry so is Grub. I just don't want to loose vista on it. As I seem to remember having this problem before!

Anyone?

---

### Post by -Outcast- on 2008-11-26
Bump.

Anyone on the Grub issue before I do this again?

---

### Post by carusoswi on 2008-11-27
> **-Outcast- said:**
> Bump.

Anyone on the Grub issue before I do this again?

Don't know where you are with your re installation, but it seems to me that you could just open your GRUB file (Menu.lst or whatever it's called), copy the code, save it to some save location (on a flash card, CD, whatever).  Go ahead and do your Linux install, taking care as noted above not to disturb your Windows partition.  Likely, Linux will build a new grub that works fine, or one that you can easily edit with copy/paste to change the OS boot order, if that is your concern.

If you aren't happy with the grub that the install leaves you, either just replace it with your saved version or, again, copy and paste from your saved version those sections that restore the arrangement you want to maintain.

You can probably tell I'm no expert, but I have done this many times, and have yet to lose my XP installation.

I have had many more GRUB problems trying out new Linux distros.  I wanted to install Puppy Linux - tried it last weekend.  The last install step delt with GRUB in a way that was not self-explanatory to me.  What resulted was some garbage that would not allow me to get back into my Ubuntu OS.  XP was fine, however.

I opened the 8.10 partitioner, deleted all non-windows partitions, started with new Linux paritions, reinstalled 8.10 and still XP was just fine.

Until someone explains to me how to finish up with Puppy without messing up the rest of the machine, I'll just run it from the live CD.

Good luck.

Caruso

---

### Post by -Outcast- on 2008-12-21
Many thanks for that reply. 

I finally got around to it. New installation went fine. Grub was replaced, but the new version booted into vista no problems. I just have to manually edit the grub list to change the names back again. 

Thanks Again

---

