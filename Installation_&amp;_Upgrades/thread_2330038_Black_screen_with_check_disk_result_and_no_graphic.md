---
title: "Black screen with check disk result and no graphic interface after install"
date: 2016-07-07
forum: Installation &amp; Upgrades
---

### Post by francoish36 on 2016-07-07
Hello,

I just installed Lubuntu 16.04 LTS on an old Dell desktop unit.

I have no trouble to start the install from my live USB but after installing, I get the result of mounting the main disk, but no graphical interface.

Swithching to different TTY shows me the login prompt but revert to this strange message automatically. It's like X is not starting or displaying correctly or I have other trouble.

Do you have a suggestion on how to solve this?

Kind regards.

---

### Post by ajgreeny on 2016-07-07
There has been a problem with some systems not installing the **xserver-xorg-video-intel** package, when the hardware has one of the ld Intel 945 graphic chips.

As you say you are able get to a TTY from Ctrl+Alt+F1 you should first try ```
sudo apt-get install xserver-xorg-video-intel
``` which may solve your problems.  If I have misunderstood the ability to get to a TTY try booting the system from the grub menu with nomodeset option; you can do this by 
1. - Hold shift at power-on to get the grub menu
2. - Hit "e" when the highlighted line is your Lubuntu install
3. - Use cursor keys to the words **quiet splash** and add **nomodeset** after that without changing anything else
4. - Ctrl+X or F10 to boot, hopefully to a low resolution desktop from which you can install tghat missing xserver package.

There is a launchpad bug for the problem, if this is the one you experience.
[https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/1575460](https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/1575460)

Good luck. If it does not work for you (it did for me), come back again and we will try to sort it out some other way.

---

