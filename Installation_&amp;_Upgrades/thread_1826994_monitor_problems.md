---
title: "monitor problems"
date: 2011-08-17
forum: Installation &amp; Upgrades
---

### Post by chrispap on 2011-08-17
Hi everyone,
I just installed the latest version of Ubuntu on an external disk(500gb) giving 12gb to Ubuntu.
After the installation process finished I did reboot.When BIOS loaded instead of the Ubuntu boot screen a message from the monitor presented like this:
_information_
out of range
93.0kHz/58Hz
So I suppose that there must be a monitor problem or something.
I would appreciate any kind of help.
Thank's

---

### Post by Grenage on 2011-08-17
Ubuntu is putting out a mode that the screen can't handle; I've never had to deal with that, but I'll have a crack.  It probably won't help, but swap out the monitor cable if you have one spare.

Failing the above, we can try manually configuring xorg.conf, to specify your monitor's capabilities.  Post the make and model of your graphics card and monitor, and we'll take it from there.

---

### Post by Bobhuber on 2011-08-17
> **chrispap said:**
> Hi everyone,
I just installed the latest version of Ubuntu on an external disk(500gb) giving 12gb to Ubuntu.
After the installation process finished I did reboot.When BIOS loaded instead of the Ubuntu boot screen a message from the monitor presented like this:
_information_
out of range
93.0kHz/58Hz
So I suppose that there must be a monitor problem or something.
I would appreciate any kind of help.
Thank's
It wont help to try and configure xorg.conf as its not getting that far. Thats a hardware problem during boot either caused by a bad cable, inline adaptor , external splitter  or the video card itself (if you have added one other than the onboard video) 
You need to post your computer setup or use the above info to find your problem.

---

### Post by chrispap on 2011-08-18
My graphics card is nvidia G73 Geforce 7600GT, my monitor is 17" Sony SDM-S73/H TC003, my motherboard is Albatron Socket 478 Mainboard PX848PV Series and my cpu is Intel Pentium 4 2.60GHz.I also have 1.50Gb ram.

---

### Post by Grenage on 2011-08-18
> **chrispap said:**
> My graphics card is nvidia G73 Geforce 7600GT, my monitor is 17" Sony SDM-S73/H TC003, my motherboard is Albatron Socket 478 Mainboard PX848PV Series and my cpu is Intel Pentium 4 2.60GHz.I also have 1.50Gb ram.

I assume that you had graphics during the install, or another OS - so I'm going to work on the basis that it is a config problem (not your doing).

Boot with the live/install CD, and when you get to the desktop, access your drive using nautilus, or whatever the file manager currently is.  Locate this file, if it exists:

```
/etc/X11/xorg.conf
```

If it does not exist, simply open gedit and add the config below; save it using the name and path above.

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "Sony"
	ModelName "SDM-S73"
	HorizSync 28 - 80
	VertRefresh 48 - 75
EndSection

Section "Device"
	Identifier "Device0"
	Driver "nouveau"
	VendorName "Geforce 7600GT"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	SubSection "Display"
		Depth 24
		Modes "1280x1024"
	EndSubSection
EndSection
```

If the above does not work, use this:

```
/etc/X11/xorg.conf
```

If it does not exist, simply open gedit and add the config below; save it using the name and path above.

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "Sony"
	ModelName "SDM-S73"
	HorizSync 28 - 80
	VertRefresh 48 - 75
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"
	Driver "nouveau"
	VendorName "Geforce 7600GT"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	SubSection "Display"
		Depth 24
		Modes "1280x1024"
	EndSubSection
EndSection
```

I've referenced the open nvidia driver, but once you're up and running, you can always use the proprietary driver (hardware acceleration).

---

### Post by chrispap on 2011-08-18
I went to that location and the file xorg.config does not exist so I opened gedit and tried to create it, but I cannot save it there because I don't have the permission.

---

### Post by Grenage on 2011-08-18
My mistake; I wasn't sure if it would have a permission issue with the live CD.  You can use this from a terminal:

```
sudo gedit
```

That will open gedit with root rights.  Make sure it's /etc/X11/ on your computer drive, and not /etc/X11/ on the liveCD, or it won't help. ;)

---

### Post by chrispap on 2011-08-18
Unfortunately, there was no success at all. The xorg.config file didn't exist but even after I created it the problem remains the same. I wonder if you wanted a video of my computer booting to see the problem yourself. Is there any possibility to be a grub problem, because after my bios boot from the disk containing Ubuntu there is nothing at all showing up but that black screen with the monitor message into.
Thanks for your help,
Chris

---

### Post by Grenage on 2011-08-19
Hi Chris, sorry about the slow reply;  My home PC decided to die, and I ended up 'fixing' it with a claw hammer.

After the BIOS, you should be able to view the grup menu by holding down shift; does grub get displayed, or is the screen still blank there?  Did you try adding the modeline?

---

### Post by chrispap on 2011-08-19
Here is a video of my computer booting:
[http://www.youtube.com/watch?v=uJQYpkEeqrU]("http://www.youtube.com/watch?v=uJQYpkEeqrU")
As you can see there is no grub menu or anything at all after the bios load, but only that black sreen with the monitor's message into. When this happens the computer does not respond to anything, but to reboot from the button on the case.

---

### Post by dino99 on 2011-08-19
to get the grub menu (hidden by default on single OS system): at bios end process hold "shift" key down

then select the second line: recovery mode, then netboot

run:
sudo rm /etc/X11/xorg.conf
sudo nvidia-xconfig -s

then reboot

[http://linux.die.net/man/1/nvidia-xconfig](http://linux.die.net/man/1/nvidia-xconfig)

---

### Post by realzippy on 2011-08-19
After watching your video I think this issue has nothing to do with xorg.conf...sorry.

I would suggest to set a vga boot option,as described here:

[http://ubuntuforums.org/showpost.php?p=1938284&postcount=2](http://ubuntuforums.org/showpost.php?p=1938284&postcount=2)

would start with vga=771.....
"interrupt GRUB" means pressing "e"

---

### Post by Grenage on 2011-08-19
It does seem less likely, I agree.  What I find curious, is that if the resolution problem was for grub alone, wouldn't the display kick in later on?

I've never had a grub resolution problem, so this is mere speculation.

---

### Post by chrispap on 2011-08-20
I discovered that if I press enter when I am on the black  screen, after some time I get a message that tells me that my hardware does not support Unity and then Ubuntu environment shows up. After that I get a message which tells me that I have to install a nvidia driver to have Unity working properly, but when I am trying to install that driver or just install a program, I always get a message to give an authorization code which I don't know. How can I find it? Have I declared it during the installation process?

---

### Post by realzippy on 2011-08-20
Yes,you have been asked for a password when installing.And confirmed it typing it twice...

---

### Post by chrispap on 2011-08-20
Finally, I fixed it!:D 
I installed all the drivers and the updates available and then I changed the resolution and the color bits with startup manager.
I would like to thank you all so much for your help,
chrispap

---

### Post by realzippy on 2011-08-20
Fine.
So you might set thread as solved ? (ThreadTools)
Have fun..

---

