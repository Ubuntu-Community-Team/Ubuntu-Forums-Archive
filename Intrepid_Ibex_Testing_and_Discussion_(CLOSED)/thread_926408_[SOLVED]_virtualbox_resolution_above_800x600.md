---
title: "[SOLVED] virtualbox resolution above 800x600"
date: 2008-09-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by zorkerz on 2008-09-21
Im running intrepid ibex as a virtual machine with virtualbox. I can only do 640x480 or 800x600. My max resolution is 1024x768 and I would like to use it so I can make virtualbox full screen.

This is a thinkpad x61 with intel x3100 graphics card.

I searched and was surprised not to find anything...
thanks

---

### Post by tuxxy on 2008-09-21
Have you installed **guest additions** in your virtualbox

---

### Post by dkasak on 2008-09-21
Are you using generic ( maybe vesa or vga or something ) video drivers in the guest? You might have to install virtual-box drivers ( ie something like xf86-video-virtualbox ) to get higher resolutions and better performance.

---

### Post by zorkerz on 2008-09-21
I did not have guest additions installed. I installed it and still cannot get larger than 800x600.

How do I check what drivers I'm  using?
Do I install the drivers in the guest?

---

### Post by FuturePilot on 2008-09-22
The last few versions of VirtualBox have been able to automatically resize the resolution even if you can't specifically specify a particular resolution. If you just put it into Full Screen Mode it should automatically change the resolution to fit your screen.

---

### Post by Peter76 on 2008-09-22
I had this problem myself... Turned out that the Guest Additions don't put the right driver in  xorg.conf ( or X loads the wrong driver... ) To solve you have to add the following line in the "Device" section of your xorg.conf:

<code>Driver    "vboxvideo"</code>

Also set "UseFBDev" to false. Restart X and dynamic resizing works.

Good luck

---

### Post by zorkerz on 2008-09-22
My screen does not automatically resize when I put it to full screen mode.

Im not sure what to do with xorg.conf in intrepid. My understanding is that they are trying to not need this file at all[SIZE=2] [SIZE=1]for most installations. My xorg.conf is greatly diminished from the one in 8.04. However adding 'driver "vboxvideo"' does allow the screen to resize.


[/SIZE][/SIZE]Just for curiosities sake here is the entire uncommented part of my xorg.conf in intrepid without the 'driver "vboxvideo"'. Does anyone know if there are any new down sides to  editing xorg.conf in intrepid? Im thinking mostly in terms of testing I guess.


&#65279;> [SIZE=1]Section "Device"
        Identifier      "Configured Video Device"[/SIZE]Possible Quick-fix for "No support for .ani cursors"
[SIZE=1]EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection[/SIZE]

Thanks alot for the ideas.

---

### Post by billstei on 2008-09-22
I've been trying to get this Intrepid screen res limitation in virtualbox resolved for quite a while, and adding the stuff into /etc/X11/xorg.conf per Peter76 has solved it:

In the Device section:

Driver "vboxvideo"
Option "UseFBDev" "false"

and in the Screen section:

SubSection "Display"
        Depth 24
        Modes "1440x900"
EndSubSection

Of course you should pick whatever res mode is appropriate for your monitor, and/or use virtualbox seamless mode to make the jump to hyperspace.

Bill

---

### Post by zorkerz on 2008-09-22
I should have said that I added only one line to the device section of my xorg.conf file.

'Driver "vboxvideo"'

I did not need to add 'Option "UseFBDev" "false"' or specify a resolution in the display section. My resolution defaults to 800x600 but it resizes as I change the window size.

---

### Post by deejross on 2008-09-23
I should mention that I have reopened a ticket with VirtualBox about this issue: [VirtualBox Bugtracker]("http://www.virtualbox.org/ticket/1591#comment:7")

---

### Post by billstei on 2008-09-23
I can now confirm that zorkerz comment above is true for me as well, I now have only the line:

Driver "vboxvideo"

however IIRC I was not able to get to 1440x900 mode initially without using the Modes line, but now that I am at that res, it remains.

Does anyone know where in the home directory the screen resolution preference as selected via the System->Preferences->Screen Resolution program gnome-display-properties is stored ?

Bill

---

### Post by deejross on 2008-09-23
billstei, I don't think that is stored anywhere except the /etc/X11/xorg.conf file. I could be wrong though.

---

### Post by billstei on 2008-09-23
On my Hardy system I have the resolution set to 1920x1200 via gnome-display-properties, but the /etc/X11/xorg.conf file does not contain any references to that res (or any other res for that matter).  Also I can do a Switch User to a different user account and set the screen res uniquely in that account without losing the res in the first account.  This setting is (probably) in the home user directory somewhere.

Bill

---

### Post by deejross on 2008-09-23
If it is user-specific, then maybe it is in the gconf-editor...I'm looking in there now.

---

### Post by billstei on 2008-09-23
I can't find it in gconf-editor ... 

I'm not sure but I think that gnome-display-properties uses xrandr to make the screen res change so it might be a question of where xrandr stores default (or last-used) settings.

As proof that the setting is in the user home directory... I had an account that got a res set that did not agree with a certain monitor, and the way I "fixed" it was to delete the entire user account and user home directory, and then (re)create the user account.  It would be nice to be able to be a bit more surgical next time :)

Bill

---

### Post by billstei on 2008-09-23
Okay I found it here:

~/.gnome2/monitors.xml

however, (apparently) this file only exists if the screen res is changed to something other than the default.

Bill

---

### Post by deejross on 2008-09-23
This is actually a good thing to know since they are basically deprecating the entire xorg.conf file in favor of automatic tools for X. Which is a good thing until the automatic part breaks, then you gotta do it manually (like now)  :)

---

### Post by zorkerz on 2008-09-23
Yes, I dont really understand how it all works. 

In the short term though now that I have specified the video driver (vboxvideo) I will not be able to test how the automated x tools are working in ubuntu. I don't actually know how well i can test them anyways while using a virtual machine.

In the long run though It will make the xorg.conf file much simpler for people who need to edit it. All of the lines and sections I know can be overwhelming and scary for somebody who does not understand it all and just wants something to work.

---

### Post by m.musashi on 2008-10-27
> **zorkerz said:**
> I should have said that I added only one line to the device section of my xorg.conf file.

'Driver "vboxvideo"'

I did not need to add 'Option "UseFBDev" "false"' or specify a resolution in the display section. My resolution defaults to 800x600 but it resizes as I change the window size.

Thanks for this info. It looks to be exactly what I was looking for. However, when I try this it breaks X. I am using Intrepid so maybe that has something to do with it.

In any case, I get an error about driver missing. Is there something else I need to install or is this probably more an Intrepid issue?

Thanks.

---

### Post by Rhubarb on 2008-10-27
I'm running Intrepid in vbox 2.0.2 (not O.S.E.), with thanks to zorkerz, I can resize Intrepid's window dynamically now.
Here is my /etc/X11/xorg.conf for intrepid that works nicely (guest additions must be installed, or re-installed after a kernel update):

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"vboxmouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vboxvideo"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Montitor	"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection
```

---

### Post by b0b138 on 2008-10-27
I believe this has been fixed with the newest vbox update, 2.0.4

---

