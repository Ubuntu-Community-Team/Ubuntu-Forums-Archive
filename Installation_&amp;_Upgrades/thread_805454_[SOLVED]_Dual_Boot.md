---
title: "[SOLVED] Dual Boot"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by khanoftartary on 2008-05-24
Alrighty. I had an interesting situation the other day; I had come, for the first time, to a hardware problem for which there was not an ubuntu alternative. And the software for this hardware would not work on my laptop (windows machine) because of memory. So I finally decided to install a windows partition on my desktop. I resized my main partition (hda1), shrinking it by about 6 Gb (I didn't plan on doing much besides using this program), and then installed Windows XP Pro on the empty space. 

The Installation went very well, and windows now works perfectly. It's the only thing that does. I cannot boot from my other partition, and on startup I go automatically to my Windows partition, without another option. Anyone have a solution? Preferably simple. I'm pretty skilled on Ubuntu, but I'm a completely newbie on dual desktops. Thanks a bunch.

---

### Post by Herman on 2008-05-24
I'm guessing you mean you installed Windows after Ubuntu in your desktop computer, and Windows overwrote GRUB and took over your MBR.

It's easy to fix that, just re-install GRUB, you can use your Ubuntu LiveCD to do that, [Re-install GRUB with a GRUB shell]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD"). - re-install GRUB from anywhere to anywhere with anything.

Or, if you prefer, you can use [Super Grub Disk.]("http://www.supergrubdisk.org/")
[I reinstalled Windows and Linux no longer boots]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#I_reinstalled_Windows_and_Linux_no").

---

### Post by khanoftartary on 2008-05-28
Thanks a bunch, that worked very well. I used the 're-install from shell' while inside the live CD.

---

