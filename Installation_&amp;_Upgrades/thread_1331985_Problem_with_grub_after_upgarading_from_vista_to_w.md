---
title: "Problem with grub after upgarading from vista to windows7"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by frriction on 2009-11-19
Well, I had Vista 64 bit and I was eligible for windows 7.
Before I get upgrade disk for windows7 I have installed Ubuntu 9.10 with grub2.

Yesterday I have received windows7-64bit disk so I have upgrade the my vista to windows7.

After reinstalling grub2 as per [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) 

I have two options in grub I can boot from vista and windows7 as well.

When I boot from vista i am going to recovery option so i want to disable or remove the entry from grub how can I do that?

---

### Post by oldfred on 2009-11-20
I think it was drs305 has a way to modify the logic in the osprober script to ignore certain titles. You can search this forum for that if you like.

My workaround is to just copy your win7 entry from /boot/grub/grub.cfg to 40_custom and turn the osprober off. You can turn the prober back on if you add other operating systems, but otherwise it is not required.

gksudo gedit /etc/grub.d/40_custom

gksudo gedit /etc/default/grub
add this entry:
GRUB_DISABLE_OS_PROBER="true"

sudo update-grub

---

