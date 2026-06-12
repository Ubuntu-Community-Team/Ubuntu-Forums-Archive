---
title: "Login screen enormous fonts"
date: 2009-08-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dawynn on 2009-08-19
Just upgraded my laptop up to Karmic.  I'm able to login, but there's a huge problem.

And when I say huge -- I mean the fonts.  The font that the login screen is using is just enormous -- to the point of being unusable.  The letters are so large, each one stretches for the height of about 1/3 of the screen.

When I try to choose the maintenance mode in grub, there is no option for resetting X or anything like that.  And I don't know the root password for my system (is there a root password on Ubuntu-based systems?)  so dropping to a root shell does not help at all.

After I login on via gdm (it does let me type name and password -- I just can't really see what I'm doing because all of the hint text is so large), my session looks normal -- the fonts are fine.

I've tried the gdmsetup tool.  It brings up a nice little screen that looks like I could do something.  But when I choose unlock, absolutely nothing happens.

Any idea how I can get rid of the enormous fonts in gdm?

---

### Post by dawynn on 2009-08-20
Trying a few different tactics.  

My system is now a karmic xubuntu / mint helena mix (as much as packages will allow).

Since gdm is having issues (bug #414140), I'm trying some of the other options.
xdm -- same issue with enormous fonts as gdm.
wdm -- login screen was simplistic, but very usable.  Did not have problems on the login screen.  However, the transition to the next screen was not so nice looking.  The splash screens that come up between login and the desktop showed enormous fonts.
kdm -- Screen was somewhat usable.  At least I could see where I needed to type everything.  But, typing of user name and password were again using gigantic fonts.

So, something is not being auto-detected correctly in the karmic login screen.  I'm using a compaq presario c300, if it helps.

Just a few tidbits gleaned from Device Manager
CPU: Genuine Intel T1350 @ 1.86Ghz
Display controller: Mobile 945 GM/GMS/GME  943/940 GML  Express Integrated Graphics Controller


Related question: how can I view update kdm settings from inside xfce?

---

### Post by stdPikachu on 2009-08-20
I've been having the same problem with my HP nx7400, also using an Intel GM945, and all t'other bug reports I've seen abiout huge fonts have revolved around 945's as well.

Here's an image of what my screen looks like on login when I click the plasma config bean thingy:
[http://launchpadlibrarian.net/30249331/karmic_corruption.jpg](http://launchpadlibrarian.net/30249331/karmic_corruption.jpg)

Thought it might be an LCD quirk, but the same hardware has worked perfectly fine with 8.04 up until now. EDID info looks fine - correct display size and resolution, correct DPI of 96...
```
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: LPL  Model: 1676  Serial#: 0
(II) intel(0): Year: 2005  Week: 0
(II) intel(0): EDID Version: 1.2
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.590 redY: 0.344   greenX: 0.323 greenY: 0.534
(II) intel(0): blueX: 0.156 blueY: 0.138   whiteX: 0.312 whiteY: 0.328
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 71.2 MHz   Image Size:  289 x 21 mm
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) intel(0): v_active: 800  v_sync: 802  v_sync_end 808 v_blanking: 823 v_border: 0
(II) intel(0):  LGPhilipsLCD
(II) intel(0):  LP154W01-TLA8
(II) intel(0): EDID (in hex):
(II) intel(0):  00ffffffffffff00320c761600000000
(II) intel(0):  000f0102802115780a0f109758528828
(II) intel(0):  23505400000001010101010101010101
(II) intel(0):  010101010101d51b00a0502017303020
(II) intel(0):  26002115100000190000000000000000
(II) intel(0):  00000000000000000000000000fe004c
(II) intel(0):  475068696c6970734c43440a000000fe
(II) intel(0):  004c503135345730312d544c41380076
(II) intel(0): EDID vendor "LPL", prod id 5750
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   71.25  1280 1328 1360 1440  800 802 808 823 -hsync -vsync (49.5 kHz)

...

(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x60.1   71.25  1280 1328 1360 1440  800 802 808 823 (49.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output TV1
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output LVDS1 connected
(II) intel(0): Output TV1 disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS1 using initial mode 1280x800
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)

```

Any help on a workaround very much appreciated so I can continue investigating the screen corruption issue...!


Edit:

Just noticed there's a line that says "image size 289 x 21mm" which is not the display size... is it the image size or max image size param I should be paying attention to?

---

### Post by stdPikachu on 2009-08-20
I've managed to find a way to work around the issue in KDE by forcing fonts to 96dpi;

On a per-user basis, create a ~/.kde/share/config/kcmfonts file containing the following:
```
[General]
forceFontDPI=96
```
Miraculously enough that also fixed my screen corruption issues. Going to do some more tinkering and then file back to the bug reports.

'fraid I don't know how to enable it globally yet, not to do the same thing in GNOME or other DE's.

---

### Post by martijntje on 2009-08-20
Have you tried setting 

DisplaySize 328 246

under monitor in your xorg.conf?

---

### Post by stdPikachu on 2009-08-21
Karmic doesn't ship with a xorg.conf, which was an irritation in itself seeing as the intel gfx card eats 256MB by itself when left unconfigured; anyone know how to configure the amount of video ram it uses without specifying in xorg.conf? And I still can't figure out how to reconfigure ctrl-alt-backspace to work...

Anyway, back on topic. Does anyone know where a global kcmfonts file does/should live?

---

### Post by martijntje on 2009-08-21
You can still use a xorg.conf. Just run Xorg -configure, edit the file and save it as /etc/X11/xorg.conf

---

### Post by dawynn on 2009-08-22
I have set the following in my xorg.conf (which was there, possibly a remnant, since my system is an upgrade):

Section "Monitor"
	Identifier	"Configured Monitor"
	DisplaySize	331	207
EndSection

(I looked up both "man xorg.conf" and the specs on a Compaq Presario C300. Specs say 33.1 cm width and 20.7 cm height.)

Even after restarting, this didn't seem to help.

I'm attaching my xorg.conf, because I can't say that I fully understand it.  It claims to recognize what I asked for:
(II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(**) intel(0): Display dimensions: (331, 207) mm
(**) intel(0): DPI set to (98, 98)

But then later gives conflicting messages, like this:
(II) intel(0): Setting screen physical size to 289 x 21

I'm also seeing messages like this in my /var/log/syslog:
gdmsetup[3832]: Gtk-WARNING: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

gdmgreeter[3965]: Gtk-CRITICAL: gtk_tree_view_get_selection: assertion `GTK_IS_TREE_VIEW (tree_view)' failed
gdmgreeter[3965]: Gtk-CRITICAL: gtk_tree_selection_unselect_all: assertion `GTK_IS_TREE_SELECTION (selection)' failed
gdmgreeter[3965]: Gtk-CRITICAL: gtk_tree_selection_select_iter: assertion `GTK_IS_TREE_SELECTION (selection)' failed
gdmgreeter[3965]: Gtk-CRITICAL: gtk_tree_view_scroll_to_cell: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

gdmgreeter[4004]: Gtk-CRITICAL: gtk_tree_view_get_selection: assertion `GTK_IS_TREE_VIEW (tree_view)' failed
gdmgreeter[4004]: Gtk-CRITICAL: gtk_tree_selection_unselect_all: assertion `GTK_IS_TREE_SELECTION (selection)' failed
gdmgreeter[4004]: Gtk-CRITICAL: gtk_tree_selection_select_iter: assertion `GTK_IS_TREE_SELECTION (selection)' failed
gdmgreeter[4004]: Gtk-CRITICAL: gtk_tree_view_scroll_to_cell: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

gdm[11108]: WARNING: gdm_slave_greeter: Cannot start greeter with gtk modules: gail:atk-bridge:/usr/lib/gtk-2.0/modules/libkeymouselistener:/usr/lib/gtk-2.0/modules/libdwellmouselistener. Trying without modules
gdm[11108]: WARNING: gdm_slave_greeter: Cannot start greeter trying default: /usr/lib/gdm/gdmlogin
gdm[11109]: atk-bridge-WARNING: AT_SPI_REGISTRY was not started at session startup.
gdm[11109]: atk-bridge-WARNING: IOR not set.
gdm[11109]: atk-bridge-WARNING: Could not locate registry
gdm[11109]: Gtk-WARNING: Ignoring the separator setting

gdm-simple-greeter[3484]: DEBUG(+): GdmChooserWidget: no rows selected
gdm-simple-greeter[3484]: DEBUG(+): GdmChooserWidget: selection cleared
gdm-simple-greeter[3484]: DEBUG(+): GdmChooserWidget: grabbing focus
gdm-simple-greeter[3484]: DEBUG(+): GdmChooserWidget: not grabbing focus - not realized
gdm-simple-greeter[3484]: DEBUG(+): GdmUserChooserWidget: font height 157; using icon size 128

---

### Post by dawynn on 2009-08-23
In case anyone else has screen font issues -- either too large or too small, please review the following:

Bug 151311 - [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/151311](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/151311)

[https://wiki.ubuntu.com/X/Troubleshooting/HugeFonts](https://wiki.ubuntu.com/X/Troubleshooting/HugeFonts)

It appears that this is a problem stemming from certain hardware.  Most specifically, it appears to attack a large number of intel screens, and some ati screens.  Effectively -- your screen is misreporting its size.  This plagued Gutsy, Hardy, and even crept into Intrepid.  It was supposedly fixed in Jaunty (my Jaunty install did not have issues), but has evidently crept back into Karmic (at least on upgrade from Jaunty, in my experience).

---

### Post by dawynn on 2009-08-24
I got the following to work.  Note that this solution is indicated a number of times in 151311...

First check xrandr.  You should get output something like this:
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 289mm x 21mm
   1280x800 60.1*+ 60.0
   1280x768 60.0
   1024x768 60.0
   800x600 60.3
   640x480 59.9
TV disconnected (normal left inverted right x axis y axis)

Notice the 289mm x 21mm?  I'm guessing your screen is not 21mm tall, but it might be around 21cm.  For me, the indicated width was not exactly right either.  If you have the manual for your notebook / monitor, or if you can find the manual online, check what the manufacturer indicates is the true width and height of your monitor display screen.  Or you could get out a ruler...

Then you'll need to make a couple changes to xorg.conf.  So, load up xorg.conf into a text editor with root privileges.  This command should work for many:

sudo gedit /etc/X11/xorg.conf

and make the following changes:

Section "Device"
    { Add the following option to what's already here: }
    Option "monitor-LVDS" "DCLCD"
EndSection

Section "Monitor"
    Identifier "DCLCD"           <-- must match 2nd part of option in Device setion
    { Add the following to what's already here: }
    DisplaySize 433 271          <-- width, height in millimeters. Adjust for your monitor
EndSection

If your computer is anything like mine, just adding these two lines was sufficient.  Restart Xorg, or just reboot, and you should be in business.  Just remember that you have now hardcoded the size of your monitor into your xorg.conf.  This shouldn't be a concern for notebook users.  But desktop users will need to make adjustments if they switch to a different monitor.

As of Jaunty, such tweaks were no longer supposed to be needed.  Feel free to submit a bug specific to yor system, if you would like to see a distribution-wide fix.  See the huge fonts troubleshooting document listed above for help guides for how to file a proper bug.

---

