---
title: "Unable to Login with GUI. Coloured lines\bars"
date: 2013-03-24
forum: Installation &amp; Upgrades
---

### Post by pradyot on 2013-03-24
Hi,
I am new to Linux  i successfully installed lubuntu 12.10 alternate version "lubuntu-12.10-alternate-i386". I checked the iso file using "winmid5Sum" and it was proper. I burned it and checked error for disk, even that was proper. After installation , from grub i went to ubuntu, then i got this weird screen full of colored bars. It didn't make any sense. I tried ctrl+alt+f1 and logged onto it, then ctrl+alt+f7. still the same screen.

i am using 

System Model: HV84510A
               BIOS: Default System BIOS
          Processor: Intel(R) Pentium(R) 4 CPU 1.60GHz
             Memory: 512MB RAM
             Hard Disk: 160 GB
Display Devices
---------------
        Card name: S3 Graphics Inc. Savage4
     Manufacturer: S3 Graphics Inc.
        Chip type: S3 Savage4
         DAC type: S3 SDAC
       Device Key: Enum\PCI\VEN_5333&DEV_8A22&SUBSYS_8A225333&REV_03
   Display Memory: 32.0 MB
     Current Mode: 1152 x 864 (32 bit) (60Hz)
          Monitor: Plug and Play Monitor
  Monitor Max Res: 1600,1200
      Driver Name: s3sav4.dll

---

### Post by matt_symes on 2013-03-24
Hi

Welcome to the forums :D

My first question: Is this a Wubi installation (inside Windows) or did you install it into its own partition ?

Can you boot into "safe mode" (to use a Windows expression) from the grub menu ? (This will help to identify if it's a driver problem or something more serious as safe mode uses the Vesa driver).

Kind regards

---

### Post by JOHNNYG713 on 2013-03-24
Driver issue !

---

### Post by pradyot on 2013-03-24
Thank you for the fast reply!

No, this is not wubi installed. I created a free space of 12GB then at the partition part i assigned 1gb for swap and  11Gb ext4 for LUBUNTU.
I referred " [http://www.youtube.com/watch?v=Xi-VPj4jzrg](http://www.youtube.com/watch?v=Xi-VPj4jzrg) " for installation . Everything went as per video. but when restarting I am getting login part with colours (Check out the pics I uploaded). I can open terminal via "ctrl+alt+1"

Yes, I can open Windows XP through grub.


[COLOR=#000000][B][U]JOHNNYG713

any idea how to solve it?[/U][/B][/COLOR]

---

### Post by pradyot on 2013-03-24
My computer is kinda ancient (You check my system info above). I just want a linux os on my system. I am doin CS engg and my college s teaching UNIX. I heard LUBUNTU is very light weight so i used it. Is there any other light distros???

---

### Post by The Cog on 2013-03-24
You've definitely got a driver issue there. Unfortunately, I'm not sure if the S3 is even supported by Linux any more. If not, then you may not be able to get Linux working on that machine at all without replacing the graphics card.

---

### Post by pradyot on 2013-03-24
Do you know any other linux which would work on my machine ??

---

### Post by matt_symes on 2013-03-24
Hi

Did you try booting into safe graphics mode from the grub menu ?

The card should work with VESA as that has been around for an age and that should get you up and running.

You can also edit the kernel command line to boot using the VESA driver.

At the grub prompt when you select a kernel, press the e key.

Navigate to the end if the text line and add this

```
video=uvesafb
```

Press ctrl + c to continue booting. 

Does that help ?

Kind regards

---

### Post by MAFoElffen on 2013-03-24
If you use a "video=x" (where x= an xorg driver or mapped port settting) kernel parameter set like matt_symes suggested, you first need to add a "nomodeset" parameter before it before that parameter will work. KMS has to be disabled before you can use a "video=x" set. That didn't use to be like that // but changed to that at about Ubuntu 11.04-11.10... and comparable other linux distro's around that same time. (When KMS was implemented.)

Fortunately, xorg does have a savage driver... so you could use parameters:
```

nomodeset video=savage

```

Just by you using "nomodeset", would turn off kms and give xorg the ability to try different drivers with your card... but setting it to savage would point it right there.

If that works, set "nomodeset" as persistent in the /etc/default/grub and create a default /etc/X11/xorg.conf file and point the driver to savage in the device section... That way you can tweak the resolutions and other settings for that driver (suggested). Once you get the xorg.conf working, then you can try taking out the nomodeset in grub to see if it is then still needed. You need it if you're telling it from grub to set a driver from grub, but not if it is set to a driver from the xorg.conf file.

You could leave it as "nomodeset video=savage" as persistent in grub without using or adding an xorg.conf file, but then you don't have as much control and aren't using that driver to it's full capabilities (just the basic functions).

If you need reference or instructions for any of that, look in the first three posts of my Graphics Resolution Sticky- link in my sig line.

---

### Post by matt_symes on 2013-03-24
Hi

> if you use a "video=x" kernel parameter set like matt_symes suggested, you first need to add a "nomodeset" parameter before it before that parameter will work.

Thanks for that MAFoElffen. I knew i had forgotten something, i just could not think what. :KS

Kind regards

---

### Post by pradyot on 2013-03-24
can you plz tell me in step by step manner. I am getting confused where I must type  [COLOR=#000000]"nomodeset video=savage"  [/COLOR] in grub cmd ("c" in grub menu) or in linux "ctrl+alt+1" login and type [COLOR=#000000]"nomodeset video=savage"  [/COLOR] . Either way nomodeset is unrecognized command :(

---

### Post by pradyot on 2013-03-24
OK so this is what I did:
RUN 1
1. In grub I typed "e" and went to editor.
2 Before quite splash i wrote [COLOR=#000000][FONT=Ubuntu Mono]nomodeset video=savage[/FONT][/COLOR]  .
3. Then ctrl+x to boot.

result: No change! same coloured lines.

RUN 2:
1. In grub I typed "e" and went to editor.
2 deleted quite splash $blahblahblah and i wrote [COLOR=#000000][FONT=Ubuntu Mono]nomodeset video=savage[/FONT][/COLOR]  .
3. Then ctrl+x to boot.

result: No change again! same coloured lines.

RUN 3
1. In grub I typed "e" and went to editor.
2 Navigated to end of file i wrote [COLOR=#000000][FONT=Ubuntu Mono]nomodeset video=savage[/FONT][/COLOR]  .
3. Then ctrl+x to boot.

result: again No change! same coloured lines.

I am irritated right now!!

---

### Post by schragge on 2013-03-24
The kernel driver is named savagefb, so try *video=savagefb* instead of *video=savage*. Strangely enough, an example on the [driver home page]("http://www.linux-fbdev.org/drivers/savagefb.html") shows *video=riva*, but I guess it must be a typo. Also, have a look at [http://www.thinkwiki.org/wiki/S3_Savage_IX8](http://www.thinkwiki.org/wiki/S3_Savage_IX8). While not exactly about your GPU model, it still may contain useful tips.

---

### Post by matt_symes on 2013-03-24
Hi

What you were doing at the grub menu was the correct way of editing the kernel command line.

Try schragge's suggestion using savagefb. If that works then fine; we can make that permanent.

If that does not work then try the vesa driver.

Incedently, do you still get the issue if you boot from a LiveCD/USB ?

Kind regards

---

### Post by pradyot on 2013-03-24
Has anyone else faced similar problem?
can u give me the edit mode of grub for my system?
I will type exactly what u write. may be that will solve the problem!

And also I am gettinh error as "I/O space for gpio unallocated"

There is no option for "trying lubuntu without installation"

---

### Post by matt_symes on 2013-03-25
Hi

Did you try savagefb and uvesafb ?

You have not told us what you tried.

Kind regards

---

### Post by pradyot on 2013-03-25
HI,

I tried savagefb

and now I tried nomodeset video=uvesafb

still no change! :'(

Just before booting i got this msg:

I/O SPACE FOR GPIO UNINITIALIZED

---

### Post by matt_symes on 2013-03-25
Hi

Try this in grub.

```
video=uvesafb:1024x768-32,mtrr:3,ywrap
```

Taken from here...

[http://www.mjmwired.net/kernel/Documentation/fb/uvesafb.txt](http://www.mjmwired.net/kernel/Documentation/fb/uvesafb.txt)

If that does not work then try this...

```
video=uvesafb:mtrr:3,ywrap,1024x768-24@60
```

Don't forget to add the ```
nomodeset
``` parameter as well.

How sure are you that there is not a hardware problem with the card ?

If you cannot even get the VESA driver working then you may have real problems.

Kind regards

---

### Post by pradyot on 2013-03-25
Maybe what I am writing in edit mode is wrong plz check out  the following pictures. 1st and 2nd are the original edit mode command, 3rd and 4th is after I edited, 5th is after booting(ctrl+x)

---

### Post by matt_symes on 2013-03-25
Hi

I don't think you are doing it wrong. I think it's just not loading the VESA driver.

I am having trouble getting it to load on my laptop and i have tried a whole host of boot options such as xforcevesa and such like. I'll get back to you when and if i succeed.

The other option is to try on old school x.org file.

EDIT:

Things have obviously changed since i last played with vesa. Anybody else with any ideas ?

Kind regards

---

### Post by pradyot on 2013-03-25
Hi

I just tried this puppy linux "slacko-5.5-4G" and macpup 529. after live booting it was proper, didnt give any graphical error!. I hope that that this problem gets solved ASAP but if nothing goes on right I am going to go with Slacko Puppy or macpup Linux. Hope you oblige.

regards
Pradyot

---

### Post by matt_symes on 2013-03-26
Hi

If slacko works for you then you can use that if you like.

You may be able to use it to fix your Ubuntu install though. I have not used slacko so i do not know if it has the same utilities as Ubuntu, however you can try if you want so ....

Boot into slacko and open a terminal. Type

```
lspci -k | grep -iA3 vga
```

(capital A above) and then 

```
xrandr
```

If you get no error about them missing or using the wrong switches then post back the output into your next post.

Kind regards

---

### Post by pradyot on 2013-03-26
Hi

The pictures I uploaded are from usb boot Macpup 529. 

And the following is xorg.conf in MACPUP 529:

#barry Kauler 2011
#pre-constructed xorg.conf, for use by /usr/sbin/xorgwizard-automatic
#110627 working on mageia1 build, this needs fixing.
#111029 Terryphi reported 1cm screen displacement, changed vert freq range from 56-76 to 59-76.
#120329 more placemarkers for xorgwizard-automatic script.

# **********************************************************************
# Module section -- this  section  is used to specify
# which dynamically loadable modules to load.
# **********************************************************************
#
Section "Module"
#    Load "synaptics" #loadsynaptics

# This loads the DBE extension module.

    Load        "dbe"      # Double buffer extension

# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection

# This loads the font modules
#    Load        "type1"
#    Load        "freetype"

# This loads xtrap extension, used by xrandr
#    Load       "xtrap"

# This loads the GLX module (if present). xorg 7.4/5, need explicit disable to disable... change "Disable" to "Load" if reqd...
#    Disable       "glx" #LOADGLX

# This loads dri module (if present). 7.4 loads it by default, have to disable... change "Disable" to "Load" if reqd...
#    Disable       "dri" #LOADDRI

EndSection

# **********************************************************************
# Files section.  This allows default font paths to be set
# **********************************************************************

Section "Files"

# Multiple FontPath entries are allowed (which are concatenated together),
# as well as specifying multiple comma-separated entries in one FontPath
# command (or a combination of both methods)

    #FontPath   "/usr/share/fonts/X11/misc/"
    #FontPath   "/usr/share/fonts/liberation/"
    FontPath   "/usr/share/X11/fonts/misc/"
    FontPath   "/usr/share/X11/fonts/Type1/"
    FontPath   "/usr/share/X11/fonts/TTF/"

EndSection

# **********************************************************************
# Server flags section.
# **********************************************************************

Section "ServerFlags"

# Uncomment this to disable the <Crtl><Alt><Fn> VT switch sequence
# (where n is 1 through 12).  This allows clients to receive these key
# events.

#    Option "DontVTSwitch"

# Enables mode switching with xrandr
# There is a report that this can cause Xorg not to work on some
# video hardware, so default is commented-out...
# but i want to use it in xorgwizard so leave on...

    Option "RandR" "on"

# With this, Xorg won't talk to HAL to add evdev devices and you'll be back
# with the old Xorg behavior (pre-7.4)...

    Option "AutoAddDevices" "false"

# For no-Hal, kirk also suggests this...

#    Option "AllowMouseOpenFail" "true"

# Xorg 7.4, Ubuntu Jaunty, CTRL-ALT-BACKSPACE is disabled by default...

    Option "DontZap" "false"

EndSection


Section "ServerLayout"
#    InputDevice "Synaptics Mouse" "AlwaysCore" #serverlayoutsynaptics
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
    Option      "XkbRules" "xorg"
    Option      "XkbModel" "pc102" #xkbmodel0
    Option      "XkbLayout" "us" #xkeymap0
    #Option      "XkbVariant" "" #xkbvariant0
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "IMPS/2" #mouse0protocol
    Option        "Device" "/dev/mouse"
    #Option      "Emulate3Buttons"
    #Option      "Emulate3Timeout" "50"
    Option      "ZAxisMapping" "4 5" #scrollwheel
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
    HorizSync    35-81
    VertRefresh  59-76
    #UseModes     "Modes0" #monitor0usemodes
    Option      "PreferredMode" "1600x900" #monitor0prefmode
    EndSection
    
Section "Modes"
    Identifier "Modes0"
    #modes0modeline0
EndSection

#110627 remove...
##server can find BusID automatically, comment out...
#Section "Device"
#    Identifier  "Card0"
#    Driver      "vesa" #card0driver
#    VendorName  "Unknown Vendor"
#    BoardName   "Unknown Board"
##    BusID       "PCI:0:2:0" #card0busid
#EndSection

Section "Screen"
    Identifier "Screen0"
#    Device     "Card0"
    Monitor    "Monitor0"
    DefaultDepth 24
    #Option         "metamodes" "1280x800_60 +0+0" #METAMODES_0
    Subsection "Display"
        Depth       24
        Modes       "1600x900" #screen0modes
    EndSubsection
EndSection
#PuppyHardwareProfile=S3_Incorporated__Savage4DELLIN2020M



Thankyou

---

### Post by pradyot on 2013-04-11
Ok, So this is what I did to solve this problem.
I formatted the drive where i installed lubuntu completely and installed "fedora 18 lxde spin" and it worked like a charm. 
So thanks to every1 ho responded to my problem.

bye

---

### Post by tormod on 2013-06-24
pradyot, can you please attach your Xorg.0.log from Fedora 18?

You probably ran into this bug [https://bugs.launchpad.net/bugs/1083032](https://bugs.launchpad.net/bugs/1083032) (fixed in Saucy) on 12.10. I guess you're using the vesa driver in Fedora.

---

### Post by pradyot on 2013-06-25
tormod

My computer was giving lots of trouble. So I decided to buy a new computer. The old one is up in my attic.(keeping it for sentimental value!).
now I am using Win 8 and ubuntu 12.10. win for game and ubuntu for work :). Thanks anyways.

regards

---

### Post by PEK3C8m on 2013-10-14
For anyone seeing this and experiencing the same problem - hoping to get Lubuntu/Xubuntu/Ubuntu to work...I found the answer.

It had to do with the video=savage & video=savagefb ideas mentioned earlier.

If you go about the whole process of editing your /etc/X11 directory to have an actual xorg.conf file (read around here or google on how to do this), you can then edit your xorg.conf file. Find the section named Device, and then where it says Driver="x", change that to say Driver="savagefb". Mine as a default had savage written in there, and after hours of troubleshooting, I changed it to read savagefb, and lo-and-behold it works.

Hopefully this helps any future persons stuck with this issue.

---

### Post by pradyot on 2013-10-15
thanks man appreciate it!

---

