---
title: "Older Laptop Install Problems"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by ironmonkeygf on 2007-05-03
I'm trying to install one of the 'buntu's on an older Vaio (PCG-FX120, 100 GB HD, 128MB RAM).  There should be 192MB, but for some reason whatever card is in the second slot the memory isn't recognized.  I'll save that issue for another day.  I'm definitely a beginner with Linux (well less than a beginner, as I read somewhere, since I'm fairly proficient in Windows), but I do have Ubuntu running on both my desktop and my regular laptop.

I first tried installing Xubuntu to no avail.  The install screen comes up fine, but when I select Text Mode Install, The machine loads the kernel, making it to 100% with no problems, and then goes to a blinking white cursor on a black screen.  No amount of button mashing (I tried Ctrl-D, Ctrl-Alt-F1, ESC, then just randomly hitting everything) does anything to change this screen.  

I wiped the disk with DBAN when the Xubuntu install wouldn't work.  I was able to boot the live GParted CD and make some partitions, but it wouldn't start X unless I used the force i810 mode.   I also tried the alternate install of Ubuntu, but I keep getting the same stupid cursor.

After the 'buntu's wouldn't work, I tried the ZenWalk Live CD.  This displays noise on the screen, but at least there's some pretty colors.  I can't seem to navigate anywhere from there either.  

Any suggestions or insights?

---

### Post by ironmonkeygf on 2007-05-05
Hah...got it.  Thanks to jarviw, [http://ubuntuforums.org/showthread.php?t=206517]("http://ubuntuforums.org/showthread.php?t=206517").  

**acpi=off** has to be added to the install options.  To do this, hit F6, which should bring up the box with the parameters in it; I just added it to the end.

---

