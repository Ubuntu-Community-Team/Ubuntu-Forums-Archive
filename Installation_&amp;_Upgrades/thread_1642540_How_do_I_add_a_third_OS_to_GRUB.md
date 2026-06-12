---
title: "How do I add a third OS to GRUB?"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by SazquatchWNC on 2010-12-10
:confused: I am currently dual booting with Grub 2 to Ubuntu 10.10 or Vista Ultimate 64 on a Gateway GT5676 Computer with an AMD Phenom processor.  I want to install Windows XP Pro on a second drive and add it to the boot menu.  What's the process?  Thanks in advance for any insight.

---

### Post by oldfred on 2010-12-10
Welcome to the forums. 

This scans all hard drives for other operating systems and adds them to the menu.
sudo update-grub

Windows will want to combine its boots into one. If using grub2 you will want to prevent that. You probably can just remove boot flag from first windows install even though you are installing to second drive.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by SazquatchWNC on 2010-12-12
:smile:   Thank you, OldFred.  I was able to install XP Pro on my second HD and update grub as suggested.  I now have all three OSes booting successfully.  A minor glitch resulted from my having another partition on the drive.  My XP System Drive is now J: rather than C:.  I might reorganize thew second drive at a later date, but for now, all is well.

---

