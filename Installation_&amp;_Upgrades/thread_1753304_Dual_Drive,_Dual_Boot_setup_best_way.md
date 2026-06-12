---
title: "Dual Drive, Dual Boot setup: best way?"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by MikeNovember on 2011-05-08
Hello all!

I've been tinkering with Ubuntu on and off for several years, but a very light user at best. Primarily, I use OSX 10.6, but now I'm building a backup workstation/NAS/Server. The requirement for it to be a functional workstation has me here in Ubuntu and not FreeNAS, along with other limitations of FreeNAS I don't care to mess with. Anyway:

Currently, I have 11.04 running stable on the hardware in my sig line. What I would like to do is add another IDE Hard Drive, with Windows XP on it, and be able to pick between the two in GRUB2 (Which I noticed isn't displaying: is this because I only have one drive right now, and it's Ubuntu?) 

What's the best way to accomplish this?

---

### Post by MAFoElffen on 2011-05-08
> **MikeNovember said:**
> Hello all!

I've been tinkering with Ubuntu on and off for several years, but a very light user at best. Primarily, I use OSX 10.6, but now I'm building a backup workstation/NAS/Server. The requirement for it to be a functional workstation has me here in Ubuntu and not FreeNAS, along with other limitations of FreeNAS I don't care to mess with. Anyway:

Currently, I have 11.04 running stable on the hardware in my sig line. What I would like to do is add another IDE Hard Drive, with Windows XP on it, and be able to pick between the two in GRUB2 (Which I noticed isn't displaying: is this because I only have one drive right now, and it's Ubuntu?) 

What's the best way to accomplish this?
Yes, Grub is not diplaying now because Ubuntu is the sole OS.

Best?  You'll have debates on that... But one way would be to first, disconnect your Ubuntu drive, connect your new drive.  Boot from a GParted LiveCD and create your Windows partition on your new drive, starting it on the second sector, not the first.  This will allow Grub updates down the road from bothering this partition.  

Install Windows XP.  Get all current updates.

After the Install, reconnect your ubuntu drive.  Boot up into Ubuntu and run update-grub.
```

sudo update-grub

```The osprober in that process will find Windows XP and add it to the Grub menu.  

That's just how I'd do it.  After a few misadventures with that, this seems to be the safest way I've found, with less teeth-nashing later.  

I have basically the same on my main box with multiple instances of various versions and flavors of Windows, Unix and Linux across multiple drives and parittions..

---

### Post by MikeNovember on 2011-05-08
MAFoElffen,

That's *exactly* what I was looking for! I knew there was something I was forgetting from back when I configured a netbook for dual boot: gparted was it!

I'll give your suggestion a shot, and then post back here with the results.

Thanks so much for the reply!

---

