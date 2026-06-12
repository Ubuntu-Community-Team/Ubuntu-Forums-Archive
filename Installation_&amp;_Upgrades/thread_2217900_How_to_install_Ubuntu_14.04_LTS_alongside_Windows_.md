---
title: "How to install Ubuntu 14.04 LTS alongside Windows 7"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by Wilman_Darnasutisn on 2014-04-18
hi guys,

i can do step by step to dual boot Ubuntu and windows. and my problem is.. in the installation type, i'll create a partition for swap. but, when i click my "unusable disk/free space", it can't add for swap.. "+" button not active/work?
or Ubuntu 14.04 can't did dual boot?

Thanks,
Wilman

---

### Post by gdesilva on 2014-04-18
I am not sure what your problem is. If your problem is that you cannot create a swap partition, then sounds like you do not have space on your disk. You can shrink one of your OS partitions to create space for swap. Hopefully, this answers your question?

---

### Post by squakie on 2014-04-18
Try booting only with the "Try Ubuntu" option first, and run the following in a terminal when it boots:

sudo gparted

When gparted starts (if it's not installed, install via sudo apt-get install gparted), be sure it is on your hard drive then try taking a screenshot (you can find it in the menus) and post it back here - it will be of help.  Don't try anything further until we see what you are dealing with as we don't want you to accidentally mess up your partitions.

---

### Post by Wilman_Darnasutisn on 2014-04-19
i have shrink my HDD. i'm create unallocated space 30 Gb..
thank you for answers.

---

### Post by Wilman_Darnasutisn on 2014-04-19
> **gdesilva said:**
> I am not sure what your problem is. If your problem is that you cannot create a swap partition, then sounds like you do not have space on your disk. You can shrink one of your OS partitions to create space for swap. Hopefully, this answers your question?

i have shrink my HDD. i'm create unallocated space 30 Gb..
thank you for answers.

---

