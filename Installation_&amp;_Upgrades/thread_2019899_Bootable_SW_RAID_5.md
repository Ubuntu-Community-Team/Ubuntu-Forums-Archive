---
title: "Bootable SW RAID 5"
date: 2012-07-07
forum: Installation &amp; Upgrades
---

### Post by Ryqiem on 2012-07-07
Hello Ubuntu pros :popcorn:

I'm planning on building a budget server with the H61 chipset, and some spare 320GB drives I have lying around. Since fakeraid is not available, I'll be using software raid.

Is it possible to, during installation, create a RAID 5 software RAID for the server, where each drive is bootable? I've been searching around, and hearing mixed results.

I'll be using 12.04, unless something else is better for me.

If it's possible, how would I go around doing it?

Thanks! ):P

---

### Post by msammels on 2012-07-07
Hey Ryqiem,

Your post put a huge smile on my face :D Those emoticons are cute! *cough* anyway... will you be installing Ubuntu Server, Ubuntu Desktop, Lubuntu, Kubuntu, Xubuntu, or...? :)

---

### Post by Ryqiem on 2012-07-07
12.04 Ubuntu Server :)

Unless I should be using something else? This is a learning/fun/practical project, so suggestions are appreciated.

---

### Post by darkod on 2012-07-07
If I'm not mistaken, when using software raid the server installer installs grub2 to all the disks members of the raid by default.

I definitely know that for raid1 it installs grub2 to both disks without the need to tell it to.

---

### Post by Ryqiem on 2012-07-07
> **darkod said:**
> If I'm not mistaken, when using software raid the server installer installs grub2 to all the disks members of the raid by default.

I definitely know that for raid1 it installs grub2 to both disks without the need to tell it to.
So I just have to create the partitions, RAID them, and that's it?

---

### Post by darkod on 2012-07-07
> **Ryqiem said:**
> So I just have to create the partitions, RAID them, and that's it?

I think so. You can give it a shot.

Even if it doesn't install on all disks automatically, you can always do it yourself once your ubuntu is booted.

---

