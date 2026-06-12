---
title: "1600x1200 screen resolution only"
date: 2011-02-12
forum: Installation &amp; Upgrades
---

### Post by TeamTP on 2011-02-12
Hey all,

This is a follow up thread in part, as I've tried to install both Xubuntu and Ubuntu onto an old Gateway laptop.

In both cases, installation has been fine except that the Screen Resolution has  defaulted to 1600x1200 0hz. The native res is 1280 x 768 60hz. It's  weird in that the icons and text look fine, but of course the bottom and  right of the screen are not visible.

BUT: if I use APPLICATIONS>SETTINGS>DISPLAY to select 1280 x 768  the screen goes nuts with a million horizontal lines (out of scan I  assume). Fortunately Ubuntu allows you to reset back to 1600x1200 where Xubuntu didn't. I've tried all posible resolutions and all are out of scan.

xrandr shows current default connected as 1600x1200+0+0 0mm x 0mm
it also shows that the machine could handle 1280 x 768 with the 60 hz.

I've used system update and everything is up to date. Additional drivers is also up to date (only a modem was of issue there).

I'm stuck now as both *buntus share this issue and I have no idea what to try next.

Any help would be GREATLY appreciated!

---

### Post by TeamTP on 2011-02-13
SOLVED!!! FINALLY!!!

It's a combo of solutions:

[http://ubuntuforums.org/showthread.php?t=1127987](http://ubuntuforums.org/showthread.php?t=1127987)

Copy paste his xorg.conf (mine was blank).
I also added an additional line of code to the: 

   SubSection "Display"
   Depth	24
   Virtual	[COLOR=Blue]**1280	 768**[/COLOR]

This made it work in Xubuntu which I had re-re-installed. Stupid S3 UniChrome Graphics!

Hope this thread helps others.

---

