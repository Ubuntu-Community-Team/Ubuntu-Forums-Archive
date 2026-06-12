---
title: "Dual Boot Windows 7, Ubuntu 12.04, Raid 0"
date: 2013-03-26
forum: Installation &amp; Upgrades
---

### Post by Slimmons on 2013-03-26
Hi everybody, I'm currently using Linux Mint, and I've set it up with raid 0, and it's been an absolute nightmare.  I had Ubuntu 12.04 setup in raid 0 and never had any related problems with it, so I'm switching back to Ubuntu.  My question is, I need to have Windows 7/Ubuntu 12.04 dual boot.  Before I start this process, I was wondering if there's anything special I should know to avoid headaches.  Questions below:

1. Which should I install first.
2. If I install Windows 7 first, Do I just set the Raid 0 up in the bios, and will Ubuntu still work if I do it that way?
3. I'm pretty sure I use the 12.04 alternate dvd, but just making sure.
4. Will I have to do anything special with grub since it's raid 0.

Thanks in advance, my specs are below.

Gateway FX
two 1tb WD Caviar Black HDD's
64 bit OS on both.

---

### Post by darkod on 2013-03-26
To dual boot you will have to use the fakeraid (bios raid) function. Ubuntu software raid with mdadm would be much better but windows can't understand it and can't work on it.

So, the steps would be like:
1. Set the raid in bios, make the array device.
2. Install win7, making sure you create the ntfs partition with the size you want for win7. DO NOT let it take the whole array, otherwise you will have to shrink which is additional complication.
3. Install ubuntu 12.04 using the Alternate CD because it has better support for raid. It should install grub2 correctly, unlike the live cd which fails installing grub2 on fakeraid.

But even if installing grub2 fails, you can add only grub2 later, no need to reinstall ubuntu.

That should be it.

---

### Post by Slimmons on 2013-03-30
Thanks, everything worked perfectly.

---

### Post by vitale232 on 2014-02-11
So when prompted to install grub to your MBR, you hit yes? I'm attempting this, and that step makes me nervous.

---

### Post by SkOrPn on 2014-06-17
> **vitale232 said:**
> So when prompted to install grub to your MBR, you hit yes? I'm attempting this, and that step makes me nervous.

Did you ever figure it out? Surprised 4 months later you still did not get an answer to your question. I'm thinking of installing 12.04 alternate in the hopes it will install along side Windows without needing to make any changes to the current partition setup. And then just upgrading to 14.04 in the hopes 14.04 will not break it.

---

