---
title: "When EXT3 or SWAP partition is altered, GUI is screwed up..."
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by atirox on 2009-11-16
Okay,
I had originally installed Ubuntu 9.04 onto my Compaq Presario R3055CA, I didnt allow it enough space, and it was so full that I couldnt boot the machine, so i reinstalled it, allowing it enough space, or so I thought. So, I booted from the installer CD, resized the partition in GParted, then booted Ubuntu. When I got to the GUI login screen, the graphics were really distorted. If you've ever cracked an LCD screen, you'll get some idea of what it looks like. Just a bunch of random colours all over the place. Then the display blanked, and it showed almost the same pattern. It did this about 3 times after the first, making a total of 4 times. Then it just stayed showing the funky colours. I tried logging into a terminal by pressing Alt+F1-6, but nothing happened. So, i rebooted the machine, and tried again, but in recovery mode, and chose the option to fix the graphics errors. This didn't work, so I reinstalled Ubuntu, with again, what I thought would be the right amount of space. It worked fine for a while, then i really started using it, and found out that, No, I still didn't partition enough space for it. *sigh* One of these days i'll learn... Anyway, what i want to know, is why I got the funky colours when i resized either the ext3 or swap, or both partitions, and what i can do to prevent it from happening this time, when i try to resize the partitions.

When i got the funky colours, I could still boot into Windows XP, and boot Memtest x86. The funky colours only showed up when using the GUI interface in Ubuntu. Since I installed Ubuntu 9.04 at the time, it was updated to Ubuntu 9.10, which i am currently using. The reason why I dont want to install Ubuntu 9.04 again, is because I have a Broadcom wireless card. As y'all probably know, Broadcom hates Linux with a passion, so it was a pain in the *** to get the card working correctly, and i dont want to have to do all that again.

---

### Post by atirox on 2009-11-18
I went ahead and did the resize, this time using gparted from a bootable usb disk, and it worked. Im pleasantly suprised. not sure why this one worked.

Just thought i'd mark this thread as solved, didnt intend to bump my own thread.

---

