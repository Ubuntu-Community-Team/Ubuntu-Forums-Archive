---
title: "Problems With Dual Boot Installation"
date: 2008-09-07
forum: Installation &amp; Upgrades
---

### Post by tnerrotbrzi on 2008-09-07
Hi to all people with good will :-)
I've Windows XP installed.I just installed Ubuntu(dual boot).
I have done partition process and everything looked fine but when I try to log on I could see just my old Windows user and beside that nothing else.
Is there anybody who can help me?
Thanks a lot.:confused:

---

### Post by caljohnsmith on 2008-09-07
Boot your Live CD, go to Applications > Accessories > Terminal, and post the output of these commands:
```
sudo fdisk -lu
sudo grub
grub> find /boot/grub/stage1
grub> quit
```
That will give us some place to start. :)

---

