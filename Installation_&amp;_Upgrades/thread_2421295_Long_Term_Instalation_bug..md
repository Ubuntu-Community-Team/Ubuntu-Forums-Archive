---
title: "Long Term Instalation bug."
date: 2019-06-19
forum: Installation &amp; Upgrades
---

### Post by NahuelMS on 2019-06-19
There is a bug in the ubuntu installer, it is there from forever. The bug: if you have an internal drive in your system with Windows or another Linux distro it puts the EFI files in there, even if you make a new EFI partition in the usb drive specificly. Every time i want to install Ubuntu in a usb drive or external disc i need to take out the internal drive of the computer. It is really a PAIN in the ... . Is it posible to fix the installer????. I need windows on my pc and use Ubuntu for other things, so i prefer to have ubuntu on an external SSD that i can plug everywhere and have the system running. I think like me there are a lot of people who needs or would like to use the system like this. A simple search can show there are thousands of results talking about this but release after release the bug is still there. Also i think it is a good way for people to try linux without afecting their original system.
Thanks!

---

### Post by oldfred on 2019-06-19
You mean these bugs?:)
       Ubuntu Installer uses wrong bootloader location for USB/sdb UEFI installs 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457)
Posted work around to manually unmount & mount correct ESP during install
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1229488)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1229488) 
    
I did find a work around to change ESP mount during install. You still have to edit fstab after install.

---

### Post by NahuelMS on 2019-06-20
Just unplug the internal drive and if the only drive present is the usb one it will work correctly. But it is a pain in the a... to open the computer and unplug the drive. This bug have been there for at least 5 years but it seems no one cares...

---

### Post by oldfred on 2019-06-20
Many newer systems have UEFI setting to turn a drive on or off. You may not need to go into case to unplug drive, but can do it logically.

---

### Post by ubfan1 on 2019-06-20
In six years, only three dozen people have clicked on the bugs' "Does this affect me" button, so Canonical has no idea how many people have really been affected.  Do feel free to go to bug [https://bugs.launchpad.net/ubuntu/+s...y/+bug/1173457]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1173457") and [https://bugs.launchpad.net/ubuntu/+s...y/+bug/1396379]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379") and click on the button.  It's too bad the superset bug 1396379 is only of "medium" importance, while it forced the original (critical) USB bug 1173457 to become a duplicate, (but that's because if the second disk is never removed, the system does not become unbootable :^(  ).

---

