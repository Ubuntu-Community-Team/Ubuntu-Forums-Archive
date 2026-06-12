---
title: "boot problem..."
date: 2008-08-17
forum: Installation &amp; Upgrades
---

### Post by jesar_gacula on 2008-08-17
I have installed WinXP on my eeePC. After doing so, I installed eeeUbuntu on a 4Gb SD card drive using 'netbootin' (installed on my 2Gb micro SD). All in all, I have 3 drives connected on my eeePC, the 4Gb SSD (for WinXp), 2Gb micro SD (eeeUbuntu installer), and the 4Gb SD card (where eeeUbuntu was installed).

On reboot, I pulled off my 2Gb micro SD card as instructed by the installation wizard. On boot, I encountered "Error 21". So what I did was, I put it back in and reboot again...fortunately, it worked! BUT...I can't use either of my OS's if I boot up my PC without my 2Gb micro SD. What should I do to make my eeePC work, without the use of my 2Gb micro SD?

Please help me with this problem..thanks! ^_^

---

### Post by caljohnsmith on 2008-08-17
Most likely what is happening is that Grub got installed to the MBR of your Win XP drive, and for some reason Grub is pointing to your 2 GB SD card for all its config files in /boot/grub, instead of using your 4 GB Ubuntu SD card like it should. Fixing your problem would be alot easier if you had a Live CD you could boot--is this possible, or am I safe to assume no since you installed Ubuntu from the 2 GB SD card? 

Also, can you change your BIOS boot order so that you can boot directly off the 4 GB SD card and not your Win XP drive? If you can do that it will be easier to fix your problem, and it will have the advantage that you can disconnect *both* your SD cards and Windows will still be able to boot (assuming we change back the MBR to Windows on your Win XP HDD). With the way things are now, even if we point Grub to the correct Ubuntu partition on your 4 GB SD card, you will always have to have your 4 GB SD card connected to boot your system.

So what would you prefer?

---

