---
title: "8600 GT and Nvidia driver problem"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by nasevz on 2008-05-05
After I upgraded from Gutsy to Hardy, I can't use nvidia's driver. 
If I enable it, the last thing I can see is "login:" in the console screen. System is trying three times to open the graphic login screen (three times blank screen) and after that, I get low graphics mode with Vesa driver. If I choose to continue in that mode, the screen goes blank and I can't see anything. 
After reset, in recovery mode if I choose to fix xorg and continue normal boot, the nvidia driver is disabled.

Please help.

---

### Post by chewearn on 2008-05-05
Do you do a dist-upgrade, or fresh hardy install?

If dist-upgrade, try purging all nvidia drivers.  Let it come back as vesa, or nv.  Then, enable nvidia restricted driver thru
System > Administration > Hardware Drivers

---

### Post by nasevz on 2008-05-05
> **AstalaVista said:**
> Do you do a dist-upgrade, or fresh hardy install?

If dist-upgrade, try purging all nvidia drivers.  Let it come back as vesa, or nv.  Then, enable nvidia restricted driver thru
System > Administration > Hardware Drivers

I upgraded from Gutsy and I already tried to uninstall/ reinstall but the result is same. I even uninstalled linux-restricted-modules.
Is there a way to track what is happening? Where is the boot process logged? I can't see anything since the screen is blank when it should turn in graphics mode.

---

### Post by darc on 2008-05-06
I'm having the same issue with the same card (8600GT).

I did the fix in recovery mode to get a workable display, however, this does not use the proprietary driver (as you mentioned, and I need it) and since I'm using dual displays this just mirrors the image on both (need TwinView).

I've tried installing the driver with Envy, but no go (get the low graphics mode).

I also tried installing it manually from the nVIDIA supplied binary, no joy there either (same problem).

"Hardware Drivers" program shows no proprietary drivers (all empty) even after I've supposedly just installed them.

Note that I did a dist-upgrade from Gutsy, and I've purged all the old nVIDIA drivers (at least, I think I got em all).

I'm trying this guide now:
[http://ubuntuforums.org/showthread.php?t=596875](http://ubuntuforums.org/showthread.php?t=596875)

And, I'll let you know how it goes.

You have any luck nasevz?
-darc

Update : This is going to be awhile, the ubuntu servers are getting hit pretty hard with every one updating so downloading the kernel sources is taking forever (2kbps)

---

### Post by darc on 2008-05-06
Update:
I just checked the "Hardware Drivers" program again (jockey-gtk is the program name I believe) and the proprietary driver now shows there... but I haven't changed anything (that I know of).

Weird, time to restart X and see if it works.

-darc

---

### Post by darc on 2008-05-06
> **darc said:**
> Update:
I just checked the "Hardware Drivers" program again (jockey-gtk is the program name I believe) and the proprietary driver now shows there... but I haven't changed anything (that I know of).

Weird, time to restart X and see if it works.

-darc

That didn't work either.  I ran nvidia-xconfig on a whim, no joy there.

However, when I restarted X this time, I was able to select the 'nvidia' driver in the "low graphics mode" dialog box.  However, when I tried to test it, it failed.

The nVIDIA proprietary driver does show up in the "Hardware Drivers" program as enabled and in use, but still running in low graphics mode and the nVIDIA config panel says that I'm still not running the nVIDIA X Driver.

Guess I'll try Envy again since I've made some headway.
-darc

---

### Post by darc on 2008-05-06
> **darc said:**
> That didn't work either.  I ran nvidia-xconfig on a whim, no joy there.

However, when I restarted X this time, I was able to select the 'nvidia' driver in the "low graphics mode" dialog box.  However, when I tried to test it, it failed.

The nVIDIA proprietary driver does show up in the "Hardware Drivers" program as enabled and in use, but still running in low graphics mode and the nVIDIA config panel says that I'm still not running the nVIDIA X Driver.

Guess I'll try Envy again since I've made some headway.
-darc


Driver still shows as enabled and in use, but still not working.

I tried to install again with Envy, no joy, still low graphics mode.

So, I tried to install manually again from the nVIDIA binary, no joy there either, still low graphics.

Bugger!
I've got to head out, but I'll poke at it some more when I return,
-darc

---

### Post by darc on 2008-05-06
JOY!

After all that, I checked the nVIDIA settings manager and it didn't error saying the driver wasn't installed.  So, I played with the settings and none really worked.

But, since it says the driver is there now, I switched back to my known good TwinView xorg.conf (from Gutsy), restarted X, and it started working.

So, SOMETHING that I did got the driver working, and then my customized xorg.conf got everything going the way I wanted it.

Afraid I can't offer too much reason why, but try everything I did and maybe you'll get some joy.

-darc
//goes off to party with his fully working Ubuntu 8.04 system : D


Update:  glxgears get's just under 6,000FPS ... WOOT!!!

---

### Post by darc on 2008-05-06
> **darc said:**
> JOY!

After all that, I checked the nVIDIA settings manager and it didn't error saying the driver wasn't installed.  So, I played with the settings and none really worked.

But, since it says the driver is there now, I switched back to my known good TwinView xorg.conf (from Gutsy), restarted X, and it started working.

So, SOMETHING that I did got the driver working, and then my customized xorg.conf got everything going the way I wanted it.

Afraid I can't offer too much reason why, but try everything I did and maybe you'll get some joy.

-darc
//goes off to party with his fully working Ubuntu 8.04 system : D


Update:  glxgears get's just under 6,000FPS ... WOOT!!!


I wooted too soon.  The driver didn't survive a reboot.  

I opened the nVIDIA Config program and got the "no nVIDIA driver" error again.  However, the Ubuntu Hard Driver's program says that it's installed and working (*******).

My xorg.conf is correct so it seems the driver just didn't get loaded for some gay reason.

I dropped out of X (killed gdm) and installed the driver manually, then restarted gdm ~ Joy.  The driver is working now.  

I had this same problem in Gutsy where the driver had to be reinstalled after every reboot in this manner.  However, I eventually fixed it... now to figure out how to do that again...  I'll post when I figure it out.
-darc

---

### Post by darc on 2008-05-06
> **darc said:**
> I wooted too soon.  The driver didn't survive a reboot.  

I opened the nVIDIA Config program and got the "no nVIDIA driver" error again.  However, the Ubuntu Hard Driver's program says that it's installed and working (*******).

My xorg.conf is correct so it seems the driver just didn't get loaded for some gay reason.

I dropped out of X (killed gdm) and installed the driver manually, then restarted gdm ~ Joy.  The driver is working now.  

I had this same problem in Gutsy where the driver had to be reinstalled after every reboot in this manner.  However, I eventually fixed it... now to figure out how to do that again...  I'll post when I figure it out.
-darc


Here's what I did to fix the "reinstall nvidia drivers after every reboot" problem:


Stop GDM:
```
sudo /etc/init.d/gdm stop
```

Remove all things nVIDIA:
```
sudo apt-get remove nvidia*
```

Reinstall the proprietary nVIDIA drivers (gotten from [www.nvidia.com):](www.nvidia.com):)
```
sudo sh NVIDIA-Linux-x86_64-169.12-pkg2.run
```

Install nvidia_glx (though many people have been reporting using the nvidia-glx-new, that didn't work for me ~ give it a try tho):
```
sudo apt-get install nvidia_glx
```

Install these packages if you don't already have them:
```
sudo apt-get install nvidia-kernel-common linux-restricted-modules-'uname -r'
```

If you -DON'T- already have a configured xorg.conf, then we need to configure it.  One way to figure this out is to open your xorg.conf and if you see "Driver "nv"" then you need to configure it (because it's using the open source driver).  If you see "Driver "nvidia"" then you're probably alright (but it couldn't hurt to back it up and reconfigure it if you run out of ideas).  
I already had one so I skipped this step, but if you need it, here you go:
```
sudo nvidia-xconfig
```

Restart GDM:
```
sudo /etc/init.d/gdm start
```


It should be good, right?  It was for me.  Now, reboot and see if the drivers persist, they did for me.

wootlets!
-darc

---

### Post by nasevz on 2008-05-07
> **darc said:**
> 

Install nvidia_glx:
```
sudo apt-get install nvidia_glx
```


Not working for me. The only difference is that I am using 32 bit UBUNTU. I see you are installing nvidia_glx, not nvidia-glx-new.

Regards

---

### Post by darc on 2008-05-07
> **nasevz said:**
> Not working for me. The only difference is that I am using 32 bit UBUNTU. I see you are installing nvidia_glx, not nvidia-glx-new.

Regards

Yes, I tried to install nvidia-glx-new, but apparently I typo'd it.  And, since I was running in single user mode on a terminal, I didn't feel like popping back up to X to look it up, so I took a guess.  Apparently my guess paid off by getting the "wrong" package which worked for me.

But, yes, let it be noted that I was trying to install nvidia-glx-new I just couldn't remember whether it was underscores or hypens.

-darc

---

### Post by caveman79 on 2008-05-07
Thank you for posting the steps.

I was able to follow the instructions that you posted with one exception, the driver. Where do I find the driver for my card (GEFORCE 7950 GT) and where should I save it to?

I am hoping that this will fix my problem too!

---

### Post by darc on 2008-05-07
> **caveman79 said:**
> Thank you for posting the steps.

I was able to follow the instructions that you posted with one exception, the driver. Where do I find the driver for my card (GEFORCE 7950 GT) and where should I save it to?

I am hoping that this will fix my problem too!

I got the "official" nVIDIA binary from their website.  Look here : 
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
You just drop down the boxes to fill in the correct information and go from there.

It looks like you'll be wanting this one (for 32bit):
[http://www.nvidia.com/object/linux_display_ia32_169.12.html](http://www.nvidia.com/object/linux_display_ia32_169.12.html)

Or, this one (for 64bit):
[http://www.nvidia.com/object/linux_display_amd64_169.12.html](http://www.nvidia.com/object/linux_display_amd64_169.12.html)

You can save it anywhere, but then you have to install it.  Which, if you're new to Linux is a bit hairy (stopping the X server, etc).  Just follow the instructions on my previous post to stop gdm (NOTE: this will be 'kdm' if you're using Kubuntu).

Also, you may have to set it executable first like this:
```
chmod a+x NVIDIA-Linux-x86_64-169.12-pkg2.run
```

Then, you can execute it with sudo to install it, just follow the directions and it'll walk you through it:
```
sudo sh NVIDIA-Linux-x86_64-169.12-pkg2.run
```

Let me know how that works for you,
-darc

---

### Post by caveman79 on 2008-05-08
I tried the steps you listed, but still get the same results. The only part I didn't do was the chmod. I am going to try that now and let you know. Other than that I still get the low-resolution window when gdm start back up. Here is what my xorg.conf looked like after.

---

### Post by caveman79 on 2008-05-08
No luck with the steps. I still get the low resolution window and I go in and select the monitor that i have and the nvidia driver. There is a nv driver there also, but I dont know which to use.


# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"nv"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Dell"
	Modelname	"Dell 2007WFP (Digital)"
	Horizsync	30.0-83.0
	Vertrefresh	56.0-76.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1792	1344
		Modes		"1600x1200@65"	"1600x1200@60"	"1400x1050@75"	"1792x1344@60"	"1400x1050@60"	"1280x960@75"	"1280x1024@60"	"1280x960@60"	"1280x1024@75"	"1152x864@75"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"nv"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by darc on 2008-05-08
1)  Doing the chmod won't matter, assuming it let you execute the binary driver installer (you would've gotten 'permission denied' if not).

2)  It looks like your xorg.conf isn't set up for the proprietary driver, note this line : 
```
Driver "nv"
```

That means it's using the open source nVIDIA driver, not the proprietary one that we need.

Try this command:
```
sudo nvidia-xconfig
```

Then, restart X.  If it works, great.  If not, check your xorg.conf again and make sure it contains:
```
Driver "nvidia"
```

Note:  The reason this wasn't in my step-by-step is because I had a previously configured xorg.conf that I've been using for years, so I didn't need to make a new one... sorry for not mentioning that.  I'll add it in.

Keep posting, and maybe we'll get this figured out.
-darc

---

### Post by MeTylerDurden on 2008-05-08
file:///home/tylerdurden/Desktop/Screenshot.png    When I upgraded to Hardy Heron   my driver would not install tried to install and uninstall ..  the update manager icon is always there telling me to upgrade ,yet it is unable to..     I really like the Heron     

The Liberator who destroyed my property has realigned my perception:popcorn:

---

### Post by caveman79 on 2008-05-08
I tried to run the nvidia-config and everything looked good. When I restarted GDM and went to login again I get the "low resolution" screen asking me to select a monitor and a graphics card. I go through and select the monitor and then under graphics card it list the vesa as the one it is using and i select NVIDIA from the list below and then the nvidia driver. Needless to say I still get the same results.

Can I edit the xorg.conf to make it look the right way? Should I be using root to do all the installs?

Thank you for all your help, I can't wait to get this working.

---

### Post by darc on 2008-05-08
> **caveman79 said:**
> I tried to run the nvidia-config and everything looked good. When I restarted GDM and went to login again I get the "low resolution" screen asking me to select a monitor and a graphics card. I go through and select the monitor and then under graphics card it list the vesa as the one it is using and i select NVIDIA from the list below and then the nvidia driver. Needless to say I still get the same results.

Can I edit the xorg.conf to make it look the right way? Should I be using root to do all the installs?

Thank you for all your help, I can't wait to get this working.

Yes, you'll have to be doing it as root (which the 'sudo' will accomplish).

When you log in (in low res mode) can you launch the 'nvidia-settings' program?  You can run it manually or find it in the menu under System>Administration or in System Tools (it moved randomly for me at one point).

Launch that, and if it says that you don't have the driver loaded, then you need to muck around with the driver some more (remove everything, re-install the binary driver, etc).  If it allows you to play with settings, then it means we got the driver running and we just have to configure the xorg.conf.
-darc

---

### Post by caveman79 on 2008-05-08
I am still in low res hell!

I tried the steps again and everything looked good, except it still comes up in low res mode. Here is the xconfig after all the changes. One thing I noted was that I did not uninstall the driver all the way. I just reinstalled the driver over the old one. They were the same drivers and the installer said that it would overwrite and try to fix it. How do you remove the driver? Maybe that will help.


# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Feb 14 18:20:37 PST 2008


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by darc on 2008-05-08
Did you log in (in low rez) and see if nvidia-settings gave you an error or not?

That's a key piece in knowing whether the driver is installed/working and if we just need to tweak your xorg.conf.

Try the nvidia-settings program and let me know what it gives you.
-darc

---

### Post by caveman79 on 2008-05-09
When I tried to login to low rez the nvidia-settings gave me:

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

When I tried doing the nvidia-xconfig it tells me that it has backed up the old and made a new one.

---

### Post by darc on 2008-05-09
> **caveman79 said:**
> When I tried to login to low rez the nvidia-settings gave me:

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

When I tried doing the nvidia-xconfig it tells me that it has backed up the old and made a new one.


If you're getting that error ("You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.") from nvidia-settings, then it means that the driver isn't installed (or at least not in use).

I was getting that too, even though I had just installed the driver, until I did the `apt-get remove nvidia*` then started over using the steps outlined on the first page of this thread.  

Have you tried EnvyNG?  It didn't work for me... but you may give it a try.  I think it's in the repo's : 
```
apt-get install envyng-gtk
```

-darc

---

### Post by caveman79 on 2008-05-09
I finally got the graphics working again. Thank for all the help.

I used:

sudo apt-get install nvidia-glx nvidia-kernel-common linux-restricted-modules-'uname -r'
sudo nvidia-xconfig

Everything is working pretty good right now. 

The last thing I need to fix is the grub so that I can dual boot to windows.

---

### Post by darc on 2008-05-09
> **caveman79 said:**
> I finally got the graphics working again. Thank for all the help.

I used:

sudo apt-get install nvidia-glx nvidia-kernel-common linux-restricted-modules-'uname -r'
sudo nvidia-xconfig

Everything is working pretty good right now. 

The last thing I need to fix is the grub so that I can dual boot to windows.


Good to hear, the linux-restricted-modules package is probably what did it... I did so much crap to get mine going I've forgotten parts of it : P

I've added your tip to the guide on the first page of this thread, thanks for posting and glad you got it going.
-darc

---

### Post by nasevz on 2008-05-10
I solved the problem installing latest beta drivers from Nvidia site. They claim that support for 9600 GT card is added, which probably means that the latest stable version simply has no support for 9600 GT.

---

