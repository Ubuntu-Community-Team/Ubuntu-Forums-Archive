---
title: "Dell M1330 - Ubuntu not even starting"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by AndrewZorn on 2008-01-24
I've used the same 7.10 disc on another laptop fine, but it just isn't working right with my brand new M1330.

I went into Vista and did the partition shrink thing (couldn't get the UBCD partition dealie to work right, whatever) and when I put in the Ubuntu disc and do "Start or install..." I get a couple minutes of black, then the prompt to run in low graphics mode.  At a screen with white text on black background where you normally get the [ OK ] several times on the right, I'm getting the same message repeated **over and over again**:

*seemingly**random**numbers* bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

I know this has something to do with the wireless card, right?  CAN WE JUST SKIP THIS and move on?  I don't want to use the Ubuntu Live CD fully, I just want to get Ubuntu installed and sort the rest out later.

And every post on every website I've come across, people are having grand luck with the M1330...

---

### Post by Rocket2DMn on 2008-01-24
Since you don't want to fiddle with the LiveCD, you can get the alternate install cd from Ubuntu's website.  Just check the box at the bottom for alternate cd and you can download it.  It is just a text-based installer without a live session, and it works very well.
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by AndrewZorn on 2008-01-24
I was scared of the text-based installer.  I just don't get why it gets hung over on the wireless card.

Which I tried disabling the wireless and bluetooth in bios, it just gets stuck after
* Running local boot scripts (/etc/rc.local)   [ OK ]
with a blinking underscore.

I redownloaded and reburned the disc.  Did nothing.

I'm getting the alternate now, but again, it's so strange... I can't even find a problem thread for installing Ubuntu on this computer, everyone seems to think it's really easy.  Why would my case be different?  SAME brand-new hardware and fresh disc.

---

### Post by Rocket2DMn on 2008-01-24
Could be that your hardware is so new it doesn't have complete support out of the box yet.  If your wireless card doesn't work after you install, that can be troubleshooted on these forums, though you should start a new thread for it if that happens to be the case.  However, I don't anticipate it being an issue.

Don't be afraid of the text based installer, although I've never used it, it seems even the more clueless users can figure it out without any problems.  I've suggested it dozens of times and nobody has ever complained about it.

---

### Post by AndrewZorn on 2008-01-25
Alternative worked!

I used this [http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/) to try to get my wireless working, but now I lost my wireless card completely... I guess the BCM94311MC**A**G is different enough...

---

### Post by Rocket2DMn on 2008-01-25
You may want to check out [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) and [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper))
If you can't get your card to work, you should start a new thread about getting wireless to work.  Include your wireless card make/model and anything you've tried.
Good luck, and welcome to Ubuntu!

---

