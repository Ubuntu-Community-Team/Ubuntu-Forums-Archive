---
title: "GRUB package fails to install, crashes Ubuntu installation"
date: 2019-02-18
forum: Installation &amp; Upgrades
---

### Post by nniranjhana on 2019-02-18
Hey, I was in the middle of erasing old Ubuntu and reinstalling new one when I ran into this error stating GRUB packages failed to install and hence OS installation has failed. I have tried running Boot-Repair but could not fix this issue. I have this paste from Boot-Info:

[http://paste.ubuntu.com/p/twKzfRx6dk/](http://paste.ubuntu.com/p/twKzfRx6dk/)

Please tell me what I should to do install Ubuntu 16.04 ASAP and proceed with my work.

Thank you!

---

### Post by yancek on 2019-02-18
Are you upgrading or installing the entire new system to the old Ubuntu partition?  If the latter, you apparently tried to install in EFI mode without creating an EFI partition on the drive.  Take a look at the Ubuntu documentation at the link below.  Scroll down to the section 'Identifying if computer boots in UEFI mode' as it explains what you should see when booting the DVD/USB.  You need to decide if you want a Legacy or UEFI install and if UEFI, you need to create an EFI partition.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2019-02-18
You also are showing the old MBR(msdos) partitioning which is standard with BIOS boot.
You can install Ubuntu in UEFI mode to MBR, but UEFI strongly suggests using the newer gpt partitioning. Windows only installs in UEFI mode to gpt partitioned drives.

You booted installer in UEFI mode, system is UEFI, but drive is old BIOS/MBR configuration.

---

### Post by nniranjhana on 2019-02-19
Thanks @oldfred and @yancek
I was actually installing this (the new one to the old partition) when I was sleepy.

I think it prompted me with a warning (10 minutes before installing) as to which mode to proceed and I had chosen the "Continue with UEFI" instead of "Go Back", since it was on the right *facepalm* side (my stupor state didn't bother to read). Once I ran into issues, I googled, ran Boot-Info and Boot-Repair and created this post here on the forum everything half-asleep.

Later, went for a walk, came back and realized what I had done. I started the  install again yesterday, and continued with booting the installer in  legacy mode itself and completed it, forgot that I posted here too. I'm sorry for the trouble, and thanks for helping me out! :)

---

