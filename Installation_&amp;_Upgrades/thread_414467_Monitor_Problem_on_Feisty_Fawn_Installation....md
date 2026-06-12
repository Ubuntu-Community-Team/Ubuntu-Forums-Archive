---
title: "Monitor Problem on Feisty Fawn Installation..."
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by PetePlatterson on 2007-04-19
Hello,

I've been trying to install Feisty Fawn from the installation CD.  Everything runs smooth until the system tries to start X, at which time I get a "Input Not Supported" message from my monitor.  I have an ACER AL1916 LCD panel and a ATI 9600 video card.  I've tried adding the boot options vsync=75 hsync=60 with no effect.

Ubuntu has worked with this monitor in the past.

Any ideas?

Thanks.

---

### Post by PetePlatterson on 2007-04-20
Hello,

I thought I'd post back in case someone else has a similar problem in the future.  

What I did was on the inital boot screen, I unplugged my monitor.  I then hit enter and let everything load up until the CD stopped.  I then replugged the monitor.  I then hit ctrl+alt+f1 to try to go to a terminal.  The screen blinked, but was still black.  I then went to X again (ctrl+alt+f7), again with a blink and black screen.  I then restarted X (ctrl+alt+backspace).  X started and after a second or two of black I got an 800x600 logon screen.  From there things went fairly smoothly.  Had to fight with Xorg a bit once I got it loaded, but so far so good.

Hope this works for someone else in the same situation.

---

### Post by thayerw on 2007-04-20
If you don't mind running the ATI proprietary driver, this workaround may be a simpler solution:

[http://ubuntuforums.org/showthread.php?t=414723]("http://ubuntuforums.org/showthread.php?t=414723")

---

