---
title: "Installing UNR 9.10"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by deanrd on 2009-11-15
Hi All,

I'm running an Asus 1005HA, 2gig mem, XP.  The harddrive is already partioned in 2 - 77 gig partitions with a hidden 1 (4 or 5 gig) also.  Probably for the builtin restore.

I've run the UNR 9.10 successfully from my usb stick and would like to install as a dual boot to WinXP.  I've read a bunch of posts and articles about not using the auto feature during install and to partition my drive ahead of time manually.  Is this required if I'm already partitioned?  Will it be safe to run install from usb or better from cd without partitioning manually?  Whats the worst that could happen?

Thanx in advance - Dean

---

### Post by TheHimself on 2009-11-16
The worst thing can happen is that installer install Ubuntu upon XP partition and then the files there would be  gone forever. 

Linux needs an ext3 (0r 4) and a swap partition. Your 77 GB partition is probably an NTFS one and if so then it wont be the right one. 

If you don't want to risk using the "auto feature" then one (stupid) solution is to install 9.04 first and then upgrade to 9.10. The installer in 9.04 (and older) gives you the "use the largest free space..." option which gives you more controll over the partitioning. BUT you have to prepare the free space first and free means "not in a partition". So you will have to first delete the 77GB partitions you've chosen for Ubuntu  using gparted. Be carefull not to delete XP's partition!!!

---

### Post by darkod on 2009-11-16
To add to the previous reply, you have two options.
1. Remove all files you need from the second 77GB partition and dedicate it for Ubuntu. But you really don't need all that space for Ubuntu.
2. Better option. Shrink the second 77GB partition for 27GB. The plan is:

hidden recovery partition
C: 77GB XP
D: 50GB ntfs for data (ubuntu can access this too so you are not limited to the 27GB for ubuntu and you still have 50GB for windows)
/ (root) ext4 15GB
swap 2GB
/home ext4 10GB

The root is like C: for windows. You don't have to have separate /home but it helps if you want to reinstall sometimes, your personl files will remain in /home. Something similar like when you reinstall windows you format C: but can keep everything on D:.

My personal recommendation is to use the manual partitioning during install, it's not complicated and you learn things that you should know anyway if entering the dual booting world. :) Ask for help here and we'll give you suggestions.

PS. I think people are way too much frightened from using manual partitioning. First of all, the tool is graphical, you don't need to know any special linux commands or whatever. You just create three partitions and that's it. If you don't want separate /home even better, just two partitions. Why let the machine do such an important job like your disk partitioning. :)

PPS. If you decide to shrink the second 77GB partition, it is recommended to use Gparted by booting with the ubuntu stick and selecting Try Ubuntu option. Win7 has a tool for shrinking too but Gparted is better. And of course, you have to have free space on the D: partition at least the amount you want to shrink, for example 27GB have to be free.

---

### Post by deanrd on 2009-11-16
> **darkod said:**
> To add to the previous reply, you have two options.
1. Remove all files you need from the second 77GB partition and dedicate it for Ubuntu. But you really don't need all that space for Ubuntu.
2. Better option. Shrink the second 77GB partition for 27GB. The plan is:

hidden recovery partition
C: 77GB XP
D: 50GB ntfs for data (ubuntu can access this too so you are not limited to the 27GB for ubuntu and you still have 50GB for windows)
/ (root) ext4 15GB
swap 2GB
/home ext4 10GB

My personal recommendation is to use the manual partitioning during install, it's not complicated and you learn things that you should know anyway if entering the dual booting world. :) Ask for help here and we'll give you suggestions.

PS. I think people are way too much frightened from using manual partitioning. First of all, the tool is graphical, you don't need to know any special linux commands or whatever. You just create three partitions and that's it. If you don't want separate /home even better, just two partitions. Why let the machine do such an important job like your disk partitioning. :)

PPS. If you decide to shrink the second 77GB partition, it is recommended to use Gparted by booting with the ubuntu stick and selecting Try Ubuntu option. Win7 has a tool for shrinking too but Gparted is better. And of course, you have to have free space on the D: partition at least the amount you want to shrink, for example 27GB have to be free.

Bingo!

Booted to usb, Gparted the 77 gig partition as suggested with root/swap/home.  Had some 48 meg undefined I just left alone.  Installed from usb and after configuring and 89 updates it appears to be dual booting as designed.  I rebooted into Ubuntu and played around some.  Rebooted into XP and now I'm waiting for updates on that.  I'm going to boot back into Ubuntu and configure my printer.  Sound, evolution email and wireless internet working now.  This has been painless to this point.  Thanx very much for the push.  I have a lot to learn.  I have some unix experience, but its been a long time now.

I just realized my id is my daughters.  Apparantly importing the user accounts didn't go as planned.  Now I need to get my pic to be me :<)  Where to look?  I'll be delving in the meantime.

Later - Dean

---

