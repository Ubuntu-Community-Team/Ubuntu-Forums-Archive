---
title: "windows partition"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by teddy101 on 2010-09-30
Not strictly linux related, but you guys really are the experts.

I am trying to install windows 7 on my harddive, I am running ubuntu 10.04 and have windows 7 on DVD.

I was until recently also using uberstudent, which I deleted (100 gigs) to make space for windows.

However once I get to the windows start up I get a message: setup cannot detect or create a partition for this partition. (not word for word)

Do you guys know what I can do to solve it? 

thanks :)

tom

---

### Post by srs5694 on 2010-09-30
Try using GParted to create a primary partition for Windows, initializing it as NTFS. If you need more advice, please post either a screen shot of GParted showing the disk or the output of "sudo fdisk -lu" (preferably between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility).

---

