---
title: "Upgrade 8.04-&gt;8.10 no X, no screen found"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by bensei on 2008-11-01
Hello:

I just upgraded from 8.04 to 8.10. Everything went smoothly. After reboot and grub, the ubuntu startup screen (i.e. X) showed, but after that I get just a text login (on Crtl-Alt-1). On Crtl-Alt-7, it is just a blank screen. I can log on the text shell without problems, everything runs perfectly, just without X. When I try to start X by command (with or without sudo), I get the message "no screen found".

I have a new lenovo W500 with WUXGA. On 8.04, X ran perfectly, without any problems.

I have found the problem of no X on these boards, but apparently with another error message and for another reason. I am rather clueless now what to do, since I have no idea what could be the reason for this problem...

---

### Post by Sorivenul on 2008-11-01
First, did you do a clean install or did you upgrade via apt?

X is getting more and more "automagic" as time goes on, and if you look at your xorg.conf, it may even be blank, especially if you did a clean install.

To get a "normal" xorg.conf back, which may or may not work, reboot in "Rescue Mode" aka Single User Mode.  From the menu select the option for "Drop to Root Shell" or something similar.  

Then, on the command line do:
```
X -configure
```

This will generate normal xorg.conf, and place it in /root/xorg.conf.new.  
Then simply:
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
and
```
cp /root/xorg.conf.new /etc/X11/xorg.conf
```

Fixed my friends Kubuntu Intrepid install this way just today.  
Good luck!

---

### Post by bensei on 2008-11-01
Thanks a lot for the reply. It did not fix the problem, but I get some info. Hope this may help finding the problem.

Here is what happens when I do as told:
1. type X -configure
2. blank screen
3. hit Crtl-Alt-1
4. see following messages
savage
...
vesa
X: symbol lookup error /usr/lib/xorg/modules/drivers//vga_drv.so:
undefined symbol:xf86GetPciVideoInfo

Also, when I just use X, I get:
1. type X
2. get following messages
...
using config file /etc/X11/xorg.conf
Primary device is not PCI
(EE) No services detected.
Fatal server error: no screens found

---

### Post by Sorivenul on 2008-11-01
Are you using an NVidia card?
If so, in the new xorg.conf, try switching the driver listed as "nvidia" to "nv", and see if that works.  
Without knowing more about your specific hardware, there is only so much we can do.  While X may not be able to find a screen, this may still be a graphics card issue.

---

### Post by bensei on 2008-11-01
The graphics card is ATI Mobility Radeon HD 3650.

Before the upgrade, Ubuntu 8.04 ran perfectly with the same hardware.

When booting to root shell, the directory /root is empty. No files in it. In particular no file named xorg.conf

---

### Post by Sorivenul on 2008-11-01
By default there would be no xorg.conf there.  It would be generated when you typed X -configure and would be labled xorg.conf.new in /root.  

Again, did you do a clean install or dist-upgrade?  If you did a clean install, have you been able to connect and install the ATI drivers?  There seem to be a multitude of X related problems with ATI cards with Intrepid.  If Hardy worked with your hardware, going back may be an option as well.

---

### Post by bensei on 2008-11-01
I did a dist-upgrade, exactly in the way recommended on the ubuntu web site.

The reason I upgraded was that Hardy does not work with my WLAN card. But I'd rather have X than WLAN. So, yes, I would love to go back. How do I actually do that?

---

### Post by CHEFSneebly on 2008-11-01
Bensei,
  Did you end up going back to 8.04, or have you found a work around for this issue.  I have a similar issue with the same Video card.  I also have an error about an Ubiquity of some sort.  It seems to be some sort of Mozilla add in.  But this new version does recognize the wireless card, so why go back?  Well I am going to continue the hunt, but if anyone has a resolution please share the wealth.  THANKS.

---

### Post by bensei on 2008-11-01
How do I actually go back to 8.04 without having X?

---

### Post by m2.g5ru6y7s on 2008-11-01
I had the same problem.
The solution I found was to edit as root the /etc/X11/xorg.conf file and comment out (or remove) just one section:

#Section "Files"
#    RgbPath         "/usr/X11R6/lib/X11/rgb"
#EndSection

After restarting the gdm with /etc/init.d/gdm restart everything worked fine.

Of course a reboot after the removal (or comment out) of the three lines is also fine to solve the issue.

Good luck and please let me know if it works after this adjustment!

---

### Post by bensei on 2008-11-01
Thanks m2.g5ru6y7s,

unfortunately, in my /etc/X11/xorg.conf, there is no Section "Files". The only thing that comes close to having to do with Graphics is
Section "Device"
        Identifyier "Configured Video Device"
End Section
but this seems too generic to be a problem.
(BTW: There is no lib folder in /usr/X11R6/)

What the current xorg.conf states is:
Commented out by update-manager, HAL is now used.
What is HAL?
Could that help somehow?

---

### Post by m2.g5ru6y7s on 2008-11-01
I'm very sorry the problem is not fixed yet. :(
HAL means Hardware Abstraction Layer. 

[http://en.wikipedia.org/wiki/Hardware_abstraction_layer](http://en.wikipedia.org/wiki/Hardware_abstraction_layer)

My NVidia card is a 7600 GS ...

Could you try to backup your current /etc/X11/xorg.conf (i.e. cp /etc/X11/xorg.conf ~ ) and replace it by this one (my xorg.conf)?

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Wed Oct  1 15:09:35 PDT 2008

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@vernadsky)  Tue Mar  4 20:24:34 UTC 2008
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#
#	# generated from default
#    Identifier     "Mouse0"
#    Driver         "mouse"
#    Option         "Protocol" "auto"
#    Option         "Device" "/dev/psaux"
#    Option         "Emulate3Buttons" "no"
#    Option         "ZAxisMapping" "4 5"
#EndSection
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#
#	# generated from default
#    Identifier     "Keyboard0"
#    Driver         "kbd"
#EndSection

Section "ServerLayout"

# commented out by update-manager, HAL is now used
#    InputDevice    "Keyboard0" "CoreKeyboard"
# commented out by update-manager, HAL is now used
#    InputDevice    "Mouse0" "CorePointer"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

#Section "Files"
#    RgbPath         "/usr/X11R6/lib/X11/rgb"
#EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
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

Section "Monitor"

	# HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer F-19"
    HorizSync       30.0 - 83.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: 1280x1024 +1280+0, DFP: 1280x1024 +0+0; CRT: 800x600 +0+0, DFP: NULL; CRT: 640x480 +0+0, DFP: NULL"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Maybe it works..?

---

### Post by bensei on 2008-11-01
I have tried out lots of different choices for /etc/X11/xorg.conf
In particular, I have tried

Section "Device"
Identifier "Configured Video Device"
Driver "radeonhd"
EndSection

Section "Device"
Identifier "Videocard0"
Driver "nvidia"
VendorName "NVIDIA Corporation"
BoardName "GeForce 7600 GS"
EndSection

Section "Device"
Identifier "Configured Video Device"
Driver "ati"
BudId "PCI:1:0:0"
EndSection

The result is the same whatever I do: No changes when doing
/etc/init.d/gdm restart.


The most confusing thing is that I DO HAVE graphics during startup and shutdown. The standard ubuntu progress bar windows show up, in full resolution and quality. Just, then, when in 8.04 the graphical login window showed up, now with 8.10, I get only a text login screen on Crtl-Alt-F1, and Crtl-Alt-F7 is blank.

This looks almost to me as if the configuration in /etc/X11/xorg.conf is not the actual problem.
Does this make any sense?
Does anyone have an explanation for this?

---

### Post by astrophoenix on 2008-11-01
the graphics during start up and shutdown are just the frame buffer stuff. it's NOT X.

---

### Post by mstipanov on 2008-11-01
> **m2.g5ru6y7s said:**
> I had the same problem.
The solution I found was to edit as root the /etc/X11/xorg.conf file and comment out (or remove) just one section:

#Section "Files"
#    RgbPath         "/usr/X11R6/lib/X11/rgb"
#EndSection

After restarting the gdm with /etc/init.d/gdm restart everything worked fine.

Of course a reboot after the removal (or comment out) of the three lines is also fine to solve the issue.

Good luck and please let me know if it works after this adjustment!

Thanks very much. It helped.

---

### Post by bensei on 2008-11-02
Unfortunately, it did not help for me...

What I did now is the following:
sudo apt-get update    (why not)
sudo apt-get install xorg-driver-fglrx    (might help)
sudo apt-get install xserver-xorg-video-radeonhd

This has made problems worse for me!

While before
X -configure
gave me the following error message
X: symbol lookup error /usr/lib/xorg/modules/drivers//vga_drv.so:
undefined symbol f86GetPciVideoInfo
now
X -configure
just hangs up my computer. Nothing works besides turning it off and rebooting. Same happens with X.

I replaced xorg.conf by an original, very neutral version.
Still the hanging up. I guess it has to do with one of the new drivers I installed.

Does this story make sense to anyone?

---

### Post by inf32n0 on 2008-11-03
Ok i figured it out.

I was having the same problems with my system.

-> the problem is, since the new thinkpads have switchable graphics, ubuntu is confused with which graphics card to use and appearently can't locate the appropriate one.

after reading the message carefully it says that no PCI Express display found or something like that, don't remember the message exactly

to solve this problem:

SOLUTION: Go into BIOS and change your display settings to:

Default Primary Video Device = PCI Express
Boot Display Device = ThinPad LCD
Graphics Device = Discrete Graphics
OS Detection for Switchable Graphics = Disabled

This worked for me

I didnt try different combinations of these setting. I might try them and post the results when i have time.

---

### Post by CHEFSneebly on 2008-11-03
inf32n0,
Thank you very much it did work for me, as I do have a Lenovo T500.  This has released a huge weekend headache.

---

### Post by CHEFSneebly on 2008-11-03
inf32n0,
Thank you very much it did work for me, as I do have a Lenovo T500.  This has released a huge weekend headache.:guitar:

---

### Post by bensei on 2008-11-03
inf32n0 is the hero of the day!

Yes, this fixed the problem for me, too.
I have a small annoying text error that states some resolution problem before the ubuntu startup window, but that is just an inconvenience. X works!

Of course, the question remains, why 8.04 detected my graphics correctly, but the upgraded 8.10 does not...

---

### Post by pine900 on 2008-11-04
I have a ThinkPad T400, I had the same problem, and this solution worked.  Thanks a lot!  Also, I did not Disable the OS detection option in BIOS, so hopefully Vista and Ubuntu will both play nice with it enabled- thx again

---

### Post by siliconbrain on 2008-11-12
Hi! I have the same problem. I **upgraded** from 8.04 to 8.10. I have an Acer laptop with an **ATI 3200 IGP** and a **3470 GPU**. None of the xorg.conf editing solutions worked and I don't have any settings in the bios for choosing GPU. Plus, the CD install doesn't work, since there's no X... Please help!

---

### Post by codetail on 2008-11-14
> **siliconbrain said:**
> Hi! I have the same problem. I **upgraded** from 8.04 to 8.10. I have an Acer laptop with an **ATI 3200 IGP** and a **3470 GPU**. None of the xorg.conf editing solutions worked and I don't have any settings in the bios for choosing GPU. Plus, the CD install doesn't work, since there's no X... Please help!

Hi,

I had the same problem with the same GPU (I have an Acer 5530G), and eventually solved adding these lines in my xorg.conf (/etc/X11/xorg.conf) in the "Device" section:

```

BusID "2:0:0"
Driver "radeon"

```

This will use the radeon open source driver, so you probably won't get 3D acceleration, but hopefully you'll get a good 1280x800 resolution and 24bit of colour depth at least.

Good luck!

---

### Post by eXtReMe_SvK on 2008-12-02
> **siliconbrain said:**
> Hi! I have the same problem. I **upgraded** from 8.04 to 8.10. I have an Acer laptop with an **ATI 3200 IGP** and a **3470 GPU**. None of the xorg.conf editing solutions worked and I don't have any settings in the bios for choosing GPU. Plus, the CD install doesn't work, since there's no X... Please help!
I have the same problem on my MSI GX610-PX.
i can´t install ubuntu cuz Xserver doesn´t work :/
now i´m trying to find any easy solution to solve this problem, but nothing.
Can any1 help?

---

### Post by Sorivenul on 2008-12-02
> **eXtReMe_SvK said:**
> I have the same problem on my MSI GX610-PX.
i can´t install ubuntu cuz Xserver doesn´t work :/
now i´m trying to find any easy solution to solve this problem, but nothing.
Can any1 help?
1.) It may be best to start your own thread, as the user experienced upgrade issues with a specific driver.
2.) If you have issues with X starting on the LiveCD, try the Alternate CD, it has a text-based installer that is easy to understand.  Once you have an installed system, if X is still giving you problems, make your post, and help will come.

---

### Post by siliconbrain on 2008-12-06
Hi! Thanks for the tip. I have the same Acer 5530G, but unfortunately it didn't work for me. I got graphics now, but the screen just goes from black to white to black again with a smooth blend. It would look cool as a screensaver, but won't get much job done for me :biggrin:

> **codetail said:**
> Hi,

I had the same problem with the same GPU (I have an Acer 5530G), and eventually solved adding these lines in my xorg.conf (/etc/X11/xorg.conf) in the "Device" section:

```

BusID "2:0:0"
Driver "radeon"

```

This will use the radeon open source driver, so you probably won't get 3D acceleration, but hopefully you'll get a good 1280x800 resolution and 24bit of colour depth at least.

Good luck!

---

### Post by apian on 2008-12-08
> **siliconbrain said:**
> Hi! I have the same problem. I **upgraded** from 8.04 to 8.10. I have an Acer laptop with an **ATI 3200 IGP** and a **3470 GPU**.

I've got multiple nVidia cards in my Dell desktop and this appears to have confused Xorg somehow after my upgrade to 8.10.  It kept reporting the No Screens error on startup.  I didn't see anything in my BIOS about disabling switching.  The solution for me was to use the BusID parameter in the Device section of xorg.conf to specify the location of a video card.  Here's what that section of my xorg.conf file looks like now:

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
        BusID           "1:0:0"
        Option          "NoLogo"        "True"
EndSection
```

Once I added the BusID parameter and rebooted, I was able to boot into the GUI normally.

I used the lspci utility to help determine the proper BusID.

Perhaps something along these lines will help with your Acer problem.

---

### Post by echofloripa on 2009-01-17
Hey guys, basically the same thing happened with me, I have a:

video card:
NVIDIA GeForce 7600 GS
Manufacturer: 
Location: PCI Slot 11 (PCI bus 2, device 0, function 0)
windows driver: NVIDIA 01/06/2006, 9.1.3.1

Inboard video driver:
VIA Chrome9 HC IGP Family
Manufacturer: S3 Graphics Co., Ltd.
Location: PCI bus 1, device 0, function 0
windows driver: S3 Graphics Co., Ltd. 16/04/2008  6.14.10.133 

My bios has one option only that is to select primary video card. I tried with both and nothing. 

I tried to configure my board all the ways that were suggested and nothing.

In the ubuntuguide I found this:
[http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Install_Latest_Nvidia.2FATI_drivers](http://ubuntuguide.org/wiki/Ubuntu:Intrepid#Install_Latest_Nvidia.2FATI_drivers)

I'm testing that now.

Emerson

---

### Post by echofloripa on 2009-01-19
> **echofloripa said:**
> Hey guys, basically the same thing happened with me, I have a:
I'm testing that now.

Emerson

Well, it turned out that 8.10 is not very nice with NVIDIA GeForce boards, I read that on the 8.10 page:
[SIZE="2"]**nVidia "legacy" video support**
The 71 and 96 series of proprietary nVidia drivers, as provided by the nvidia-glx-legacy and nvidia-glx packages in Ubuntu 8.04 LTS, are not compatible with the X.Org included in Ubuntu 8.10. Users with the nVidia TNT, TNT2, TNT Ultra, GeForce, GeForce2, GeForce3, and GeForce4 chipsets are affected and will be transitioned on upgrade to the free nv driver instead. This driver does not support 3D acceleration.
[/SIZE]

I managed to get back to graphic mode only removing the Nvidia card, which is not the best solution :)

And I got the latest VIA driver for my onboard card, unfortunately it didn't work better than 800x600. So, the 8.10 is a bit useless at this point to me :(

They say on the 8.10 release that "GeForce2,... chipsets are affected and will be transitioned on upgrade to the free nv driver instead". Is this the driver that you can install form the package manager if you look for nvidia?

I tried to change the primary video card, that didn't change much things.

I tried to get in the recovery mode and fix X, I tried to run dpkg-reconfig xserver-xorg, I tried the nvidia_xconfig, I tried to get the driver I posted above, it built the driver for my 64 bits kernel, but nothing worked.

I got two different messages:

(ww) Falling back to add probe method for v41
No devices detected
Fatal server error:
no screens found

the other time instead of the first (ww) line i got:
failed to load module "type1" (module does not exist,0)

Any idea of how this can be fixed. Is it actually possible to have 8.10 running with both the VIA and NVIDIA cards???? The details are in my last post. Or should I just go back to the 8.04? Anyway, the 8.04 also didn't recognized automatically the Nvidia, but at least I could boot in graphic mode (800x600) without the need to remove the NVIDIA card.

I have quite good experience with linux (Suse) and Unix, but to be honest, this installation is becoming a nightmare, a few sleepless nights!! :)

Please help me!!!
Emerson

---

### Post by echofloripa on 2009-01-20
> **echofloripa said:**
> Well, it turned out that 8.10 is not very nice with NVIDIA GeForce boards, I read that on the 8.10 page:
...
Please help me!!!
Emerson

Update: I used the latest beta driver for the 7600:
[http://www.nvnews.net/vbulletin/showthread.php?t=122139](http://www.nvnews.net/vbulletin/showthread.php?t=122139)

That alone didn't solve my problem. The only way to get ubuntu 8.10 to boot with my Nvidia geforce 7600 card was disabling the onboard video card.

I get now a better resolution, but not 3d support :(

Also, I have two monitors, how am I going to use the second monitor now??

regards
Emerson

---

