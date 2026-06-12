---
title: "Cannot install any Linux distro on Asus P5GZ-MX Motherboard"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by ravs009 on 2008-04-25
Hey everyone! Can anyone of U please solve this problem which has been nagging me for the last 1 year ! The problem is that no linux distibution is willing to install on my PC ! I have tried every linux distro : UBUNTU,open suse,mandriva,fedora etc. Out of these only Mandriva linux powerpack 2007 managed to install on my pc ! But then it refused to boot ! So I had to format its partition !

  Most of the time I get this message: " Kernel panic ! not syncing !"  and other times the installation screen  just freezes ! Please help me! I have got Asus P5GZ-MX motherboard,Intel Core 2 Duo(E4300,1.8GHz,800MHz FSB,2MB L2 Cache) processor,NVIDIA 7300 GT graphics card(256 MB), 2GB DDR2 RAM( Simmtronics),250 GB Seagate SATA  hard drive!
If you want any additional information to diagnose the problem,please tell me ! I will reply!

   By the way, I have tried UBUNTU alternate cd. It installs, but doesn't boot ! I personally think that the problem is with the Asus motherboard. But I am not in a position to buy a new one at this time ! So please tell me a fix that DOES NOT require CHANGING the Motherboard !

 Another ques. : I am confused as to which version I should download everytime I download some OS ! i386,i586,x86 or x64 ! At present I have only one OS installed -Windows Vista Ultimate (x64) .


Please HELP me ! I desperately want to try and use LINUX on my PC !

---

### Post by wandalalakers on 2008-04-25
I think a lot of users are frustrated and will have unanswered posts.
I normally end up figuring out my own problem.
I have an Asus **[COLOR="Red"]P5GC-MX/1333[/COLOR]** motherboard.
I have a few minor problems after my upgraded from 7.10 to 8.04.
I now have no sound and two of my ksplash screens are off center.
Maybe someone else with the same Asus motherboard can help.
I have an EVGA nvidia geforce 7300 with 256mb.
I also have 2gb of ram.
This might be reaching but what about updating the bios?
Which versions of ubuntu have you tried 32 bit or 64 bit?
Did you have any problems with vista ultimate?
I was using kubuntu 7.10 but now I have kubuntu 8.04 with this motherboard.

Try pclinux os and see what happens.
[http://pclinuxos.com/index.php?option=com_ionfiles&Itemid=28](http://pclinuxos.com/index.php?option=com_ionfiles&Itemid=28)

Try foresight linux and see what happens.
[http://www.rpath.org/rbuilder/downloadImage?fileId=24519](http://www.rpath.org/rbuilder/downloadImage?fileId=24519)

---

### Post by wandalalakers on 2008-04-25
I got a kernel panic on a verrrry old pc that I testing out but that only happened after I installed puppy linux on the hard drive and tried to boot.  Other linuxes worked fine.

---

### Post by ravs009 on 2008-04-25
Hi pcdoctor ! I have tried every popular linux os including pclinux os ! Everytime the same thing : "Kernel panic! not syncing! Then an error code is generated . Tried "Safe graphics mode" as well ! Nothing works for me ! Must be the **** Asus motherboard I bought ! Never going to buy Asus again! Maybe Gigabyte next time !

---

### Post by wandalalakers on 2008-04-25
Is your board under warranty and did you have any problems running vista ultimate?

---

### Post by ravs009 on 2008-04-25
Yes, I bought the board last year and it had 3 years warranty then .That makes it 2 years now ! So yeah !  And Vista ultimate works like a dream ! Have used 32 bit version of vista earlier, but now I am using the 64 bit version! Never got a problem with MS os'es : both XP and Vista work !( Not using XP now !)

---

### Post by wandalalakers on 2008-04-25
Go to Asus' website and see if there is a bios update for your board.  That's probably reaching but I can't figure out why M$ would work and linux not.  Since ubuntu doesn't work, I'm sure linux mint would give the same result since it ubuntu based too.  How about this?  Have you tried ubuntu 6.06?

---

### Post by ravs009 on 2008-04-25
Hey pcdoctor ! I had updated the bios 2 weeks ago ! Nothing changed ! Linux still didn't install ! Why would I use version 6.06 when 8.04 is in the market ? Man ! I don't want to live in the Stone Age !
IT seems the only thing left is to throw this m-board out the window, and get a new one from some different maker !

---

### Post by wandalalakers on 2008-04-25
Trying a different version might yield different results.  Maybe someone else will chime in.

---

### Post by enchesss on 2008-04-29
The problem with this motherboard is that if you have another graphics card you have to disable the motherboard's intel on board graphics and the installation does not do it automatically. Good news is that the drivers for most cards are supported and if yuo can blacklist the intel drivers it should work.

I have the same mother board and a friend had to disable (blacklist) the intel on board graphics. Kubuntu works but with no sound - am fixing it now. 

Have upgraded since from Hardy to gutsy with no problems but you have to keep the blacklist and another mod prob setting during the installation process. It automatically gives a prompt to keep the settings during the installation.

I am currently upgrading to the KDE 4.o beta becuase it installed without a hitch on another system.
Maybe this distro will install without a problem if you do a fresh one instead of an upgrade.

Good luck and let us know if this works !

---

### Post by enchesss on 2008-04-30
These instructions have worked:

[http://ubuntuforums.org/showthread.php?t=406205](http://ubuntuforums.org/showthread.php?t=406205)

The important part is blacklisting "agpgart" (note the typo in the howto) and "intel_apg".

I had to reboot the PC and then <ctrl>+<alt>+<F1> to get a console, login and run "sudo nvidia-xconfig" again and reboot.

You may have further issues with the resolution depending on your monitor model.

I now have 8.04 after upgrading and am now installing as i type (probably not a good idea) but it is stable and highly enjoyable.

here is my xorg.conf in etc/x11/(xorg.conf) :- you may have to change the resolution depending on your monitor:

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Apr 16 20:37:13 PDT 2007

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "DELL 2407WFP"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Intel Corporation 82945G/GZ Integrated Graphics Controller"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Intel Corporation 82945G/GZ Integrated Graphics Controller"
    Monitor        "DELL 2407WFP"
    Option         "AddARGBGLXVisuals" "True"
#    Option         "DisableGLXRootClipping" "True"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200" "1680x1680" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

---

### Post by Gnezzo on 2008-05-22
I had the same problem. I have an Asus P5GZ-MX motherboard with a pentium4 cpu, and an Asus Geforce 7300 Graphics card. I was planning to have a linux system, but no distro would install, or boot after installing. So I had to install Windows XP after all. Months later, I tried a dual boot install with Gutsy Gibbon an guess what, it worked. I still don't know if it was the version or the fact that Windows was allready installed (I read some forum entries that suggested this could make a difference)

Still, problems are not over yet. Recently I "Upgraded" to Hardy and sound is my problem now.

---

