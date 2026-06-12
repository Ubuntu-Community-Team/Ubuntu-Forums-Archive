---
title: "cant start graphics after install"
date: 2004-12-21
forum: Installation &amp; Upgrades
---

### Post by steve007 on 2004-12-21
Hi,

I have a problem after install that it says cant start X Server because its not setup properly, but i dont remember being given options to set it up.

I'm a complete novice I'm afraid

I'm installing on a Digital Prioris MX6200 (duel pentium pro 200).

Can anyone help please?

Edit:

During boot following things fail:

Input RC
Cant synthasize pci hotplug events

I have tried apt-get install gdm & apt-get --reinstall install gdm

still no luck! :(

---

### Post by wallijonn on 2004-12-22
Have you tried disabling USB in the BIOS to see how far it proceeds? What USB devices do you have connected? If it is a camera, mem stick, webcam, etc., disconnect them all.

---

### Post by Chokableu on 2004-12-23
Hello!
I managed to install Ubuntu 2 days ago and everything went well (internet connection, thunderbird mail ...). But here my pbs:

1)  On each boot, the OS displays a message about pnpbios fatal error, but it did not  hinder the OS from going on smoothly (until today); I tried the alternatives on my bios setup (Asus motherboard P4C800-E) under the USB section : let the bios or the OS configure the usb devices; but both choices were ineffectual.

2) When I started this evening, I got an X in the middle of a black screen. When i switch to terminal mode, and enter the command startx -- -bbp 24 , i get the message "Xserver error" (or sth like that).  I can't run  in graphics mode anymore

That's a pity. I was so happy to have been able to run Ununtu on 1st trial. 

Thanks for any help. 

PS: before the crash, my Nvidia config (Geforce FX 5700) was only available at 60 Hz if I chosed 1280x1024, but i could go higher at 1280x768.

---

### Post by randy on 2004-12-24
Before we can help  you with the X Server were going to need to know more about the hardware (Monitor specs, and Graphics Card specs)

---

### Post by bluelaser on 2004-12-24
I have had pretty much the same problem as the original poster. Tried just about everything.

Specs:
Athlon 1800+
GeForce 6600GT
1024mb pc2100

Mediocre 17" display...

The Ubuntu live disc gives me no problems.

---

### Post by nemin on 2004-12-25
[QUOTE=bluelaser]I have had pretty much the same problem as the original poster. Tried just about everything.

Specs:
Athlon 1800+
GeForce 6600GT
1024mb pc2100

Mediocre 17" display...

The Ubuntu live disc gives me no problems.[/QUOTE]
You could copy the X configuration file the LiveCD creates to a floppy or so and replace the config file of your normal installation with it. Hope that helps.

---

### Post by BrianGon on 2004-12-27
I got almost the exact same problem after installation. In my case it was different, I have an onboard i810 graphics chip and a nvidia geforce fx 5200. What happened was ubuntu somehow detected my intel chip and configuired X to use that as my display device and driver, even though it is disabled in my bios and the PCI card is in use as primary VGA adaptor. You can imagine i was left at a blank screen at startup. So, what I did was boot in recovery mode, then i had to use command line (ugh#-o)

cd /etc/X11 to change directory, then
nano XF86<tab> to get the rest of filename.

then i could edit the XF86 config file. I snooped around a bit then found the area under "device", changed the ID deleted the 'PCI bus 0:1:0' entry and changed the driver from 'i810' to 'nv'. btw "Cant synthasize pci hotplug events" fails for me to but has nothing to do with X not starting, becuz im typing this from gnome this moment. :D

---

### Post by steve007 on 2004-12-27
[QUOTE=randy]Before we can help  you with the X Server were going to need to know more about the hardware (Monitor specs, and Graphics Card specs)[/QUOTE]

Its very basic. Its a Digital Prioris MX6200 server made in 1997 (dual Pentium pro 200's should indicate how old it is!). The monitor is a Compaq V570 and the graphics is S3 Trio 32/64 PCI. 

I'm a complete beginner, what I was hoping was to ditch nasty MS in favour of Linux with a friendly interface and gradually learn how it works!

---

### Post by BrianGon on 2004-12-27
try rebooting in recovery mode, then try 
root$ xf86config
and follow the step by step instructions to set up X
what im thinking is, maybe installation detected some hardware wrong and manually setting it up might clear things.

---

### Post by billputer on 2005-01-09
I also have a 6600gt and by default I wasn't able to boot.  I changed the video card driver in the xfree86 config from "nv" to "vesa" and was able to boot x that way.  You can then install the Nvidia drivers later (i'm having a problem with that).

---

### Post by jbh on 2005-01-09
[QUOTE=bluelaser]I have had pretty much the same problem as the original poster. Tried just about everything.

Specs:
Athlon 1800+
GeForce 6600GT
1024mb pc2100

Mediocre 17" display...

The Ubuntu live disc gives me no problems.[/QUOTE]

after X fails.. (it did for me the first few times too after install)

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo nvidia-glx-config enable

then edit /etc/X11/XF86Config-4 (for the warty version)
or /etc/X11/xorg.conf (for hoary)

and change this:
```
Section "Device"
	Identifier	"NVIDIA Corporation GeForce 6800GT"
	Driver 		"nvidia"
	Option 		"RenderAccel" "true"
	Option 		"AllowGLXWithComposite" "True"
	Option 		"NoLogo" "1"
	Option 		"NvAgp" "3"
	BusID 		"PCI:1:0:0"
EndSection
```

Try playing around with the NvAgp option, set it to "1" to use the nvidia agp module, which I can't get to work, and x won't boot unless i have it set to "3" (which means use the AGPGART linux driver)

then enter  ```
sudo ln -s /usr/X11R6/lib/modules/extensions/libglx.{so,a}
```

startx. doesn't work, reboot. still doesn't work search for other threads on this forum of screwed up nvidia configs.


you know everything works if X boots and the command 'glxgears' at the prompt works. or 'cat /proc/driver/nvidia/agp/status'

---

