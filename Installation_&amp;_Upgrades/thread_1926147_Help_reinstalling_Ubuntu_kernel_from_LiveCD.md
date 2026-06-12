---
title: "Help reinstalling Ubuntu kernel from LiveCD"
date: 2012-02-15
forum: Installation &amp; Upgrades
---

### Post by Rtedmonston on 2012-02-15
I have so many partitions on my drive it's not funny. a couple are showing up as duplicates in the boot loader. I want to delete my Windows 7 recovery partition, seeing as I dont really need it anymore, that would take away two entries out of 10 (sda). I have Gparted, can I re-allocate the space used up by those and add them to my main Windows/Ubuntu partition w/ Gparted? I don't want to accidentally delete my swap file or have to re-install Ubuntu because once I remove anything I know Grub2 is going to go berserk and Ill have to re-install that.

---

### Post by Rtedmonston on 2012-02-15
Nvm figured it out, I was mounting the wrong partition :p. Got Ubuntu back. Mark [SOLVED] please

However can I still get some advice on deleting multiple obsolete partitions like i mentioned?

---

### Post by grahammechanical on 2012-02-15
Are they actually obsolete partitions or old kernel versions? If they are kernel versions then make a note of their labels and open the Synaptic Package Manager. You may have to install it if you are on 11.10.

You can use Synaptic to remove old kernels but be careful do not remove the latest kernel (the one with the highest number). That is the one that you are using. Remove that and you break Ubuntu. Keep the next newest kernel as well. It is always good to have at least two kernels in the Grub menu in case the one you are using breaks then you can boot into an earlier kernel and get a working Ubuntu.

regards.

---

