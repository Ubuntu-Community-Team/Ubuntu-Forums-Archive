---
title: "Ubuntu 7.04 and NVidia 8800 GTS Install Failure"
date: 2007-08-26
forum: Installation &amp; Upgrades
---

### Post by cebrown on 2007-08-26
I have been poking around now for a few hours on the support site and quite can't seem to find the solution.  Here are the facts so far.

Machine:
1.  Dual core Intel 2.4
2.  4 GB RAM
3.  Dual booting with Vista
4.  Two internal SATA Drives
      A.  150 GB drive (Windows has 90 GB)
      B.  320 GB drive (entire drive is NTFS)
5.  Video is an NVidia 8800 GTS 320
6.  Audio is SoundBlaster X-Fi Xtreme Gamer
7.  Desired Ubuntu is 7.04 64-bit

Issues:
1.  Used GParted to successfully shrink Windows boot drive (above)
2.  Failed to use graphic installer of Ubuntu 7.04 64-bit
3.  Successfully installed Ubuntu 7.04 64-bit with text installer
4.  System fails to launch Gnome Desktop Manager (screen is black)
5.  I have manually installed the latest NVidia drivers
     A.  I downloaded the drivers in Windows
     B.  I mounted the Windows folder to copy the file & execute
     C.  Still unable to launch GDM
6.  I followed someone else's guide on the support site to set the card to VESA only.
     A.  That worked, and was the first time in Gnome, but I want the real drivers.
7.  I have run ENVY and removed and installed NVidia drivers
     A.  Still same problem

I have installed 6.10 before but that was on a different video card and that went flawlessly.

Any help would be awesome.  I don't want to go back to a Windows-only world, but don't have the expertise to continue with this struggle.

Thanks again!

---

### Post by chek2fire on 2007-08-26
log in to recovery console and give
sudo dpkg-reconfigure xserver-xorg
in the wizard there select vesa driver an simply press enter to the other options.

---

### Post by dabl on 2007-08-26
Maybe follow this guy's method : [http://ubuntuforums.org/showthread.php?t=514161](http://ubuntuforums.org/showthread.php?t=514161)

---

### Post by cebrown on 2007-08-26
I did the VESA configuration and it did work, but I do want to play games and this simply won't work.

I also followed the other guy's guide and it did end up loading Gnome but then I received an error message that the HAL failed to load.  

Basically, thanks for the help guys, but I think I will wait for the next version of Ubuntu where they have hopefully worked out the issues with the nVidia upper-end cards.  

Oh well, back to Windows for now.

Thanks again.

---

### Post by Pumalite on 2007-08-26
Check this: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation) And this: [http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html](http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html)

---

