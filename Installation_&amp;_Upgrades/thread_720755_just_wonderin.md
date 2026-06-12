---
title: "just wonderin"
date: 2008-03-10
forum: Installation &amp; Upgrades
---

### Post by daryl874 on 2008-03-10
when i preportion my hard drive before installing xubuntuwill all my old data be deleted and will the windows OS im using at the moment still work

---

### Post by Shazaam on 2008-03-10
If you are careful you will be fine. Boot up the Xubuntu Livecd. When you get to the desktop go to Applications>Accessories>Terminal. Once it's open type this in......
```
sudo fdisk -l
```
(small L)
This code will print out your current partition list. Write those numbers down with a description of what they are so when you do decide to install you won't accidently partition/format needed partitions.
If you are running Vista you should defragment Vista first, then use the Vista disk partitioner to shrink/resize your current Vista partition(s). Do NOT delete any OEM RECOVERY partitions if you have them unless you want to clean off the whole drive. Then when you install Xubuntu don't choose "Guided- use whole drive" but choose "Guided-resize" or "Manual".

---

