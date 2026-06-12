---
title: "Replacing one distro with another."
date: 2011-07-27
forum: Installation &amp; Upgrades
---

### Post by tes151 on 2011-07-27
I have XP Pro, and Xubuntu 11.04 set up as a dual boot on my Dell Latitude D830.  If I wanted to replace Xubuntu with another Ubuntu, or Mint, or whatever, can I do a clean install and replace Xubuntu without disturbing the Windows side?  Is it just as simple as when I installed Xubuntu?

---

### Post by MSPdwalt on 2011-07-27
Yeah,

What I would do is first and foremost take a backup. Then find your XP pro disk (you will need it).  Then boot into XP, and delete the partition(s) with Xbuntu on it. Then put the XP disk in and boot to the recovery console and do a fixboot and fixmbr. That should allow windows to boot.

Then just setup dual boot with your new distro like you did with xbuntu.

BE CAREFUL you are deleting data and if you do it wrong you may end up re-building entirely from scratch.

---

### Post by smallfryfury on 2011-08-30
I do not have the OS cd for windows. Should I go about it in a similar way? I have heard GRUB can incur problems that won't allow one of the OS to boot afterwards. That's pretty nerve wracking to me. So, i've been sitting on the fence for a while with this. Currently I have XP and Mint 9, but want to switch Mint for Ubuntu 10.10. Thank you

---

### Post by Iantos on 2011-08-30
trust me, if it is the ubuntu 10.10 you want to install, there is no problem because xp is already installed so you wont have a problem with dual boot afterwards but the point is you will not use grub to choose which partition to boot anymore, instead you will use the windows boot loader because windows will now have been the first installation before ubuntu 10.10. so no problem, just install,  dual boot option will be there afterwards. normally GRUB gets destroyed if you are installing windows afresh while having ubuntu already on another partition.

---

