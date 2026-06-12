---
title: "Live CD Hangs at Black Screen after Ubuntu Logo+Loading Bar"
date: 2007-03-30
forum: Installation &amp; Upgrades
---

### Post by otakumark on 2007-03-30
**SOLUTION AT END OF FIRST POST. NOTE, DIRECTIONS ARE FOR ATI CARDS SPECIFICALLY AFTER STEP 6**
[http://ubuntuforums.org/showthread.php?t=348189&highlight=live+cd+hangs+after+loading+bar](http://ubuntuforums.org/showthread.php?t=348189&highlight=live+cd+hangs+after+loading+bar)

This problem has been posted before in the thread above and others, I read the stickies and it said to make your own thread, so here's mine. :)

AMD64 3500+
2GB of RAM
ATI x800XT 256mb
ASUS motherboard
250GB SATA 3.0GB/s Western Digital HDD
Windows XP already installed, 30-40GB of space ready to be made into a Linux partition through the linux installers software.

Fully functioning, healthy and happy NEC CD-RW Drive
Both 32-bit and 64-bit versions of the newest stable Ubuntu release, 6.10.
CDs burned at a lower rate (16x) to ensure quality of the burn.
Md5sums are correct on all files involved.
The built-in CD check gives the CDs a greenlight.
This problem seems to extend beyond just ATI video cards, in the above thread it affects Nvidia and other less common video adapters.

Reproducing the problem is as follows:
1. Boot from the Live CD, and choose either the first option (Boot from Live CD/Install) or the Safe Graphical Mode option.
2. Kernel is loaded, green loading text appears momentarily at the top of the screen.
3. User is presented with a Ubuntu logo (in some cases off-color in either grayscale or orange with "artifact"-like problems oftentimes occurring).
4. After a moment, the back and forth movement ends. The bar becomes a true loading bar, fills, and the screen goes black.
5. The black screen persists as your monitor stays active (greenlighted), your CD drive stops moving (and actually wont open during this in my situation!), and you stare at the screen ad infinitum.

**SOLUTION FOUND FOR ATI CARDS SPECIFICALLY:**
If you are having a hanging Live CD boot, or getting the black screen described above, do the following.
1. You have to use the Alternate Install CD. Completely install Ubuntu (with a boot loader in my case).
2. After installation, when given the option of a normal boot or a ¨recovery¨ boot, choose the recovery.
3. At the prompt, type ¨sudo dpkg-reconfigure xserver-xorg¨
4. Follow the prompts to accurately setup your video, both your monitor and video card. Choose VESA as your video driver.
5. After that is done, type startx at the prompt/console.
6. This will load your desktop, congratulations, we are almost done. (If moving windows are very stuttery, dont worry its normal at this point.)
7. Open [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu) in a Firefox window, and open a terminal window from Applications -> Accessories.
8. Choose your distro (currently shows 5.10, 6.06, 6.10, and 7.04), and follow the directions by copying and pasting the commands in the terminal.
9. The last direction is a copy+paste of a reboot command, after the reboot choose the normal startup, it will load your desktop and you can set your preferred desktop resolution and refresh rate.

---

### Post by Kamikaze Wardriver on 2007-03-30
> **otakumark said:**
> [http://ubuntuforums.org/showthread.php?t=348189&highlight=live+cd+hangs+after+loading+bar](http://ubuntuforums.org/showthread.php?t=348189&highlight=live+cd+hangs+after+loading+bar)

This problem has been posted before in the thread above and others, I read the stickies and it said to make your own thread, so here's mine. :)

AMD64 3500+
2GB of RAM
ATI x800XT 256mb
ASUS motherboard
250GB SATA 3.0GB/s Western Digital HDD
Windows XP already installed, 30-40GB of space ready to be made into a Linux partition through the linux installers software.

Fully functioning, healthy and happy NEC CD-RW Drive
Both 32-bit and 64-bit versions of the newest stable Ubuntu release, 6.10.
CDs burned at a lower rate (16x) to ensure quality of the burn.
Md5sums are correct on all files involved.
The built-in CD check gives the CDs a greenlight.
This problem seems to extend beyond just ATI video cards, in the above thread it affects Nvidia and other less common video adapters.

Reproducing the problem is as follows:
1. Boot from the Live CD, and choose either the first option (Boot from Live CD/Install) or the Safe Graphical Mode option.
2. Kernel is loaded, green loading text appears momentarily at the top of the screen.
3. User is presented with a Ubuntu logo (in some cases off-color in either grayscale or orange with "artifact"-like problems oftentimes occurring).
4. After a moment, the back and forth movement ends. The bar becomes a true loading bar, fills, and the screen goes black.
5. The black screen persists as your monitor stays active (greenlighted), your CD drive stops moving (and actually wont open during this in my situation!), and you stare at the screen ad infinitum.

Have you tried changing graphics mode at the boot screen? It sound to me like it is not liking something about the video settings.

---

### Post by Pragmatik on 2007-03-30
Mine did exactly that, and it turned out to be an issue with 6.10 and my gear.  I had checked the CD image and burned it at 4X, but it was the computer.  Installing 6.06 worked without a hitch and took like ten minutes.

I think I remember reading that some folks have the same issue with the 6.10 disk.  You can always just stick with 6.06 until April 19th:)  That's what I plan on doing.

---

### Post by otakumark on 2007-03-30
> **Kamikaze Wardriver said:**
> Have you tried changing graphics mode at the boot screen? It sound to me like it is not liking something about the video settings.

Yeah, I've attempted using the safe graphics mode but it was a no-go. Time to test 6.06. :>

---

### Post by otakumark on 2007-03-31
Okay, I tested 6.06, it loads with the loadng bar + this time it displays the list of loading services, etc. 

However, at the end of this loading it gives another black screen.

If this is a video problem, how do I circumvent this issue? Or, rather, if using the Alernate Install CD will work, where can I get instructions on it as well as what I need to do especially for this situation?

---

