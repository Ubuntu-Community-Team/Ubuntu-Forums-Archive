---
title: "GRUB Error 22"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by tech13 on 2008-03-09
Hey everyone.

I am sort of a noob when it comes to linux, I am just starting out. I am having a problem with my GRUB.

Initially I had three partitions on my disk (1 for swap, 1 for ubuntu and 1 unpartitioned). I installed ubuntu and had it all configured and working properly, then I wanted to install another distro, so I tried installing debian on my unpartitioned space. Apparently it did not work out as planned because my graphics card wouldnt work with that distro out of the box and i couldnt read anything on the screen and i didnt feel like going into fail-safe to fix it. so I DELETED that partition.

Right now I just have sda2, sda5 (ubuntu), sda6 (swap) partitions on my disk (sda1 used to be debian but now it is unpartitioned). Now when I try to boot into ubuntu since it is the only OS left on the disk, I get the following message when grub tries to load:

GRUB Loading stage1.5.
GRUB loading, please wait...
Error 22
_

I booted to ubuntu live CD and made sure sda5 was set as boot and that my config files for menu.lst and that boot1 and boot2 were in mnt. I did have a similar issue where grub was not configured properly but I had a Grub>_ prompt to type in "setup (hd0) to fix that issue, but now there is no prompt it just says Error 22 with nothing but a solid underscore underneath it.

I am not sure how to repair grub and i do not want to reinstall ubuntu because I have stuff on there that i want to keep. any help would be appreciated.

---

### Post by tech13 on 2008-03-09
I think I fixed the issue, i booted to livecd and went into terminal and did the following:

```
sudo passwd
```
the insert new password and confirm
```
sudo grub
```
to edit grub
```
find /boot/grub/stage1
```
to find which disk boots
```
root (hd?,?)
```
then i replace ? mark with the result from previous code (IE: it returned hd0,4 so i put in "root (hd0,4)
```
setup (hd0)
```
to setup grub
```
quit
```
exit grub editor

I rebooted and it works... so all is good.

---

