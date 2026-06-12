---
title: "Problem with 7.10 installation"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by Abrupto on 2007-11-25
Hi,

The live  cd boots up and I select start or install. Setup shows the ubuntu logo and the bouncing orange bar but the welcome screen to choose my language and begin the installation does not show up. The screen goes black and nothing happens.

My computer is an HP dc7100

Tanks for your help

Regards
Abrupto

---

### Post by PmDematagoda on 2007-11-25
Why don't you give the Ubuntu [Alternate CD]("http://www.ubuntu.com/getubuntu/download") a try. Visit the download area of Ubuntu and check the check box near the bottom of the web page which allows you to download the Alternate CD.

---

### Post by erginemr on 2007-11-25
Hello and welcome to Ubuntu Forums.

You could also check the Live CD for errors (there should be such an option in the boot up menu), to make sure that your Live CD is error-free.

---

### Post by Abrupto on 2007-12-08
> **erginemr said:**
> Hello and welcome to Ubuntu Forums.

You could also check the Live CD for errors (there should be such an option in the boot up menu), to make sure that your Live CD is error-free.

I´ve tried everything suggested but there is an error after booting. ""The display server has been shut down about 6 times in the last 90 seconds. It is lekely that something bad is going on. Waiting for 2 minutes before trying again on display:0."
I think this is a graphics card problem. I have an ATI X1600 and until now I did this:

```
sudo nano -w /etc/X11/xorg.conf
```

I went to the device section and found this:

```

        Identifier     "ATI Technologies Inc ATI Default Card"
        Driver          "vesa"
        Busid           "PCI:1:0:0"

```

I don't know what to do further. Can you help me?

Regards
Abrupto

---

### Post by erginemr on 2007-12-10
Hello Again,

Sorry that the problem persists. I can only make a wild guess by commenting on the problem and its solution, as I am using an NVidia card. I have googled the web with the 
>  "The display server has been shut down about 6 times in the last 90 seconds." 
keyword and have found the following pages with suggestions on what to do:
[http://wiki.eyermonkey.com/My_Ubuntu_(7.10)_Installation](http://wiki.eyermonkey.com/My_Ubuntu_(7.10)_Installation)
[http://ubuntuforums.org/showthread.php?t=585145](http://ubuntuforums.org/showthread.php?t=585145)

In summary, the problem is your ATI card and the installer is trying to force it to an incompatible resolution. What they suggest is:
> Skip this section if you're not having a problem booting to the live CD.
    * Boot to normal install CD in safe graphics mode.
    * While booting up, the log screen will show "Running local boot scripts (/etc/rc.local)". At this point, a script will run that tries to auto-configure your graphics. For my X1800 mobility, this didn't complete properly. and resulted in the following error "The display server has been shut down about 6 times in the last 90 seconds. It is likely that something bad is going on. Waiting for 2 minutes before trying again on display :1."
    * Ignore that error. If you take too long doing the next couple scripts, the auto-config script might run again and your monitor will flash.
    * Press Alt+F2 to get to terminal
    * Perform:

sudo apt-get install xorg-driver-fglrx
startx

    * After you install 7.10 and get it working, you will need to repeat these steps on your first boot. Then you will need to enable restricted drivers. An information should be presented to you on your first boot prompting you to enable these drivers.  

However, for this trick to work, you need to have a working internet connection on boot, otherwise, you will not be able to download the necessary ATI drivers. You need to select "boot into safe graphics mode" as shown in the attached screenshot. 

And if for some reason, you cannot enable the command line by following the method given above, you can always use "Ctrl+Alt+F1 to F6" to choose and virtual terminal and issue the commands above to install ATI drivers. You can always return to the graphical mode by using "Ctrl+Alt+F7".

Alternatively, you can try the "Alternate CD" as PmDematagoda also suggested above, which installs Ubuntu from a command line. It is a shame that ATI users (mainly because of ATI's policies) are still suffering from problems in this era, when Linux is intruduced to the masses as ready for the desktop use.

Anyway, please do not give up; Ubuntu is well worth the effort.

---

### Post by erginemr on 2007-12-10
I can think of two alternate ways to overcome this problem, but you should be able to find your way in Linux command line interface (CLI), especially how to mount external drives: 

1) I you do not have a working internet connection on boot, you can try donwloading the necessary packages to a USB drive or similar and try mounting them from CLI. Apparently, the package "xorg-driver-fglrx" needs two other packages: "gcc-3.3-base" and "libstdc++5". You can get them from "http://packages.ubuntu.com" from under the "Gutsy" section and put them into a USB memory stick. 

After you mount the drive (USB drives may automatically mount if you plug them in before booting the Live CD, I don't know), you can "cd" to the drive and issue the following command:
```
sudo dpkg --install *.deb
```

2) The xorg.conf file I have attached is a generic one, that supposedly should work for any card. You can unzip and copy the file to a floppy diskette, mount it (again, sorry) and copy it to the original xorg.conf file with:

```
sudo cp ./xorg.conf /etc/X11/xorg.conf
startx
```

If the above tricks do not work because you cannot have access to external drives/floppies for some reason, the relevant sections of the xorg.file are:

```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection
```

Write these down on a scrap of paper and try changing the relevant sections of your xorg.conf file accordingly.

Good Luck...

---

