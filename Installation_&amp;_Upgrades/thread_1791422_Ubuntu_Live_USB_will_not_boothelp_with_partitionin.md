---
title: "Ubuntu Live USB will not boot/help with partitioning"
date: 2011-06-26
forum: Installation &amp; Upgrades
---

### Post by fallenashes on 2011-06-26
I used the official ubuntu instructions on how to create a Live USB, and when I reboot, it freezes on an underscore in the top right flashing on and off. All I am trying to do is partition my main hard drive because it shipped with 2 partitions. I tried a Gparted Live USB as well and it is stuck at the splash screen. How do I make a live USB to succesfully boot so I can edit my partition?

notes:
- Computer: Asus U35JC
- Cannot Change boot order, have to boot into bios and select 'Cruzer....' option to boot from USB
- Windows 7 Home Premium 64 bit
- no optical drive

(Cross posted from Asus section of forums)

---

### Post by nzjethro on 2011-06-26
Did you create a Live USB using unetbootin? It may be a bad download. What is the size of your Ubuntu .iso file?

---

### Post by fallenashes on 2011-06-26
> **nzjethro said:**
> Did you create a Live USB using unetbootin? It may be a bad download. What is the size of your Ubuntu .iso file?

No I used Universal USB installer, recommended by ubuntu.com themselves, and the .iso has the correct md5 hash, so I'm sure its not corrupted.  But I'll try unetbootin now.  Thanks for the response.

---

### Post by mörgæs on 2011-06-27
A flashing underscore is not necessarily a bad sign. For how long did you wait?

---

### Post by fallenashes on 2011-06-27
> **mörgæs said:**
> A flashing underscore is not necessarily a bad sign. For how long did you wait?

2 minutes tops.  I'll wait, say 15 or 20 minutes just to be sure.  And unetbootin did not work. Should I try an older distro, like the last LTS?

---

### Post by fallenashes on 2011-06-27
Solved!  It was the USB stick, tried another and it worked!

---

