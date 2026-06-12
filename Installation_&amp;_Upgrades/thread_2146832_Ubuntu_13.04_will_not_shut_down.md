---
title: "Ubuntu 13.04 will not shut down"
date: 2013-05-19
forum: Installation &amp; Upgrades
---

### Post by GUZZLR on 2013-05-19
Hello All,
Installed Ubuntu 13.04 on an old Dell, and the install looks good, the problem is it will not turn off.  When I go to shut down the computer, it tries to shut down; however, the Ubuntu splash screen, with the little orange and white dots underneath stays on, and on, and on...I have to do a hard shut down. 
Dell Latitude D-630
Full Ubuntu 13.04 install over XP Pro
 Thanks for the help

---

### Post by claracc on 2013-05-20
Perhaps, this is the same bug as [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1010981](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1010981).

Have you tried to shutdown the laptop on battery and on ac power to see is there is any difference?

This thread [http://ubuntuforums.org/showthread.php?t=2146575](http://ubuntuforums.org/showthread.php?t=2146575) reports the same wrong behaviour.

---

### Post by GUZZLR on 2013-05-20
Tried different installs, just got through reinstalling, only this time I used Logical Value Management...I think that is what it was called. Not sure if I should have done that, what ever LVM is?
I did read the above thread and this is also my case.  My install is loading in BIOS emmulation because I do see the accessibility and Key Board at the bottom of the screen.  So, I need to get to an EFI boot partition and a GUILD partition table.  This is where I will need help as I do not know what all of this means?  but this is my problem as described in the above links

---

### Post by Ralph L on 2013-05-20
You might try Xubuntu.  Installing Xubuntu 12.04.x rather than Ubuntu/Kubuntu 12.04.x fixed my shutdown problems with a Compaq Presario 2100.  I am sticking with Long Term Support so I haven't tried 13.04.

---

### Post by GUZZLR on 2013-05-21
Unfortunately, I tried that.  Installed 12.04 over 13.04 and still have the problem.  I then reinstalled 13.04 and see the accessibility and Keyboard at the bottom.  I have  to perform a hard shut  down to get t he machine to close...

---

