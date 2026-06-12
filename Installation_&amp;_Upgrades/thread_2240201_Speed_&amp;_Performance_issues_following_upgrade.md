---
title: "Speed &amp; Performance issues following upgrade"
date: 2014-08-18
forum: Installation &amp; Upgrades
---

### Post by crs501 on 2014-08-18
I have just upgraded from 12.04 LTS to 14.04 LTS. Everything functions - but very slowly. The Unity Launcher is performing *very slow* and *jerky*, and my Firefox browser is *slow to launch* too. I'm getting occasional error messages that say the OS needs to close unexpectedly, this has happened numerous times over the past 48 hrs. I'm curious whether there are any fixes available for my computer's speed/performance issues. I'm also wondering whether I need to re-install 14.04 LTS? 

I'm just an average user, and don't understand a lot of technical stuff, but if it's helpful, I use an old Dell Dimension 8100 PC, with a Pentium 4 1500 MHz cpu. My hard drive is 28.5 GB and from what I can determine I'm only using about 10 GB at the moment. Not sure what other info would help but I sure could use some advice here. Richard...

---

### Post by ajgreeny on 2014-08-18
I am a bit surprised that unity ran properly at all on that old hardware, and I suspect that you now do not have hardware, in particular the graphic card, powerful enough to run the 3D graphics needed for a good unity desktop experience.

Everything will probably depend on what graphics card do you have as a new driver for that might speed things up a bit, but in all honesty, I would suggest you try XFCE instead of unity, and you can try that by either running ```
sudo apt-get install xfce
``` or ```
sudo apt-get install xubuntu-desktop
```then logout and at the login screen choose **xfce4** or **xubuntu** depending on which package you installed.

---

### Post by kansasnoob on 2014-08-18
Is this the same failed upgrade you spoke of [here]("http://ubuntuforums.org/showthread.php?t=2239218&p=13096653#post13096653"), [here]("http://ubuntuforums.org/showthread.php?t=2239215"), and [here]("http://ubuntuforums.org/showthread.php?t=2239213")?

If so that's all the more reason to consider something lighter like Lubuntu or Xubuntu.

---

