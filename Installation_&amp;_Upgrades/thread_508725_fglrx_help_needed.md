---
title: "fglrx help needed"
date: 2007-07-24
forum: Installation &amp; Upgrades
---

### Post by jdoliner on 2007-07-24
I've run Ubuntu for a while now and I've tried a number of times to get the graphics drivers a bit more up to date but everytime it eventually backfires. Everytime I install fglrx I get these 6 lines in the bottom right corner like this:
|        |
|        |
|        |

and various things stop working the last time I did it I was immediately unable to, logon without crashing. I'm on a T60p laptop with a Mobility Firegl v5200 card. Which drivers will work here every attempt I make backfires

---

### Post by Circuit99 on 2007-07-26
I've setup ati cards best place to get drivers from here

[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)


Every time you install drivers, if  they fail you have to clean the system up. I tend to use the method from here

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

Other links for help

[http://ubuntuforums.org/showthread.php?p=423589](http://ubuntuforums.org/showthread.php?p=423589)

[http://ubuntuforums.org/showthread.php?t=32495&highlight=fglrx+kernal+module+version+does+-match+driver](http://ubuntuforums.org/showthread.php?t=32495&highlight=fglrx+kernal+module+version+does+-match+driver)

[http://ubuntuforums.org/showthread.php?t=24557](http://ubuntuforums.org/showthread.php?t=24557)

[http://linuxhelp.150m.com/ati/ati.htm](http://linuxhelp.150m.com/ati/ati.htm)


What has happened they become corrupted when I have updated the system. I think it is something  to do with updates related to graphics. Also I've seen there are known bugs within restricted drivers provided by ATI. I think my system problem is related to my sound card which is built into my motherboard.

What i like to do is open a terminal and use "fglrxinfo" to find confirm ATI drivers are setup. 

So far the latest ones are working, but I get problems with avi, divx and mpeg playback.

Try disabling your sound card from bois  or my have some other hardware problem or the video card drivers haven't developed enough. They don't produce .deb version for some reason or convert from installer.

---

