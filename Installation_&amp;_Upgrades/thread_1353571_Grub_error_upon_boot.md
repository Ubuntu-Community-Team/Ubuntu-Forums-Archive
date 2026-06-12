---
title: "Grub error upon boot"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by Sarr on 2009-12-12
After recently doing a fresh install of Ubuntu (I had an obsolete version) I realized that for some reason I made the Ubuntu partition too small. So I used a partitioning software on XP to resize the Ubuntu partition. It told me I needed to restart for the changes to take effect.  I didn't do it right away but when I did I didn't get past the startup HP screen. I received the following message:

GRUB loading.
error: unknown filesystem
grub rescue> _(blinking underscore)

Now I can at least figure this out if I could load the live cd, which I cannot as for some reason it refuses to enter setup, no matter how many times I press the key. (edit: I got it to load from cd though still not sure how to solve it. )So it's not set to boot from cd and refuses to boot anything else.

I have XP and Karmic on dual boot on an hp pavilion 533w. (sort of old)

What can I do?

---

### Post by oldfred on 2009-12-13
XP will not see and let you resize the ext3/ext4 partitions. You may have reformatted it?

Use the liveCD and use gparted to look at your partitions. That should tell you what you have. You can then also resize from there if the partitions are ok, but just need resizing.

---

