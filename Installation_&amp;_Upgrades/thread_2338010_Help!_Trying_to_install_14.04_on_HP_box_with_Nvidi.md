---
title: "Help! Trying to install 14.04 on HP box with Nvidia GTX-745."
date: 2016-09-23
forum: Installation &amp; Upgrades
---

### Post by dtree46 on 2016-09-23
Trying to install 14.04 on a HP Envy with a Nivida GTX-745 graphics card.
The 14.04 cd is running as if installing. However, the monitor screen is black.
Did not get a 'no signal' error.

Any help appreciated as the computer does not work now.

dlw

---

### Post by ajgreeny on 2016-09-23
Have you installed yet or are you still trying and just running the live system from DVD or USB?

With an nvidia graphic card you will probably need to use the nomodeset boot option which you can get to if still using the live system by hitting F6 when you see the first purple screen with **keyboard** and **man** icons at the bottom.

If you've already installed the OS you will need to hold Shift at power-on and when the grub menu appears hit "e".  navigate to the line with "quiet splash" and add the word "nomodeset" so that you see "quiet splash nomodeset" then use Ctrl+X to boot.

Hopefully that will give you a low resolution GUI from which you can use Additional Drivers to install the needed nvidia graphics driver for your card.

---

### Post by dtree46 on 2016-09-23
Can not even boot now with 14.04 dvd or the w10 that was already installed.
I been able to get into the bios, set it to boot from cd, but it will not. Just reads a bit then quits.
What happens now is, a blue screen with Your PC/Device needs repair when trying to boot.
Use a recovery system to repair.

I do not have a recovery system.
Searching the net now.

Thanks for replying.
Any suggestion appreciated.

dlw

---

### Post by ajgreeny on 2016-09-23
BIOS or UEFI?

If Win 10 was preinstalled it will undoubtedly be UEFI.

More info here which may help, [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) and tips here [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

See also Boot-Repair in my signature and follow the instructions there.  
**Do not run default repair** just run the boot-info-script and show us the pastebin link you are given. Someone here will be able to decipher that and give you some more help.

---

### Post by dtree46 on 2016-10-08
Update:
Ubuntu starts installing with UEFI mode.
However, my Nividia GTX-745 doesn't play well with Ubuntu.
An Nvidia driver needs installed. That means Ubuntu has to be installed.
Since Ubuntu will not install because of the Nividia card, how, or can this be accomplished.

Any help appreciated.
dlw

---

### Post by Bucky Ball on 2016-10-08
Run with the 'nomodeset' option as suggested by ajgreeny in post #2.

When you see the purple screen described, hit F6, choose 'nomodeset', proceed. You can install the correct driver when you're installed. Untick 'Install third-party drivers' and 'update during install' during the install. Sometimes it causes problems and you can do both later.

---

### Post by dtree46 on 2016-10-09
Success, Thanks guys. nomodeset did the trick.

dlw

---

### Post by Bucky Ball on 2016-10-09
Great. Before you mark this solved, a point.

If nomodeset worked by choosing that option for install you should now install the correct driver once the OS is installed if you're having issues. Look in Additional Drivers. What do you see there for video?

Please mark this thread as 'solved' using Thread Tools at top right.

---

