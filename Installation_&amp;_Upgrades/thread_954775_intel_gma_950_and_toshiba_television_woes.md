---
title: "intel gma 950 and toshiba television woes"
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by tdcrenshaw on 2008-10-21
i'm currently trying to set up a shuttle kpc k45 with an integrated intel gma 950 video card to a toshiba television with a resolution of 1368x768 (model number 23HLV86 if it helps). I'm using intrepid ibex beta, and connecting though an svga cable. 

Unfortunately, no matter what fixes i try, ubuntu starts in low graphics mode. I've attempted to just list the resolutions i want in my xorg.conf, swap my driver from i810 to intel, use the 915resolution hack (which has been obsoleted in intrepid), and several other things i can't recall.

if anyone has any suggestions they would be greatly appreciated.

oh, my xorg.conf is essentially blank as of now and the screen resolution app only reports 600x800 and 640x48

---

### Post by Etrruugo on 2008-10-21
bump then lurk as soon as possible&#12288;&#12288;Let us take a moment of the time just to pay tribute and show appreciation to the person called mom though some may not say it openly to their mother. There's no substitute for her. Cherish every single moment. Though at times she may not be the best of friends, may not agree to our thoughts, she is still your mother!!! She will be there for you...to listen to your woes, your braggings, your frustrations, etc. Ask yourself...have you put aside enough time for her, to listen to her &#8220;blues&#8221; of working in the kitchen, her tiredness? Be tactful, loving and still show her due respect though you may have a different view from hers. Once gone, only fond memories of the past and also regrets will be left.&#12288;&#12288;Don't take for granted the things closest to your heart. Love her more than you love yourself. Life is meaningless without her ...Thsale is a professional, loyal and reliable wow gold supplier online, we pioneered selling cheap wow gold. Welcome to thsale buy world of warcraft gold Buy Cheap WoW Gold, World of Warcraft Gold, Please look here! We are a Great MMORPG company. wow money and wow items,which is very cheap WOW Gold&#65281;All US Server 24.99$/1000G on sell! Cheap wow gold,rs powerleveling,wow power leveling,Buy Cheapest/Safe/Fast WoW US EU Gold Power leveling ---------------------------------------------------**  [Pet products](http://www.lovelonglong.com),     [dog bed](http://www.lovelonglong.com),   [pet supply](http://www.lovelonglong.com)    [wow power level](http://www.powerleveling-wow.com/siteMap.asp),     [WoW Power Leveling](http://www.powerleveling-wow.com),**

---

### Post by Thelasko on 2008-10-21
> **tdcrenshaw said:**
> Unfortunately, no matter what fixes i try, ubuntu starts in low graphics mode. I've attempted to just list the resolutions i want in my xorg.conf, swap my driver from i810 to intel, use the 915resolution hack (which has been obsoleted in intrepid), and several other things i can't recall.
Wow! 915resolution was obsolete *way* before Intrepid.  More like Gusty.  The Intel driver is definitely the one you want.  I recommend restarting the machine after switching back to the Intel driver.

Is the resolution you are looking for just not an option in system>preferences>screen resolution?  You should be able to add it in xorg.conf.

---

### Post by tdcrenshaw on 2008-10-21
would these be the two relevant sections?

> Section "Device"
  Identifier  "Card0"
  BoardName   "Intel GMA 950"
  VendorName  "Intel"   
  Driver      "Intel"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Toshiba"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1368x766"
        EndSubSection
EndSection

---

### Post by Thelasko on 2008-10-21
Heads up, it's been a while since I messed with xorg.conf and the last time I did it was in virtualbox.  I think your format is incorrect.

Under "screen" it should say something like
```
Modes		"1920x1200@60.00"    "1680x1050@60.00" "1440x900@60"	"1280x800@60"
```
(of course change the resolution on one of them)
And under "monitor" you may need
```
modeline "1680x1050@60"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -hsync +vsync

```
(once again, another example)

The only thing I'm sure about is the Intel driver.  The other ones are completely obsolete.  Unfortunately, they neutered "dpkg reconfigure xserver-xorg" so we are stuck editing xorg.conf by hand when the automatic method doesn't work.:(

---

### Post by tdcrenshaw on 2008-10-21
no luck so far:
exerpt from my log file

> Parse error on line 35 of section Screen in file etc/X11/xorg.conf
"Modes" is not a valid keyword in this section.
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal Server Error:
no screens found


---

