---
title: "Gutsy to Hardy Compiz and Video Issues with fglrx"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by hamidaddin on 2008-05-20
I have just upgraded last week from Gutsy to Hardy and had some problems related to fglrx and video.

I am using a Toshiba Satellite A100 with an ATI Mobility Radeon X1600. 

Compiz was not running and when I ran fglrxinfo or any related command (i.e. glxinfo, fgl_glxgears... etc) by any normal user I was getting a "Segmentation fault" error. Using sudo all these commands were working properly.

After some searching, I found the following solution:

sudo gedit /etc/ati/ati-fglrx.sh
comment all lines (put # at the beginning of all lines in the file)

I had another problem with running videos while running Compiz. 
I was getting the following error in Movie Player (totem) "The video output is in use by another application. Please close other video applications, or select another video output in the Multimedia Systems Selector." 
Mplayer was giving the following error: "Error opening/initialize the selected video_out (-vo) device". 

When running totem from command line I was getting this error: ```
** Message: Error: Could not initialise Xv output
xvimagesink.c(1333): gst_xvimagesink_get_xv_support (): /video-sink/bin0/xvimagesink0:
No port available
```


VLC and Real Player were working perfectly for the same video files. There was no flickering.

I found some suggestions to change the xorg.conf files and add the following lines in the Device section:

```
Option		"VideoOverlay"	"on"
Option		"OpenGLOverlay"	"off"
Option		"TexturedVideo"	"on"
```


This fixed the above errors but now all videos and some screen savers started flickering. So my current situation is either to take out the overlay lines from xorg.conf and use VLC for all my videos, or live with the flickering problem.

I am sure this can be fixed by adjusting the configuration of totem and Mplayer without adding anything to xorg.conf

Was someone able to resolve this?

This is how the device section in my xorg.conf file look like currently:

```
Section "Device"
	Identifier	"Configured Video Device"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	Option		"TexturedVideo"	"on"
	Option		"XaaNoOffscreenPixmaps"
        Option		"UseFastTLS"	"2"
        Option		"RenderAccel"	"true"
EndSection
```

---

### Post by peitschie on 2008-06-27
You will want to change your default video output module for totem and mplayer.  These need to be changed seperately.

To change totem, open a terminal and type in the following:
```
gstreamer-properties
```
In the video tab select the X Windows System (no Xv) and test that.  Test the other ones if you want and find one that works well for you.

To change the mplayer settings, simply open mplayer up with the following command
```
gmplayer
```
And right-click on the video window and go to preferences.  Change the Video output module (Video tab) to x11 or similar.  To make this change permenant, you may need to manually edit the ~/.mplayer/config AND the ~/.mplayer/gui.conf files.  Simply put in a line like the following (replacing any existing vo_driver = reference):
```
vo_driver = "x11"
```

Let me know if that fixes anything for you :)

---

### Post by xanatos451 on 2008-07-02
I don't know if that helped the original guy or not, but it certainly addressed my issues running fglrx with effects on. Thanks a ton bro! You rock!  :guitar:

---

### Post by hamidaddin on 2008-07-29
Thanks peitschie. This resolved my problem in both players. 

I managed to fix this as well in VLC:

Settings => Preferences => Video => Output modules => check Advanced options at the bottom of the window => select "X11 video output" from the drop down list

The change recreated an old issue in MPlayer. The videos in full screen mode do not stretch. They maintain the same size and get centered with black filling the rest of the screen.

Anyone got a solution?

---

### Post by peitschie on 2008-07-29
Possibly have a look at [http://ubuntuforums.org/showpost.php?p=146359&postcount=2](http://ubuntuforums.org/showpost.php?p=146359&postcount=2) .  This seems to be a limitation of the x11 output driver with mplayer, i.e., it won't automatically scale or resize.

---

### Post by hamidaddin on 2008-08-05
```
gmplayer -zoom
```
worked for me...

Thanks again!

---

