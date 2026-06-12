---
title: "Will this work or kill my computer?"
date: 2008-10-19
forum: Installation &amp; Upgrades
---

### Post by pavan115 on 2008-10-19
Hey all, 

I want to know if this will work without having to test it out myself (cannot afford to :(). So any knowledgeable multi-boot master, please respond and give me feedback.

I am running a dual boot with XP and Xubuntu, so:

1) I boot my computer with Xubuntu live CD

2) I use Gparted to delete all of the linux partitions (ext, swap etc) to free space.

3) I then install Xubuntu (again, but back to default settings) in the same partition.

Will this cause some problems with the GRUB? If so, are there any solutions to this that does not involve a fresh install of XP? Have a lot of data there ._. 

- Thanks

Also, If you need any specs, please ask.

---

### Post by logos34 on 2008-10-19
You can skip the gparted part--simply reinstall Xubuntu over the old root and swap.  It will rewrite grub to the Master Boot Record.  An entry for Windows should appear on on menu.lst screen just like before.

---

### Post by oilchangeguy on 2008-10-19
always, always, backup any data you have before you do anything else. this means in both operating systems.

---

### Post by pavan115 on 2008-10-20
Thank you both! I will try that when I get the chance to :P

---

