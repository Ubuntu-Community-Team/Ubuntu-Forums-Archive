---
title: "Trying to install Heron over Vista... Unique Problems Ahead..."
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by cmlewin on 2008-04-25
Hey All-
A few weeks ago I decided to be an imbecile and install my friend's copy of Vista Ultimate as an upgrade over XP.  Problem I didn't know at the time was it was a Dell copy and my computer is an HP Pavilion a1520y.  As a result I gradually lost all functioning of my CD drive.  And I can't install drivers for it because it sees my computer as a Dell so I 'do not meet minimum system requirements'.  Is there a way to mount the .iso to a partition to boot from it? Is it in the vista boot sequence that's screwing things up (boot menu still shows drive, but when I try to boot from there it goes to vista as normal)? Is there a way to install Wubi then do a full install there?  Please help as I'm a former Ubuntu user who moved in with a windows user and now am at a loss on our computer.

Thanks!

---

### Post by r3m0t on 2008-04-25
> **cmlewin said:**
> Hey All-
A few weeks ago I decided to be an imbecile and install my friend's copy of Vista Ultimate as an upgrade over XP.  Problem I didn't know at the time was it was a Dell copy and my computer is an HP Pavilion a1520y.  As a result I gradually lost all functioning of my CD drive.  And I can't install drivers for it because it sees my computer as a Dell so I 'do not meet minimum system requirements'.  Is there a way to mount the .iso to a partition to boot from it? Is it in the vista boot sequence that's screwing things up (boot menu still shows drive, but when I try to boot from there it goes to vista as normal)? Is there a way to install Wubi then do a full install there?  Please help as I'm a former Ubuntu user who moved in with a windows user and now am at a loss on our computer.

Thanks!

OK, just download wubi.exe from wubi-installer.org. If you've already downloaded the .iso, put it in the same directory as wubi.exe.

Now run wubi.exe, and it should detect your .iso if you've downloaded one. Otherwise it will help you download the .iso.

Now reboot and choose Ubuntu from the boot menu.

Now, using LVPM, you can remove Windows and "fully install" Ubuntu. The only problem is that LVPM is not quite ready for Ubuntu 8.04 yet.

---

### Post by cmlewin on 2008-04-25
Wow you are a king amongst men. I'm going to try that soon. So do you think I should install 7.10 first? or is that the only way to do a fresh install through Wubi?

Thanks again.

---

### Post by cmlewin on 2008-04-25
Okay new issue. I can't shrink my windows partition more than 732 MB. Don't know why (says it might be something about a disk image or something), but it won't let me create alternate partitions. Anyone got any clue?

---

