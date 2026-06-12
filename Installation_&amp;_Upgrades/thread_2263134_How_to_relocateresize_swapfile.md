---
title: "How to relocate/resize swapfile?"
date: 2015-01-29
forum: Installation &amp; Upgrades
---

### Post by nechen on 2015-01-29
I recently screwed up my fakeRAID1 array but I have that all sorted now. However prior to me fixing this I attempted to make a swapfile due to me only have 4GB of DDR2-800 which fills up fast w/ browsers tabs.

Anyway I now have a 4GB partition ON my RAID drive instead of the 640GB spare I have sitting in there. I'd like to do two things:

1.) Move it off the RAID1 volume and onto the 640GB 

2.) Increase the size, I was hoping for 8GB or something in that neighborhood even though the R/W times are only 60MB/s with an 18ms access time...

I've been all over the place and every command I've found has me worried I'll end up screwing this up again especially since I somehow put it on the wrong bloody device in the first place.

---

### Post by SeijiSensei on 2015-01-29
Create a new swapfile in the location of your choice using any of the various guides out there on the Net.  In /etc/fstab repoint the swap entry to the new file.  Reboot.

---

### Post by nechen on 2015-01-29
cool thanks!

---

