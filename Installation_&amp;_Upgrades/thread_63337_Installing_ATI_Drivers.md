---
title: "Installing ATI Drivers"
date: 2005-09-07
forum: Installation &amp; Upgrades
---

### Post by Zigbigadoorlue on 2005-09-07
I am really new to Linux, but I figure that the only way I'm going to learn it is by using it, so i recently struggled through the installation of Ubuntu. I made three partitions: the swap, root and /var.

Now its all well and good the install was fine but now I cant seem to install the ATI Radion Linux drivers. Now I know almost nothing about Linux so i am assuming that .run is like .exe. But when i opened ati-driver-installer-8.16.20-i386.run it give me a error message: “Could not open the file '/home/katz/Desktop/ati-...staller-8.16.20-i386.run' gedit was not able to automatically detect the character coding. Please check that you are not trying to open a binary file and try again selecting a character coding in the 'Open File...' (or 'Open Location') dialog.”

On the ATI website it gave me the impression that I needed to access the file through terminal, so i navigated terminal (painfully) to the desktop. The web site says as follows: “Enter the command ./ati-driver-installer-8.14.13.run to launch the ATI Proprietary Linux driver installer.” so i typed “katz@THEMONOLITH:~/Desktop$ /ati-driver-installer-8.14.13.run” and got this: “bash: /ati-driver-installer-8.14.13.run: No such file or directory” i also tried “./ati-driver-installer-8.14.13.run” as it describes in the text but that did not help either. 

This would not be such a problem if the refresh rate on my screen could not go above 60Hz, its giving me a head ache and making me nauseous. I tried looking at the BinaryDriverHowto/ATI but was very confused. Is there any way I'm going to solve this problem without getting a Linux guru to help me install some friken video drivers?

---

### Post by mlomker on 2005-09-07
I just made a post about that a few hours ago.  To be blunt, if you aren't comfortable with the command line then you're going to hate linux.  If things go wrong with a video card update then you will not be able to boot into the graphical shell at all--when Xwindows blows up it leaves you at the command prompt.

[Here's how I did it.](http://www.ubuntuforums.org/showthread.php?t=63290&highlight=ati+driver)

---

### Post by Zigbigadoorlue on 2005-09-07
I hate to disagree but your problem seems to have little to do with mine. I'm having a problem simply initializing the driver, once i do i suspect i will have little trouble installing it. Additionally i am not uncomfortable with using command prompt, I'm just not familiar with Linux terminal and am in the process of learning.

---

### Post by Thulemanden on 2005-09-12
Why not select either 'ati' or 'radeon' after running xf86config in a terminal as root?

Have you tried:   ./abcd.run?  (dot slash)

---

