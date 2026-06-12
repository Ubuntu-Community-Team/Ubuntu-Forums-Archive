---
title: "[SOLVED] Maintaining GRUB after installing windows"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by dean20007 on 2008-01-27
Hi Folks

I have to install windows on a partition on my machine for some development work I am doing, however I wish to keep my GRUB intact so I can still boot into Ubuntu. As I remember in ym early Ubuntu days I tried this and and could no longer boot into Ubuntu an dhad to reinstall everything. Can anyone help/ point me in the direction of a how to? 


Thanks

---

### Post by zvacet on 2008-01-27
> I wish to keep my GRUB intact 

It is not possible,because Windows will overwrite your grub.But,you don´t have to reinstall Ubuntu,just [grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub).

---

### Post by vojtech.t on 2008-01-27
Windows has rewrited MBR and deleted Grub - you have to recover it - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by dean20007 on 2008-01-30
Cheers guys, the HOW-TO directed to worked a treat

---

