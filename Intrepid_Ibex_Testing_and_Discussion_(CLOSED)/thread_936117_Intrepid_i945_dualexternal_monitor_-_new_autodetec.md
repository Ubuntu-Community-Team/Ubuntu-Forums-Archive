---
title: "Intrepid: i945 dual/external monitor - new autodetect"
date: 2008-10-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by penguin42 on 2008-10-02
Hi,
  I have a Tosh laptop (Equium A200) with an i945GM graphics chip in and am having problems with a new external monitor on Intrepid.

 1) The internal 1280x800 LCD works fine.
 2) I've added a Dell S2409W (1920x1080 - note the 1080!) VGA monitor external
 3) The most I've so far been able to get out of the Dell is 1280x768.

I don' think the [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
is uptodate for Intrepid (for example the gconf entry it references doesn't seem to be there for me); so some questions:

1) Where does GNOME store it's display res/dual monitor settings on Intrepid? What actually reads them?
2) Same for KDE - the KDE monitor settings dialog doesn't seem to make any changes at all for me.
3) The xorg.conf on Intrepid has a comment saying some things are automatically configured and some settings in the config file are ignored - which things are ignored? Is it documented anywhere?

The dual head xorg.conf that I tried a CRT with on Hardy complains of no devices found; so does anyone have an xorg.conf from Intrepid with an internal LCD+external display?

I'm happy with just having the external display as 1980x1080 - although I'd prefer to have both; but I'm worried about throwing in a v/h sync when I don't seem to be able to specify two monitors in the xorg.conf on Intrepid.

Both the GNOME and KDE dialogs see the monitor - but both show 'unknown';
the GNOME one is letting me set the res of the Dell to 1360x768, 1024x768 or lower - it's currently set to 1360x768 but the monitor says it is seeing 1280x768 - although xdpyinfo is saying 1360.

Is there anyway to get Intrepid to actually not do autodetect and let me do old style xorg.conf ?

Dave

---

### Post by penguin42 on 2008-10-02
Just a quick reply to say I've got the external monitor going with a hack but it's not totally happy:
  1) I'm using xrandr to set a mode 
xrandr --newmode "1920x1080" 138.407 1920 1984 2016 2096 1080 1082 1087 1111 +hsync -vsync
     and then I can pick it from the gnome dialog and get this display at full res (I found it here: 
[http://www.mythtv.org/wiki/index.php/Modeline_Database](http://www.mythtv.org/wiki/index.php/Modeline_Database))

  2) If I enable the internal LCD at the same time I see a corruption of a long horizontal line that appears to be a copy of the top of some windows droppings on different parts of both displays.

I've included my current X config - for thos efighting the same problem.

Dave

---

### Post by penguin42 on 2008-10-02
I now have both heads working and include here the X config file for anyone else who might hit this:

So this is an i945GM  (Tosh Equium A200) with internal 1280x800 display
   +          Dell S2409W external display (1920x1080)
with GL.
The trick to getting GL to work is that the chipset can't do more than 2048 accross with GL - so I stack the two displays vertically (as far as X knows) and so my virtual screen is only 1920 accross) - I'm not sure we could ever hope for an autodetect to find that!
Note: Make sure you don't let the GNOME tools rewrite your X config to adjust anything - they'll lose all the custom stuff.
(The corruption I saw doesn't seem to happen with them vertically stacked)

The only other problem I have is that when I login I get compiz on (I can't turn it off by default) and at that point I get a desktop displayed in only a small part of the display - until I turn compiz off.

Dave :-)#

Section "Device"
	Identifier	"dev0"
	Driver          "intel"
	Busid           "PCI:0:2:0"
	Option "monitor-LVDS" "moninternal"
	Option "monitor-VGA" "monexternal"
EndSection

Section "Monitor"
	Identifier	"moninternal"
	Option          "Position" "0 1080"
	Option          "PreferredMode"  "1280x800"
EndSection

Section "Monitor"
	Identifier	"monexternal"
	HorizSync       30-70
	Vertrefresh     30-70
	Option         "Position" "0 0"
        ModeLine       "1920x1080" 138.407 1920 1984 2016 2096 1080 1082 1087 11
11 +hsync -vsync
	Option         "PreferredMode"  "1920x1080"
EndSection

Section "Screen"
	Identifier	"scr0"
	Monitor		"mon0"
	Device		"dev0"
	SubSection "Display"
		Virtual	1920 1880
	EndSubSection
EndSection

---

