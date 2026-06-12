---
title: "BadDevice, invalid or uninitialized input device"
date: 2006-09-23
forum: Installation &amp; Upgrades
---

### Post by thumper on 2006-09-23
At some stage over the last few days, something has gone a little screwy.

Running aptitude from the command line is showing me some unexpected errors.  Here I'm trying to revert the flash plugin fubar:
```
tim@spike:/var/lib/dpkg/info$ sudo apt-get install flashplugin-nonfree/dapper
Reading package lists... Done
Building dependency tree... Done
Selected version 7.0.63.3ubuntu3 (Ubuntu:6.06/dapper) for flashplugin-nonfree
Suggested packages:
  mozilla-browser mozilla-firefox ttf-xfree86-nonfree xfs
Recommended packages:
  libesd0-alsa libstdc++2.10-glibc2.2
The following packages will be DOWNGRADED:
  flashplugin-nonfree
0 upgraded, 0 newly installed, 1 downgraded, 0 to remove and 0 not upgraded.
Need to get 0B/16.5kB of archives.
After unpacking 28.7kB disk space will be freed.
Do you want to continue [Y/n]?
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
DESTROY created new reference to dead object ' Qt::SpacerItem', <> line 1 during global destruction.
Preconfiguring packages ...
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 2.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.
dpkg - warning: downgrading flashplugin-nonfree from 7.0.68~ubuntu2~dapper1 to 7.0.63.3ubuntu3.
(Reading database ... 91374 files and directories currently installed.)
Preparing to replace flashplugin-nonfree 7.0.68~ubuntu2~dapper1 (using .../flashplugin-nonfree_7.0.63.3ubuntu3_i386.deb) ...
Unpacking replacement flashplugin-nonfree ...
Setting up flashplugin-nonfree (7.0.63.3ubuntu3) ...
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 2.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 5.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83, <GEN6> line 5.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84, <GEN6> line 5.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83, <GEN6> line 5.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84, <GEN6> line 5.

```

Why am I now getting errors with Debconf?  Or is it an X error?

I dunno... :-(

---

### Post by DySleeper on 2006-10-13
I've just run into some BadDevice errors myself.  I'm trying to run IntelliCAD 6.1 SE with wine.  I've got Dapper Drake installed.  When I type wine icad.exe in the appropriate directory, this is what I get:

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
fixme:ole:CoRegisterMessageFilter message filter has been registered, but will not be used
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  144 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  467
  Current serial number in output stream:  467

```

I've tried commenting out the Wacom sections of xorg.conf, but it seems to make no difference.  In both cases, the splash screen appears briefly.  Potentially complicating the issue is that I once had a Wacom tablet connected to this computer, but that was long before I installed any form of Linux.  Your thoughts?

---

### Post by cornik on 2006-10-17
I had the same problem. Here are the fixes for 2 of those problems.

The fix for the error "DESTROY created new reference to dead object ' Qt::****" is in the thread "Problem when using apt-get" in the "Desktop Environments" forum.

The fix for the error ....
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

... is to delete or comment out these input devices (stylus, curser, eraser) in your /etc/X11/xorg.conf.

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # Change to
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection
#
#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "eraser"
#  Option        "Device"        "/dev/wacom"          # Change to
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection
#
#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "cursor"
#  Option        "Device"        "/dev/wacom"          # Change to
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

....

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
#       InputDevice     "stylus" "SendCoreEvents"
#       InputDevice     "cursor" "SendCoreEvents"
#       InputDevice     "eraser" "SendCoreEvents"
EndSection
===============================

---

### Post by peterx14 on 2007-01-26
> **cornik said:**
> 
... is to delete or comment out these input devices (stylus, curser, eraser) in your /etc/X11/xorg.conf.

Thanks absolutely loads for that! I had the same error trying to start Paint Shop Pro 7 under Wine (Wine 0.9.22 running on Edgy 6.10), and although I had read elsewhere that I needed to comment out/delete the Wacom bits from my xorg.conf, I didn't realise I also had to comment out those last three "InputDevice" lines at the end.  (note to anyone else: commenting out the Wacom bits but *not* commenting out the corresponding InputDevice lines causes your system not to boot properly!).

Cheers!! :D

---

### Post by triple_entendre on 2007-02-13
> **peterx14 said:**
> although I had read elsewhere that I needed to comment out/delete the Wacom bits from my xorg.conf, I didn't realise I also had to comment out those last three "InputDevice" lines at the end.  (note to anyone else: commenting out the Wacom bits but *not* commenting out the corresponding InputDevice lines causes your system not to boot properly!).

Cheers!! :D

I just tried it, and it looks like it's OK to do it the other way around -- just comment out the three InputDevice lines. The Wacom bits are then still in there, but aren't used.

---

### Post by daxdog on 2007-02-15
> **cornik said:**
> 
The fix for the error ....
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

... is to delete or comment out these input devices (stylus, curser, eraser) in your /etc/X11/xorg.conf.

===============================

Hey, this worked.  Thanks for posting this to the group.

---

### Post by Kropotkin on 2007-02-24
I suddenly started getting this error message as well. The thing is, I do want to be able to use my Wacom tablet. Is there anyway of fixing things so that is possible?

I'm running 6.10.

---

