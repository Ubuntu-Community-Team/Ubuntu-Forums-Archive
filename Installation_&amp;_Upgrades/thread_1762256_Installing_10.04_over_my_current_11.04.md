---
title: "Installing 10.04 over my current 11.04"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by samsational on 2011-05-19
I have 11.04 installed, but I want to go back to 10.04 due to issues. I plan on installing off of my USB drive. I am currently downloading the image.

I plan on backing up my important files. 

Can I install 10.04 and keep the files that are on my machine at the moment? That is, will installing delete them? I am mostly concerned about /home/me/ files which are separated from /

---

### Post by tommcd on 2011-05-19
If you have /home on a separate partition, then all of your data will be safe. 
Just choose manual partitioning. Choose to install 10.04 over the current 11.04 root partition. The swap partition will be the same. Choose the current /home partition as mount point /home. Be sure to choose 
*do not format* for the home partition.
If home and root are on one big partition, then you would need to backup all data in the home directory before reinstalling 10.04.
Write back if you need more help.

And welcome to the Ubuntu forums!

---

