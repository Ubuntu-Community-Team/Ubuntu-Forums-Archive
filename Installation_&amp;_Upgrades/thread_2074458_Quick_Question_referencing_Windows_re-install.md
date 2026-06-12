---
title: "Quick Question referencing Windows re-install"
date: 2012-10-21
forum: Installation &amp; Upgrades
---

### Post by lemonoid on 2012-10-21
I know there is a ton of documentation on this, and they are good with telling how to do it, but as always, no guide is perfect in that it includes every detail of every situation, because that's just unreal. So I wanted to ask a community where live people have been through the process. I have a current installation of Win7 beside my Ubuntu 12.04, my Win installation is messed up for some reason. I have a Win7 premium iso that I'm going to burn to disk. I want to simply replace my current installation of Windows with the one I have now, so that's a little different than just installing after Ubuntu because I already have partitions made on my custom built desktop. I have never had to re-install Windows after installing Ubuntu. I just wanted to ask, in this situation, is the best convention for me to delete the current Windows partitions and make new ones? Or how should I go about that in a different way if there is a better one? Will Win7 make partitions for me? It is the 3.1GB iso, so its not a set of four recovery discs.

---

### Post by funicorn on 2012-10-21
I know I posted for a reason.

[http://ubuntuforums.org/showthread.php?t=2035071](http://ubuntuforums.org/showthread.php?t=2035071)

---

### Post by oldfred on 2012-10-22
Windows installs to the NTFS primary partition with the boot flag or active partition in Windows. Not sure with Windows 7 as it normally installs to two partitions - one a hidden 100MB boot/repair that has boot flas and the main install. 

Be sure to have current version of Ubuntu liveCD so you can reinstall grub2.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

### Post by Mark Phelps on 2012-10-22
> **lemonoid said:**
> ... I want to simply replace my current installation of Windows with the one I have now ...

Then, you should check over at the Window 7 forums (sevenforums.com) -- as they have instructions for doing a reinstall of Win7 from DVD that will not wipe out what you have.

---

### Post by lemonoid on 2012-10-22
If the main problem with this is usually grub getting wiped out? Can't I just use Boot Repair cd I have? Or will that not do the trick?

---

### Post by oldfred on 2012-10-22
Boot repair will work.

---

