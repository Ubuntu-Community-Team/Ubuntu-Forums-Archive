---
title: "Cannot install GRUB2 after windows 7 install"
date: 2010-09-27
forum: Installation &amp; Upgrades
---

### Post by olig1905 on 2010-09-27
Right I had to uninstall windows xp and install windows 7 to play more games! I use windows to play games and that is it.

I have restored grub before and i even double checked with this guide:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

i have two hard drives

sda - 320gb with windows

sdb- 100gb /home
      -12 gb /
      -480gb (NTFS) shared

however after reinstalling grub it still boots into windows!

please help

*/ Edit i will boot into windows properly then shut it down cos its coming up with windows was not shut down properly and if that doesnt work it has then been shutdown properly and i will install grub again but arrrrrrrrrrgh

---

### Post by olig1905 on 2010-09-27
sorry for doublle post just wanted to subscribe to this thread and it was the quickest way i could think of

---

### Post by Rubi1200 on 2010-09-27
Where did you install GRUB to?

Have you tried booting by changing the BIOS settings?

---

### Post by efflandt on 2010-09-27
If you installed grub on the 2nd hard drive mbr, you may still need to press some key during the BIOS splash screen to select which drive to boot from.  That is necessary for many computers even if you change drive boot order in BIOS, maybe to avoid inadvertently booting to the wrong drive, like a CD or DVD with something nasty on it.

The first and only virus I ever caught was a boot sector virus spread by floppy disks (Stoned Empire Monk or Monkey) before the internet as we know it.

---

