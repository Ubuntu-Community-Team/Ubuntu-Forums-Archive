---
title: "Black screen whenever I try to install Ubuntu"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by silvermage91 on 2010-02-13
Hello, I've recently gotten interested in installing Ubuntu on my computer alongside Windows 7, and set aside a partition for ubuntu. When I boot up my computer with the CD in it, I'm able to see the ubuntu install screen, but once I try to run the demo or to install ubuntu, my screen simply goes black and seems to do nothing. A friend of mine told me that it might be my video card, which is an intel mobile chipset. could that be the problem?

---

### Post by JayPeeJay on 2010-02-13
Hey, I'm kinda a noob, but the same thing happened to me.  From the Grub bootloader menu, you will see a command that brings up additional options (I think it's F8 but my memory is fuzzy on that).  Hit that, and remove the "quiet splash" from the command line that appears, then boot it.  If your computer is anything like mine, that will be enough to make it run right there.  If not, at least you have the splash to show you where your computer is freezing up.  Let me know if that helps.

---

### Post by presence1960 on 2010-02-13
> **silvermage91 said:**
> Hello, I've recently gotten interested in installing Ubuntu on my computer alongside Windows 7, and set aside a partition for ubuntu. When I boot up my computer with the CD in it, I'm able to see the ubuntu install screen, but once I try to run the demo or to install ubuntu, my screen simply goes black and seems to do nothing. A friend of mine told me that it might be my video card, which is an intel mobile chipset. could that be the problem?

At the menu screen after you boot the Live CD hit F4 and choose safe graphics mode. For more info about that and other boot options see [here]("https://help.ubuntu.com/community/BootOptions").

If that does not work try installing with the alternate text based installer. Get it [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

---

### Post by silvermage91 on 2010-02-14
the splash to see where its messing up? well, sometimes when I try to use the live CD option, I see a dark screen with some color design, and then the screen goes completely black. I think im going to try the text based installer

---

