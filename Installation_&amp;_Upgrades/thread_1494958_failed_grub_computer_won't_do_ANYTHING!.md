---
title: "failed grub computer won't do ANYTHING!"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by puzzlebs on 2010-05-27
Hi guys I am a super newbie in linux. I have desktop with window installed on one hard drive and karmic installed into another. of course when i turned computer on grub was letting me choose which OS run. ok so now 2 days ago I upgraded to lucid lynx with the upgrade option (without using a cd) and at the end of installation I remember it told me there were a grub failure (sorry didn't write down what else said). Now it seems same as other case BUT in my case now computer in turning on stops at the starting screen (acer logo) and doesn't allow me to choose booting setup (f12) or doing anything so I have to turn it off with the main button. I tried to turn it on with the karmic live cd but nothing happens. I even tried to disconnect the hard drive where linux is installed but I guess the booting is still controlled by the failed grub. what I can do????
I read other thread like:
[http://ubuntuforums.org/showthread.php?t=1470685&page=2](http://ubuntuforums.org/showthread.php?t=1470685&page=2)
[http://ubuntuforums.org/showthread.php?t=1471798](http://ubuntuforums.org/showthread.php?t=1471798)
[http://ubuntuforums.org/showthread.php?t=1452718](http://ubuntuforums.org/showthread.php?t=1452718)
[http://ubuntuforums.org/showthread.php?t=1448840&page=1](http://ubuntuforums.org/showthread.php?t=1448840&page=1)
[http://ubuntuforums.org/showthread.php?t=1476927](http://ubuntuforums.org/showthread.php?t=1476927)

 but none of those look like mine. If even the recover cd works how to crack the problem and do actually something on the computer?
PLEASE HELP
Thanks
P.

---

### Post by darkod on 2010-05-27
If you can't even boot the ubuntu cd that has nothing to do with grub. Make sure cd-rom is before hdd in boot devices in BIOS and try again.

If you can boot into live mode you probably only need to reinstall (or install) grub2, depending what failed.

That's why a clean install of the new version is always better then relying on upgrade.

---

### Post by puzzlebs on 2010-05-28
the problem is that i cannot even get into the bios to change the booting setting...the computer doesn't do anything...

---

### Post by puzzlebs on 2010-06-03
ok guys somehow I managed to log in from cd (with the 10.04) and "tried without installing" then I restarted and grub appeared again so I could get into linux. It seems that now lucid linx is installed I even did some last updated. Now the problems are 2:

1) Since the update linux doesn't recognise the screen (LG 19" 82Hz freq) and get into "out of frequency" problem. I log in in recovery mode and low resolution I try to change the graphic preference but since it appears "unknown screen" I can't change the setting

 I read similar problem here [http://ubuntuforums.org/showthread.php?t=233481](http://ubuntuforums.org/showthread.php?t=233481) and I am tempted to do "sudo dpkg-reconfigure xserver-xorg" but since I have no idea what does it mean I would be careful and wait your suggestion

2) _IMPORTANT_ If i select to start windows (located in another HD) IT WON'T START!!! (just black screen with blinking cursor) I can see from ubuntu the HD and hence I transfered on external HD personal file but I would really really like to avoid to reinstall windows. Hence even if I know here is not the best place to speak about such OS anyone has any idea how to fix it. I checked the BIOS but doesn't look anything strange to me.

If there is any data/specification/info I have to post to help you to understand this don't hesitate to ask
Thank You in advance
Paolo

---

