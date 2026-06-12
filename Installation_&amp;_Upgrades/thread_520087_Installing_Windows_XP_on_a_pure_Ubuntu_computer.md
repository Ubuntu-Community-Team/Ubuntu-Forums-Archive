---
title: "Installing Windows XP on a pure Ubuntu computer"
date: 2007-08-07
forum: Installation &amp; Upgrades
---

### Post by botulismo on 2007-08-07
I've found a few posts regarding doing this, and I don't want to get flamed - but I would like to use XP for a couple of applications that don't work on Ubuntu - mainly Photoshop (I have tried many times to install 7 with WINe, but I can never successfully finish the install), and a couple of games. I do understand it is better to install Ubuntu after Windows, but as that is not an option, I was wondering if there are any hints anyone can offer me? Or, alternatively, has the Direct3D support in VMWare matured enough to allow for the usage of modern 3D games? I have seen [this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") but I was wondering if there's any other things I need to know...

Questions I do have:

-Does Windows have to be the first partition? Isn't it impossible to resize a partition so it is no longer the first partition?
-Would it be easier if I just rescued an older hard drive I had and installed XP on that - and how?
-The last two times I tried to set up a dual boot system the proper way (XP first, Ubuntu second) the Windows boot would work once after I installed Ubuntu, and then, afterwards, Windows simply wouldn't load... Any idea why that is, and if I do set up a dual boot, how do I stop that?

I do love Ubuntu, and have no desire to switch back to XP, and yes, I do understand that the reason Linux doesn't have support for these applications is because narrow-minded companies do not write their applications for Linux systems. But, pragmatically, if I want to do these things, I require a copy of XP on my computer.

Thanks, everyone.

---

### Post by lisati on 2007-08-07
The wisdom I've read through these forums suggest that it's sometimes easier to install Windows first then Ubuntu. You might find that Windows will replace "Grub" with its own loader, and make Ubuntu appear "invisible" to the boot process, even though it's still on your computer. The exact reference for a suitable workaround that saves having to re-install Ubuntu from scratch eludes me for the moment.

---

### Post by Pumalite on 2007-08-07
After installing Windblows, re-install Grub following these guidelines: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Or use Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

