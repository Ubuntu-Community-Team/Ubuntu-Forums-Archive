---
title: "Graphics problem: stuck at 640x480"
date: 2012-01-11
forum: Installation &amp; Upgrades
---

### Post by Keith_Beef on 2012-01-11
I'm trying to set up a computer for work. I have no control over the hardware; I need to set up this to run Windows XP in a VM, and it has to be off the network, so any updates beyond what are on the installation CD need to be downloadable and then installable from a USB stick or CD.

The computer has the following graphics:
Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

The monitor is a NEC LCD 175M capable of 1280x1024

I've tried both 11.04 and 11.10 today, and neither give me anything but 640x480.

When I try the the Preferences - Display I cannot change the resolution, cannot detect a monitor...

I tried creating an xorg.conf file.

```
Section "Monitor"
        Identifier      "NEC 175M-BK"
        HorizSync       39-75
        VertRefresh     56-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "NEC 175M-BK"
        Device          "Configured Video Device"
        DefaultDepth    24
             SubSection      "Display"
                Viewport        0 0
                Depth           24
                Modes           "1280x1024"
             EndSubSection
EndSection
```

"Driver can't support depth 24"

Changed DefaultDepth and Depth to 16 and tried again.
X server started, but 640 x 480 resolution.

I looked in /var/log/Xorg.0.log and found a list of "Supported established timings" including
	1024x768@60Hz
	1024x768@70Hz
	1024x768@75Hz
	1280x1024@75Hz
Also, monitor was identified as NEC LCD175M and its serial number was correct...

I don't understand what's going on here; why the xorg log can identify the monitor, yet the GUI cannot...

any ideas?

K.

---

### Post by Buntumatic on 2012-01-11
Is the Intel driver loading, paste your Xorg.log in pastebin if you want us to look at it.

---

### Post by Keith_Beef on 2012-01-12
OK. This is my first time at using pastebin... I hope it works.

[Here ]("http://pastebin.com/X8669iYk")is the XOrg.0.log that was generated from my attempt at an xorg.conf file. That xorg.conf file looks like this:

```
Section "Monitor"
        Identifier      "NEC 175M-BK"
        HorizSync       39-75
        VertRefresh     56-75
EndSection

Section "Device"
	Identifier	"Card0"
	Driver		"intel"
	Option		"Shadow"	"true"
	Option		"DRI"		"false"
	Boardname	"Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)"
	BusID		"PCI:0.2.0"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "NEC 175M-BK"
        Device          "Card0"

        DefaultDepth    8
             SubSection      "Display"
                Viewport        0 0
                Depth           8
                Modes           "1280x1024"
             EndSubSection
EndSection
```

You'll notice I changed it a little from what I posted yesterday; I tried combining ideas from a couple of other threads, but got more or less the same bad results.

If I delete the xorg.conf file, and allow the system to boot and X to start in the 640x480 resolution, I get [this]("http://pastebin.com/fkvY1uYc").

---

### Post by Buntumatic on 2012-01-12
You tried to force intel to load and it didn't work. The funny thing is there is no reason to be seen why it fails.
As I suspected, you are running VESA generic driver right now, that's why only low res is available.
The only thing I can think of is for some reason KMS is not enabled, starting with intel-2.10 or so KMS is mandatory.

---

