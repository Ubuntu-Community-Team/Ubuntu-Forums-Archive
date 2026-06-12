---
title: "Boot Managers and CompizConfig manager"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by fulc on 2010-02-07
Hello everyone. I'm new to this forum and I hope to meet some nice people in here.

So let me start with the few "problems" I have.

I installed Ubuntu 9.10 32-bit via Wubi manager. Now when I start the computer, I get both Windows 7 boot manager and GRUB. If I choose the Ubuntu option on the Win 7 boot manager it leads to GRUB, where I can choose 2 different versions of Ubuntu (which is not clear to me) - Ubuntu,Linux 2.6.31-19-generic-pae and Ubuntu,Linux 2.6.31-17-generic-pae. I guess the second option appeared after some update. If I choose Win 7 in Grub it leads back to the Win 7 manager where I can boot Win7 normally. Now, it all works good, but I would like to remove one of the 2 boot managers as it is annoying. Which one is easier to remove and could you explain it to me please?

Next, I used to have Windows Vista with 9.04 Ubuntu installed via Wubi. Back then, I used Compizconfig manager and it worked pretty well. Now when I try changing anything, it simply doesnt work. I cant activate Expo and Desktop cube, and I also cannot set the number of desktops I want. I usually use 2x2 desktop size, but now I cannot make it happen :S.

Any help is greatly appreciated. Thanks!

---

### Post by Mark Phelps on 2010-02-08
You've installed Ubuntu INSIDE MS Windows.  MS Windows needs its own boot loader.  Ubuntu needs its own boot loader as well.

When you select Ubuntu from the MS Windows loader, you are actually launching GRUB4DOS (not GRUB).  This is a version of GRUB that runs in MS Windows.  It, in turn, launches the GRUB menu, allowing you to select the kernel version you want.

If you only want to deal with one boot manager, you would have to install Ubuntu OUTSIDE MS Windows.  But even then, you would still have to retain the MS Windows loader because GRUB can not boot MS Windows.

---

