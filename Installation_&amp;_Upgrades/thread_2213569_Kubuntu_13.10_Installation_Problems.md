---
title: "Kubuntu 13.10 Installation Problems"
date: 2014-03-27
forum: Installation &amp; Upgrades
---

### Post by k-me-n on 2014-03-27
Hello,

I tried to install Kubuntu 13.10 today onto my second drive which is a 2TB Sata, and currently has 2 partitions formatted to NTFS. My primary drive is a 128GB SSD and runs Windows 8.1, with a third drive which is a 128GB SSD and Fedora 20 on it. I figured it would be fun to play with KDE for a bit, and so thought to try and install it onto the 2TB drive in a 100GB partition or something.

I experienced no end of issues, from the installer on the live DVD detecting the 2TB as 2TB of freespace, through to it reporting when I ran parted -l and gparted that /dev/sdb had GPT issues!

I tried using WUBI to install twice as well but that failed both times at the final stage of the installation with an error about corrupt installation media.

At this point I have given up installing it, and am thinking if I want to use KDE, then I would be best off buying another disk to stick it on!

But I would love to know if anyone has any idea what the problem was, I ran a check on the drive in windows and it shows error free.

Perhaps the weirdest thing is despite the installer seeing the 2TB drive as a block of freespace with nothing on it, if I booted to the live CD version of Kubuntu and opened the file manager I could access the drive and its files, however gparted and the installer running under the live CD still saw it as a block of freespace, even when I have file manager open looking at the files and the installer next to it, which seems weird because clearly it can mount and use it for file manager and recognises the file system, but the installer see's something completely different at the same time!

Anyway, any thoughts on what is going on with it would be welcome!

---

### Post by kc1di on 2014-03-27
Hi k-me-n  and welcome to the Ubuntu forums.  
GPT and UEFI can be a pain to install on.  But it can be done. Kparted or Gparted don't always read GPT partitions correctly. 

One thing you'll want to do to get the live dvd running is if your machine has secure boot, you'll need to turn that off. 

[here is a page]("https://help.ubuntu.com/community/UEFI") that will be of help.  it for ubuntu/ but the process is the same for kubuntu.
Good luck.

---

