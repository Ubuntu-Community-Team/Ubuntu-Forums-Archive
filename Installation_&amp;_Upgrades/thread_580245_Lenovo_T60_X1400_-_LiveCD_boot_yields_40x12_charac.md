---
title: "Lenovo T60 X1400 - LiveCD boot yields 40x12 character mode only"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by brunjes on 2007-10-18
I popped in the Gutsy Live CD (not beta) and tried to boot. It tries to start gdm and fails 6 times in a row. It then gives me a message which is hard to read with all of the graphical fragments on the screen:

The display server has been shut down about 6 times in the last 90 seconds. It is likely that something bad is going on. Waiting for 2 minutes before trying again on display :0

And it sits there forever. I pressed Ctrl-F1 and saw a 40x12 display (I can only see 40 chars across and 12 lines down, but the screen is really 80x24 and I cannot see what I type at the command prompt unless I press 12 returns.

I have no clue as to how to proceed. ATI support in Gutsy seems lacking in Gutsy if this is what I get. I can boot from 6.10 (yes, 6.10) just fine from LiveCD. But 7.04 and 7.10 have problems; with 7.10's problems being the worst yet.

I have not yet tried an alternate CD install (downloading that as I write this from my nVidia-based Gutsy system working like a dream).

Roy

---

### Post by blanktear on 2007-11-08
I'm having the exact same problem with the exact system.  Anybody have any pointer?

---

### Post by blanktear on 2007-11-08
[http://ubuntuforums.org/showthread.php?t=580522](http://ubuntuforums.org/showthread.php?t=580522)

It looks like they are having the same problem in this thread...

---

### Post by mikesname on 2008-01-18
I ran into this problem with my new 1650x1080 T60 - you can imagine how happy I was...

In case it'd useful to anyone (not least myself in the future!), here's how I got things working:

[LIST]
[*]Download Gutsy Alternate (non-live) install CD
[*]Install normally - this will result in the same gfx problems as the live CD
[/LIST]

Reboot in single user mode:
[LIST]
[*]At Grub prompt, highlight normal Ubuntu and press 'e' to edit
[*]Highlight the line starting with "kernel", and press 'e' to edit
[*]Append " single" to end of line
[*]Press 'b' to boot
[/LIST]

At root prompt type:
```
apt-get install xorg-driver-fglrx
``` (Note: you don't need 'sudo' in single user mode)

Edit the xorg.conf:

If you want, back up the non-working one:
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Then edit in Vim (or whatever):
```
vim /etc/X11/xorg.conf
```

(Quick note for non-vim users: press 'i' to enter insert mode and edit text as usual.  After you are done, exit insert modeby pressing ESC, and save and exit with ':wq' - that's colon-w-q for command-write-quit)

Change the 'Device' and 'Screen' sections to the following (taken from the awesome Thinkpad Wiki):
```

Section "Device"
       Identifier  "ATI Graphics Adapter 0"
       Driver      "fglrx"
       Option      "ForceMonitors" "lvds,crt1"
       Option      "Centermode" "off"
       Option      "VideoOverlay" "on"
       Option      "OpenGLOverlay" "off"
       Option      "OverlayOnCRTC2" "0"
       Option      "PseudoColorVisuals" "off"
       Option      "HSync2" "31-64"
       Option      "VRefresh2" "56-75"
       Option      "UseFastTLS" "off"
       Option      "Mode2" "1280x1024,1024x768,800x600,640x480"
       BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier 		"Default Screen"
	Device			"ATI Graphics Adapter 0"
	Monitor			"Generic Monitor"
	DefaultDepth	24
	SubSection 		"Display"
		Modes		"1650x1080" "1400x1050" "1280x768" "1024x768" "800x600"
	EndSubSection
EndSection

```

(Note:  I can't vouch for all the details since they're mostly over my head, but it seems to work on my machine.) 

Now reboot

This should get you a working Ubuntu desktop.  Install 200-odd MB of updates.  At this point, Compiz won't work, it'll just say "Destop effects could not be enabled".  To fix this, open a terminal and type:

```
sudo apt-get install xserver-xgl
```

Give it a reboot and if you're lucky desktop effects should be enabled

---

