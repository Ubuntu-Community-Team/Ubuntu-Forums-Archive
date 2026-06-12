---
title: "intel i810 graphics 3d acceleration problem"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by JoeJaz2 on 2007-10-23
Good afternoon,
  Yesterday I upgraded kubuntu from 7.04 to 7.10.  Before that time, I was able to run fully 3d accelerated programs, including beryl.  The original install of 7.04 could not have been easier and I was very satisfied. After the install of 7.10, I have no 3d support. Here is an excerpt from my xorg.conf.  I added the two option strings after reading a post that these may help, but with no avail.  

Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option "AddARGBGLXVisuals" "True"
        Option "AllowGLXWithComposite" "True"
EndSection

Though compiz is neat.  I really don't need it.  What I do need is the ability to run 3d applications using glx as before.  Without the 3d support, by desktop experience is very choppy and the desktop crashes often, and I don't have access to programs that depend on 3d. 

I'm thinking I may have to 'downgrade' to 7.04 if possible in order to retain my ability to use Linux on this laptop, but I don't really want to do that. I have checked various online forums, including this one, but none of the suggestions have worked so far.  Any additional suggestions or comments would be very much appreciated.
Thanks,
Joe

vaio
    description: Notebook
    product: VGN-TX750P
    vendor: Sony Corporation
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.20GHz
          vendor: Intel Corp.
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 1536MB
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1

jj@vaio:/etc/X11$ glxinfo
name of display: :1.0
display: :1  screen: 0
direct rendering: No

---

### Post by TrueJk7 on 2007-10-25
I'm having the same problems with that chipset on a Dell Latitude D610

Here's my lshw
  *-display:0             
       description: VGA compatible controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: vga bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

and my xorg

Section "device" #  
        Identifier      "device1"
        Boardname       "i810"
        Busid           "PCI:0:2:0"
        Driver          "intel"
        Screen  1
EndSection
Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Boardname       "i810"
        Busid           "PCI:0:2:0"
        Driver          "intel"
        Screen  0
EndSection
Section "Module"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
        Load            "extmod"
        Load            "freetype"
        Load            "int10"
        Load            "type1"
        Load            "vbe"
        Load            "glx"
        Load            "GLcore"
        Load            "v4l"
EndSection


Can anyone help us?

---

### Post by JoeJaz2 on 2007-10-25
One thing I have noticed is that if I boot into single user mode and run X and an Xterm from the command line, I am able to run my 3D apps just fine as normal.  glxgears works just as normal (but it crashes when I boot normally after the upgrade) and I can even run startkde to boot up a KDE desktop (running as root).  However, if I start kde via the init script /etc/rc5.d/S13kdm, or boot normally, I still have the problem.  

This tells me that my hardware and drivers are working fine and X is working fine and kde is working fine.  Something has changed  during the upgrade that has done this.  Specifically, some process triggered downstream of that KDE init process.  Perhaps the problem occurs somewhere between just after the init process was triggered but before X starts.  Just speculating.

Sadly, I am writing this note from my (3d accelerated) windows partition.  Hopefully I can resolve this issue soon, but I am headed into unfamiliar territory.  Any advice is much appreciated.

---

### Post by Pumalite on 2007-10-25
Boardname "i810"
Install 915resolution

---

### Post by JoeJaz2 on 2007-10-25
TrueJk7,
Just wondering if you did a fresh install or an upgrade.  I have considered installing a fresh copy of 7.10 on a seperate partition to see if the problem exists only during an upgrade.  But if yours was is a fresh install and you are having the same problem, then it probably wouldn't make much of a difference. 
Joe

---

### Post by JoeJaz2 on 2007-10-25
> **Pumalite said:**
> Boardname "i810"
Install 915resolution

I like the quote.

---

### Post by TrueJk7 on 2007-10-29
JoeJaz2,
No I did an upgrade. 

Pumalite  Pumalite,
Thanks for the suggestion, however the D610 I own is the cheaper version. 915 resolution wont work. I've got the 1024x768 display on the laptop LCD.

So I'm still in trouble here. :P But half the mission here is learning. JoeJaz2 you're right there when you say X is working, Drivers are working... My problem has been with the compiz intigration. Right now I am booted with Failsafe Gnome, which works the best. This may sound insane but the 3D acceleration works just fine right now. 

Through research I found really the only difference between 7.10's Gnome && Failsafe Gnome is failsafe does not have compiz running... I honestly wish there is a way to get rid of that. 

If you find out. Please let me know!

---

### Post by kvonb on 2007-10-29
I would try 2 things:

1. remove any compiz/beryl related packages with adept.  Also remove it from your session (control centre).

2. reset your xorg.conf by running *sudo dpkg-reconfigure -phigh xserver-xorg* in a teminal.  Restart X.

---

### Post by ZZT32 on 2007-10-30
Having the exact same problem here, although I'm using Dapper Drake. My graphics chipset is: Intel i915 (which should work with the i810 driver; it did in Fedora and it did in Debian Etch). Currently performing a system upgrade, but as soon as it's done I'll try installing "915resolution".

EDIT: Nope, didn't work.:/

---

### Post by JoeJaz2 on 2007-12-05
Thank you all for your input.  

Though not an ideal solution, I have found that a fresh install resolved this issue.  Therefore, it must have been an upgrade issue.  After the install, it works just fine.

---

