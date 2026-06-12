---
title: "I would like to do clean install of 8.04. How?"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by neocortex on 2008-04-24
Hello ALL!
Since 8.06 is shinning now, I would like to install it, and not to do upgrade from 7.10. Previously, I left small Windows partition, and made swap, root and /home partitions for Linux. Now I wonder how to keep my /home partition during install. Will 8.04 recognize partitions and install itself on the root partition, keeping /home safe and sound?
I followed instructions for having both, root and home partitions, but there are no infos how-to do fresh install and keeping home.

Best,
PM

---

### Post by vishzilla on 2008-04-24
Install using the Desktop CD. During installation when you come across setting the partitions uncheck the Format option for your home partition while checking only the root partition for formatting. Continue forward installing the system, and you will be fine.

---

### Post by lordrick112 on 2008-04-24
Run the live cd installer, once it gets into the partition section of the install process, choose manual and reset your mount points and reformat them all except your home partition.

Ive did this a few times with my older computer with 2 HDDs on it. I used the primary for the root and swap partition and slave for my home partition.

You MIGHT want to delete some hidden folders off your home partiton since i noticed that some of your settings are saved into the home partiton like pigin accounts, firefox bookmarks n such. But thats user preference I guess.

Ctrl + H displays your hidden files.

the folders begin with a "." example = ".adobe" ".macromedia" ect, ect.

the only ones that I couldnt delete were ".cache" and ".thumbnails", they kept reappearing so I thought it was ok to live with.

Hope this helps you out!

---

