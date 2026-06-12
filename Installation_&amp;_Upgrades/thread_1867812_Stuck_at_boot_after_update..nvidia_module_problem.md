---
title: "Stuck at boot after update..nvidia module problem??"
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by Krakken on 2011-10-23
Hi guys,
i've just updated my desktop, nvidia GeForce 9400 GT and now i'm stuck  at boot with problems. The systems says is not able to locate the nvidia  module. I'm stuck also with previous kernel (probably my bad <) can  anyone help me??

I'm trying from recovery mode to purge nvidia* but i'm in a read-olnly filesystem and I cannot unlock /var/lib/dpkg/lock

Help!!!

Thanks 

K

---

### Post by MAFoElffen on 2011-10-23
> **Krakken said:**
> Hi guys,
i've just updated my desktop, nvidia GeForce 9400 GT and now i'm stuck  at boot with problems. The systems says is not able to locate the nvidia  module. I'm stuck also with previous kernel (probably my bad <) can  anyone help me??

I'm trying from recovery mode to purge nvidia* but i'm in a read-olnly filesystem and I cannot unlock /var/lib/dpkg/lock

Help!!!
Here we go...
- At boot, hold down shift key, Grub Menu should come up...
- Press "e" key, that should put you into an edit mode.
- Arrow Down to the Line that starts with "linux", that is the kernel Boot line.
- Arrow Right to where is says "quiet splash vt.handoff=7"
- Replace that text with "--verbose single"
- Press <cntrl><x>, It will boot with those options.

That will boot into a TTY Text Console. Login.
```

sudo apt-get update
sudo nvidia-installer --uninstall
sudo apt-get remove nvidia-*
sudo apt-get install nvidia-current  
sudo nvidia-xconfig  
sudo reboot

```The uninstall line or the purge may give a message that they don't exist, but just do them to make sure they aren't there.  NVidia drivers have problems when pieces of types or versions are mixed in together at the same time.

Tell me if that helps...

---

### Post by Krakken on 2011-10-23
Hi MAFoElffen
I'm not sure what you mean for ```
sudo update
```is it maybe ```
sudo apt-get update
``` ??

Is yes I may have some problem with apt-get. Gives error with many http that it cannot resolve, and failed to fetch most oneiric archive...

What now??

Thank for your quick post!

UPDATE:

There are no nvidia* installed but when I use
```
sudo apt-get install nvidia-current
```

I get the following:

```
Err http://ppa.lunchpad.net/ubuntu-x-swat/x-updates/ubuntu/ oneiric/main nvidia-settings i386 285.05.09-0ubuntu1~oneiric~xup1
could not resolve 'ppa.lunchpad.net'
Failed to fetch http://ppa.lunchpad.net/ubuntu-x-swat/x-updates/ubuntu/ oneiric/main nvidia-settings i386 285.05.09-0ubuntu1~oneiric~xup1_i386.deb
Could not resolve 'ppa.lunchpad.net'
E:Unable to fetch some archives maybe run apt-get update or try with --fix-missing?
```

---

### Post by Krakken on 2011-10-23
Found and fixed network issues... i'm trying now your suggestion...

---

### Post by Krakken on 2011-10-23
mmmhh..I keep getting previous errors...

```

FATAL: Module nvidia_current not found.
(EE) NVIDIA:Failed to load the NVIDIA kernel module.
(EE)Please check your system's kernel log for additional error messages.
(EE)Failed to load Module "nvidia" (module-specific error, 0)
(EE) no driver available.

Fatal server error:
no screens found

ddxSigGiveUp: Closing log
xinit:giving up
xinit: unable to connect to X server: connection refused
xinit:server error
```

Thank you!

---

### Post by MAFoElffen on 2011-10-23
> **Krakken said:**
> Hi MAFoElffen
I'm not sure what you mean for ```
sudo update
```is it maybe ```
sudo apt-get update
``` ??

Is yes I may have some problem with apt-get. Gives error with many http that it cannot resolve, and failed to fetch most oneiric archive...

What now??

Thank for your quick post!

UPDATE:

There are no nvidia* installed but when I use
```
sudo apt-get install nvidia-current
```I get the following:

```
Err http://ppa.lunchpad.net/ubuntu-x-swat/x-updates/ubuntu/ oneiric/main nvidia-settings i386 285.05.09-0ubuntu1~oneiric~xup1
could not resolve 'ppa.lunchpad.net'
Failed to fetch http://ppa.lunchpad.net/ubuntu-x-swat/x-updates/ubuntu/ oneiric/main nvidia-settings i386 285.05.09-0ubuntu1~oneiric~xup1_i386.deb
Could not resolve 'ppa.lunchpad.net'
E:Unable to fetch some archives maybe run apt-get update or try with --fix-missing?
```
Did you have the x-swat PPA left in when you did your dist-upgrade? X-SSwar Ream says to do a PPA Purge before a Dist Upgrade, then add back in after.

More important, how are you accessing the Command Line Interface?  If mounted to the installed system files, can you
```

ping -c 5 www.google.com

```If not and you have network from that box using other OS, it may have "other" problems also.

---

### Post by Krakken on 2011-10-23
Hi,
network works now. I installed nvidia-current from x-swat PPA but when i boot i'm stuck and from --verbose single if I do ```
startx
``` I get the same err:

```
FATAL: Module nvidia_current not found. 
(EE) NVIDIA:Failed to load the NVIDIA kernel module. 
(EE)Please check your system's kernel log for additional error messages. 
(EE)Failed to load Module "nvidia" (module-specific error, 0) 
(EE) no driver available.  
Fatal server error: no screens found  
ddxSigGiveUp: Closing log 
xinit:giving up 
xinit: unable to connect to X server: connection refused 
xinit:server error
```

can you guide me troughs?? I'm not an experienced user!!

---

### Post by Krakken on 2011-10-23
Thinking about downgrading back to natty hoping to get a working x session...

---

### Post by Krakken on 2011-10-23
Downgraded but with no luck...still no nvidia module loaded...

HELP PLEASE!!

---

### Post by MAFoElffen on 2011-10-23
> **Krakken said:**
> Thinking about downgrading back to natty hoping to get a working x session...
Please post your /var/log/xorg.0.log and your /etc/X11/conf files (remember to put them within CODE tags.)

So you installed the drivers, but it can't find them?  I guess we'll see.  Are you married to X-Swat?  My experience with that in tast 6 months has been Nvidia releases a driver > Within 1-2 days, the "man" (I forget his name) already has taken the binaries and built them into Ubuntu packages and has them place into Edgers (Test).  A few days later (usually) they are moved to X-Swat (Porposed).  Usually they hit the Release Pero's about a week.  Last Nvidia release went from Nvidia release to Ubuntu Main in 3 days! 

Just saying...  I'm a bored dev tester and I expect to break things.  (I have a card on my monitor that says "I Void Warranties...") But if your looking for stable, a test of dev version may not be what you are expecting.

---

### Post by Krakken on 2011-10-23
mmmh.i'm writing from a different computer, how can I export the output of files in this one??


No I don't know x-Swat and is first time I come up close to one of is driver, but i have to say is not my type!! Anyway I like your style and thanks for the help! I hope we get around this quickly..

---

### Post by Krakken on 2011-10-23
here it is...i-m working on the desktop machine with problem from a liveUSB 11.10:

```
[    17.963] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    17.963] X Protocol Version 11, Revision 0
[    17.963] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    17.963] Current Operating System: Linux home 3.0.0-13-generic-pae #21-Ubuntu SMP Mon Oct 17 20:36:56 UTC 2011 i686
[    17.963] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-13-generic-pae root=UUID=9738bd5f-32a2-4f6d-b9c1-7389c5dcca4a ro quiet splash vt.handoff=7
[    17.963] Build Date: 13 October 2011  05:38:22PM
[    17.963] xorg-server 2:1.10.1-1ubuntu1.3 (For technical support please see http://www.ubuntu.com/support) 
[    17.963] Current version of pixman: 0.20.2
[    17.963]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    17.963] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    17.963] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Oct 23 22:14:34 2011
[    17.983] (==) Using config file: "/etc/X11/xorg.conf"
[    17.983] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.030] (==) ServerLayout "Default Layout"
[    18.030] (**) |-->Screen "Screen0" (0)
[    18.030] (**) |   |-->Monitor "Monitor0"
[    18.030] (**) |   |-->Device "Device0"
[    18.030] (**) |-->Input Device "Keyboard0"
[    18.030] (**) |-->Input Device "Mouse0"
[    18.030] (**) Option "Xinerama" "0"
[    18.030] (==) Automatically adding devices
[    18.030] (==) Automatically enabling devices
[    18.077] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.077]     Entry deleted from font path.
[    18.158] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    18.158] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    18.158] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    18.158] (WW) Disabling Keyboard0
[    18.158] (WW) Disabling Mouse0
[    18.158] (II) Loader magic: 0x8200ac0
[    18.158] (II) Module ABI versions:
[    18.158]     X.Org ANSI C Emulation: 0.4
[    18.158]     X.Org Video Driver: 10.0
[    18.158]     X.Org XInput driver : 12.3
[    18.158]     X.Org Server Extension : 5.0
[    18.159] (--) PCI:*(0:1:0:0) 10de:0641:1043:82be rev 161, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/524288
[    18.159] (II) Open ACPI successful (/var/run/acpid.socket)
[    18.159] (II) "extmod" will be loaded by default.
[    18.159] (II) "dbe" will be loaded by default.
[    18.159] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    18.159] (II) "record" will be loaded by default.
[    18.159] (II) "dri" will be loaded by default.
[    18.159] (II) "dri2" will be loaded by default.
[    18.159] (II) LoadModule: "glx"
[    18.203] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    20.072] (II) Module glx: vendor="NVIDIA Corporation"
[    20.072]     compiled for 4.0.2, module version = 1.0.0
[    20.072]     Module class: X.Org Server Extension
[    20.072] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:11:28 PDT 2011
[    20.072] (II) Loading extension GLX
[    20.072] (II) LoadModule: "extmod"
[    20.113] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    20.149] (II) Module extmod: vendor="X.Org Foundation"
[    20.149]     compiled for 1.10.1, module version = 1.0.0
[    20.149]     Module class: X.Org Server Extension
[    20.149]     ABI class: X.Org Server Extension, version 5.0
[    20.149] (II) Loading extension MIT-SCREEN-SAVER
[    20.149] (II) Loading extension XFree86-VidModeExtension
[    20.149] (II) Loading extension XFree86-DGA
[    20.149] (II) Loading extension DPMS
[    20.149] (II) Loading extension XVideo
[    20.149] (II) Loading extension XVideo-MotionCompensation
[    20.149] (II) Loading extension X-Resource
[    20.149] (II) LoadModule: "dbe"
[    20.149] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    20.171] (II) Module dbe: vendor="X.Org Foundation"
[    20.171]     compiled for 1.10.1, module version = 1.0.0
[    20.171]     Module class: X.Org Server Extension
[    20.171]     ABI class: X.Org Server Extension, version 5.0
[    20.171] (II) Loading extension DOUBLE-BUFFER
[    20.171] (II) LoadModule: "record"
[    20.172] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    20.192] (II) Module record: vendor="X.Org Foundation"
[    20.192]     compiled for 1.10.1, module version = 1.13.0
[    20.192]     Module class: X.Org Server Extension
[    20.192]     ABI class: X.Org Server Extension, version 5.0
[    20.192] (II) Loading extension RECORD
[    20.192] (II) LoadModule: "dri"
[    20.192] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    20.212] (II) Module dri: vendor="X.Org Foundation"
[    20.212]     compiled for 1.10.1, module version = 1.0.0
[    20.212]     ABI class: X.Org Server Extension, version 5.0
[    20.212] (II) Loading extension XFree86-DRI
[    20.212] (II) LoadModule: "dri2"
[    20.212] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    20.226] (II) Module dri2: vendor="X.Org Foundation"
[    20.226]     compiled for 1.10.1, module version = 1.2.0
[    20.226]     ABI class: X.Org Server Extension, version 5.0
[    20.226] (II) Loading extension DRI2
[    20.226] (II) LoadModule: "nvidia"
[    20.226] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    20.335] (II) Module nvidia: vendor="NVIDIA Corporation"
[    20.335]     compiled for 4.0.2, module version = 1.0.0
[    20.335]     Module class: X.Org Video Driver
[    20.586] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[    20.586] (EE) NVIDIA:     system's kernel log for additional error messages.
[    20.586] (II) UnloadModule: "nvidia"
[    20.586] (II) Unloading nvidia
[    20.586] (EE) Failed to load module "nvidia" (module-specific error, 0)
[    20.586] (EE) No drivers available.
[    20.586] 
Fatal server error:
[    20.586] no screens found
[    20.586] 
```and X11 conf

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 270.41.06  (buildmeister@swio-display-x86-rhel47-07.nvidia.com)  Mon Apr 18 15:15:12 PDT 2011

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 260.19.06  (buildd@palmer)  Mon Oct  4 16:01:38 UTC 2010
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#
#    # generated from default
#    Identifier     "Keyboard0"
#    Driver         "kbd"
#EndSection
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#
#    # generated from default
#    Identifier     "Mouse0"
#    Driver         "mouse"
#    Option         "Protocol" "auto"
#    Option         "Device" "/dev/psaux"
#    Option         "Emulate3Buttons" "no"
#    Option         "ZAxisMapping" "4 5"
#EndSection

Section "ServerLayout"

# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#    InputDevice    "Keyboard0" "CoreKeyboard"
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#    InputDevice    "Mouse0" "CorePointer"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Module"
    Load           "glx"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nv"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9400 GT"
EndSection

Section "Screen"
    Identifier     "Configured Screen Device"
    Device         "Configured Video Device"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Virtual    3000  1080
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT: nvidia-auto-select +1920+0, DFP: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: nvidia-auto-select +1920+56, DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```Hope this will help...

The liveUSB works in low resolution but at least boot on graphic mode...why upgrade are always more painfull than clean install??

---

### Post by MAFoElffen on 2011-10-23
> **Krakken said:**
> here it is...i-m working on the desktop machine with problem from a liveUSB 11.10:

Hope this will help...

The liveUSB works in low resolution but at least boot on graphic mode...why upgrade are always more painfull than clean install??
Biting lip... I didn't know that the opensourced NV driver would support as new a card as yours.  Even then, that driver is 2D acceleration and will not support Unity 3D.

Your xorg.conf says it's using the NV driver.  I figured you would be using the nvidia-current with that card.  Since I know how what's going on now...

Boot the PC-
- At boot, hold down shift key, Grub Menu should come up...
- Press "e" key, that should put you into an edit mode.
- Arrow Down to the Line that starts with "linux", that is the kernel Boot line.
- Arrow Right to where after where is says "quiet splash" and before where it says "vt.handoff=7"
- Replace that text with "--verbose single"
- Press <cntrl><x>, It will boot with those options.

That will boot to a TTY Text Console. Login, then edit your sources list...
```

sudo nano /etc/apt/sources.list

```A comment character in that file is "#". Comment out the 2 lines pointing to the X-Swat Repo's. Press <cntrl><o> to save and then <cntrl><x> to exit.

After that we can take care or your graphics drivers:
```

sudo update
sudo nvidia-installer --uninstall
sudo apt-get remove nvidia-*
sudo apt-get install nvidia-current  
sudo nvidia-xconfig  
sudo apt-get upgrade

```The 2 lines removing old or residual drivers files may throw some errors saying none found, but we have to check and make sure they're not there.

Test via
```

sudo service lightdm start

```EDIT- You have "nvidia GeForce 9400 GT"... On this box I'm running 3 each nVidia GeForce 9500 GTX SLI-bridged and the driver works fine for me... Since this is my "main" box I stay stable.  My 7 "test" boxes are another story.

---

### Post by Krakken on 2011-10-23
NV driver eh?? I did not note that before. 
I cannot find X-swat repo's in my source.list:

```
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://it.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://it.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://it.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://it.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://it.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://it.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://it.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://it.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://it.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://it.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://it.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu oneiric partner
deb-src http://archive.canonical.com/ubuntu oneiric partner

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb http://it.archive.ubuntu.com/ubuntu/ oneiric restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb http://extras.ubuntu.com/ubuntu oneiric main #Third party developers repository

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://it.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb-src http://extras.ubuntu.com/ubuntu oneiric main
```

But after downgrading and upgrading again i'm finally in graphic mode with low resolution and only one screen working:

```
[    14.113] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    14.113] X Protocol Version 11, Revision 0
[    14.113] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    14.113] Current Operating System: Linux pbd-desk 3.0.0-13-generic-pae #21-Ubuntu SMP Mon Oct 17 20:36:56 UTC 2011 i686
[    14.113] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-13-generic-pae root=UUID=9738bd5f-32a2-4f6d-b9c1-7389c5dcca4a ro quiet splash vt.handoff=7
[    14.113] Build Date: 29 September 2011  12:48:48AM
[    14.113] xorg-server 2:1.10.4-1ubuntu4 (For technical support please see http://www.ubuntu.com/support) 
[    14.113] Current version of pixman: 0.22.2
[    14.113]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    14.113] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.113] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Oct 23 23:12:18 2011
[    14.217] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.257] (==) No Layout section.  Using the first Screen section.
[    14.257] (==) No screen section available. Using defaults.
[    14.257] (**) |-->Screen "Default Screen Section" (0)
[    14.257] (**) |   |-->Monitor "<default monitor>"
[    14.257] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    14.257] (==) Automatically adding devices
[    14.257] (==) Automatically enabling devices
[    14.368] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.368]     Entry deleted from font path.
[    14.368] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    14.368]     Entry deleted from font path.
[    14.368] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    14.368]     Entry deleted from font path.
[    14.369] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    14.369]     Entry deleted from font path.
[    14.369] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    14.369]     Entry deleted from font path.
[    14.426] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    14.426] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.426] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    14.426] (II) Loader magic: 0x823ada0
[    14.426] (II) Module ABI versions:
[    14.426]     X.Org ANSI C Emulation: 0.4
[    14.426]     X.Org Video Driver: 10.0
[    14.426]     X.Org XInput driver : 12.3
[    14.426]     X.Org Server Extension : 5.0
[    14.426] (--) PCI:*(0:1:0:0) 10de:0641:1043:82be rev 161, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/524288
[    14.426] (II) Open ACPI successful (/var/run/acpid.socket)
[    14.426] (II) LoadModule: "extmod"
[    14.485] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.509] (II) Module extmod: vendor="X.Org Foundation"
[    14.509]     compiled for 1.10.4, module version = 1.0.0
[    14.509]     Module class: X.Org Server Extension
[    14.509]     ABI class: X.Org Server Extension, version 5.0
[    14.509] (II) Loading extension MIT-SCREEN-SAVER
[    14.509] (II) Loading extension XFree86-VidModeExtension
[    14.509] (II) Loading extension XFree86-DGA
[    14.510] (II) Loading extension DPMS
[    14.510] (II) Loading extension XVideo
[    14.510] (II) Loading extension XVideo-MotionCompensation
[    14.510] (II) Loading extension X-Resource
[    14.510] (II) LoadModule: "dbe"
[    14.510] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    14.529] (II) Module dbe: vendor="X.Org Foundation"
[    14.529]     compiled for 1.10.4, module version = 1.0.0
[    14.529]     Module class: X.Org Server Extension
[    14.529]     ABI class: X.Org Server Extension, version 5.0
[    14.529] (II) Loading extension DOUBLE-BUFFER
[    14.529] (II) LoadModule: "glx"
[    14.529] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    14.607] (II) Module glx: vendor="X.Org Foundation"
[    14.607]     compiled for 1.10.4, module version = 1.0.0
[    14.607]     ABI class: X.Org Server Extension, version 5.0
[    14.607] (==) AIGLX enabled
[    14.607] (II) Loading extension GLX
[    14.607] (II) LoadModule: "record"
[    14.607] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    14.613] (II) Module record: vendor="X.Org Foundation"
[    14.613]     compiled for 1.10.4, module version = 1.13.0
[    14.613]     Module class: X.Org Server Extension
[    14.613]     ABI class: X.Org Server Extension, version 5.0
[    14.613] (II) Loading extension RECORD
[    14.613] (II) LoadModule: "dri"
[    14.613] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    14.640] (II) Module dri: vendor="X.Org Foundation"
[    14.640]     compiled for 1.10.4, module version = 1.0.0
[    14.640]     ABI class: X.Org Server Extension, version 5.0
[    14.640] (II) Loading extension XFree86-DRI
[    14.640] (II) LoadModule: "dri2"
[    14.640] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    14.652] (II) Module dri2: vendor="X.Org Foundation"
[    14.652]     compiled for 1.10.4, module version = 1.2.0
[    14.652]     ABI class: X.Org Server Extension, version 5.0
[    14.652] (II) Loading extension DRI2
[    14.652] (==) Matched nvidia as autoconfigured driver 0
[    14.652] (==) Matched nouveau as autoconfigured driver 1
[    14.652] (==) Matched nv as autoconfigured driver 2
[    14.652] (==) Matched vesa as autoconfigured driver 3
[    14.652] (==) Matched fbdev as autoconfigured driver 4
[    14.652] (==) Assigned the driver to the xf86ConfigLayout
[    14.652] (II) LoadModule: "nvidia"
[    14.685] (WW) Warning, couldn't open module nvidia
[    14.685] (II) UnloadModule: "nvidia"
[    14.685] (II) Unloading nvidia
[    14.685] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    14.685] (II) LoadModule: "nouveau"
[    14.685] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    14.715] (II) Module nouveau: vendor="X.Org Foundation"
[    14.715]     compiled for 1.10.1, module version = 0.0.16
[    14.715]     Module class: X.Org Video Driver
[    14.715]     ABI class: X.Org Video Driver, version 10.0
[    14.715] (II) LoadModule: "nv"
[    14.716] (WW) Warning, couldn't open module nv
[    14.716] (II) UnloadModule: "nv"
[    14.716] (II) Unloading nv
[    14.716] (EE) Failed to load module "nv" (module does not exist, 0)
[    14.716] (II) LoadModule: "vesa"
[    14.716] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.716] (II) Module vesa: vendor="X.Org Foundation"
[    14.716]     compiled for 1.10.2, module version = 2.3.0
[    14.716]     Module class: X.Org Video Driver
[    14.716]     ABI class: X.Org Video Driver, version 10.0
[    14.716] (II) LoadModule: "fbdev"
[    14.716] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    14.722] (II) Module fbdev: vendor="X.Org Foundation"
[    14.722]     compiled for 1.10.0, module version = 0.4.2
[    14.722]     ABI class: X.Org Video Driver, version 10.0
[    14.722] (II) NOUVEAU driver Date:   Thu Mar 24 02:13:12 2011 +1000
[    14.722] (II) NOUVEAU driver for NVIDIA chipset families :
[    14.722]     RIVA TNT        (NV04)
[    14.722]     RIVA TNT2       (NV05)
[    14.722]     GeForce 256     (NV10)
[    14.722]     GeForce 2       (NV11, NV15)
[    14.722]     GeForce 4MX     (NV17, NV18)
[    14.722]     GeForce 3       (NV20)
[    14.722]     GeForce 4Ti     (NV25, NV28)
[    14.722]     GeForce FX      (NV3x)
[    14.722]     GeForce 6       (NV4x)
[    14.722]     GeForce 7       (G7x)
[    14.722]     GeForce 8       (G8x)
[    14.722]     GeForce GTX 200 (NVA0)
[    14.722]     GeForce GTX 400 (NVC0)
[    14.722] (II) VESA: driver for VESA chipsets: vesa
[    14.722] (II) FBDEV: driver for framebuffer: fbdev
[    14.723] (++) using VT number 7

[    14.723] drmOpenDevice: node name is /dev/dri/card0
[    14.727] [drm] failed to load kernel module "nouveau"
[    14.727] (EE) [drm] failed to open device
[    14.727] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    14.728] (WW) Falling back to old probe method for fbdev
[    14.728] (II) Loading sub module "fbdevhw"
[    14.728] (II) LoadModule: "fbdevhw"
[    14.728] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    14.761] (II) Module fbdevhw: vendor="X.Org Foundation"
[    14.761]     compiled for 1.10.4, module version = 0.0.2
[    14.761]     ABI class: X.Org Video Driver, version 10.0
[    14.761] (EE) open /dev/fb0: No such file or directory
[    14.761] (II) Loading sub module "vbe"
[    14.761] (II) LoadModule: "vbe"
[    14.761] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    14.769] (II) Module vbe: vendor="X.Org Foundation"
[    14.769]     compiled for 1.10.4, module version = 1.1.0
[    14.769]     ABI class: X.Org Video Driver, version 10.0
[    14.769] (II) Loading sub module "int10"
[    14.769] (II) LoadModule: "int10"
[    14.769] (II) Loading /usr/lib/xorg/modules/libint10.so
[    14.776] (II) Module int10: vendor="X.Org Foundation"
[    14.776]     compiled for 1.10.4, module version = 1.0.0
[    14.776]     ABI class: X.Org Video Driver, version 10.0
[    14.776] (II) VESA(0): initializing int10
[    14.780] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    14.833] (II) VESA(0): VESA BIOS detected
[    14.833] (II) VESA(0): VESA VBE Version 3.0
[    14.833] (II) VESA(0): VESA VBE Total Mem: 14336 kB
[    14.833] (II) VESA(0): VESA VBE OEM: NVIDIA
[    14.833] (II) VESA(0): VESA VBE OEM Software Rev: 98.148
[    14.833] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[    14.833] (II) VESA(0): VESA VBE OEM Product: G96 Board - 07290040
[    14.833] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[    14.927] (II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    14.927] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[    14.927] (==) VESA(0): RGB weight 888
[    14.927] (==) VESA(0): Default visual is TrueColor
[    14.927] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    14.927] (II) Loading sub module "ddc"
[    14.927] (II) LoadModule: "ddc"
[    14.927] (II) Module "ddc" already built-in
[    14.992] (II) VESA(0): VESA VBE DDC supported
[    14.992] (II) VESA(0): VESA VBE DDC Level 2
[    14.992] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[    15.076] (II) VESA(0): VESA VBE DDC read successfully
[    15.076] (II) VESA(0): Manufacturer: ACI  Model: 22f2  Serial#: 16843009
[    15.076] (II) VESA(0): Year: 2008  Week: 44
[    15.076] (II) VESA(0): EDID Version: 1.3
[    15.076] (II) VESA(0): Digital Display Input
[    15.076] (II) VESA(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[    15.076] (II) VESA(0): Gamma: 2.20
[    15.076] (II) VESA(0): DPMS capabilities: StandBy Suspend Off
[    15.076] (II) VESA(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    15.076] (II) VESA(0): Default color space is primary color space
[    15.076] (II) VESA(0): First detailed timing is preferred mode
[    15.076] (II) VESA(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.609
[    15.076] (II) VESA(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.330
[    15.076] (II) VESA(0): Supported established timings:
[    15.076] (II) VESA(0): 720x400@70Hz
[    15.076] (II) VESA(0): 640x480@60Hz
[    15.076] (II) VESA(0): 640x480@67Hz
[    15.076] (II) VESA(0): 640x480@72Hz
[    15.076] (II) VESA(0): 640x480@75Hz
[    15.076] (II) VESA(0): 800x600@56Hz
[    15.076] (II) VESA(0): 800x600@60Hz
[    15.076] (II) VESA(0): 800x600@72Hz
[    15.076] (II) VESA(0): 800x600@75Hz
[    15.076] (II) VESA(0): 832x624@75Hz
[    15.076] (II) VESA(0): 1024x768@60Hz
[    15.076] (II) VESA(0): 1024x768@70Hz
[    15.076] (II) VESA(0): 1024x768@75Hz
[    15.076] (II) VESA(0): 1280x1024@75Hz
[    15.076] (II) VESA(0): Manufacturer's mask: 0
[    15.076] (II) VESA(0): Supported standard timings:
[    15.076] (II) VESA(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    15.076] (II) VESA(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    15.076] (II) VESA(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    15.076] (II) VESA(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    15.076] (II) VESA(0): #4: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    15.076] (II) VESA(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    15.076] (II) VESA(0): #6: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[    15.076] (II) VESA(0): Supported detailed timing:
[    15.076] (II) VESA(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[    15.076] (II) VESA(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    15.076] (II) VESA(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    15.076] (II) VESA(0): Ranges: V min: 50 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 175 MHz
[    15.076] (II) VESA(0): Monitor name: VH226
[    15.076] (II) VESA(0): Serial No: 8ALMQS035720
[    15.076] (II) VESA(0): EDID (in hex):
[    15.076] (II) VESA(0):     00ffffffffffff000469f22201010101
[    15.076] (II) VESA(0):     2c12010380301b78eec4f6a3574a9c23
[    15.076] (II) VESA(0):     114f54bfef00714f818081409500a940
[    15.076] (II) VESA(0):     b300d1c00101023a801871382d40582c
[    15.077] (II) VESA(0):     4500dd0c1100001e000000fd00324c1f
[    15.077] (II) VESA(0):     5311000a202020202020000000fc0056
[    15.077] (II) VESA(0):     483232360a20202020202020000000ff
[    15.077] (II) VESA(0):     0038414c4d51533033353732300a0008
[    15.077] (II) VESA(0): EDID vendor "ACI", prod id 8946
[    15.077] (II) VESA(0): Using EDID range info for horizontal sync
[    15.077] (II) VESA(0): Using EDID range info for vertical refresh
[    15.077] (II) VESA(0): Printing DDC gathered Modelines:
[    15.077] (II) VESA(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    15.077] (II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    15.077] (II) VESA(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    15.077] (II) VESA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    15.077] (II) VESA(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    15.077] (II) VESA(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    15.077] (II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    15.077] (II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    15.077] (II) VESA(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    15.077] (II) VESA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    15.077] (II) VESA(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    15.077] (II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    15.077] (II) VESA(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    15.077] (II) VESA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    15.077] (II) VESA(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    15.077] (II) VESA(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    15.077] (II) VESA(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    15.077] (II) VESA(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    15.077] (II) VESA(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    15.077] (II) VESA(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    15.077] (II) VESA(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    15.077] (II) VESA(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
[    15.077] (II) VESA(0): Searching for matching VESA mode(s):
[    15.078] Mode: 100 (640x400)
[    15.078]     ModeAttributes: 0x3bf
[    15.078]     WinAAttributes: 0x7
[    15.078]     WinBAttributes: 0x0
[    15.078]     WinGranularity: 64
[    15.078]     WinSize: 64
[    15.078]     WinASegment: 0xa000
[    15.078]     WinBSegment: 0x0
[    15.078]     WinFuncPtr: 0xc0009280
[    15.078]     BytesPerScanline: 640
[    15.078]     XResolution: 640
[    15.078]     YResolution: 400
[    15.078]     XCharSize: 8
[    15.078]     YCharSize: 16
[    15.078]     NumberOfPlanes: 1
[    15.078]     BitsPerPixel: 8
[    15.078]     NumberOfBanks: 1
[    15.078]     MemoryModel: 4
[    15.078]     BankSize: 0
[    15.078]     NumberOfImages: 14
[    15.078]     RedMaskSize: 0
[    15.078]     RedFieldPosition: 0
[    15.078]     GreenMaskSize: 0
[    15.078]     GreenFieldPosition: 0
[    15.078]     BlueMaskSize: 0
[    15.078]     BlueFieldPosition: 0
[    15.078]     RsvdMaskSize: 0
[    15.078]     RsvdFieldPosition: 0
[    15.078]     DirectColorModeInfo: 0
[    15.078]     PhysBasePtr: 0xfb000000
[    15.078]     LinBytesPerScanLine: 640
[    15.078]     BnkNumberOfImagePages: 14
[    15.078]     LinNumberOfImagePages: 14
[    15.078]     LinRedMaskSize: 0
[    15.078]     LinRedFieldPosition: 0
[    15.078]     LinGreenMaskSize: 0
[    15.078]     LinGreenFieldPosition: 0
[    15.078]     LinBlueMaskSize: 0
[    15.078]     LinBlueFieldPosition: 0
[    15.078]     LinRsvdMaskSize: 0
[    15.078]     LinRsvdFieldPosition: 0
[    15.078]     MaxPixelClock: 229500000
[    15.080] Mode: 101 (640x480)
[    15.080]     ModeAttributes: 0x3bf
[    15.080]     WinAAttributes: 0x7
[    15.080]     WinBAttributes: 0x0
[    15.080]     WinGranularity: 64
[    15.080]     WinSize: 64
[    15.080]     WinASegment: 0xa000
[    15.080]     WinBSegment: 0x0
[    15.080]     WinFuncPtr: 0xc0009280
[    15.080]     BytesPerScanline: 640
[    15.080]     XResolution: 640
[    15.080]     YResolution: 480
[    15.080]     XCharSize: 8
[    15.080]     YCharSize: 16
[    15.080]     NumberOfPlanes: 1
[    15.080]     BitsPerPixel: 8
[    15.080]     NumberOfBanks: 1
[    15.080]     MemoryModel: 4
[    15.080]     BankSize: 0
[    15.080]     NumberOfImages: 10
[    15.080]     RedMaskSize: 0
[    15.080]     RedFieldPosition: 0
[    15.080]     GreenMaskSize: 0
[    15.080]     GreenFieldPosition: 0
[    15.080]     BlueMaskSize: 0
[    15.080]     BlueFieldPosition: 0
[    15.080]     RsvdMaskSize: 0
[    15.080]     RsvdFieldPosition: 0
[    15.080]     DirectColorModeInfo: 0
[    15.080]     PhysBasePtr: 0xfb000000
[    15.080]     LinBytesPerScanLine: 640
[    15.080]     BnkNumberOfImagePages: 10
[    15.080]     LinNumberOfImagePages: 10
[    15.080]     LinRedMaskSize: 0
[    15.080]     LinRedFieldPosition: 0
[    15.080]     LinGreenMaskSize: 0
[    15.080]     LinGreenFieldPosition: 0
[    15.080]     LinBlueMaskSize: 0
[    15.080]     LinBlueFieldPosition: 0
[    15.080]     LinRsvdMaskSize: 0
[    15.080]     LinRsvdFieldPosition: 0
[    15.080]     MaxPixelClock: 229500000
[    15.081] Mode: 102 (800x600)
[    15.081]     ModeAttributes: 0x33f
[    15.081]     WinAAttributes: 0x7
[    15.081]     WinBAttributes: 0x0
[    15.081]     WinGranularity: 64
[    15.081]     WinSize: 64
[    15.081]     WinASegment: 0xa000
[    15.081]     WinBSegment: 0x0
[    15.081]     WinFuncPtr: 0xc0009280
[    15.081]     BytesPerScanline: 100
[    15.081]     XResolution: 800
[    15.081]     YResolution: 600
[    15.081]     XCharSize: 8
[    15.081]     YCharSize: 16
[    15.081]     NumberOfPlanes: 4
[    15.081]     BitsPerPixel: 4
[    15.081]     NumberOfBanks: 1
[    15.081]     MemoryModel: 3
[    15.081]     BankSize: 0
[    15.081]     NumberOfImages: 2
[    15.081]     RedMaskSize: 0
[    15.081]     RedFieldPosition: 0
[    15.081]     GreenMaskSize: 0
[    15.081]     GreenFieldPosition: 0
[    15.081]     BlueMaskSize: 0
[    15.081]     BlueFieldPosition: 0
[    15.081]     RsvdMaskSize: 0
[    15.081]     RsvdFieldPosition: 0
[    15.081]     DirectColorModeInfo: 0
[    15.081]     PhysBasePtr: 0x0
[    15.081]     LinBytesPerScanLine: 100
[    15.081]     BnkNumberOfImagePages: 2
[    15.081]     LinNumberOfImagePages: 2
[    15.081]     LinRedMaskSize: 0
[    15.082]     LinRedFieldPosition: 0
[    15.082]     LinGreenMaskSize: 0
[    15.082]     LinGreenFieldPosition: 0
[    15.082]     LinBlueMaskSize: 0
[    15.082]     LinBlueFieldPosition: 0
[    15.082]     LinRsvdMaskSize: 0
[    15.082]     LinRsvdFieldPosition: 0
[    15.082]     MaxPixelClock: 108500000
[    15.083] Mode: 103 (800x600)
[    15.083]     ModeAttributes: 0x3bf
[    15.083]     WinAAttributes: 0x7
[    15.083]     WinBAttributes: 0x0
[    15.083]     WinGranularity: 64
[    15.083]     WinSize: 64
[    15.083]     WinASegment: 0xa000
[    15.083]     WinBSegment: 0x0
[    15.083]     WinFuncPtr: 0xc0009280
[    15.083]     BytesPerScanline: 800
[    15.083]     XResolution: 800
[    15.083]     YResolution: 600
[    15.083]     XCharSize: 8
[    15.083]     YCharSize: 16
[    15.083]     NumberOfPlanes: 1
[    15.083]     BitsPerPixel: 8
[    15.083]     NumberOfBanks: 1
[    15.083]     MemoryModel: 4
[    15.083]     BankSize: 0
[    15.083]     NumberOfImages: 6
[    15.083]     RedMaskSize: 0
[    15.083]     RedFieldPosition: 0
[    15.083]     GreenMaskSize: 0
[    15.083]     GreenFieldPosition: 0
[    15.083]     BlueMaskSize: 0
[    15.083]     BlueFieldPosition: 0
[    15.083]     RsvdMaskSize: 0
[    15.083]     RsvdFieldPosition: 0
[    15.083]     DirectColorModeInfo: 0
[    15.083]     PhysBasePtr: 0xfb000000
[    15.083]     LinBytesPerScanLine: 800
[    15.083]     BnkNumberOfImagePages: 6
[    15.083]     LinNumberOfImagePages: 6
[    15.083]     LinRedMaskSize: 0
[    15.083]     LinRedFieldPosition: 0
[    15.083]     LinGreenMaskSize: 0
[    15.083]     LinGreenFieldPosition: 0
[    15.083]     LinBlueMaskSize: 0
[    15.083]     LinBlueFieldPosition: 0
[    15.083]     LinRsvdMaskSize: 0
[    15.083]     LinRsvdFieldPosition: 0
[    15.083]     MaxPixelClock: 229500000
[    15.084] Mode: 104 (1024x768)
[    15.084]     ModeAttributes: 0x33f
[    15.084]     WinAAttributes: 0x7
[    15.084]     WinBAttributes: 0x0
[    15.084]     WinGranularity: 64
[    15.084]     WinSize: 64
[    15.084]     WinASegment: 0xa000
[    15.084]     WinBSegment: 0x0
[    15.084]     WinFuncPtr: 0xc0009280
[    15.084]     BytesPerScanline: 128
[    15.084]     XResolution: 1024
[    15.084]     YResolution: 768
[    15.084]     XCharSize: 8
[    15.085]     YCharSize: 16
[    15.085]     NumberOfPlanes: 4
[    15.085]     BitsPerPixel: 4
[    15.085]     NumberOfBanks: 1
[    15.085]     MemoryModel: 3
[    15.085]     BankSize: 0
[    15.085]     NumberOfImages: 1
[    15.085]     RedMaskSize: 0
[    15.085]     RedFieldPosition: 0
[    15.085]     GreenMaskSize: 0
[    15.085]     GreenFieldPosition: 0
[    15.085]     BlueMaskSize: 0
[    15.085]     BlueFieldPosition: 0
[    15.085]     RsvdMaskSize: 0
[    15.085]     RsvdFieldPosition: 0
[    15.085]     DirectColorModeInfo: 0
[    15.085]     PhysBasePtr: 0x0
[    15.085]     LinBytesPerScanLine: 128
[    15.085]     BnkNumberOfImagePages: 1
[    15.085]     LinNumberOfImagePages: 1
[    15.085]     LinRedMaskSize: 0
[    15.085]     LinRedFieldPosition: 0
[    15.085]     LinGreenMaskSize: 0
[    15.085]     LinGreenFieldPosition: 0
[    15.085]     LinBlueMaskSize: 0
[    15.085]     LinBlueFieldPosition: 0
[    15.085]     LinRsvdMaskSize: 0
[    15.085]     LinRsvdFieldPosition: 0
[    15.085]     MaxPixelClock: 108500000
[    15.086] Mode: 105 (1024x768)
[    15.086]     ModeAttributes: 0x3bf
[    15.086]     WinAAttributes: 0x7
[    15.086]     WinBAttributes: 0x0
[    15.086]     WinGranularity: 64
[    15.086]     WinSize: 64
[    15.086]     WinASegment: 0xa000
[    15.086]     WinBSegment: 0x0
[    15.086]     WinFuncPtr: 0xc0009280
[    15.086]     BytesPerScanline: 1024
[    15.086]     XResolution: 1024
[    15.086]     YResolution: 768
[    15.086]     XCharSize: 8
[    15.086]     YCharSize: 16
[    15.086]     NumberOfPlanes: 1
[    15.086]     BitsPerPixel: 8
[    15.086]     NumberOfBanks: 1
[    15.086]     MemoryModel: 4
[    15.086]     BankSize: 0
[    15.086]     NumberOfImages: 3
[    15.086]     RedMaskSize: 0
[    15.086]     RedFieldPosition: 0
[    15.086]     GreenMaskSize: 0
[    15.086]     GreenFieldPosition: 0
[    15.086]     BlueMaskSize: 0
[    15.086]     BlueFieldPosition: 0
[    15.086]     RsvdMaskSize: 0
[    15.086]     RsvdFieldPosition: 0
[    15.086]     DirectColorModeInfo: 0
[    15.086]     PhysBasePtr: 0xfb000000
[    15.086]     LinBytesPerScanLine: 1024
[    15.086]     BnkNumberOfImagePages: 3
[    15.086]     LinNumberOfImagePages: 3
[    15.086]     LinRedMaskSize: 0
[    15.086]     LinRedFieldPosition: 0
[    15.086]     LinGreenMaskSize: 0
[    15.086]     LinGreenFieldPosition: 0
[    15.086]     LinBlueMaskSize: 0
[    15.086]     LinBlueFieldPosition: 0
[    15.086]     LinRsvdMaskSize: 0
[    15.086]     LinRsvdFieldPosition: 0
[    15.086]     MaxPixelClock: 229500000
[    15.088] Mode: 106 (1280x1024)
[    15.088]     ModeAttributes: 0x33f
[    15.088]     WinAAttributes: 0x7
[    15.088]     WinBAttributes: 0x0
[    15.088]     WinGranularity: 64
[    15.088]     WinSize: 64
[    15.088]     WinASegment: 0xa000
[    15.088]     WinBSegment: 0x0
[    15.088]     WinFuncPtr: 0xc0009280
[    15.088]     BytesPerScanline: 160
[    15.088]     XResolution: 1280
[    15.088]     YResolution: 1024
[    15.088]     XCharSize: 8
[    15.088]     YCharSize: 16
[    15.088]     NumberOfPlanes: 4
[    15.088]     BitsPerPixel: 4
[    15.088]     NumberOfBanks: 1
[    15.088]     MemoryModel: 3
[    15.088]     BankSize: 0
[    15.088]     NumberOfImages: 1
[    15.088]     RedMaskSize: 0
[    15.088]     RedFieldPosition: 0
[    15.088]     GreenMaskSize: 0
[    15.088]     GreenFieldPosition: 0
[    15.088]     BlueMaskSize: 0
[    15.088]     BlueFieldPosition: 0
[    15.088]     RsvdMaskSize: 0
[    15.088]     RsvdFieldPosition: 0
[    15.088]     DirectColorModeInfo: 0
[    15.088]     PhysBasePtr: 0x0
[    15.088]     LinBytesPerScanLine: 160
[    15.088]     BnkNumberOfImagePages: 1
[    15.088]     LinNumberOfImagePages: 1
[    15.088]     LinRedMaskSize: 0
[    15.088]     LinRedFieldPosition: 0
[    15.088]     LinGreenMaskSize: 0
[    15.088]     LinGreenFieldPosition: 0
[    15.088]     LinBlueMaskSize: 0
[    15.088]     LinBlueFieldPosition: 0
[    15.088]     LinRsvdMaskSize: 0
[    15.088]     LinRsvdFieldPosition: 0
[    15.088]     MaxPixelClock: 108500000
[    15.089] Mode: 107 (1280x1024)
[    15.089]     ModeAttributes: 0x3bf
[    15.089]     WinAAttributes: 0x7
[    15.089]     WinBAttributes: 0x0
[    15.089]     WinGranularity: 64
[    15.089]     WinSize: 64
[    15.089]     WinASegment: 0xa000
[    15.089]     WinBSegment: 0x0
[    15.089]     WinFuncPtr: 0xc0009280
[    15.089]     BytesPerScanline: 1280
[    15.089]     XResolution: 1280
[    15.089]     YResolution: 1024
[    15.089]     XCharSize: 8
[    15.089]     YCharSize: 16
[    15.089]     NumberOfPlanes: 1
[    15.089]     BitsPerPixel: 8
[    15.089]     NumberOfBanks: 1
[    15.089]     MemoryModel: 4
[    15.089]     BankSize: 0
[    15.089]     NumberOfImages: 1
[    15.089]     RedMaskSize: 0
[    15.089]     RedFieldPosition: 0
[    15.089]     GreenMaskSize: 0
[    15.089]     GreenFieldPosition: 0
[    15.089]     BlueMaskSize: 0
[    15.089]     BlueFieldPosition: 0
[    15.089]     RsvdMaskSize: 0
[    15.089]     RsvdFieldPosition: 0
[    15.089]     DirectColorModeInfo: 0
[    15.089]     PhysBasePtr: 0xfb000000
[    15.089]     LinBytesPerScanLine: 1280
[    15.089]     BnkNumberOfImagePages: 1
[    15.089]     LinNumberOfImagePages: 1
[    15.089]     LinRedMaskSize: 0
[    15.089]     LinRedFieldPosition: 0
[    15.089]     LinGreenMaskSize: 0
[    15.089]     LinGreenFieldPosition: 0
[    15.089]     LinBlueMaskSize: 0
[    15.089]     LinBlueFieldPosition: 0
[    15.089]     LinRsvdMaskSize: 0
[    15.089]     LinRsvdFieldPosition: 0
[    15.089]     MaxPixelClock: 229500000
[    15.091] Mode: 10e (320x200)
[    15.091]     ModeAttributes: 0x3bf
[    15.091]     WinAAttributes: 0x7
[    15.091]     WinBAttributes: 0x0
[    15.091]     WinGranularity: 64
[    15.091]     WinSize: 64
[    15.091]     WinASegment: 0xa000
[    15.091]     WinBSegment: 0x0
[    15.091]     WinFuncPtr: 0xc0009280
[    15.091]     BytesPerScanline: 640
[    15.091]     XResolution: 320
[    15.091]     YResolution: 200
[    15.091]     XCharSize: 8
[    15.091]     YCharSize: 8
[    15.091]     NumberOfPlanes: 1
[    15.091]     BitsPerPixel: 16
[    15.091]     NumberOfBanks: 1
[    15.091]     MemoryModel: 6
[    15.091]     BankSize: 0
[    15.091]     NumberOfImages: 30
[    15.091]     RedMaskSize: 5
[    15.091]     RedFieldPosition: 11
[    15.091]     GreenMaskSize: 6
[    15.091]     GreenFieldPosition: 5
[    15.091]     BlueMaskSize: 5
[    15.091]     BlueFieldPosition: 0
[    15.091]     RsvdMaskSize: 0
[    15.091]     RsvdFieldPosition: 0
[    15.091]     DirectColorModeInfo: 0
[    15.091]     PhysBasePtr: 0xfb000000
[    15.091]     LinBytesPerScanLine: 640
[    15.091]     BnkNumberOfImagePages: 30
[    15.091]     LinNumberOfImagePages: 30
[    15.091]     LinRedMaskSize: 5
[    15.091]     LinRedFieldPosition: 11
[    15.091]     LinGreenMaskSize: 6
[    15.091]     LinGreenFieldPosition: 5
[    15.091]     LinBlueMaskSize: 5
[    15.091]     LinBlueFieldPosition: 0
[    15.091]     LinRsvdMaskSize: 0
[    15.091]     LinRsvdFieldPosition: 0
[    15.091]     MaxPixelClock: 229500000
[    15.092] *Mode: 10f (320x200)
[    15.092]     ModeAttributes: 0x3bf
[    15.092]     WinAAttributes: 0x7
[    15.092]     WinBAttributes: 0x0
[    15.092]     WinGranularity: 64
[    15.092]     WinSize: 64
[    15.092]     WinASegment: 0xa000
[    15.092]     WinBSegment: 0x0
[    15.092]     WinFuncPtr: 0xc0009280
[    15.092]     BytesPerScanline: 1280
[    15.092]     XResolution: 320
[    15.092]     YResolution: 200
[    15.092]     XCharSize: 8
[    15.092]     YCharSize: 8
[    15.092]     NumberOfPlanes: 1
[    15.092]     BitsPerPixel: 32
[    15.092]     NumberOfBanks: 1
[    15.092]     MemoryModel: 6
[    15.092]     BankSize: 0
[    15.092]     NumberOfImages: 14
[    15.092]     RedMaskSize: 8
[    15.092]     RedFieldPosition: 16
[    15.092]     GreenMaskSize: 8
[    15.092]     GreenFieldPosition: 8
[    15.092]     BlueMaskSize: 8
[    15.092]     BlueFieldPosition: 0
[    15.092]     RsvdMaskSize: 8
[    15.092]     RsvdFieldPosition: 24
[    15.092]     DirectColorModeInfo: 0
[    15.092]     PhysBasePtr: 0xfb000000
[    15.092]     LinBytesPerScanLine: 1280
[    15.092]     BnkNumberOfImagePages: 14
[    15.092]     LinNumberOfImagePages: 14
[    15.092]     LinRedMaskSize: 8
[    15.092]     LinRedFieldPosition: 16
[    15.092]     LinGreenMaskSize: 8
[    15.092]     LinGreenFieldPosition: 8
[    15.092]     LinBlueMaskSize: 8
[    15.092]     LinBlueFieldPosition: 0
[    15.092]     LinRsvdMaskSize: 8
[    15.092]     LinRsvdFieldPosition: 24
[    15.092]     MaxPixelClock: 229500000
[    15.094] Mode: 111 (640x480)
[    15.094]     ModeAttributes: 0x3bf
[    15.094]     WinAAttributes: 0x7
[    15.094]     WinBAttributes: 0x0
[    15.094]     WinGranularity: 64
[    15.094]     WinSize: 64
[    15.094]     WinASegment: 0xa000
[    15.094]     WinBSegment: 0x0
[    15.094]     WinFuncPtr: 0xc0009280
[    15.094]     BytesPerScanline: 1280
[    15.094]     XResolution: 640
[    15.094]     YResolution: 480
[    15.094]     XCharSize: 8
[    15.094]     YCharSize: 16
[    15.094]     NumberOfPlanes: 1
[    15.094]     BitsPerPixel: 16
[    15.094]     NumberOfBanks: 1
[    15.094]     MemoryModel: 6
[    15.094]     BankSize: 0
[    15.094]     NumberOfImages: 4
[    15.094]     RedMaskSize: 5
[    15.094]     RedFieldPosition: 11
[    15.094]     GreenMaskSize: 6
[    15.094]     GreenFieldPosition: 5
[    15.094]     BlueMaskSize: 5
[    15.094]     BlueFieldPosition: 0
[    15.094]     RsvdMaskSize: 0
[    15.094]     RsvdFieldPosition: 0
[    15.094]     DirectColorModeInfo: 0
[    15.094]     PhysBasePtr: 0xfb000000
[    15.094]     LinBytesPerScanLine: 1280
[    15.094]     BnkNumberOfImagePages: 4
[    15.094]     LinNumberOfImagePages: 4
[    15.094]     LinRedMaskSize: 5
[    15.094]     LinRedFieldPosition: 11
[    15.094]     LinGreenMaskSize: 6
[    15.094]     LinGreenFieldPosition: 5
[    15.094]     LinBlueMaskSize: 5
[    15.094]     LinBlueFieldPosition: 0
[    15.094]     LinRsvdMaskSize: 0
[    15.094]     LinRsvdFieldPosition: 0
[    15.094]     MaxPixelClock: 229500000
[    15.095] *Mode: 112 (640x480)
[    15.095]     ModeAttributes: 0x3bf
[    15.095]     WinAAttributes: 0x7
[    15.095]     WinBAttributes: 0x0
[    15.095]     WinGranularity: 64
[    15.095]     WinSize: 64
[    15.095]     WinASegment: 0xa000
[    15.095]     WinBSegment: 0x0
[    15.095]     WinFuncPtr: 0xc0009280
[    15.095]     BytesPerScanline: 2560
[    15.095]     XResolution: 640
[    15.095]     YResolution: 480
[    15.095]     XCharSize: 8
[    15.095]     YCharSize: 16
[    15.095]     NumberOfPlanes: 1
[    15.095]     BitsPerPixel: 32
[    15.095]     NumberOfBanks: 1
[    15.095]     MemoryModel: 6
[    15.095]     BankSize: 0
[    15.095]     NumberOfImages: 1
[    15.095]     RedMaskSize: 8
[    15.095]     RedFieldPosition: 16
[    15.095]     GreenMaskSize: 8
[    15.095]     GreenFieldPosition: 8
[    15.095]     BlueMaskSize: 8
[    15.095]     BlueFieldPosition: 0
[    15.095]     RsvdMaskSize: 8
[    15.095]     RsvdFieldPosition: 24
[    15.095]     DirectColorModeInfo: 0
[    15.095]     PhysBasePtr: 0xfb000000
[    15.095]     LinBytesPerScanLine: 2560
[    15.095]     BnkNumberOfImagePages: 1
[    15.095]     LinNumberOfImagePages: 1
[    15.095]     LinRedMaskSize: 8
[    15.095]     LinRedFieldPosition: 16
[    15.095]     LinGreenMaskSize: 8
[    15.095]     LinGreenFieldPosition: 8
[    15.095]     LinBlueMaskSize: 8
[    15.095]     LinBlueFieldPosition: 0
[    15.095]     LinRsvdMaskSize: 8
[    15.095]     LinRsvdFieldPosition: 24
[    15.095]     MaxPixelClock: 229500000
[    15.097] Mode: 114 (800x600)
[    15.097]     ModeAttributes: 0x3bf
[    15.097]     WinAAttributes: 0x7
[    15.097]     WinBAttributes: 0x0
[    15.097]     WinGranularity: 64
[    15.097]     WinSize: 64
[    15.097]     WinASegment: 0xa000
[    15.097]     WinBSegment: 0x0
[    15.097]     WinFuncPtr: 0xc0009280
[    15.097]     BytesPerScanline: 1600
[    15.097]     XResolution: 800
[    15.097]     YResolution: 600
[    15.097]     XCharSize: 8
[    15.097]     YCharSize: 16
[    15.097]     NumberOfPlanes: 1
[    15.097]     BitsPerPixel: 16
[    15.097]     NumberOfBanks: 1
[    15.097]     MemoryModel: 6
[    15.097]     BankSize: 0
[    15.097]     NumberOfImages: 2
[    15.097]     RedMaskSize: 5
[    15.097]     RedFieldPosition: 11
[    15.097]     GreenMaskSize: 6
[    15.097]     GreenFieldPosition: 5
[    15.097]     BlueMaskSize: 5
[    15.097]     BlueFieldPosition: 0
[    15.097]     RsvdMaskSize: 0
[    15.097]     RsvdFieldPosition: 0
[    15.097]     DirectColorModeInfo: 0
[    15.097]     PhysBasePtr: 0xfb000000
[    15.097]     LinBytesPerScanLine: 1600
[    15.097]     BnkNumberOfImagePages: 2
[    15.097]     LinNumberOfImagePages: 2
[    15.097]     LinRedMaskSize: 5
[    15.097]     LinRedFieldPosition: 11
[    15.097]     LinGreenMaskSize: 6
[    15.097]     LinGreenFieldPosition: 5
[    15.097]     LinBlueMaskSize: 5
[    15.097]     LinBlueFieldPosition: 0
[    15.097]     LinRsvdMaskSize: 0
[    15.097]     LinRsvdFieldPosition: 0
[    15.097]     MaxPixelClock: 229500000
[    15.098] *Mode: 115 (800x600)
[    15.098]     ModeAttributes: 0x3bf
[    15.098]     WinAAttributes: 0x7
[    15.098]     WinBAttributes: 0x0
[    15.098]     WinGranularity: 64
[    15.098]     WinSize: 64
[    15.098]     WinASegment: 0xa000
[    15.098]     WinBSegment: 0x0
[    15.098]     WinFuncPtr: 0xc0009280
[    15.098]     BytesPerScanline: 3200
[    15.098]     XResolution: 800
[    15.098]     YResolution: 600
[    15.098]     XCharSize: 8
[    15.098]     YCharSize: 16
[    15.098]     NumberOfPlanes: 1
[    15.098]     BitsPerPixel: 32
[    15.098]     NumberOfBanks: 1
[    15.098]     MemoryModel: 6
[    15.098]     BankSize: 0
[    15.098]     NumberOfImages: 1
[    15.098]     RedMaskSize: 8
[    15.098]     RedFieldPosition: 16
[    15.098]     GreenMaskSize: 8
[    15.098]     GreenFieldPosition: 8
[    15.098]     BlueMaskSize: 8
[    15.098]     BlueFieldPosition: 0
[    15.098]     RsvdMaskSize: 8
[    15.098]     RsvdFieldPosition: 24
[    15.098]     DirectColorModeInfo: 0
[    15.098]     PhysBasePtr: 0xfb000000
[    15.099]     LinBytesPerScanLine: 3200
[    15.099]     BnkNumberOfImagePages: 1
[    15.099]     LinNumberOfImagePages: 1
[    15.099]     LinRedMaskSize: 8
[    15.099]     LinRedFieldPosition: 16
[    15.099]     LinGreenMaskSize: 8
[    15.099]     LinGreenFieldPosition: 8
[    15.099]     LinBlueMaskSize: 8
[    15.099]     LinBlueFieldPosition: 0
[    15.099]     LinRsvdMaskSize: 8
[    15.099]     LinRsvdFieldPosition: 24
[    15.099]     MaxPixelClock: 229500000
[    15.100] Mode: 117 (1024x768)
[    15.100]     ModeAttributes: 0x3bf
[    15.100]     WinAAttributes: 0x7
[    15.100]     WinBAttributes: 0x0
[    15.100]     WinGranularity: 64
[    15.100]     WinSize: 64
[    15.100]     WinASegment: 0xa000
[    15.100]     WinBSegment: 0x0
[    15.100]     WinFuncPtr: 0xc0009280
[    15.100]     BytesPerScanline: 2048
[    15.100]     XResolution: 1024
[    15.100]     YResolution: 768
[    15.100]     XCharSize: 8
[    15.100]     YCharSize: 16
[    15.100]     NumberOfPlanes: 1
[    15.100]     BitsPerPixel: 16
[    15.100]     NumberOfBanks: 1
[    15.100]     MemoryModel: 6
[    15.100]     BankSize: 0
[    15.100]     NumberOfImages: 1
[    15.100]     RedMaskSize: 5
[    15.100]     RedFieldPosition: 11
[    15.100]     GreenMaskSize: 6
[    15.100]     GreenFieldPosition: 5
[    15.100]     BlueMaskSize: 5
[    15.100]     BlueFieldPosition: 0
[    15.100]     RsvdMaskSize: 0
[    15.100]     RsvdFieldPosition: 0
[    15.100]     DirectColorModeInfo: 0
[    15.100]     PhysBasePtr: 0xfb000000
[    15.100]     LinBytesPerScanLine: 2048
[    15.100]     BnkNumberOfImagePages: 1
[    15.100]     LinNumberOfImagePages: 1
[    15.100]     LinRedMaskSize: 5
[    15.100]     LinRedFieldPosition: 11
[    15.100]     LinGreenMaskSize: 6
[    15.100]     LinGreenFieldPosition: 5
[    15.100]     LinBlueMaskSize: 5
[    15.100]     LinBlueFieldPosition: 0
[    15.100]     LinRsvdMaskSize: 0
[    15.100]     LinRsvdFieldPosition: 0
[    15.100]     MaxPixelClock: 229500000
[    15.102] *Mode: 118 (1024x768)
[    15.102]     ModeAttributes: 0x3bf
[    15.102]     WinAAttributes: 0x7
[    15.102]     WinBAttributes: 0x0
[    15.102]     WinGranularity: 64
[    15.102]     WinSize: 64
[    15.102]     WinASegment: 0xa000
[    15.102]     WinBSegment: 0x0
[    15.102]     WinFuncPtr: 0xc0009280
[    15.102]     BytesPerScanline: 4096
[    15.102]     XResolution: 1024
[    15.102]     YResolution: 768
[    15.102]     XCharSize: 8
[    15.102]     YCharSize: 16
[    15.102]     NumberOfPlanes: 1
[    15.102]     BitsPerPixel: 32
[    15.102]     NumberOfBanks: 1
[    15.102]     MemoryModel: 6
[    15.102]     BankSize: 0
[    15.102]     NumberOfImages: 1
[    15.102]     RedMaskSize: 8
[    15.102]     RedFieldPosition: 16
[    15.102]     GreenMaskSize: 8
[    15.102]     GreenFieldPosition: 8
[    15.102]     BlueMaskSize: 8
[    15.102]     BlueFieldPosition: 0
[    15.102]     RsvdMaskSize: 8
[    15.102]     RsvdFieldPosition: 24
[    15.102]     DirectColorModeInfo: 0
[    15.102]     PhysBasePtr: 0xfb000000
[    15.102]     LinBytesPerScanLine: 4096
[    15.102]     BnkNumberOfImagePages: 1
[    15.102]     LinNumberOfImagePages: 1
[    15.102]     LinRedMaskSize: 8
[    15.102]     LinRedFieldPosition: 16
[    15.102]     LinGreenMaskSize: 8
[    15.102]     LinGreenFieldPosition: 8
[    15.102]     LinBlueMaskSize: 8
[    15.102]     LinBlueFieldPosition: 0
[    15.102]     LinRsvdMaskSize: 8
[    15.102]     LinRsvdFieldPosition: 24
[    15.102]     MaxPixelClock: 229500000
[    15.103] Mode: 11a (1280x1024)
[    15.103]     ModeAttributes: 0x3bf
[    15.103]     WinAAttributes: 0x7
[    15.103]     WinBAttributes: 0x0
[    15.103]     WinGranularity: 64
[    15.103]     WinSize: 64
[    15.103]     WinASegment: 0xa000
[    15.103]     WinBSegment: 0x0
[    15.103]     WinFuncPtr: 0xc0009280
[    15.103]     BytesPerScanline: 2560
[    15.103]     XResolution: 1280
[    15.103]     YResolution: 1024
[    15.103]     XCharSize: 8
[    15.103]     YCharSize: 16
[    15.103]     NumberOfPlanes: 1
[    15.103]     BitsPerPixel: 16
[    15.103]     NumberOfBanks: 1
[    15.103]     MemoryModel: 6
[    15.103]     BankSize: 0
[    15.103]     NumberOfImages: 1
[    15.103]     RedMaskSize: 5
[    15.103]     RedFieldPosition: 11
[    15.103]     GreenMaskSize: 6
[    15.103]     GreenFieldPosition: 5
[    15.103]     BlueMaskSize: 5
[    15.103]     BlueFieldPosition: 0
[    15.103]     RsvdMaskSize: 0
[    15.103]     RsvdFieldPosition: 0
[    15.103]     DirectColorModeInfo: 0
[    15.103]     PhysBasePtr: 0xfb000000
[    15.103]     LinBytesPerScanLine: 2560
[    15.103]     BnkNumberOfImagePages: 1
[    15.103]     LinNumberOfImagePages: 1
[    15.103]     LinRedMaskSize: 5
[    15.103]     LinRedFieldPosition: 11
[    15.103]     LinGreenMaskSize: 6
[    15.103]     LinGreenFieldPosition: 5
[    15.103]     LinBlueMaskSize: 5
[    15.103]     LinBlueFieldPosition: 0
[    15.103]     LinRsvdMaskSize: 0
[    15.103]     LinRsvdFieldPosition: 0
[    15.103]     MaxPixelClock: 229500000
[    15.105] *Mode: 11b (1280x1024)
[    15.105]     ModeAttributes: 0x3bf
[    15.105]     WinAAttributes: 0x7
[    15.105]     WinBAttributes: 0x0
[    15.105]     WinGranularity: 64
[    15.105]     WinSize: 64
[    15.105]     WinASegment: 0xa000
[    15.105]     WinBSegment: 0x0
[    15.105]     WinFuncPtr: 0xc0009280
[    15.105]     BytesPerScanline: 5120
[    15.105]     XResolution: 1280
[    15.105]     YResolution: 1024
[    15.105]     XCharSize: 8
[    15.105]     YCharSize: 16
[    15.105]     NumberOfPlanes: 1
[    15.105]     BitsPerPixel: 32
[    15.105]     NumberOfBanks: 1
[    15.105]     MemoryModel: 6
[    15.105]     BankSize: 0
[    15.105]     NumberOfImages: 1
[    15.105]     RedMaskSize: 8
[    15.105]     RedFieldPosition: 16
[    15.105]     GreenMaskSize: 8
[    15.105]     GreenFieldPosition: 8
[    15.105]     BlueMaskSize: 8
[    15.105]     BlueFieldPosition: 0
[    15.105]     RsvdMaskSize: 8
[    15.105]     RsvdFieldPosition: 24
[    15.105]     DirectColorModeInfo: 0
[    15.105]     PhysBasePtr: 0xfb000000
[    15.105]     LinBytesPerScanLine: 5120
[    15.105]     BnkNumberOfImagePages: 1
[    15.105]     LinNumberOfImagePages: 1
[    15.105]     LinRedMaskSize: 8
[    15.105]     LinRedFieldPosition: 16
[    15.105]     LinGreenMaskSize: 8
[    15.105]     LinGreenFieldPosition: 8
[    15.105]     LinBlueMaskSize: 8
[    15.105]     LinBlueFieldPosition: 0
[    15.105]     LinRsvdMaskSize: 8
[    15.105]     LinRsvdFieldPosition: 24
[    15.105]     MaxPixelClock: 229500000
[    15.106] Mode: 130 (320x200)
[    15.106]     ModeAttributes: 0x3bf
[    15.106]     WinAAttributes: 0x7
[    15.106]     WinBAttributes: 0x0
[    15.106]     WinGranularity: 64
[    15.106]     WinSize: 64
[    15.106]     WinASegment: 0xa000
[    15.106]     WinBSegment: 0x0
[    15.106]     WinFuncPtr: 0xc0009280
[    15.106]     BytesPerScanline: 320
[    15.106]     XResolution: 320
[    15.106]     YResolution: 200
[    15.106]     XCharSize: 8
[    15.106]     YCharSize: 8
[    15.106]     NumberOfPlanes: 1
[    15.106]     BitsPerPixel: 8
[    15.106]     NumberOfBanks: 1
[    15.106]     MemoryModel: 4
[    15.106]     BankSize: 0
[    15.106]     NumberOfImages: 62
[    15.106]     RedMaskSize: 0
[    15.106]     RedFieldPosition: 0
[    15.106]     GreenMaskSize: 0
[    15.106]     GreenFieldPosition: 0
[    15.106]     BlueMaskSize: 0
[    15.106]     BlueFieldPosition: 0
[    15.106]     RsvdMaskSize: 0
[    15.106]     RsvdFieldPosition: 0
[    15.106]     DirectColorModeInfo: 0
[    15.106]     PhysBasePtr: 0xfb000000
[    15.106]     LinBytesPerScanLine: 320
[    15.106]     BnkNumberOfImagePages: 62
[    15.106]     LinNumberOfImagePages: 62
[    15.106]     LinRedMaskSize: 0
[    15.106]     LinRedFieldPosition: 0
[    15.106]     LinGreenMaskSize: 0
[    15.106]     LinGreenFieldPosition: 0
[    15.106]     LinBlueMaskSize: 0
[    15.106]     LinBlueFieldPosition: 0
[    15.106]     LinRsvdMaskSize: 0
[    15.106]     LinRsvdFieldPosition: 0
[    15.106]     MaxPixelClock: 229500000
[    15.108] Mode: 131 (320x400)
[    15.108]     ModeAttributes: 0x3bf
[    15.108]     WinAAttributes: 0x7
[    15.108]     WinBAttributes: 0x0
[    15.108]     WinGranularity: 64
[    15.108]     WinSize: 64
[    15.108]     WinASegment: 0xa000
[    15.108]     WinBSegment: 0x0
[    15.108]     WinFuncPtr: 0xc0009280
[    15.108]     BytesPerScanline: 320
[    15.108]     XResolution: 320
[    15.108]     YResolution: 400
[    15.108]     XCharSize: 8
[    15.108]     YCharSize: 16
[    15.108]     NumberOfPlanes: 1
[    15.108]     BitsPerPixel: 8
[    15.108]     NumberOfBanks: 1
[    15.108]     MemoryModel: 4
[    15.108]     BankSize: 0
[    15.108]     NumberOfImages: 30
[    15.108]     RedMaskSize: 0
[    15.108]     RedFieldPosition: 0
[    15.108]     GreenMaskSize: 0
[    15.108]     GreenFieldPosition: 0
[    15.108]     BlueMaskSize: 0
[    15.108]     BlueFieldPosition: 0
[    15.108]     RsvdMaskSize: 0
[    15.108]     RsvdFieldPosition: 0
[    15.108]     DirectColorModeInfo: 0
[    15.108]     PhysBasePtr: 0xfb000000
[    15.108]     LinBytesPerScanLine: 320
[    15.108]     BnkNumberOfImagePages: 30
[    15.108]     LinNumberOfImagePages: 30
[    15.108]     LinRedMaskSize: 0
[    15.108]     LinRedFieldPosition: 0
[    15.108]     LinGreenMaskSize: 0
[    15.108]     LinGreenFieldPosition: 0
[    15.108]     LinBlueMaskSize: 0
[    15.108]     LinBlueFieldPosition: 0
[    15.108]     LinRsvdMaskSize: 0
[    15.108]     LinRsvdFieldPosition: 0
[    15.108]     MaxPixelClock: 229500000
[    15.109] Mode: 132 (320x400)
[    15.109]     ModeAttributes: 0x3bf
[    15.109]     WinAAttributes: 0x7
[    15.109]     WinBAttributes: 0x0
[    15.109]     WinGranularity: 64
[    15.109]     WinSize: 64
[    15.109]     WinASegment: 0xa000
[    15.109]     WinBSegment: 0x0
[    15.109]     WinFuncPtr: 0xc0009280
[    15.109]     BytesPerScanline: 640
[    15.109]     XResolution: 320
[    15.109]     YResolution: 400
[    15.109]     XCharSize: 8
[    15.109]     YCharSize: 16
[    15.109]     NumberOfPlanes: 1
[    15.109]     BitsPerPixel: 16
[    15.109]     NumberOfBanks: 1
[    15.109]     MemoryModel: 6
[    15.109]     BankSize: 0
[    15.109]     NumberOfImages: 14
[    15.109]     RedMaskSize: 5
[    15.109]     RedFieldPosition: 11
[    15.109]     GreenMaskSize: 6
[    15.109]     GreenFieldPosition: 5
[    15.109]     BlueMaskSize: 5
[    15.109]     BlueFieldPosition: 0
[    15.109]     RsvdMaskSize: 0
[    15.109]     RsvdFieldPosition: 0
[    15.109]     DirectColorModeInfo: 0
[    15.109]     PhysBasePtr: 0xfb000000
[    15.109]     LinBytesPerScanLine: 640
[    15.109]     BnkNumberOfImagePages: 14
[    15.109]     LinNumberOfImagePages: 14
[    15.109]     LinRedMaskSize: 5
[    15.109]     LinRedFieldPosition: 11
[    15.109]     LinGreenMaskSize: 6
[    15.109]     LinGreenFieldPosition: 5
[    15.109]     LinBlueMaskSize: 5
[    15.109]     LinBlueFieldPosition: 0
[    15.109]     LinRsvdMaskSize: 0
[    15.109]     LinRsvdFieldPosition: 0
[    15.109]     MaxPixelClock: 229500000
[    15.111] *Mode: 133 (320x400)
[    15.111]     ModeAttributes: 0x3bf
[    15.111]     WinAAttributes: 0x7
[    15.111]     WinBAttributes: 0x0
[    15.111]     WinGranularity: 64
[    15.111]     WinSize: 64
[    15.111]     WinASegment: 0xa000
[    15.111]     WinBSegment: 0x0
[    15.111]     WinFuncPtr: 0xc0009280
[    15.111]     BytesPerScanline: 1280
[    15.111]     XResolution: 320
[    15.111]     YResolution: 400
[    15.111]     XCharSize: 8
[    15.111]     YCharSize: 16
[    15.111]     NumberOfPlanes: 1
[    15.111]     BitsPerPixel: 32
[    15.111]     NumberOfBanks: 1
[    15.111]     MemoryModel: 6
[    15.111]     BankSize: 0
[    15.111]     NumberOfImages: 6
[    15.111]     RedMaskSize: 8
[    15.111]     RedFieldPosition: 16
[    15.111]     GreenMaskSize: 8
[    15.111]     GreenFieldPosition: 8
[    15.111]     BlueMaskSize: 8
[    15.111]     BlueFieldPosition: 0
[    15.111]     RsvdMaskSize: 8
[    15.111]     RsvdFieldPosition: 24
[    15.111]     DirectColorModeInfo: 0
[    15.111]     PhysBasePtr: 0xfb000000
[    15.111]     LinBytesPerScanLine: 1280
[    15.111]     BnkNumberOfImagePages: 6
[    15.111]     LinNumberOfImagePages: 6
[    15.111]     LinRedMaskSize: 8
[    15.111]     LinRedFieldPosition: 16
[    15.111]     LinGreenMaskSize: 8
[    15.111]     LinGreenFieldPosition: 8
[    15.111]     LinBlueMaskSize: 8
[    15.111]     LinBlueFieldPosition: 0
[    15.111]     LinRsvdMaskSize: 8
[    15.111]     LinRsvdFieldPosition: 24
[    15.111]     MaxPixelClock: 229500000
[    15.112] Mode: 134 (320x240)
[    15.112]     ModeAttributes: 0x3bf
[    15.112]     WinAAttributes: 0x7
[    15.112]     WinBAttributes: 0x0
[    15.112]     WinGranularity: 64
[    15.112]     WinSize: 64
[    15.112]     WinASegment: 0xa000
[    15.112]     WinBSegment: 0x0
[    15.112]     WinFuncPtr: 0xc0009280
[    15.112]     BytesPerScanline: 320
[    15.112]     XResolution: 320
[    15.112]     YResolution: 240
[    15.112]     XCharSize: 8
[    15.112]     YCharSize: 8
[    15.112]     NumberOfPlanes: 1
[    15.112]     BitsPerPixel: 8
[    15.112]     NumberOfBanks: 1
[    15.112]     MemoryModel: 4
[    15.112]     BankSize: 0
[    15.112]     NumberOfImages: 30
[    15.112]     RedMaskSize: 0
[    15.112]     RedFieldPosition: 0
[    15.112]     GreenMaskSize: 0
[    15.112]     GreenFieldPosition: 0
[    15.112]     BlueMaskSize: 0
[    15.112]     BlueFieldPosition: 0
[    15.112]     RsvdMaskSize: 0
[    15.112]     RsvdFieldPosition: 0
[    15.112]     DirectColorModeInfo: 0
[    15.112]     PhysBasePtr: 0xfb000000
[    15.112]     LinBytesPerScanLine: 320
[    15.112]     BnkNumberOfImagePages: 30
[    15.112]     LinNumberOfImagePages: 30
[    15.112]     LinRedMaskSize: 0
[    15.112]     LinRedFieldPosition: 0
[    15.112]     LinGreenMaskSize: 0
[    15.112]     LinGreenFieldPosition: 0
[    15.112]     LinBlueMaskSize: 0
[    15.112]     LinBlueFieldPosition: 0
[    15.112]     LinRsvdMaskSize: 0
[    15.112]     LinRsvdFieldPosition: 0
[    15.112]     MaxPixelClock: 229500000
[    15.114] Mode: 135 (320x240)
[    15.114]     ModeAttributes: 0x3bf
[    15.114]     WinAAttributes: 0x7
[    15.114]     WinBAttributes: 0x0
[    15.114]     WinGranularity: 64
[    15.114]     WinSize: 64
[    15.114]     WinASegment: 0xa000
[    15.114]     WinBSegment: 0x0
[    15.114]     WinFuncPtr: 0xc0009280
[    15.114]     BytesPerScanline: 640
[    15.114]     XResolution: 320
[    15.114]     YResolution: 240
[    15.114]     XCharSize: 8
[    15.114]     YCharSize: 8
[    15.114]     NumberOfPlanes: 1
[    15.114]     BitsPerPixel: 16
[    15.114]     NumberOfBanks: 1
[    15.114]     MemoryModel: 6
[    15.114]     BankSize: 0
[    15.114]     NumberOfImages: 19
[    15.114]     RedMaskSize: 5
[    15.114]     RedFieldPosition: 11
[    15.114]     GreenMaskSize: 6
[    15.114]     GreenFieldPosition: 5
[    15.114]     BlueMaskSize: 5
[    15.114]     BlueFieldPosition: 0
[    15.114]     RsvdMaskSize: 0
[    15.114]     RsvdFieldPosition: 0
[    15.114]     DirectColorModeInfo: 0
[    15.114]     PhysBasePtr: 0xfb000000
[    15.114]     LinBytesPerScanLine: 640
[    15.114]     BnkNumberOfImagePages: 19
[    15.114]     LinNumberOfImagePages: 19
[    15.114]     LinRedMaskSize: 5
[    15.114]     LinRedFieldPosition: 11
[    15.114]     LinGreenMaskSize: 6
[    15.114]     LinGreenFieldPosition: 5
[    15.114]     LinBlueMaskSize: 5
[    15.114]     LinBlueFieldPosition: 0
[    15.114]     LinRsvdMaskSize: 0
[    15.114]     LinRsvdFieldPosition: 0
[    15.114]     MaxPixelClock: 229500000
[    15.115] *Mode: 136 (320x240)
[    15.115]     ModeAttributes: 0x3bf
[    15.115]     WinAAttributes: 0x7
[    15.115]     WinBAttributes: 0x0
[    15.115]     WinGranularity: 64
[    15.115]     WinSize: 64
[    15.115]     WinASegment: 0xa000
[    15.115]     WinBSegment: 0x0
[    15.115]     WinFuncPtr: 0xc0009280
[    15.115]     BytesPerScanline: 1280
[    15.115]     XResolution: 320
[    15.115]     YResolution: 240
[    15.115]     XCharSize: 8
[    15.115]     YCharSize: 8
[    15.115]     NumberOfPlanes: 1
[    15.115]     BitsPerPixel: 32
[    15.115]     NumberOfBanks: 1
[    15.115]     MemoryModel: 6
[    15.115]     BankSize: 0
[    15.115]     NumberOfImages: 10
[    15.115]     RedMaskSize: 8
[    15.115]     RedFieldPosition: 16
[    15.115]     GreenMaskSize: 8
[    15.115]     GreenFieldPosition: 8
[    15.115]     BlueMaskSize: 8
[    15.115]     BlueFieldPosition: 0
[    15.115]     RsvdMaskSize: 8
[    15.115]     RsvdFieldPosition: 24
[    15.115]     DirectColorModeInfo: 0
[    15.115]     PhysBasePtr: 0xfb000000
[    15.115]     LinBytesPerScanLine: 1280
[    15.115]     BnkNumberOfImagePages: 10
[    15.115]     LinNumberOfImagePages: 10
[    15.115]     LinRedMaskSize: 8
[    15.115]     LinRedFieldPosition: 16
[    15.115]     LinGreenMaskSize: 8
[    15.115]     LinGreenFieldPosition: 8
[    15.115]     LinBlueMaskSize: 8
[    15.115]     LinBlueFieldPosition: 0
[    15.115]     LinRsvdMaskSize: 8
[    15.115]     LinRsvdFieldPosition: 24
[    15.115]     MaxPixelClock: 229500000
[    15.117] Mode: 13d (640x400)
[    15.117]     ModeAttributes: 0x3bf
[    15.117]     WinAAttributes: 0x7
[    15.117]     WinBAttributes: 0x0
[    15.117]     WinGranularity: 64
[    15.117]     WinSize: 64
[    15.117]     WinASegment: 0xa000
[    15.117]     WinBSegment: 0x0
[    15.117]     WinFuncPtr: 0xc0009280
[    15.117]     BytesPerScanline: 1280
[    15.117]     XResolution: 640
[    15.117]     YResolution: 400
[    15.117]     XCharSize: 8
[    15.117]     YCharSize: 16
[    15.117]     NumberOfPlanes: 1
[    15.117]     BitsPerPixel: 16
[    15.117]     NumberOfBanks: 1
[    15.117]     MemoryModel: 6
[    15.117]     BankSize: 0
[    15.117]     NumberOfImages: 6
[    15.117]     RedMaskSize: 5
[    15.117]     RedFieldPosition: 11
[    15.117]     GreenMaskSize: 6
[    15.117]     GreenFieldPosition: 5
[    15.117]     BlueMaskSize: 5
[    15.117]     BlueFieldPosition: 0
[    15.117]     RsvdMaskSize: 0
[    15.117]     RsvdFieldPosition: 0
[    15.117]     DirectColorModeInfo: 0
[    15.117]     PhysBasePtr: 0xfb000000
[    15.117]     LinBytesPerScanLine: 1280
[    15.117]     BnkNumberOfImagePages: 6
[    15.117]     LinNumberOfImagePages: 6
[    15.117]     LinRedMaskSize: 5
[    15.117]     LinRedFieldPosition: 11
[    15.117]     LinGreenMaskSize: 6
[    15.117]     LinGreenFieldPosition: 5
[    15.117]     LinBlueMaskSize: 5
[    15.117]     LinBlueFieldPosition: 0
[    15.117]     LinRsvdMaskSize: 0
[    15.117]     LinRsvdFieldPosition: 0
[    15.117]     MaxPixelClock: 229500000
[    15.118] *Mode: 13e (640x400)
[    15.118]     ModeAttributes: 0x3bf
[    15.118]     WinAAttributes: 0x7
[    15.118]     WinBAttributes: 0x0
[    15.118]     WinGranularity: 64
[    15.118]     WinSize: 64
[    15.118]     WinASegment: 0xa000
[    15.118]     WinBSegment: 0x0
[    15.118]     WinFuncPtr: 0xc0009280
[    15.118]     BytesPerScanline: 2560
[    15.118]     XResolution: 640
[    15.118]     YResolution: 400
[    15.118]     XCharSize: 8
[    15.118]     YCharSize: 16
[    15.118]     NumberOfPlanes: 1
[    15.118]     BitsPerPixel: 32
[    15.118]     NumberOfBanks: 1
[    15.118]     MemoryModel: 6
[    15.118]     BankSize: 0
[    15.118]     NumberOfImages: 2
[    15.118]     RedMaskSize: 8
[    15.118]     RedFieldPosition: 16
[    15.118]     GreenMaskSize: 8
[    15.118]     GreenFieldPosition: 8
[    15.118]     BlueMaskSize: 8
[    15.118]     BlueFieldPosition: 0
[    15.118]     RsvdMaskSize: 8
[    15.118]     RsvdFieldPosition: 24
[    15.118]     DirectColorModeInfo: 0
[    15.118]     PhysBasePtr: 0xfb000000
[    15.118]     LinBytesPerScanLine: 2560
[    15.118]     BnkNumberOfImagePages: 2
[    15.118]     LinNumberOfImagePages: 2
[    15.118]     LinRedMaskSize: 8
[    15.118]     LinRedFieldPosition: 16
[    15.118]     LinGreenMaskSize: 8
[    15.118]     LinGreenFieldPosition: 8
[    15.118]     LinBlueMaskSize: 8
[    15.118]     LinBlueFieldPosition: 0
[    15.118]     LinRsvdMaskSize: 8
[    15.118]     LinRsvdFieldPosition: 24
[    15.118]     MaxPixelClock: 229500000
[    15.120] Mode: 160 (1280x800)
[    15.120]     ModeAttributes: 0x3bf
[    15.120]     WinAAttributes: 0x7
[    15.120]     WinBAttributes: 0x0
[    15.120]     WinGranularity: 64
[    15.120]     WinSize: 64
[    15.120]     WinASegment: 0xa000
[    15.120]     WinBSegment: 0x0
[    15.120]     WinFuncPtr: 0xc0009280
[    15.120]     BytesPerScanline: 1280
[    15.120]     XResolution: 1280
[    15.120]     YResolution: 800
[    15.120]     XCharSize: 8
[    15.120]     YCharSize: 16
[    15.120]     NumberOfPlanes: 1
[    15.120]     BitsPerPixel: 8
[    15.120]     NumberOfBanks: 1
[    15.120]     MemoryModel: 4
[    15.120]     BankSize: 0
[    15.120]     NumberOfImages: 2
[    15.120]     RedMaskSize: 0
[    15.120]     RedFieldPosition: 0
[    15.120]     GreenMaskSize: 0
[    15.120]     GreenFieldPosition: 0
[    15.120]     BlueMaskSize: 0
[    15.120]     BlueFieldPosition: 0
[    15.120]     RsvdMaskSize: 0
[    15.120]     RsvdFieldPosition: 0
[    15.120]     DirectColorModeInfo: 0
[    15.120]     PhysBasePtr: 0xfb000000
[    15.120]     LinBytesPerScanLine: 1280
[    15.120]     BnkNumberOfImagePages: 2
[    15.120]     LinNumberOfImagePages: 2
[    15.120]     LinRedMaskSize: 0
[    15.120]     LinRedFieldPosition: 0
[    15.120]     LinGreenMaskSize: 0
[    15.120]     LinGreenFieldPosition: 0
[    15.120]     LinBlueMaskSize: 0
[    15.120]     LinBlueFieldPosition: 0
[    15.120]     LinRsvdMaskSize: 0
[    15.120]     LinRsvdFieldPosition: 0
[    15.120]     MaxPixelClock: 229500000
[    15.121] *Mode: 161 (1280x800)
[    15.121]     ModeAttributes: 0x3bf
[    15.121]     WinAAttributes: 0x7
[    15.121]     WinBAttributes: 0x0
[    15.121]     WinGranularity: 64
[    15.121]     WinSize: 64
[    15.121]     WinASegment: 0xa000
[    15.121]     WinBSegment: 0x0
[    15.121]     WinFuncPtr: 0xc0009280
[    15.121]     BytesPerScanline: 5120
[    15.121]     XResolution: 1280
[    15.121]     YResolution: 800
[    15.121]     XCharSize: 8
[    15.121]     YCharSize: 16
[    15.121]     NumberOfPlanes: 1
[    15.121]     BitsPerPixel: 32
[    15.121]     NumberOfBanks: 1
[    15.121]     MemoryModel: 6
[    15.122]     BankSize: 0
[    15.122]     NumberOfImages: 1
[    15.122]     RedMaskSize: 8
[    15.122]     RedFieldPosition: 16
[    15.122]     GreenMaskSize: 8
[    15.122]     GreenFieldPosition: 8
[    15.122]     BlueMaskSize: 8
[    15.122]     BlueFieldPosition: 0
[    15.122]     RsvdMaskSize: 8
[    15.122]     RsvdFieldPosition: 24
[    15.122]     DirectColorModeInfo: 0
[    15.122]     PhysBasePtr: 0xfb000000
[    15.122]     LinBytesPerScanLine: 5120
[    15.122]     BnkNumberOfImagePages: 1
[    15.122]     LinNumberOfImagePages: 1
[    15.122]     LinRedMaskSize: 8
[    15.122]     LinRedFieldPosition: 16
[    15.122]     LinGreenMaskSize: 8
[    15.122]     LinGreenFieldPosition: 8
[    15.122]     LinBlueMaskSize: 8
[    15.122]     LinBlueFieldPosition: 0
[    15.122]     LinRsvdMaskSize: 8
[    15.122]     LinRsvdFieldPosition: 24
[    15.122]     MaxPixelClock: 229500000
[    15.123] Mode: 162 (768x480)
[    15.123]     ModeAttributes: 0x3bf
[    15.123]     WinAAttributes: 0x7
[    15.123]     WinBAttributes: 0x0
[    15.123]     WinGranularity: 64
[    15.123]     WinSize: 64
[    15.123]     WinASegment: 0xa000
[    15.123]     WinBSegment: 0x0
[    15.123]     WinFuncPtr: 0xc0009280
[    15.123]     BytesPerScanline: 768
[    15.123]     XResolution: 768
[    15.123]     YResolution: 480
[    15.123]     XCharSize: 8
[    15.123]     YCharSize: 16
[    15.123]     NumberOfPlanes: 1
[    15.123]     BitsPerPixel: 8
[    15.123]     NumberOfBanks: 1
[    15.123]     MemoryModel: 4
[    15.123]     BankSize: 0
[    15.123]     NumberOfImages: 8
[    15.123]     RedMaskSize: 0
[    15.123]     RedFieldPosition: 0
[    15.123]     GreenMaskSize: 0
[    15.123]     GreenFieldPosition: 0
[    15.123]     BlueMaskSize: 0
[    15.123]     BlueFieldPosition: 0
[    15.123]     RsvdMaskSize: 0
[    15.123]     RsvdFieldPosition: 0
[    15.123]     DirectColorModeInfo: 0
[    15.123]     PhysBasePtr: 0xfb000000
[    15.123]     LinBytesPerScanLine: 768
[    15.123]     BnkNumberOfImagePages: 8
[    15.123]     LinNumberOfImagePages: 8
[    15.123]     LinRedMaskSize: 0
[    15.123]     LinRedFieldPosition: 0
[    15.123]     LinGreenMaskSize: 0
[    15.123]     LinGreenFieldPosition: 0
[    15.123]     LinBlueMaskSize: 0
[    15.123]     LinBlueFieldPosition: 0
[    15.123]     LinRsvdMaskSize: 0
[    15.123]     LinRsvdFieldPosition: 0
[    15.123]     MaxPixelClock: 229500000
[    15.125] *Mode: 17b (1280x720)
[    15.125]     ModeAttributes: 0x3bf
[    15.125]     WinAAttributes: 0x7
[    15.125]     WinBAttributes: 0x0
[    15.125]     WinGranularity: 64
[    15.125]     WinSize: 64
[    15.125]     WinASegment: 0xa000
[    15.125]     WinBSegment: 0x0
[    15.125]     WinFuncPtr: 0xc0009280
[    15.125]     BytesPerScanline: 5120
[    15.125]     XResolution: 1280
[    15.125]     YResolution: 720
[    15.125]     XCharSize: 8
[    15.125]     YCharSize: 16
[    15.125]     NumberOfPlanes: 1
[    15.125]     BitsPerPixel: 32
[    15.125]     NumberOfBanks: 1
[    15.125]     MemoryModel: 6
[    15.125]     BankSize: 0
[    15.125]     NumberOfImages: 1
[    15.125]     RedMaskSize: 8
[    15.125]     RedFieldPosition: 16
[    15.125]     GreenMaskSize: 8
[    15.125]     GreenFieldPosition: 8
[    15.125]     BlueMaskSize: 8
[    15.125]     BlueFieldPosition: 0
[    15.125]     RsvdMaskSize: 8
[    15.125]     RsvdFieldPosition: 24
[    15.125]     DirectColorModeInfo: 0
[    15.125]     PhysBasePtr: 0xfb000000
[    15.125]     LinBytesPerScanLine: 5120
[    15.125]     BnkNumberOfImagePages: 1
[    15.125]     LinNumberOfImagePages: 1
[    15.125]     LinRedMaskSize: 8
[    15.125]     LinRedFieldPosition: 16
[    15.125]     LinGreenMaskSize: 8
[    15.125]     LinGreenFieldPosition: 8
[    15.125]     LinBlueMaskSize: 8
[    15.125]     LinBlueFieldPosition: 0
[    15.125]     LinRsvdMaskSize: 8
[    15.125]     LinRsvdFieldPosition: 24
[    15.125]     MaxPixelClock: 229500000
[    15.125] 
[    15.125] (II) VESA(0): Total Memory: 224 64KB banks (14336kB)
[    15.125] (II) VESA(0): <default monitor>: Using hsync range of 31.00-83.00 kHz
[    15.125] (II) VESA(0): <default monitor>: Using vrefresh range of 50.00-76.00 Hz
[    15.125] (II) VESA(0): <default monitor>: Using maximum pixel clock of 175.00 MHz
[    15.125] (WW) VESA(0): Unable to estimate virtual size
[    15.126] (II) VESA(0): Not using built-in mode "1280x800" (no mode of this name)
[    15.126] (II) VESA(0): Not using built-in mode "1280x720" (no mode of this name)
[    15.128] (II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
[    15.128] (II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
[    15.128] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[    15.128] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[    15.128] (--) VESA(0): Virtual size is 1280x1024 (pitch 1280)
[    15.128] (**) VESA(0): *Built-in mode "1280x1024"
[    15.128] (**) VESA(0): *Built-in mode "1024x768"
[    15.128] (**) VESA(0): *Built-in mode "800x600"
[    15.128] (**) VESA(0): *Built-in mode "640x480"
[    15.128] (**) VESA(0): Display dimensions: (480, 270) mm
[    15.128] (**) VESA(0): DPI set to (67, 96)
[    15.128] (**) VESA(0): Using "Shadow Framebuffer"
[    15.128] (II) Loading sub module "shadow"
[    15.128] (II) LoadModule: "shadow"
[    15.128] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    15.224] (II) Module shadow: vendor="X.Org Foundation"
[    15.224]     compiled for 1.10.4, module version = 1.1.0
[    15.224]     ABI class: X.Org ANSI C Emulation, version 0.4
[    15.224] (II) Loading sub module "fb"
[    15.224] (II) LoadModule: "fb"
[    15.224] (II) Loading /usr/lib/xorg/modules/libfb.so
[    15.241] (II) Module fb: vendor="X.Org Foundation"
[    15.241]     compiled for 1.10.4, module version = 1.0.0
[    15.241]     ABI class: X.Org ANSI C Emulation, version 0.4
[    15.241] (II) UnloadModule: "fbdev"
[    15.242] (II) Unloading fbdev
[    15.242] (II) UnloadModule: "fbdevhw"
[    15.242] (II) Unloading fbdevhw
[    15.242] (==) Depth 24 pixmap format is 32 bpp
[    15.242] (II) Loading sub module "int10"
[    15.242] (II) LoadModule: "int10"
[    15.242] (II) Loading /usr/lib/xorg/modules/libint10.so
[    15.242] (II) Module int10: vendor="X.Org Foundation"
[    15.242]     compiled for 1.10.4, module version = 1.0.0
[    15.242]     ABI class: X.Org Video Driver, version 10.0
[    15.242] (II) VESA(0): initializing int10
[    15.242] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    15.295] (II) VESA(0): VESA BIOS detected
[    15.295] (II) VESA(0): VESA VBE Version 3.0
[    15.295] (II) VESA(0): VESA VBE Total Mem: 14336 kB
[    15.295] (II) VESA(0): VESA VBE OEM: NVIDIA
[    15.295] (II) VESA(0): VESA VBE OEM Software Rev: 98.148
[    15.295] (II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[    15.295] (II) VESA(0): VESA VBE OEM Product: G96 Board - 07290040
[    15.295] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[    15.297] (II) VESA(0): virtual address = 0xb63de000,
    physical address = 0xfb000000, size = 14680064
[    15.300] (II) VESA(0): Setting up VESA Mode 0x11B (1280x1024)
[    15.494] (==) VESA(0): Default visual is TrueColor
[    15.588] (==) VESA(0): Backing store disabled
[    15.588] (==) VESA(0): DPMS enabled
[    15.588] (==) RandR enabled
[    15.588] (II) Initializing built-in extension Generic Event Extension
[    15.588] (II) Initializing built-in extension SHAPE
[    15.588] (II) Initializing built-in extension MIT-SHM
[    15.588] (II) Initializing built-in extension XInputExtension
[    15.588] (II) Initializing built-in extension XTEST
[    15.588] (II) Initializing built-in extension BIG-REQUESTS
[    15.588] (II) Initializing built-in extension SYNC
[    15.588] (II) Initializing built-in extension XKEYBOARD
[    15.588] (II) Initializing built-in extension XC-MISC
[    15.588] (II) Initializing built-in extension SECURITY
[    15.588] (II) Initializing built-in extension XINERAMA
[    15.588] (II) Initializing built-in extension XFIXES
[    15.588] (II) Initializing built-in extension RENDER
[    15.588] (II) Initializing built-in extension RANDR
[    15.588] (II) Initializing built-in extension COMPOSITE
[    15.588] (II) Initializing built-in extension DAMAGE
[    15.588] (II) Initializing built-in extension GESTURE
[    15.606] (II) AIGLX: Screen 0 is not DRI2 capable
[    15.606] (II) AIGLX: Screen 0 is not DRI capable
[    15.606] (II) AIGLX: Trying DRI driver /usr/lib/i386-linux-gnu/dri/swrast_dri.so
[    15.728] (II) AIGLX: Loaded and initialized swrast
[    15.728] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    16.035] (II) XKB: generating xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    16.256] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    16.256] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.256] (II) LoadModule: "evdev"
[    16.256] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.301] (II) Module evdev: vendor="X.Org Foundation"
[    16.301]     compiled for 1.10.2, module version = 2.6.0
[    16.301]     Module class: X.Org XInput Driver
[    16.301]     ABI class: X.Org XInput driver, version 12.3
[    16.301] (II) Using input driver 'evdev' for 'Power Button'
[    16.301] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.301] (**) Power Button: always reports core events
[    16.301] (**) Power Button: Device: "/dev/input/event1"
[    16.301] (--) Power Button: Found keys
[    16.301] (II) Power Button: Configuring as keyboard
[    16.301] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    16.301] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    16.301] (**) Option "xkb_rules" "evdev"
[    16.301] (**) Option "xkb_model" "pc105"
[    16.301] (**) Option "xkb_layout" "it"
[    16.303] (II) XKB: generating xkmfile /var/lib/xkb/server-3781FECB9CB8D26EE03343DB2C93394EA704B98F.xkm
[    16.331] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    16.331] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.331] (II) Using input driver 'evdev' for 'Power Button'
[    16.331] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.331] (**) Power Button: always reports core events
[    16.331] (**) Power Button: Device: "/dev/input/event0"
[    16.331] (--) Power Button: Found keys
[    16.331] (II) Power Button: Configuring as keyboard
[    16.331] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    16.331] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    16.331] (**) Option "xkb_rules" "evdev"
[    16.331] (**) Option "xkb_model" "pc105"
[    16.331] (**) Option "xkb_layout" "it"
[    16.335] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event3)
[    16.335] (**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    16.335] (II) Using input driver 'evdev' for 'Logitech USB Optical Mouse'
[    16.335] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.335] (**) Logitech USB Optical Mouse: always reports core events
[    16.335] (**) Logitech USB Optical Mouse: Device: "/dev/input/event3"
[    16.335] (--) Logitech USB Optical Mouse: Found 3 mouse buttons
[    16.335] (--) Logitech USB Optical Mouse: Found scroll wheel(s)
[    16.335] (--) Logitech USB Optical Mouse: Found relative axes
[    16.335] (--) Logitech USB Optical Mouse: Found x and y relative axes
[    16.335] (II) Logitech USB Optical Mouse: Configuring as mouse
[    16.335] (II) Logitech USB Optical Mouse: Adding scrollwheel support
[    16.335] (**) Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    16.335] (**) Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    16.335] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input3/event3"
[    16.335] (II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE)
[    16.335] (II) Logitech USB Optical Mouse: initialized for relative axes.
[    16.335] (**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
[    16.335] (**) Logitech USB Optical Mouse: (accel) acceleration profile 0
[    16.335] (**) Logitech USB Optical Mouse: (accel) acceleration factor: 2.000
[    16.335] (**) Logitech USB Optical Mouse: (accel) acceleration threshold: 4
[    16.336] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse0)
[    16.336] (II) No input driver/identifier specified (ignoring)
[    16.338] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    16.338] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    16.339] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    16.339] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.339] (**) AT Translated Set 2 keyboard: always reports core events
[    16.339] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    16.339] (--) AT Translated Set 2 keyboard: Found keys
[    16.339] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    16.339] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    16.339] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    16.339] (**) Option "xkb_rules" "evdev"
[    16.339] (**) Option "xkb_model" "pc105"
[    16.339] (**) Option "xkb_layout" "it"
[    37.727] (II) XKB: generating xkmfile /var/lib/xkb/server-F852E81D2903E78D24267D023F61A4200171B031.xkm
```


After downgrade and upgrade, my system now is not fully updated (74 packages to update) and from additional driver no NVIDIA graphic driver is installed or active...

mmmhhh..what now??

Thank you very much!!

---

### Post by MAFoElffen on 2011-10-23
> **Krakken said:**
> NV driver eh?? I did not note that before. 
I cannot find X-swat repo's in my source.list:

After downgrade and upgrade, my system now is not fully updated (74 packages to update) and from additional driver no NVIDIA graphic driver is installed or active...

mmmhhh..what now??

Thank you very much!!Correct. There was no PPA's at all.

Go to additional drivers and try to install the nvidia-current... if that doesn't work, all you have to do to get back is to rename the xorg.conf (to anything other than).

---

### Post by Krakken on 2011-10-24
Here i'm back,
when I try to install the current driver I get the following error:

Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

and here is the output of the file:

```
2011-10-23 23:13:45,944 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c>
2011-10-23 23:13:47,284 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-10-23 23:13:47,288 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-10-23 23:13:47,290 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-10-23 23:13:47,309 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-10-23 23:13:47,324 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:13:47,324 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-10-23 23:13:47,339 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-10-23 23:13:47,340 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-10-23 23:13:47,342 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:13:47,343 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-10-23 23:13:47,343 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-10-23 23:13:47,343 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-10-23 23:13:47,360 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-10-23 23:13:47,360 ERROR: could not open /proc/asound/cards: [Errno 2] No such file or directory: '/proc/asound/cards'
2011-10-23 23:13:47,379 DEBUG: Software modem not available
2011-10-23 23:13:47,379 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-10-23 23:13:47,382 WARNING: modinfo for module dvb_usb failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:13:47,393 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-10-23 23:13:47,393 DEBUG: Firmware for DVB cards not available
2011-10-23 23:13:47,393 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-10-23 23:13:47,407 WARNING: modinfo for module wl failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:13:47,421 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-10-23 23:13:47,422 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-10-23 23:13:47,422 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-10-23 23:13:47,458 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:13:47,460 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-10-23 23:13:47,461 DEBUG: nvidia.available: falling back to default
2011-10-23 23:13:47,589 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-23 23:13:47,596 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:13:47,599 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-10-23 23:13:47,599 DEBUG: nvidia.available: falling back to default
2011-10-23 23:13:47,636 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-23 23:13:47,638 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:13:47,640 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-10-23 23:13:47,640 DEBUG: nvidia.available: falling back to default
2011-10-23 23:13:47,672 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-23 23:13:47,672 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-10-23 23:13:47,683 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:13:47,685 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-10-23 23:13:47,685 DEBUG: nvidia.available: falling back to default
2011-10-23 23:13:47,720 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-23 23:13:47,722 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:13:47,730 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-10-23 23:13:47,730 DEBUG: nvidia.available: falling back to default
2011-10-23 23:13:47,764 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-23 23:13:47,768 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:13:47,771 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-10-23 23:13:47,771 DEBUG: nvidia.available: falling back to default
2011-10-23 23:13:47,800 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-23 23:13:47,800 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-10-23 23:13:47,807 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:13:47,810 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-10-23 23:13:47,811 DEBUG: fglrx.available: falling back to default
2011-10-23 23:13:47,842 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-23 23:13:47,846 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:13:47,850 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-10-23 23:13:47,850 DEBUG: fglrx.available: falling back to default
2011-10-23 23:13:47,879 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-10-23 23:13:47,879 DEBUG: all custom handlers loaded
2011-10-23 23:13:47,879 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001043sd000082D4bc0Csc03i00')
2011-10-23 23:13:47,879 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001043sd000082D4bc0Csc05i00')
2011-10-23 23:13:47,879 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'pci:v00008086d00003A18sv00001043sd000082D4bc06sc01i00')
2011-10-23 23:13:47,879 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-23 23:13:47,879 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'acpi:PNP0800:')
2011-10-23 23:13:47,879 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001043sd000082D4bc0Csc03i00')
2011-10-23 23:13:47,879 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-23 23:13:47,879 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-10-23 23:13:47,879 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'pci:v00008086d00003A26sv00001043sd000082D4bc01sc01i85')
2011-10-23 23:13:47,880 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-10-23 23:13:47,880 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-23 23:13:47,880 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'platform:pcspkr')
2011-10-23 23:13:47,880 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001043sd000082D4bc0Csc03i00')
2011-10-23 23:13:47,880 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'platform:eisa')
2011-10-23 23:13:47,880 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'pci:v00008086d00003A20sv00001043sd000082D4bc01sc01i8f')
2011-10-23 23:13:47,880 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'pci:v00008086d00002E20sv00001043sd000082D3bc06sc00i00')
2011-10-23 23:13:47,880 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'acpi:PNP0501:')
2011-10-23 23:13:47,880 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-23 23:13:47,880 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'pci:v000010DEd00000641sv00001043sd000082BEbc03sc00i00')
2011-10-23 23:13:48,079 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2011-10-23 23:13:48,242 DEBUG: NVidia(nvidia_current).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:13:48,242 DEBUG: nvidia_current is not the alternative in use
2011-10-23 23:13:48,080 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-10-23 23:13:48,244 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:13:48,247 DEBUG: nvidia.available: falling back to default
2011-10-23 23:13:48,275 DEBUG: NVidia(nvidia_current).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:13:48,275 DEBUG: nvidia_current is not the alternative in use
2011-10-23 23:13:48,261 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-10-23 23:13:48,275 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_173_updates', 'package': 'nvidia-173-updates'}
2011-10-23 23:13:48,288 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:13:48,288 DEBUG: nvidia_173_updates is not the alternative in use
2011-10-23 23:13:48,275 DEBUG: found match in handler pool xorg:nvidia_173_updates([NvidiaDriver173Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-23 23:13:48,290 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:13:48,292 DEBUG: nvidia.available: falling back to default
2011-10-23 23:13:48,320 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:13:48,320 DEBUG: nvidia_173_updates is not the alternative in use
2011-10-23 23:13:48,307 DEBUG: got handler xorg:nvidia_173_updates([NvidiaDriver173Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-23 23:13:48,321 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_173', 'package': 'nvidia-173'}
2011-10-23 23:13:48,333 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:13:48,333 DEBUG: nvidia_173 is not the alternative in use
2011-10-23 23:13:48,321 DEBUG: found match in handler pool xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-10-23 23:13:48,335 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:13:48,337 DEBUG: nvidia.available: falling back to default
2011-10-23 23:13:48,361 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:13:48,361 DEBUG: nvidia_173 is not the alternative in use
2011-10-23 23:13:48,348 DEBUG: got handler xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-10-23 23:13:48,362 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2011-10-23 23:13:48,374 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:13:48,374 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-23 23:13:48,362 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-23 23:13:48,376 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:13:48,378 DEBUG: nvidia.available: falling back to default
2011-10-23 23:13:48,402 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:13:48,402 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-23 23:13:48,389 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-23 23:13:48,402 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'acpi:ATK0110:')
2011-10-23 23:13:48,402 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-23 23:13:48,402 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-23 23:13:48,403 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'acpi:PNP0700:')
2011-10-23 23:13:48,403 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'usb:v148Fp2573d0001dc00dsc00dp00icFFiscFFipFF')
2011-10-23 23:13:48,403 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001043sd00008346bc04sc03i00')
2011-10-23 23:13:48,403 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001043sd000082D4bc06sc04i01')
2011-10-23 23:13:48,403 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'usb:v046DpC018d4301dc00dsc00dp00ic03isc01ip02')
2011-10-23 23:13:48,403 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001043sd000082D4bc0Csc03i20')
2011-10-23 23:13:48,403 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-10-23 23:13:48,403 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr0402:bd09/23/2008:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnP5QSE2:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:')
2011-10-23 23:13:48,403 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-23 23:13:48,403 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'usb:v056Ap00D4d0106dc00dsc00dp00ic03isc01ip02')
2011-10-23 23:13:48,403 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'usb:v056Ap00D4d0106dc00dsc00dp00ic03isc00ip00')
2011-10-23 23:13:48,403 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-23 23:13:48,403 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-10-23 23:13:48,403 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001043sd000082D4bc0Csc03i20')
2011-10-23 23:13:48,403 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'usb:v0951p1625d0200dc00dsc00dp00ic08isc06ip50')
2011-10-23 23:13:48,404 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001043sd000082D4bc0Csc03i00')
2011-10-23 23:13:48,404 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001043sd000082D4bc0Csc03i00')
2011-10-23 23:13:48,404 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'pci:v000011ABd00006101sv00001043sd000082E0bc01sc01i8f')
2011-10-23 23:13:48,404 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-23 23:13:48,404 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-23 23:13:48,404 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-23 23:13:48,404 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008367bc02sc00i00')
2011-10-23 23:13:48,404 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-23 23:13:48,404 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001043sd000082D4bc0Csc03i00')
2011-10-23 23:13:48,404 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'input:b0003v046DpC018e0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2011-10-23 23:13:48,404 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a4f86c> about HardwareID('modalias', 'acpi:INT0800:')
2011-10-23 23:13:48,404 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001043sd000082D4bc0Csc03i00')
2011-10-23 23:13:48,404 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001043sd000082D4bc0Csc05i00')
2011-10-23 23:13:48,404 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'pci:v00008086d00003A18sv00001043sd000082D4bc06sc01i00')
2011-10-23 23:13:48,404 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-23 23:13:48,404 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'acpi:PNP0800:')
2011-10-23 23:13:48,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001043sd000082D4bc0Csc03i00')
2011-10-23 23:13:48,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-23 23:13:48,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-10-23 23:13:48,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'pci:v00008086d00003A26sv00001043sd000082D4bc01sc01i85')
2011-10-23 23:13:48,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-10-23 23:13:48,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-23 23:13:48,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'platform:pcspkr')
2011-10-23 23:13:48,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001043sd000082D4bc0Csc03i00')
2011-10-23 23:13:48,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'platform:eisa')
2011-10-23 23:13:48,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'pci:v00008086d00003A20sv00001043sd000082D4bc01sc01i8f')
2011-10-23 23:13:48,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'pci:v00008086d00002E20sv00001043sd000082D3bc06sc00i00')
2011-10-23 23:13:48,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'acpi:PNP0501:')
2011-10-23 23:13:48,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-23 23:13:48,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'pci:v000010DEd00000641sv00001043sd000082BEbc03sc00i00')
2011-10-23 23:13:48,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'acpi:ATK0110:')
2011-10-23 23:13:48,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-23 23:13:48,405 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-23 23:13:48,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'acpi:PNP0700:')
2011-10-23 23:13:48,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'usb:v148Fp2573d0001dc00dsc00dp00icFFiscFFipFF')
2011-10-23 23:13:48,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001043sd00008346bc04sc03i00')
2011-10-23 23:13:48,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001043sd000082D4bc06sc04i01')
2011-10-23 23:13:48,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'usb:v046DpC018d4301dc00dsc00dp00ic03isc01ip02')
2011-10-23 23:13:48,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001043sd000082D4bc0Csc03i20')
2011-10-23 23:13:48,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-10-23 23:13:48,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr0402:bd09/23/2008:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnP5QSE2:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:')
2011-10-23 23:13:48,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-23 23:13:48,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'usb:v056Ap00D4d0106dc00dsc00dp00ic03isc01ip02')
2011-10-23 23:13:48,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'usb:v056Ap00D4d0106dc00dsc00dp00ic03isc00ip00')
2011-10-23 23:13:48,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-23 23:13:48,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-10-23 23:13:48,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001043sd000082D4bc0Csc03i20')
2011-10-23 23:13:48,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'usb:v0951p1625d0200dc00dsc00dp00ic08isc06ip50')
2011-10-23 23:13:48,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001043sd000082D4bc0Csc03i00')
2011-10-23 23:13:48,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001043sd000082D4bc0Csc03i00')
2011-10-23 23:13:48,406 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'pci:v000011ABd00006101sv00001043sd000082E0bc01sc01i8f')
2011-10-23 23:13:48,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-23 23:13:48,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-23 23:13:48,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-23 23:13:48,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008367bc02sc00i00')
2011-10-23 23:13:48,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-23 23:13:48,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001043sd000082D4bc0Csc03i00')
2011-10-23 23:13:48,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'input:b0003v046DpC018e0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2011-10-23 23:13:48,407 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a52acc> about HardwareID('modalias', 'acpi:INT0800:')
2011-10-23 23:13:48,427 DEBUG: handler xorg:nvidia_173 previously unseen
2011-10-23 23:13:48,428 DEBUG: handler xorg:nvidia_173_updates previously unseen
2011-10-23 23:13:48,428 DEBUG: handler xorg:nvidia_current previously unseen
2011-10-23 23:13:48,428 DEBUG: handler xorg:nvidia_current_updates previously unseen
2011-10-23 23:13:48,428 DEBUG: writing back check cache /var/cache/jockey/check
2011-10-23 23:13:48,442 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:13:48,442 DEBUG: nvidia_173 is not the alternative in use
2011-10-23 23:13:48,455 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:13:48,455 DEBUG: nvidia_173_updates is not the alternative in use
2011-10-23 23:13:48,468 DEBUG: NVidia(nvidia_current).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:13:48,468 DEBUG: nvidia_current is not the alternative in use
2011-10-23 23:13:48,481 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:13:48,481 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-23 23:13:48,507 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:13:48,507 DEBUG: nvidia_173 is not the alternative in use
2011-10-23 23:18:50,800 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:18:50,800 DEBUG: nvidia_173 is not the alternative in use
2011-10-23 23:18:51,030 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:18:51,030 DEBUG: nvidia_173_updates is not the alternative in use
2011-10-23 23:18:51,739 DEBUG: NVidia(nvidia_current).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:18:51,739 DEBUG: nvidia_current is not the alternative in use
2011-10-23 23:18:52,438 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:18:52,438 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-23 23:18:53,129 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:18:53,129 DEBUG: nvidia_173 is not the alternative in use
2011-10-23 23:18:53,169 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:18:53,169 DEBUG: nvidia_173 is not the alternative in use
2011-10-23 23:18:53,197 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:18:53,197 DEBUG: nvidia_173_updates is not the alternative in use
2011-10-23 23:18:53,222 DEBUG: NVidia(nvidia_current).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:18:53,222 DEBUG: nvidia_current is not the alternative in use
2011-10-23 23:18:53,251 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:18:53,251 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-23 23:19:03,063 DEBUG: Shutting down
2011-10-23 23:56:28,445 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c>
2011-10-23 23:56:29,714 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-10-23 23:56:29,718 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-10-23 23:56:29,720 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-10-23 23:56:29,739 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-10-23 23:56:29,762 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:56:29,763 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-10-23 23:56:29,784 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-10-23 23:56:29,784 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-10-23 23:56:29,787 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:56:29,787 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-10-23 23:56:29,787 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-10-23 23:56:29,787 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-10-23 23:56:29,799 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-10-23 23:56:29,800 ERROR: could not open /proc/asound/cards: [Errno 2] No such file or directory: '/proc/asound/cards'
2011-10-23 23:56:29,803 DEBUG: Software modem not available
2011-10-23 23:56:29,804 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-10-23 23:56:29,807 WARNING: modinfo for module dvb_usb failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:56:29,821 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-10-23 23:56:29,822 DEBUG: Firmware for DVB cards not available
2011-10-23 23:56:29,822 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-10-23 23:56:29,824 WARNING: modinfo for module wl failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:56:29,834 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-10-23 23:56:29,834 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-10-23 23:56:29,834 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-10-23 23:56:29,869 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:56:29,872 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-10-23 23:56:29,873 DEBUG: nvidia.available: falling back to default
2011-10-23 23:56:29,982 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-23 23:56:29,985 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:56:29,988 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-10-23 23:56:29,988 DEBUG: nvidia.available: falling back to default
2011-10-23 23:56:30,019 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-23 23:56:30,021 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:56:30,024 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-10-23 23:56:30,024 DEBUG: nvidia.available: falling back to default
2011-10-23 23:56:30,054 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-23 23:56:30,054 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-10-23 23:56:30,071 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:56:30,074 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-10-23 23:56:30,075 DEBUG: nvidia.available: falling back to default
2011-10-23 23:56:30,104 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-23 23:56:30,107 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:56:30,110 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-10-23 23:56:30,110 DEBUG: nvidia.available: falling back to default
2011-10-23 23:56:30,140 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-23 23:56:30,142 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:56:30,145 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-10-23 23:56:30,145 DEBUG: nvidia.available: falling back to default
2011-10-23 23:56:30,175 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-23 23:56:30,175 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-10-23 23:56:30,179 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:56:30,182 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-10-23 23:56:30,182 DEBUG: fglrx.available: falling back to default
2011-10-23 23:56:30,213 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-23 23:56:30,215 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:56:30,218 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-10-23 23:56:30,218 DEBUG: fglrx.available: falling back to default
2011-10-23 23:56:30,248 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-10-23 23:56:30,249 DEBUG: all custom handlers loaded
2011-10-23 23:56:30,249 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001043sd000082D4bc0Csc03i00')
2011-10-23 23:56:30,249 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001043sd000082D4bc0Csc05i00')
2011-10-23 23:56:30,249 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'pci:v00008086d00003A18sv00001043sd000082D4bc06sc01i00')
2011-10-23 23:56:30,249 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-23 23:56:30,249 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'acpi:PNP0800:')
2011-10-23 23:56:30,249 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001043sd000082D4bc0Csc03i00')
2011-10-23 23:56:30,249 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-23 23:56:30,249 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-10-23 23:56:30,249 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'pci:v00008086d00003A26sv00001043sd000082D4bc01sc01i85')
2011-10-23 23:56:30,250 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-10-23 23:56:30,250 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-23 23:56:30,250 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'platform:pcspkr')
2011-10-23 23:56:30,250 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001043sd000082D4bc0Csc03i00')
2011-10-23 23:56:30,250 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'platform:eisa')
2011-10-23 23:56:30,250 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'pci:v00008086d00003A20sv00001043sd000082D4bc01sc01i8f')
2011-10-23 23:56:30,250 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'pci:v00008086d00002E20sv00001043sd000082D3bc06sc00i00')
2011-10-23 23:56:30,250 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'acpi:PNP0501:')
2011-10-23 23:56:30,250 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-23 23:56:30,250 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'pci:v000010DEd00000641sv00001043sd000082BEbc03sc00i00')
2011-10-23 23:56:30,408 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2011-10-23 23:56:30,562 DEBUG: NVidia(nvidia_current).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:56:30,562 DEBUG: nvidia_current is not the alternative in use
2011-10-23 23:56:30,408 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-10-23 23:56:30,564 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:56:30,567 DEBUG: nvidia.available: falling back to default
2011-10-23 23:56:30,601 DEBUG: NVidia(nvidia_current).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:56:30,601 DEBUG: nvidia_current is not the alternative in use
2011-10-23 23:56:30,583 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-10-23 23:56:30,601 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_173_updates', 'package': 'nvidia-173-updates'}
2011-10-23 23:56:30,618 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:56:30,618 DEBUG: nvidia_173_updates is not the alternative in use
2011-10-23 23:56:30,601 DEBUG: found match in handler pool xorg:nvidia_173_updates([NvidiaDriver173Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-23 23:56:30,621 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:56:30,624 DEBUG: nvidia.available: falling back to default
2011-10-23 23:56:30,656 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:56:30,656 DEBUG: nvidia_173_updates is not the alternative in use
2011-10-23 23:56:30,639 DEBUG: got handler xorg:nvidia_173_updates([NvidiaDriver173Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-23 23:56:30,657 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_173', 'package': 'nvidia-173'}
2011-10-23 23:56:30,674 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:56:30,674 DEBUG: nvidia_173 is not the alternative in use
2011-10-23 23:56:30,657 DEBUG: found match in handler pool xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-10-23 23:56:30,676 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:56:30,679 DEBUG: nvidia.available: falling back to default
2011-10-23 23:56:30,712 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:56:30,712 DEBUG: nvidia_173 is not the alternative in use
2011-10-23 23:56:30,694 DEBUG: got handler xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-10-23 23:56:30,712 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2011-10-23 23:56:30,729 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:56:30,729 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-23 23:56:30,712 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-23 23:56:30,731 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:56:30,734 DEBUG: nvidia.available: falling back to default
2011-10-23 23:56:30,767 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:56:30,767 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-23 23:56:30,749 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-23 23:56:30,767 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'acpi:ATK0110:')
2011-10-23 23:56:30,767 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-23 23:56:30,767 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-23 23:56:30,767 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'acpi:PNP0700:')
2011-10-23 23:56:30,768 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'usb:v148Fp2573d0001dc00dsc00dp00icFFiscFFipFF')
2011-10-23 23:56:30,768 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001043sd00008346bc04sc03i00')
2011-10-23 23:56:30,768 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001043sd000082D4bc06sc04i01')
2011-10-23 23:56:30,768 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001043sd000082D4bc0Csc03i20')
2011-10-23 23:56:30,768 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-10-23 23:56:30,768 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr0402:bd09/23/2008:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnP5QSE2:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:')
2011-10-23 23:56:30,768 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-23 23:56:30,768 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'usb:v056Ap00D4d0106dc00dsc00dp00ic03isc01ip02')
2011-10-23 23:56:30,768 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'usb:v056Ap00D4d0106dc00dsc00dp00ic03isc00ip00')
2011-10-23 23:56:30,768 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-23 23:56:30,769 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-10-23 23:56:30,769 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001043sd000082D4bc0Csc03i20')
2011-10-23 23:56:30,769 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'usb:v046DpC018d4301dc00dsc00dp00ic03isc01ip02')
2011-10-23 23:56:30,769 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001043sd000082D4bc0Csc03i00')
2011-10-23 23:56:30,769 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001043sd000082D4bc0Csc03i00')
2011-10-23 23:56:30,769 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'pci:v000011ABd00006101sv00001043sd000082E0bc01sc01i8f')
2011-10-23 23:56:30,769 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-23 23:56:30,769 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-23 23:56:30,769 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-23 23:56:30,769 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008367bc02sc00i00')
2011-10-23 23:56:30,770 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-23 23:56:30,770 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001043sd000082D4bc0Csc03i00')
2011-10-23 23:56:30,770 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'input:b0003v046DpC018e0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2011-10-23 23:56:30,770 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb739864c> about HardwareID('modalias', 'acpi:INT0800:')
2011-10-23 23:56:30,770 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001043sd000082D4bc0Csc03i00')
2011-10-23 23:56:30,770 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001043sd000082D4bc0Csc05i00')
2011-10-23 23:56:30,770 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'pci:v00008086d00003A18sv00001043sd000082D4bc06sc01i00')
2011-10-23 23:56:30,770 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-23 23:56:30,770 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'acpi:PNP0800:')
2011-10-23 23:56:30,770 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001043sd000082D4bc0Csc03i00')
2011-10-23 23:56:30,770 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-23 23:56:30,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-10-23 23:56:30,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'pci:v00008086d00003A26sv00001043sd000082D4bc01sc01i85')
2011-10-23 23:56:30,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-10-23 23:56:30,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-23 23:56:30,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'platform:pcspkr')
2011-10-23 23:56:30,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001043sd000082D4bc0Csc03i00')
2011-10-23 23:56:30,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'platform:eisa')
2011-10-23 23:56:30,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'pci:v00008086d00003A20sv00001043sd000082D4bc01sc01i8f')
2011-10-23 23:56:30,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'pci:v00008086d00002E20sv00001043sd000082D3bc06sc00i00')
2011-10-23 23:56:30,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'acpi:PNP0501:')
2011-10-23 23:56:30,771 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-23 23:56:30,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'pci:v000010DEd00000641sv00001043sd000082BEbc03sc00i00')
2011-10-23 23:56:30,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'acpi:ATK0110:')
2011-10-23 23:56:30,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-23 23:56:30,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-23 23:56:30,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'acpi:PNP0700:')
2011-10-23 23:56:30,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'usb:v148Fp2573d0001dc00dsc00dp00icFFiscFFipFF')
2011-10-23 23:56:30,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001043sd00008346bc04sc03i00')
2011-10-23 23:56:30,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001043sd000082D4bc06sc04i01')
2011-10-23 23:56:30,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001043sd000082D4bc0Csc03i20')
2011-10-23 23:56:30,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-10-23 23:56:30,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr0402:bd09/23/2008:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnP5QSE2:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:')
2011-10-23 23:56:30,772 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-23 23:56:30,773 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'usb:v056Ap00D4d0106dc00dsc00dp00ic03isc01ip02')
2011-10-23 23:56:30,773 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'usb:v056Ap00D4d0106dc00dsc00dp00ic03isc00ip00')
2011-10-23 23:56:30,773 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-23 23:56:30,773 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-10-23 23:56:30,773 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001043sd000082D4bc0Csc03i20')
2011-10-23 23:56:30,773 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'usb:v046DpC018d4301dc00dsc00dp00ic03isc01ip02')
2011-10-23 23:56:30,773 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001043sd000082D4bc0Csc03i00')
2011-10-23 23:56:30,773 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001043sd000082D4bc0Csc03i00')
2011-10-23 23:56:30,773 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'pci:v000011ABd00006101sv00001043sd000082E0bc01sc01i8f')
2011-10-23 23:56:30,773 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-23 23:56:30,773 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-23 23:56:30,774 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-23 23:56:30,774 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008367bc02sc00i00')
2011-10-23 23:56:30,774 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-23 23:56:30,774 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001043sd000082D4bc0Csc03i00')
2011-10-23 23:56:30,774 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'input:b0003v046DpC018e0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2011-10-23 23:56:30,774 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8c9ac> about HardwareID('modalias', 'acpi:INT0800:')
2011-10-23 23:56:30,836 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:56:30,836 DEBUG: nvidia_173 is not the alternative in use
2011-10-23 23:56:31,576 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:56:31,576 DEBUG: nvidia_173_updates is not the alternative in use
2011-10-23 23:56:32,262 DEBUG: NVidia(nvidia_current).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:56:32,263 DEBUG: nvidia_current is not the alternative in use
2011-10-23 23:56:32,943 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:56:32,943 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-23 23:56:33,631 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:56:33,631 DEBUG: nvidia_173 is not the alternative in use
2011-10-23 23:56:33,672 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:56:33,672 DEBUG: nvidia_173 is not the alternative in use
2011-10-23 23:56:33,702 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:56:33,702 DEBUG: nvidia_173_updates is not the alternative in use
2011-10-23 23:56:33,733 DEBUG: NVidia(nvidia_current).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:56:33,733 DEBUG: nvidia_current is not the alternative in use
2011-10-23 23:56:33,758 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:56:33,758 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-23 23:56:35,602 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:56:35,602 DEBUG: nvidia_173_updates is not the alternative in use
2011-10-23 23:56:36,017 DEBUG: NVidia(nvidia_current).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:56:36,018 DEBUG: nvidia_current is not the alternative in use
2011-10-23 23:56:39,561 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:56:39,561 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-23 23:56:42,970 DEBUG: NVidia(nvidia_current).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:56:42,970 DEBUG: nvidia_current is not the alternative in use
2011-10-23 23:56:44,056 DEBUG: NVidia(nvidia_current).enabled(): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2011-10-23 23:56:44,057 DEBUG: nvidia_current is not the alternative in use
2011-10-23 23:56:47,951 DEBUG: Installing package: nvidia-current
2011-10-23 23:56:48,157 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 0.000000
2011-10-23 23:56:48,159 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 0.000000
2011-10-23 23:56:48,180 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 0.000000
2011-10-23 23:56:48,206 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 0.000000
2011-10-23 23:56:48,257 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 0.003380
2011-10-23 23:56:48,406 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 0.263850
2011-10-23 23:56:48,406 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 0.263850
2011-10-23 23:56:48,434 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 0.263850
2011-10-23 23:56:48,484 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 0.267230
2011-10-23 23:56:48,616 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 0.484390
2011-10-23 23:56:48,617 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 0.484390
2011-10-23 23:56:48,644 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 0.484390
2011-10-23 23:56:48,690 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 0.484390
2011-10-23 23:56:48,834 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 0.733202
2011-10-23 23:56:48,834 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 0.733202
2011-10-23 23:56:48,860 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 0.733202
2011-10-23 23:56:48,903 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 0.733202
2011-10-23 23:56:49,404 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 1.896668
2011-10-23 23:56:49,905 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 3.188022
2011-10-23 23:56:50,405 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 4.479376
2011-10-23 23:56:50,906 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 5.770730
2011-10-23 23:56:51,407 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 7.057849
2011-10-23 23:56:51,907 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 8.349203
2011-10-23 23:56:52,408 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 9.636323
2011-10-23 23:56:52,909 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 10.927677
2011-10-23 23:56:53,409 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 12.219031
2011-10-23 23:56:53,910 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 13.510385
2011-10-23 23:56:54,411 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 14.797505
2011-10-23 23:56:54,912 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 16.088858
2011-10-23 23:56:55,412 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 17.380212
2011-10-23 23:56:55,913 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 18.671566
2011-10-23 23:56:56,414 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 19.962920
2011-10-23 23:56:56,915 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 21.250040
2011-10-23 23:56:57,415 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 22.541394
2011-10-23 23:56:57,916 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 23.832748
2011-10-23 23:56:58,417 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 25.124101
2011-10-23 23:56:58,918 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 26.411221
2011-10-23 23:56:59,418 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 27.702575
2011-10-23 23:56:59,919 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 28.993929
2011-10-23 23:57:00,420 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 30.285283
2011-10-23 23:57:00,920 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 31.572403
2011-10-23 23:57:01,421 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 32.863757
2011-10-23 23:57:01,922 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 34.155111
2011-10-23 23:57:02,422 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 35.442230
2011-10-23 23:57:02,923 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 36.733584
2011-10-23 23:57:03,423 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 38.024938
2011-10-23 23:57:03,924 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 39.312058
2011-10-23 23:57:04,425 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 40.603412
2011-10-23 23:57:04,925 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 41.894766
2011-10-23 23:57:05,426 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 43.186120
2011-10-23 23:57:05,927 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 44.473239
2011-10-23 23:57:06,428 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 45.764593
2011-10-23 23:57:06,928 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 47.055947
2011-10-23 23:57:07,429 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 48.347301
2011-10-23 23:57:07,930 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 49.638655
2011-10-23 23:57:08,431 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 50.925775
2011-10-23 23:57:08,931 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 52.212895
2011-10-23 23:57:09,432 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 53.500015
2011-10-23 23:57:09,933 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 54.787134
2011-10-23 23:57:10,434 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 56.078488
2011-10-23 23:57:10,934 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 57.365608
2011-10-23 23:57:11,435 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 58.652728
2011-10-23 23:57:11,936 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 59.944082
2011-10-23 23:57:12,437 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 61.231202
2011-10-23 23:57:12,937 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 62.518322
2011-10-23 23:57:13,438 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 63.805442
2011-10-23 23:57:13,939 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 65.096796
2011-10-23 23:57:14,440 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 66.383915
2011-10-23 23:57:14,941 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 67.671035
2011-10-23 23:57:15,441 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 68.958155
2011-10-23 23:57:15,942 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 70.249509
2011-10-23 23:57:16,443 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 71.536629
2011-10-23 23:57:16,944 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 72.823749
2011-10-23 23:57:17,444 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 74.110869
2011-10-23 23:57:17,945 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 75.397989
2011-10-23 23:57:18,445 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 76.685109
2011-10-23 23:57:18,946 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 77.976462
2011-10-23 23:57:19,447 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 79.153500
2011-10-23 23:57:19,948 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 80.550702
2011-10-23 23:57:20,448 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 81.837822
2011-10-23 23:57:20,949 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 83.124942
2011-10-23 23:57:21,450 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 84.412062
2011-10-23 23:57:21,950 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 85.703416
2011-10-23 23:57:22,451 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 86.990536
2011-10-23 23:57:22,952 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 88.277656
2011-10-23 23:57:23,453 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 89.564776
2011-10-23 23:57:23,953 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 90.851895
2011-10-23 23:57:24,454 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 92.143249
2011-10-23 23:57:24,954 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 93.430369
2011-10-23 23:57:25,455 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 94.717489
2011-10-23 23:57:25,956 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 96.004609
2011-10-23 23:57:26,349 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 97.016638
2011-10-23 23:57:26,349 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 97.016638
2011-10-23 23:57:26,377 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 97.016638
2011-10-23 23:57:26,416 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 97.016638
2011-10-23 23:57:26,511 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 97.143251
2011-10-23 23:57:26,511 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 97.143251
2011-10-23 23:57:26,539 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 97.143251
2011-10-23 23:57:26,575 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 97.146634
2011-10-23 23:57:26,610 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 97.183995
2011-10-23 23:57:26,610 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 97.183995
2011-10-23 23:57:26,636 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 97.183995
2011-10-23 23:57:26,685 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 97.183995
2011-10-23 23:57:27,186 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 98.347473
2011-10-23 23:57:27,686 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 99.638827
2011-10-23 23:57:27,826 DEBUG: download progress <Package: name:'nvidia-current' architecture='i386' id:4383L> 100.000000
2011-10-23 23:57:28,733 DEBUG: install progress dpkg-exec 0.000000
2011-10-23 23:57:29,813 DEBUG: install progress patch 0.000000
2011-10-23 23:57:29,813 DEBUG: install progress patch 2.857140
2011-10-23 23:57:30,186 DEBUG: install progress patch 5.714290
2011-10-23 23:57:30,244 DEBUG: install progress patch 8.571430
2011-10-23 23:57:30,503 DEBUG: install progress dkms 8.571430
2011-10-23 23:57:30,503 DEBUG: install progress dkms 11.428600
2011-10-23 23:57:30,891 DEBUG: install progress dkms 14.285700
2011-10-23 23:57:30,949 DEBUG: install progress dkms 17.142900
2011-10-23 23:57:31,218 DEBUG: install progress fakeroot 17.142900
2011-10-23 23:57:31,318 DEBUG: install progress fakeroot 20.000000
2011-10-23 23:57:31,537 DEBUG: install progress fakeroot 22.857100
2011-10-23 23:57:31,595 DEBUG: install progress fakeroot 25.714300
2011-10-23 23:57:31,928 DEBUG: install progress nvidia-current 25.714300
2011-10-23 23:57:32,029 DEBUG: install progress nvidia-current 28.571400
2011-10-23 23:57:35,572 DEBUG: install progress nvidia-current 31.428600
2011-10-23 23:57:35,629 DEBUG: install progress nvidia-current 34.285700
2011-10-23 23:57:35,898 DEBUG: install progress python-central 34.285700
2011-10-23 23:57:35,998 DEBUG: install progress python-central 37.142900
2011-10-23 23:57:36,245 DEBUG: install progress python-central 40.000000
2011-10-23 23:57:36,302 DEBUG: install progress python-central 42.857100
2011-10-23 23:57:36,637 DEBUG: install progress screen-resolution-extra 42.857100
2011-10-23 23:57:36,638 DEBUG: install progress screen-resolution-extra 45.714300
2011-10-23 23:57:36,958 DEBUG: install progress screen-resolution-extra 48.571400
2011-10-23 23:57:37,024 DEBUG: install progress screen-resolution-extra 51.428600
2011-10-23 23:57:37,309 DEBUG: install progress nvidia-settings 51.428600
2011-10-23 23:57:37,410 DEBUG: install progress nvidia-settings 54.285700
2011-10-23 23:57:37,575 DEBUG: install progress nvidia-settings 57.142900
2011-10-23 23:57:37,632 DEBUG: install progress nvidia-settings 60.000000
2011-10-23 23:57:37,694 DEBUG: install progress man-db 60.000000
2011-10-23 23:57:39,964 DEBUG: install progress dpkg-exec 60.000000
2011-10-23 23:57:39,989 DEBUG: install progress patch 60.000000
2011-10-23 23:57:40,056 DEBUG: install progress patch 62.857100
2011-10-23 23:57:40,116 DEBUG: install progress patch 65.714300
2011-10-23 23:57:40,175 DEBUG: install progress dkms 65.714300
2011-10-23 23:57:40,998 DEBUG: install progress dkms 68.571400
2011-10-23 23:57:41,058 DEBUG: install progress dkms 71.428600
2011-10-23 23:57:41,116 DEBUG: install progress fakeroot 71.428600
2011-10-23 23:57:41,175 DEBUG: install progress fakeroot 74.285700
2011-10-23 23:57:41,268 DEBUG: install progress fakeroot 77.142900
2011-10-23 23:57:41,346 DEBUG: install progress nvidia-current 77.142900
2011-10-23 23:57:41,413 DEBUG: install progress nvidia-current 80.000000
2011-10-23 23:57:44,025 DEBUG: install progress nvidia-current 82.857100
2011-10-23 23:57:44,393 DEBUG: install progress python-central 82.857100
2011-10-23 23:57:44,452 DEBUG: install progress python-central 85.714300
2011-10-23 23:57:44,512 DEBUG: install progress python-central 88.571400
2011-10-23 23:57:44,579 DEBUG: install progress screen-resolution-extra 88.571400
2011-10-23 23:57:44,706 DEBUG: install progress screen-resolution-extra 91.428600
2011-10-23 23:57:44,972 DEBUG: install progress screen-resolution-extra 94.285700
2011-10-23 23:57:45,153 DEBUG: install progress python-central 94.285700
2011-10-23 23:57:45,365 DEBUG: install progress nvidia-settings 94.285700
2011-10-23 23:57:45,432 DEBUG: install progress nvidia-settings 97.142900
2011-10-23 23:57:45,619 DEBUG: install progress nvidia-settings 100.000000
2011-10-23 23:57:45,822 DEBUG: install progress bamfdaemon 100.000000
2011-10-23 23:57:45,967 DEBUG: install progress gnome-menus 100.000000
2011-10-23 23:57:46,194 DEBUG: install progress initramfs-tools 100.000000
2011-10-23 23:57:48,398 DEBUG: Selecting previously deselected package patch.
(Reading database ... 137684 files and directories currently installed.)
Unpacking patch (from .../patch_2.6.1-2_i386.deb) ...
Selecting previously deselected package dkms.
Unpacking dkms (from .../dkms_2.2.0.2-1ubuntu4_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.17-1_i386.deb) ...
Selecting previously deselected package nvidia-current.
Unpacking nvidia-current (from .../nvidia-current_280.13-0ubuntu6_i386.deb) ...
Selecting previously deselected package python-central.
Unpacking python-central (from .../python-central_0.6.17_all.deb) ...
Selecting previously deselected package screen-resolution-extra.
Unpacking screen-resolution-extra (from .../screen-resolution-extra_0.14build2_all.deb) ...
Selecting previously deselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_280.13-0ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up patch (2.6.1-2) ...
Setting up dkms (2.2.0.2-1ubuntu4) ...
Setting up fakeroot (1.17-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up nvidia-current (280.13-0ubuntu6) ...
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/lib32/libOpenCL.so because associated file /usr/lib32/nvidia-current/libOpenCL.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.1 (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libvdpau_nvidia.so because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/nvidia-current/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-3.0.0-13-generic-pae
WARNING: missing /lib/modules/3.0.0-13-generic-pae
Device driver support needs thus be built-in linux image!
WARNING: Couldn't open directory /lib/modules/3.0.0-13-generic-pae: No such file or directory
FATAL: Could not open /lib/modules/3.0.0-13-generic-pae/modules.dep.temp for writing: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
Loading new nvidia-current-280.13 DKMS files...
First Installation: checking all kernels...
Building for 3.0.0-13-generic-pae and 3.0.0-13-generic
Building for architecture i686
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Setting up python-central (0.6.17) ...
Setting up screen-resolution-extra (0.14build2) ...
Processing triggers for python-central ...
Setting up nvidia-settings (280.13-0ubuntu2) ...
update-alternatives: using /usr/lib/nvidia-settings/ld.so.conf to provide /etc/ld.so.conf.d/nvidia_settings.conf (nvidia_settings_conf) in auto mode.
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-13-generic-pae
WARNING: missing /lib/modules/3.0.0-13-generic-pae
Device driver support needs thus be built-in linux image!
WARNING: Couldn't open directory /lib/modules/3.0.0-13-generic-pae: No such file or directory
FATAL: Could not open /lib/modules/3.0.0-13-generic-pae/modules.dep.temp for writing: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/3.0.0-13-generic-pae/modules.dep: No such file or directory

2011-10-23 23:57:48,508 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:57:48,508 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-10-23 23:57:52,604 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-23 23:57:52,604 DEBUG: KMH enabled: False
2011-10-23 23:57:52,620 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-23 23:57:52,620 DEBUG: KMH enabled: False
2011-10-23 23:58:07,517 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-23 23:58:07,517 DEBUG: nvidia_173 is not the alternative in use
2011-10-23 23:58:07,555 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-23 23:58:07,555 DEBUG: nvidia_173_updates is not the alternative in use
2011-10-23 23:58:07,593 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-23 23:58:07,593 DEBUG: KMH enabled: False
2011-10-23 23:58:07,614 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-23 23:58:07,614 DEBUG: KMH enabled: False
2011-10-23 23:58:07,652 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-23 23:58:07,652 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-23 23:58:07,695 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-23 23:58:07,695 DEBUG: KMH enabled: False
2011-10-23 23:58:07,716 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-23 23:58:07,717 DEBUG: KMH enabled: False
2011-10-23 23:58:07,767 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-23 23:58:07,767 DEBUG: nvidia_173 is not the alternative in use
2011-10-23 23:58:07,802 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-23 23:58:07,802 DEBUG: nvidia_173_updates is not the alternative in use
2011-10-23 23:58:07,838 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-23 23:58:07,838 DEBUG: KMH enabled: False
2011-10-23 23:58:07,859 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-23 23:58:07,859 DEBUG: KMH enabled: False
2011-10-23 23:58:07,894 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-23 23:58:07,895 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-23 23:58:17,376 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-23 23:58:17,376 DEBUG: nvidia_173 is not the alternative in use
2011-10-23 23:58:18,624 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-23 23:58:18,625 DEBUG: nvidia_173_updates is not the alternative in use
2011-10-23 23:58:20,398 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-23 23:58:20,398 DEBUG: KMH enabled: False
2011-10-23 23:58:20,418 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-23 23:58:20,419 DEBUG: KMH enabled: False
2011-10-23 23:58:21,128 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-23 23:58:21,128 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-23 23:58:24,591 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-23 23:58:24,591 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-23 23:58:24,718 DEBUG: Installing package: nvidia-current-updates
2011-10-23 23:58:25,407 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 0.000000
2011-10-23 23:58:25,407 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 0.000000
2011-10-23 23:58:25,426 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 0.000000
2011-10-23 23:58:25,447 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 0.000000
2011-10-23 23:58:25,478 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 0.003190
2011-10-23 23:58:25,978 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 1.217050
2011-10-23 23:58:26,479 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 2.520666
2011-10-23 23:58:26,980 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 3.824283
2011-10-23 23:58:27,481 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 5.123625
2011-10-23 23:58:27,981 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 6.427241
2011-10-23 23:58:28,482 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 7.730858
2011-10-23 23:58:28,983 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 9.034474
2011-10-23 23:58:29,484 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 10.333817
2011-10-23 23:58:29,984 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 11.637433
2011-10-23 23:58:30,485 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 12.941050
2011-10-23 23:58:30,986 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 14.244666
2011-10-23 23:58:31,486 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 15.548283
2011-10-23 23:58:31,987 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 16.847625
2011-10-23 23:58:32,488 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 18.151242
2011-10-23 23:58:32,989 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 19.377924
2011-10-23 23:58:33,490 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 20.758475
2011-10-23 23:58:33,991 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 22.062091
2011-10-23 23:58:34,491 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 23.361434
2011-10-23 23:58:34,992 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 24.665050
2011-10-23 23:58:35,493 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 25.968667
2011-10-23 23:58:35,994 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 27.272283
2011-10-23 23:58:36,495 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 28.575900
2011-10-23 23:58:36,995 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 29.875242
2011-10-23 23:58:37,496 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 31.178859
2011-10-23 23:58:37,997 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 32.482475
2011-10-23 23:58:38,497 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 33.786092
2011-10-23 23:58:38,998 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 35.085434
2011-10-23 23:58:39,499 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 36.389051
2011-10-23 23:58:39,999 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 37.692667
2011-10-23 23:58:40,500 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 38.992009
2011-10-23 23:58:41,001 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 40.295626
2011-10-23 23:58:41,502 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 41.599243
2011-10-23 23:58:42,002 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 42.902859
2011-10-23 23:58:42,503 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 44.206476
2011-10-23 23:58:43,004 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 45.505818
2011-10-23 23:58:43,504 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 46.809434
2011-10-23 23:58:44,005 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 48.113051
2011-10-23 23:58:44,506 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 49.412393
2011-10-23 23:58:45,007 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 50.711736
2011-10-23 23:58:45,508 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 52.015352
2011-10-23 23:58:46,008 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 53.314695
2011-10-23 23:58:46,509 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 54.614037
2011-10-23 23:58:47,010 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 55.917653
2011-10-23 23:58:47,510 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 57.216996
2011-10-23 23:58:48,011 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 58.516338
2011-10-23 23:58:48,512 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 59.815681
2011-10-23 23:58:49,012 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 61.115023
2011-10-23 23:58:49,513 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 62.414365
2011-10-23 23:58:50,014 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 63.713708
2011-10-23 23:58:50,515 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 64.927567
2011-10-23 23:58:51,015 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 65.996105
2011-10-23 23:58:51,516 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 66.940693
2011-10-23 23:58:52,017 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 68.184471
2011-10-23 23:58:52,518 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 69.419701
2011-10-23 23:58:53,019 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 70.672028
2011-10-23 23:58:53,520 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 71.868791
2011-10-23 23:58:54,020 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 73.082650
2011-10-23 23:58:54,521 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 74.334977
2011-10-23 23:58:55,022 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 75.638593
2011-10-23 23:58:55,523 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 76.942210
2011-10-23 23:58:56,023 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 78.241552
2011-10-23 23:58:56,524 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 79.545169
2011-10-23 23:58:57,025 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 80.848785
2011-10-23 23:58:57,526 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 82.152402
2011-10-23 23:58:58,026 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 83.451744
2011-10-23 23:58:58,527 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 84.755361
2011-10-23 23:58:59,028 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 86.058977
2011-10-23 23:58:59,529 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 87.362594
2011-10-23 23:59:00,029 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 88.666210
2011-10-23 23:59:00,530 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 89.965552
2011-10-23 23:59:01,031 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 91.269169
2011-10-23 23:59:01,532 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 92.572785
2011-10-23 23:59:02,032 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 93.872128
2011-10-23 23:59:02,533 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 95.175744
2011-10-23 23:59:03,034 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 96.479361
2011-10-23 23:59:03,296 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 97.159773
2011-10-23 23:59:03,297 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 97.162157
2011-10-23 23:59:03,797 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 98.465773
2011-10-23 23:59:04,298 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 99.769390
2011-10-23 23:59:04,387 DEBUG: download progress <Package: name:'nvidia-current-updates' architecture='i386' id:12117L> 100.000000
2011-10-23 23:59:04,525 DEBUG: install progress dpkg-exec 0.000000
2011-10-23 23:59:04,970 DEBUG: install progress nvidia-current-updates 0.000000
2011-10-23 23:59:05,070 DEBUG: install progress nvidia-current-updates 10.000000
2011-10-23 23:59:08,405 DEBUG: install progress nvidia-current-updates 20.000000
2011-10-23 23:59:08,462 DEBUG: install progress nvidia-current-updates 30.000000
2011-10-23 23:59:08,705 DEBUG: install progress nvidia-settings-updates 30.000000
2011-10-23 23:59:08,805 DEBUG: install progress nvidia-settings-updates 40.000000
2011-10-23 23:59:08,955 DEBUG: install progress nvidia-settings-updates 50.000000
2011-10-23 23:59:09,012 DEBUG: install progress nvidia-settings-updates 60.000000
2011-10-23 23:59:09,082 DEBUG: install progress man-db 60.000000
2011-10-23 23:59:10,125 DEBUG: install progress dpkg-exec 60.000000
2011-10-23 23:59:10,152 DEBUG: install progress nvidia-current-updates 60.000000
2011-10-23 23:59:10,238 DEBUG: install progress nvidia-current-updates 70.000000
2011-10-23 23:59:10,676 DEBUG: install progress nvidia-current-updates 80.000000
2011-10-23 23:59:11,022 DEBUG: install progress nvidia-settings-updates 80.000000
2011-10-23 23:59:11,081 DEBUG: install progress nvidia-settings-updates 90.000000
2011-10-23 23:59:11,252 DEBUG: install progress nvidia-settings-updates 100.000000
2011-10-23 23:59:11,456 DEBUG: install progress bamfdaemon 100.000000
2011-10-23 23:59:11,566 DEBUG: install progress gnome-menus 100.000000
2011-10-23 23:59:12,367 DEBUG: Selecting previously deselected package nvidia-current-updates.
(Reading database ... 138010 files and directories currently installed.)
Unpacking nvidia-current-updates (from .../nvidia-current-updates_280.13-0ubuntu5_i386.deb) ...
Selecting previously deselected package nvidia-settings-updates.
Unpacking nvidia-settings-updates (from .../nvidia-settings-updates_280.13-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up nvidia-current-updates (280.13-0ubuntu5) ...
Loading new nvidia-current-updates-280.13 DKMS files...
First Installation: checking all kernels...
Building for 3.0.0-13-generic-pae and 3.0.0-13-generic
Building for architecture i686
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Setting up nvidia-settings-updates (280.13-0ubuntu1) ...
update-alternatives: using /usr/lib/nvidia-settings-updates/ld.so.conf to provide /etc/ld.so.conf.d/nvidia_settings.conf (nvidia_settings_conf) in auto mode.
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...

2011-10-23 23:59:12,475 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not open /lib/modules/3.0.0-13-generic-pae/modules.dep

2011-10-23 23:59:12,475 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-10-23 23:59:16,622 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-23 23:59:16,622 DEBUG: KMH enabled: False
2011-10-23 23:59:16,645 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-23 23:59:16,645 DEBUG: KMH enabled: False
2011-10-23 23:59:23,759 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-23 23:59:23,759 DEBUG: nvidia_173 is not the alternative in use
2011-10-23 23:59:23,798 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-23 23:59:23,798 DEBUG: nvidia_173_updates is not the alternative in use
2011-10-23 23:59:23,837 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-23 23:59:23,837 DEBUG: nvidia_current is not the alternative in use
2011-10-23 23:59:23,860 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-23 23:59:23,860 DEBUG: nvidia_current is not the alternative in use
2011-10-23 23:59:23,899 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-23 23:59:23,899 DEBUG: KMH enabled: False
2011-10-23 23:59:23,922 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-23 23:59:23,922 DEBUG: KMH enabled: False
2011-10-23 23:59:23,966 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-23 23:59:23,967 DEBUG: KMH enabled: False
2011-10-23 23:59:23,989 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-23 23:59:23,990 DEBUG: KMH enabled: False
2011-10-23 23:59:24,041 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-23 23:59:24,041 DEBUG: nvidia_173 is not the alternative in use
2011-10-23 23:59:24,077 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-23 23:59:24,077 DEBUG: nvidia_173_updates is not the alternative in use
2011-10-23 23:59:24,113 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-23 23:59:24,114 DEBUG: nvidia_current is not the alternative in use
2011-10-23 23:59:24,136 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-23 23:59:24,136 DEBUG: nvidia_current is not the alternative in use
2011-10-23 23:59:24,172 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-23 23:59:24,173 DEBUG: KMH enabled: False
2011-10-23 23:59:24,195 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-23 23:59:24,195 DEBUG: KMH enabled: False
2011-10-23 23:59:26,588 DEBUG: Shutting down
2011-10-24 21:50:04,193 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec>
2011-10-24 21:50:05,481 DEBUG: reading modalias file /lib/modules/3.0.0-12-generic-pae/modules.alias
2011-10-24 21:50:05,599 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-10-24 21:50:05,602 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-10-24 21:50:05,629 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-10-24 21:50:05,650 DEBUG: loading custom handler /usr/share/jockey/handlers/vmware-client.py
2011-10-24 21:50:05,696 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet

2011-10-24 21:50:05,697 DEBUG: Instantiated Handler subclass __builtin__.VmwareClientHandler from name VmwareClientHandler
2011-10-24 21:50:05,723 DEBUG: VMWare Client Tools availability undetermined, adding to pool
2011-10-24 21:50:05,723 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-10-24 21:50:05,726 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-10-24 21:50:05,727 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-10-24 21:50:05,727 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-10-24 21:50:05,727 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-10-24 21:50:05,741 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-10-24 21:50:05,747 DEBUG: Software modem not available
2011-10-24 21:50:05,748 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-10-24 21:50:05,781 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-10-24 21:50:05,781 DEBUG: Firmware for DVB cards not available
2011-10-24 21:50:05,781 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-10-24 21:50:05,785 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-10-24 21:50:05,796 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-10-24 21:50:05,796 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-10-24 21:50:05,796 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-10-24 21:50:05,836 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-10-24 21:50:05,838 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-10-24 21:50:05,839 DEBUG: nvidia.available: falling back to default
2011-10-24 21:50:05,935 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-24 21:50:05,938 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-10-24 21:50:05,941 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-10-24 21:50:05,942 DEBUG: nvidia.available: falling back to default
2011-10-24 21:50:05,967 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-24 21:50:05,971 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-10-24 21:50:05,974 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173Updates from name NvidiaDriver173Updates
2011-10-24 21:50:05,974 DEBUG: nvidia.available: falling back to default
2011-10-24 21:50:06,000 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-24 21:50:06,000 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/jockey/detection.py", line 962, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-10-24 21:50:06,015 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-10-24 21:50:06,017 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrentUpdates from name NvidiaDriverCurrentUpdates
2011-10-24 21:50:06,017 DEBUG: nvidia.available: falling back to default
2011-10-24 21:50:06,042 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-24 21:50:06,045 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-10-24 21:50:06,048 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-10-24 21:50:06,048 DEBUG: nvidia.available: falling back to default
2011-10-24 21:50:06,075 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-24 21:50:06,078 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates

2011-10-24 21:50:06,081 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96Updates from name NvidiaDriver96Updates
2011-10-24 21:50:06,081 DEBUG: nvidia.available: falling back to default
2011-10-24 21:50:06,107 DEBUG: NVIDIA accelerated graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-24 21:50:06,107 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-10-24 21:50:06,111 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-10-24 21:50:06,114 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriverUpdate from name FglrxDriverUpdate
2011-10-24 21:50:06,114 DEBUG: fglrx.available: falling back to default
2011-10-24 21:50:06,138 DEBUG: ATI/AMD proprietary FGLRX graphics driver (post-release updates) availability undetermined, adding to pool
2011-10-24 21:50:06,141 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-10-24 21:50:06,145 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-10-24 21:50:06,145 DEBUG: fglrx.available: falling back to default
2011-10-24 21:50:06,170 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-10-24 21:50:06,170 DEBUG: all custom handlers loaded
2011-10-24 21:50:06,170 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001043sd000082D4bc0Csc03i00')
2011-10-24 21:50:06,392 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001043sd000082D4bc0Csc05i00')
2011-10-24 21:50:06,394 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801'}
2011-10-24 21:50:06,488 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-10-24 21:50:06,489 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'pci:v00008086d00003A18sv00001043sd000082D4bc06sc01i00')
2011-10-24 21:50:06,491 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt'}
2011-10-24 21:50:06,492 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-10-24 21:50:06,492 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-24 21:50:06,492 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'acpi:PNP0800:')
2011-10-24 21:50:06,492 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001043sd000082D4bc0Csc03i00')
2011-10-24 21:50:06,494 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'platform:eisa')
2011-10-24 21:50:06,495 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-10-24 21:50:06,511 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'pci:v00008086d00003A26sv00001043sd000082D4bc01sc01i85')
2011-10-24 21:50:06,513 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-10-24 21:50:06,516 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-24 21:50:06,517 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-24 21:50:06,517 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-24 21:50:06,517 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-24 21:50:06,517 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001043sd000082D4bc0Csc03i00')
2011-10-24 21:50:06,519 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'platform:pcspkr')
2011-10-24 21:50:06,520 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr'}
2011-10-24 21:50:06,520 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-10-24 21:50:06,520 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp'}
2011-10-24 21:50:06,520 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-10-24 21:50:06,520 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'pci:v00008086d00003A20sv00001043sd000082D4bc01sc01i8f')
2011-10-24 21:50:06,523 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'pci:v00008086d00002E20sv00001043sd000082D3bc06sc00i00')
2011-10-24 21:50:06,525 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'acpi:INT0800:')
2011-10-24 21:50:06,525 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-24 21:50:06,525 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'pci:v000010DEd00000641sv00001043sd000082BEbc03sc00i00')
2011-10-24 21:50:06,733 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current', 'package': 'nvidia-current'}
2011-10-24 21:50:06,963 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-24 21:50:06,963 DEBUG: nvidia_current is not the alternative in use
2011-10-24 21:50:06,733 DEBUG: found match in handler pool xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-10-24 21:50:06,965 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-10-24 21:50:06,968 DEBUG: nvidia.available: falling back to default
2011-10-24 21:50:06,994 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-24 21:50:06,995 DEBUG: nvidia_current is not the alternative in use
2011-10-24 21:50:06,979 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-10-24 21:50:06,995 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_173_updates', 'package': 'nvidia-173-updates'}
2011-10-24 21:50:07,010 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-24 21:50:07,010 DEBUG: nvidia_173_updates is not the alternative in use
2011-10-24 21:50:06,995 DEBUG: found match in handler pool xorg:nvidia_173_updates([NvidiaDriver173Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-24 21:50:07,012 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates

2011-10-24 21:50:07,015 DEBUG: nvidia.available: falling back to default
2011-10-24 21:50:07,047 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-24 21:50:07,047 DEBUG: nvidia_173_updates is not the alternative in use
2011-10-24 21:50:07,027 DEBUG: got handler xorg:nvidia_173_updates([NvidiaDriver173Updates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-24 21:50:07,047 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_173', 'package': 'nvidia-173'}
2011-10-24 21:50:07,064 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-24 21:50:07,065 DEBUG: nvidia_173 is not the alternative in use
2011-10-24 21:50:07,048 DEBUG: found match in handler pool xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-10-24 21:50:07,067 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-10-24 21:50:07,069 DEBUG: nvidia.available: falling back to default
2011-10-24 21:50:07,101 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-24 21:50:07,101 DEBUG: nvidia_173 is not the alternative in use
2011-10-24 21:50:07,083 DEBUG: got handler xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-10-24 21:50:07,102 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidia_current_updates', 'package': 'nvidia-current-updates'}
2011-10-24 21:50:07,116 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-24 21:50:07,117 DEBUG: KMH enabled: False
2011-10-24 21:50:07,102 DEBUG: found match in handler pool xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-24 21:50:07,120 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates

2011-10-24 21:50:07,123 DEBUG: nvidia.available: falling back to default
2011-10-24 21:50:07,160 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-24 21:50:07,160 DEBUG: KMH enabled: False
2011-10-24 21:50:07,138 DEBUG: got handler xorg:nvidia_current_updates([NvidiaDriverCurrentUpdates, nonfree, disabled] NVIDIA accelerated graphics driver (post-release updates))
2011-10-24 21:50:07,160 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb'}
2011-10-24 21:50:07,160 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2011-10-24 21:50:07,161 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'nouveau'}
2011-10-24 21:50:07,161 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2011-10-24 21:50:07,161 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-24 21:50:07,161 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-10-24 21:50:07,161 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-24 21:50:07,161 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'acpi:PNP0700:')
2011-10-24 21:50:07,161 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'usb:v148Fp2573d0001dc00dsc00dp00icFFiscFFipFF')
2011-10-24 21:50:07,168 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'rt73usb'}
2011-10-24 21:50:07,168 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'rt73usb', 'jockey_handler': 'KernelModuleHandler'}
2011-10-24 21:50:07,169 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001043sd00008346bc04sc03i00')
2011-10-24 21:50:07,173 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel'}
2011-10-24 21:50:07,173 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-24 21:50:07,173 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001043sd000082D4bc06sc04i01')
2011-10-24 21:50:07,176 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'input:b0003v046DpC018e0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2011-10-24 21:50:07,177 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-24 21:50:07,177 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-24 21:50:07,177 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'input:b0003v056Ap00D4e0106-e0,1,3,k110,111,115,116,145,14A,14D,ra0,1,18,2F,35,36,39,3A,mlsfw')
2011-10-24 21:50:07,177 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-24 21:50:07,177 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-24 21:50:07,177 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-24 21:50:07,177 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-24 21:50:07,177 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-24 21:50:07,177 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-24 21:50:07,177 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-24 21:50:07,177 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-24 21:50:07,178 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001043sd000082D4bc0Csc03i20')
2011-10-24 21:50:07,180 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr0402:bd09/23/2008:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnP5QSE2:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:')
2011-10-24 21:50:07,190 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-24 21:50:07,190 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'usb:v056Ap00D4d0106dc00dsc00dp00ic03isc01ip02')
2011-10-24 21:50:07,213 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wacom'}
2011-10-24 21:50:07,213 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'wacom', 'jockey_handler': 'KernelModuleHandler'}
2011-10-24 21:50:07,213 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-24 21:50:07,213 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-24 21:50:07,214 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-10-24 21:50:07,214 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-10-24 21:50:07,214 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'usb:v056Ap00D4d0106dc00dsc00dp00ic03isc00ip00')
2011-10-24 21:50:07,214 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wacom'}
2011-10-24 21:50:07,214 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'wacom', 'jockey_handler': 'KernelModuleHandler'}
2011-10-24 21:50:07,214 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-24 21:50:07,214 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-24 21:50:07,214 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-24 21:50:07,215 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'acpi:PNP0501:')
2011-10-24 21:50:07,215 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001043sd000082D4bc0Csc03i20')
2011-10-24 21:50:07,217 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'usb:v046DpC018d4301dc00dsc00dp00ic03isc01ip02')
2011-10-24 21:50:07,237 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbhid'}
2011-10-24 21:50:07,237 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-24 21:50:07,237 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse'}
2011-10-24 21:50:07,237 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-10-24 21:50:07,237 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001043sd000082D4bc0Csc03i00')
2011-10-24 21:50:07,240 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001043sd000082D4bc0Csc03i00')
2011-10-24 21:50:07,242 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'pci:v000011ABd00006101sv00001043sd000082E0bc01sc01i8f')
2011-10-24 21:50:07,259 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'pata_marvell'}
2011-10-24 21:50:07,259 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_marvell', 'jockey_handler': 'KernelModuleHandler'}
2011-10-24 21:50:07,259 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-24 21:50:07,260 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-24 21:50:07,260 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-24 21:50:07,260 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-24 21:50:07,260 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-24 21:50:07,260 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-24 21:50:07,260 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008367bc02sc00i00')
2011-10-24 21:50:07,266 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'r8169'}
2011-10-24 21:50:07,266 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'r8169', 'jockey_handler': 'KernelModuleHandler'}
2011-10-24 21:50:07,266 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'platform:regulatory')
2011-10-24 21:50:07,267 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001043sd000082D4bc0Csc03i00')
2011-10-24 21:50:07,269 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'input:b0003v056Ap00D4e0106-e0,1,3,k140,141,14A,14B,14C,ra0,1,18,mlsfw')
2011-10-24 21:50:07,269 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'evbug'}
2011-10-24 21:50:07,269 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-24 21:50:07,270 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-24 21:50:07,270 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-24 21:50:07,270 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'joydev'}
2011-10-24 21:50:07,270 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}
2011-10-24 21:50:07,270 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xb6a86bec> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-10-24 21:50:07,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001043sd000082D4bc0Csc03i00')
2011-10-24 21:50:07,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001043sd000082D4bc0Csc05i00')
2011-10-24 21:50:07,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'pci:v00008086d00003A18sv00001043sd000082D4bc06sc01i00')
2011-10-24 21:50:07,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-24 21:50:07,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'acpi:PNP0800:')
2011-10-24 21:50:07,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001043sd000082D4bc0Csc03i00')
2011-10-24 21:50:07,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'platform:eisa')
2011-10-24 21:50:07,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'usb:v1D6Bp0001d0300dc09dsc00dp00ic09isc00ip00')
2011-10-24 21:50:07,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'pci:v00008086d00003A26sv00001043sd000082D4bc01sc01i85')
2011-10-24 21:50:07,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-10-24 21:50:07,270 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-24 21:50:07,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-24 21:50:07,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001043sd000082D4bc0Csc03i00')
2011-10-24 21:50:07,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'platform:pcspkr')
2011-10-24 21:50:07,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'pci:v00008086d00003A20sv00001043sd000082D4bc01sc01i8f')
2011-10-24 21:50:07,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'pci:v00008086d00002E20sv00001043sd000082D3bc06sc00i00')
2011-10-24 21:50:07,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'acpi:INT0800:')
2011-10-24 21:50:07,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-24 21:50:07,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'pci:v000010DEd00000641sv00001043sd000082BEbc03sc00i00')
2011-10-24 21:50:07,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-24 21:50:07,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-10-24 21:50:07,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-24 21:50:07,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'acpi:PNP0700:')
2011-10-24 21:50:07,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'usb:v148Fp2573d0001dc00dsc00dp00icFFiscFFipFF')
2011-10-24 21:50:07,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001043sd00008346bc04sc03i00')
2011-10-24 21:50:07,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001043sd000082D4bc06sc04i01')
2011-10-24 21:50:07,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'input:b0003v046DpC018e0111-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')
2011-10-24 21:50:07,271 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'input:b0003v056Ap00D4e0106-e0,1,3,k110,111,115,116,145,14A,14D,ra0,1,18,2F,35,36,39,3A,mlsfw')
2011-10-24 21:50:07,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001043sd000082D4bc0Csc03i20')
2011-10-24 21:50:07,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr0402:bd09/23/2008:svnSystemmanufacturer:pnSystemProductName:pvrSystemVersion:rvnASUSTeKComputerINC.:rnP5QSE2:rvrRevX.0x:cvnChassisManufacture:ct3:cvrChassisVersion:')
2011-10-24 21:50:07,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-24 21:50:07,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'usb:v056Ap00D4d0106dc00dsc00dp00ic03isc01ip02')
2011-10-24 21:50:07,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'usb:v056Ap00D4d0106dc00dsc00dp00ic03isc00ip00')
2011-10-24 21:50:07,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-24 21:50:07,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'acpi:PNP0501:')
2011-10-24 21:50:07,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001043sd000082D4bc0Csc03i20')
2011-10-24 21:50:07,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'usb:v046DpC018d4301dc00dsc00dp00ic03isc01ip02')
2011-10-24 21:50:07,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001043sd000082D4bc0Csc03i00')
2011-10-24 21:50:07,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001043sd000082D4bc0Csc03i00')
2011-10-24 21:50:07,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'pci:v000011ABd00006101sv00001043sd000082E0bc01sc01i8f')
2011-10-24 21:50:07,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-24 21:50:07,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-24 21:50:07,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-24 21:50:07,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'usb:v1D6Bp0002d0300dc09dsc00dp00ic09isc00ip00')
2011-10-24 21:50:07,272 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'pci:v000010ECd00008168sv00001043sd00008367bc02sc00i00')
2011-10-24 21:50:07,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'platform:regulatory')
2011-10-24 21:50:07,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001043sd000082D4bc0Csc03i00')
2011-10-24 21:50:07,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'input:b0003v056Ap00D4e0106-e0,1,3,k140,141,14A,14B,14C,ra0,1,18,mlsfw')
2011-10-24 21:50:07,273 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xb6a8f6cc> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-10-24 21:50:07,340 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-24 21:50:07,340 DEBUG: nvidia_173 is not the alternative in use
2011-10-24 21:50:08,142 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-24 21:50:08,142 DEBUG: nvidia_173_updates is not the alternative in use
2011-10-24 21:50:08,868 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-24 21:50:08,868 DEBUG: nvidia_current is not the alternative in use
2011-10-24 21:50:09,601 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-24 21:50:09,601 DEBUG: KMH enabled: False
2011-10-24 21:50:10,321 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-24 21:50:10,321 DEBUG: nvidia_173 is not the alternative in use
2011-10-24 21:50:10,361 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-24 21:50:10,361 DEBUG: nvidia_173 is not the alternative in use
2011-10-24 21:50:10,390 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-24 21:50:10,390 DEBUG: nvidia_173_updates is not the alternative in use
2011-10-24 21:50:10,419 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-24 21:50:10,419 DEBUG: nvidia_current is not the alternative in use
2011-10-24 21:50:10,450 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-24 21:50:10,450 DEBUG: KMH enabled: False
2011-10-24 21:50:12,326 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-24 21:50:12,326 DEBUG: nvidia_current is not the alternative in use
2011-10-24 21:50:14,928 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current-updates/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current-updates/alt_ld.so.conf
2011-10-24 21:50:14,928 DEBUG: nvidia_current is not the alternative in use
2011-10-24 21:50:18,403 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-10-24 21:50:18,403 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-10-24 21:50:32,044 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-24 21:50:32,044 DEBUG: KMH enabled: False
2011-10-24 21:50:32,071 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-24 21:50:32,071 DEBUG: KMH enabled: False
2011-10-24 21:50:42,989 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-24 21:50:42,989 DEBUG: nvidia_173 is not the alternative in use
2011-10-24 21:50:43,021 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-24 21:50:43,021 DEBUG: nvidia_173_updates is not the alternative in use
2011-10-24 21:50:43,066 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-24 21:50:43,066 DEBUG: KMH enabled: False
2011-10-24 21:50:43,093 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-24 21:50:43,093 DEBUG: KMH enabled: False
2011-10-24 21:50:43,136 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-24 21:50:43,136 DEBUG: nvidia_current_updates is not the alternative in use
2011-10-24 21:50:43,184 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-24 21:50:43,184 DEBUG: KMH enabled: False
2011-10-24 21:50:43,219 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-24 21:50:43,219 DEBUG: KMH enabled: False
2011-10-24 21:50:43,271 DEBUG: NVidia(nvidia_173).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-24 21:50:43,272 DEBUG: nvidia_173 is not the alternative in use
2011-10-24 21:50:43,303 DEBUG: NVidia(nvidia_173_updates).enabled(): target_alt None current_alt /usr/lib/nvidia-current/ld.so.conf other target alt None other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-24 21:50:43,303 DEBUG: nvidia_173_updates is not the alternative in use
2011-10-24 21:50:43,333 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-24 21:50:43,333 DEBUG: KMH enabled: False
2011-10-24 21:50:43,359 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-24 21:50:43,360 DEBUG: KMH enabled: False
2011-10-24 21:50:43,401 DEBUG: NVidia(nvidia_current_updates).enabled(): target_alt /usr/lib/nvidia-current-updates/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current-updates/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2011-10-24 21:50:43,401 DEBUG: nvidia_current_updates is not the alternative in use
```

---

### Post by Krakken on 2011-10-24
Also I get different boot result with different kernel (maybe it's obvious...doh!!)

3.0.0-13          small screen and no mouse working
3.0.0-12 pae   small screen
3.0.0-12          bad splash screen, low resolution, double screen mirrow

and no possibility to install nvidia driver for all three...

---

### Post by Krakken on 2011-10-24
OK guess what??? I cleaned out my systems and reinstalled a fresh 11.10..
After install activated nvidia-current this time without problems.
Now my 22" asus screen work well but no dual screen available. The second screen gets reconized as samsung 19" but when  try to configure it as twinscreen from the nvidia pannel averithing disappear and I get a mouse pointer on an empty screen...after boot back to normality, one screen right resolution...


I think I will buy a new hard-disk and install ubuntu 10.10 LTS there...no more surprise..

Do you have any suggestion on how to configure xorg to make dual screen work??

Thanks appreciated your help!!

---

### Post by MAFoElffen on 2011-10-24
> **Krakken said:**
> Also I get different boot result with different kernel (maybe it's obvious...doh!!)

3.0.0-13          small screen and no mouse working
3.0.0-12 pae   small screen
3.0.0-12          bad splash screen, low resolution, double screen mirrow

and no possibility to install nvidia driver for all three...
Looking thru your jockey log, You installed nvidia-96, nvidia-173 and nvidia-current.  When it updates, it tries to update each and crashes on that with conflicting pieces.

Being it's a NVidia GeoForce 9400GT, nvidia-96 doesn't work with that at all. nVidia-173 might work, but if it did, it wouldn't be well.  Nvidia-current is the one recommended, but it is not going for you because of residuals left over from the other 2 drivers...

So:
1. First we want to check and update our blacklist to make sure any files and modules that we know of can cause conflicts are in there.     
```
     [FONT=monospace]
[/FONT]sudo gedit /etc/modprobe.d/blacklist.conf

```We want to make sure they have these lines... Some of these wouldn't be  on a fresh install but would be a problem if it was updated from a  previous version. Check these lines and save:     
```

blacklist vga16fb 
blacklist rivafb 
blacklist rivatv 
blacklist nouveau 
blacklist lbm-nouveau 
blacklist nvidiafb 
blacklist nvidia-96
blacklist nvidia-173 

```"Then" we should be able to clean up and install the driver:
```
[FONT=monospace]
[/FONT]sudo apt-get update 
sudo apt-get install linux-headers-'uname -r' 
sudo apt-get remove nvidia-* 
sudo apt-get install nvidia-current   
sudo nvidia-xconfig
sudo apt-get upgrade

```Tell me how it goes...

---

### Post by subehsharma on 2011-11-10
Best method to getaway from this problem is to install fix404. You can read about it more here:

Under Ubuntu, the APT package index is a database containing all packages of repositories (PPAs) defined in the /etc/apt/sources.list file. To update this database after adding some repositories, we need to use this command from the Terminal:

sudo apt-get update

Sometimes, when running the command given above, we get error messages (404 Not Found) that are the result of wrong PPAs, which may slow down the update process via the Terminal. In fact, this 404 Not Found error messages are not harmful at all, but you can use Fix404 to detect and remove these PPAs.

To install Fix404 on Ubuntu 11.04, launch the Terminal and run these commands:

sudo apt-add-repository ppa:lkjoel/fix404
sudo apt-get update
sudo apt-get install fix404

To install on Ubuntu 10.10/10.04, download this deb package here.

To start using Fix404, run this command (root privileges required):

sudo fix404

Then follow displayed instructions to disable PPAs causing the 404 Not Found Error.

[http://www.upubuntu.com/2011/07/remove-ubuntu-ppas-that-cause-404-not.html](http://www.upubuntu.com/2011/07/remove-ubuntu-ppas-that-cause-404-not.html)

---

### Post by Solomoriah on 2011-11-14
As I noted in another thread, I can't install fix404 because I get a 404 error (irony!) during apt-get update for that PPA.

Running Oneiric, BTW, and I'm getting

Building only for 3.0.0-12-generic-pae
Building for architecture i686
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.

while running dpkg-reconfigure nvidia-current.  I've found someone else with this issue (in a blog post) though I've lost the link just now... he said he needed to install the kernel headers to get this to install.

But I have them installed already.  What now?  What the heck does it need?

EDIT:  Just to show that I have them, here's the relevant part of the output from dpkg -l:

ii  linux-headers-3.0.0-1 3.0.0-12.20           Header files related to Linux kernel version 3.0.0
ii  linux-headers-3.0.0-1 3.0.0-12.20           Linux kernel headers for version 3.0.0 on x86/x86_64

---

### Post by MAFoElffen on 2011-11-14
> **Solomoriah said:**
> As I noted in another thread, I can't install fix404 because I get a 404 error (irony!) during apt-get update for that PPA.

Running Oneiric, BTW, and I'm getting

Building only for 3.0.0-12-generic-pae
Building for architecture i686
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.

while running dpkg-reconfigure nvidia-current.  I've found someone else with this issue (in a blog post) though I've lost the link just now... he said he needed to install the kernel headers to get this to install.

But I have them installed already.  What now?  What the heck does it need?

EDIT:  Just to show that I have them, here's the relevant part of the output from dpkg -l:

ii  linux-headers-3.0.0-1 3.0.0-12.20           Header files related to Linux kernel version 3.0.0
ii  linux-headers-3.0.0-1 3.0.0-12.20           Linux kernel headers for version 3.0.0 on x86/x86_64
Okay... lets get you going again.  Sorry, there was such a time between posts, I sort of lost track of you.

Yes, not having a headers file messes with NVidia drivers.  Used to be a problem with Natty, but don't see that often at current. (Still sometimes) I usually have the in my instructions as a safeguard... as it doesn't do anything if it is present...

First problem in just booting is your xorg.conf file... It has two different drivers being loaded for the same card... That isn't going to work out.  

I suggested a method to boot to a Command-line in post #2... do that, then
```

sudo mv /etc/X11/xorg.conf ~/Documents/xorg.conf.old[FONT=monospace]
[/FONT]echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf
echo RUN+="/sbin/modprobe nvidia" > /etc/udev/rules.d/90-modprobe.rules
sudo update-initramfs -u
sudo reboot

```That should get you back in to your sytem, where you can be in an environment you are use to while you work out your driver problems.

Please refer to these to use as reference:
**[B]Sticky:**[/B]                                      [COLOR=#008C00]**[all variants]**[/COLOR]                          [Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535") (Look at the bottom of post #1 and post #2)
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Installing NVidia Binary Drivers]("http://ubuntuforums.org/showpost.php?p=10909540&postcount=280")**[/SIZE][/COLOR][/SIZE][/COLOR] (Even though geared for nvidia binaries, the same file dependencies apply)

If you purge any remnants of old drivers as i instructed in post #2
then before installing anything, did
```

sudo apt-get install linux-headers-'uname -r'

```That would "verfiy" that it's there before you install your drivers.

I'll keep this thread up in my browser for a couple days and see how things go for you.

---

### Post by Solomoriah on 2011-11-14
I believe you've mistaken me for the other fellow.  However, the thread you posted a link to may contain my solution.  I hope the other guy has good luck also.

---

### Post by efflandt on 2011-11-15
> **Krakken said:**
> ```
Err http://ppa.lunchpad.net/ubuntu-x-swat/x-updates/ubuntu/ oneiric/main nvidia-settings i386 285.05.09-0ubuntu1~oneiric~xup1
could not resolve 'ppa.lunchpad.net'
Failed to fetch http://ppa.lunchpad.net/ubuntu-x-swat/x-updates/ubuntu/ oneiric/main nvidia-settings i386 285.05.09-0ubuntu1~oneiric~xup1_i386.deb
Could not resolve 'ppa.lunchpad.net'
E:Unable to fetch some archives maybe run apt-get update or try with --fix-missing?
```

Didn't anyone notice the missing letter in this error earlier in the thread?  Maybe a typo was made when this ppa was added to software sources (it should be ppa.launchpad.net, not lunchpad)? That may be a reason for something missing.

---

### Post by Krakken on 2011-11-24
Reinstalled everything band no works smoothly...the only thingh i didn't ma ke this ti me is TO update packages, expecially x-org...

Now it works well but i'm afraid TO ma ke the updates.

Thanks TO everyone.

K

---

### Post by Dukius on 2011-11-27
Thank you a million MAFoElffen!!!!

It worked for me like a charm, I was desesperated. Many thanks!!! :P



> **MAFoElffen said:**
> Looking thru your jockey log, You installed nvidia-96, nvidia-173 and nvidia-current.  When it updates, it tries to update each and crashes on that with conflicting pieces.

Being it's a NVidia GeoForce 9400GT, nvidia-96 doesn't work with that at all. nVidia-173 might work, but if it did, it wouldn't be well.  Nvidia-current is the one recommended, but it is not going for you because of residuals left over from the other 2 drivers...

So:
1. First we want to check and update our blacklist to make sure any files and modules that we know of can cause conflicts are in there.     
```
     [FONT=monospace]
[/FONT]sudo gedit /etc/modprobe.d/blacklist.conf

```We want to make sure they have these lines... Some of these wouldn't be  on a fresh install but would be a problem if it was updated from a  previous version. Check these lines and save:     
```

blacklist vga16fb 
blacklist rivafb 
blacklist rivatv 
blacklist nouveau 
blacklist lbm-nouveau 
blacklist nvidiafb 
blacklist nvidia-96
blacklist nvidia-173 

```"Then" we should be able to clean up and install the driver:
```
[FONT=monospace]
[/FONT]sudo apt-get update 
sudo apt-get install linux-headers-'uname -r' 
sudo apt-get remove nvidia-* 
sudo apt-get install nvidia-current   
sudo nvidia-xconfig
sudo apt-get upgrade

```Tell me how it goes...

---

### Post by MAFoElffen on 2011-11-27
> **Dukius said:**
> Thank you a million MAFoElffen!!!!

It worked for me like a charm, I was desesperated. Many thanks!!! :P
Your very welcome. Please use the thread tools link above to mark this thread as solved.

---

### Post by ray field on 2011-12-18
> **MAFoElffen said:**
> Looking thru your jockey log, You installed nvidia-96, nvidia-173 and nvidia-current.  When it updates, it tries to update each and crashes on that with conflicting pieces.

Being it's a NVidia GeoForce 9400GT, nvidia-96 doesn't work with that at all. nVidia-173 might work, but if it did, it wouldn't be well.  Nvidia-current is the one recommended, but it is not going for you because of residuals left over from the other 2 drivers...

So:
1. First we want to check and update our blacklist to make sure any files and modules that we know of can cause conflicts are in there.     
```
     [FONT=monospace]
[/FONT]sudo gedit /etc/modprobe.d/blacklist.conf

```We want to make sure they have these lines... Some of these wouldn't be  on a fresh install but would be a problem if it was updated from a  previous version. Check these lines and save:     
```

blacklist vga16fb 
blacklist rivafb 
blacklist rivatv 
blacklist nouveau 
blacklist lbm-nouveau 
blacklist nvidiafb 
blacklist nvidia-96
blacklist nvidia-173 

```"Then" we should be able to clean up and install the driver:
```
[FONT=monospace]
[/FONT]sudo apt-get update 
sudo apt-get install linux-headers-'uname -r' 
sudo apt-get remove nvidia-* 
sudo apt-get install nvidia-current   
sudo nvidia-xconfig
sudo apt-get upgrade

```Tell me how it goes...

I've been having difficulty with my Lucid installation -- since I upgraded to PAE every time I update the kernel the system throws an graphics config error on reboot, where it's stuck in VGA.  I wonder if this remedy would work for me.  

```
lspci | grep VGA
```

returns

```
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)
```

I don't have a jockey.log, but here is /var/log/jockey.log.1:
```

2011-10-29 22:05:48,635 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc>
2011-10-29 22:05:48,644 DEBUG: reading modalias file /lib/modules/2.6.38-12-generic-pae/modules.alias
2011-10-29 22:05:48,827 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2011-10-29 22:05:48,841 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-10-29 22:05:48,876 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2011-10-29 22:05:48,877 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2011-10-29 22:05:48,880 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2011-10-29 22:05:48,890 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2011-10-29 22:05:48,903 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-10-29 22:05:49,157 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-10-29 22:05:49,249 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-10-29 22:05:49,250 DEBUG: Firmware for DVB cards not available
2011-10-29 22:05:49,250 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2011-10-29 22:05:49,312 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2011-10-29 22:05:49,312 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2011-10-29 22:05:49,327 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2011-10-29 22:05:49,327 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2011-10-29 22:05:49,327 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-10-29 22:05:49,369 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-10-29 22:05:49,389 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-10-29 22:05:49,397 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-29 22:05:49,430 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-10-29 22:05:49,438 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-29 22:05:49,439 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-10-29 22:05:49,450 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-10-29 22:05:49,453 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-10-29 22:05:49,460 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-29 22:05:49,460 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-10-29 22:05:49,465 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-10-29 22:05:49,465 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-10-29 22:05:49,465 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-10-29 22:05:49,465 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-10-29 22:05:49,470 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-10-29 22:05:49,473 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-10-29 22:05:49,480 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-10-29 22:05:49,481 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-10-29 22:05:49,493 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-10-29 22:05:49,500 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-10-29 22:05:49,500 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-10-29 22:05:49,500 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-10-29 22:05:49,509 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-10-29 22:05:49,652 DEBUG: Software modem not available
2011-10-29 22:05:49,653 DEBUG: all custom handlers loaded
2011-10-29 22:05:49,653 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001043sd000082D4bc0Csc03i00')
2011-10-29 22:05:49,944 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001043sd000082D4bc0Csc05i00')
2011-10-29 22:05:50,177 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:50,177 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v00008086d00003A16sv00001043sd000082D4bc06sc01i00')
2011-10-29 22:05:50,181 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:50,181 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-29 22:05:50,181 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'acpi:PNP0800:')
2011-10-29 22:05:50,182 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001043sd000082D4bc0Csc03i00')
2011-10-29 22:05:50,185 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-29 22:05:50,186 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-10-29 22:05:50,211 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v00008086d00003A26sv00001043sd000082D4bc01sc01i85')
2011-10-29 22:05:50,215 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-29 22:05:50,220 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:50,220 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-29 22:05:50,220 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'platform:pcspkr')
2011-10-29 22:05:50,221 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:50,221 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:50,221 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001043sd000082D4bc0Csc03i00')
2011-10-29 22:05:50,225 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'platform:eisa')
2011-10-29 22:05:50,225 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v00008086d00003A20sv00001043sd000082D4bc01sc01i8a')
2011-10-29 22:05:50,229 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v000010DEd000006E4sv0000196Esd000005CCbc03sc00i00')
2011-10-29 22:05:50,562 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:50,562 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:50,564 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, enabled] NVIDIA accelerated graphics driver)
2011-10-29 22:05:51,077 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-10-29 22:05:51,175 DEBUG: nvidia_173 is not the alternative in use
2011-10-29 22:05:51,079 DEBUG: got handler xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-10-29 22:05:51,178 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, enabled] NVIDIA accelerated graphics driver)
2011-10-29 22:05:51,275 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'usb:v0C0BpB159d0112dc00dsc00dp00ic08isc06ip50')
2011-10-29 22:05:51,276 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,277 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'usb:v050Dp0307d0000dc09dsc00dp02ic09isc00ip02')
2011-10-29 22:05:51,293 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-10-29 22:05:51,293 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-29 22:05:51,293 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('printer_deviceid', 'MFG:Canon;MDL:MP530;DES:Canon MP530;CMD:BJL,BJRaster3,BSCCe;')
2011-10-29 22:05:51,294 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v00008086d00002E20sv00001043sd000082D3bc06sc00i00')
2011-10-29 22:05:51,297 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'acpi:INT0800:')
2011-10-29 22:05:51,298 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001043sd000082D4bc0Csc03i20')
2011-10-29 22:05:51,301 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-29 22:05:51,301 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-29 22:05:51,301 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'usb:v05ACp1294d0001dc00dsc00dp00icFFiscFEip02')
2011-10-29 22:05:51,326 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v000011ABd00004364sv00001043sd000081F8bc02sc00i00')
2011-10-29 22:05:51,354 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,354 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'usb:v046Dp0990d0008dcEFdsc02dp01ic01isc01ip00')
2011-10-29 22:05:51,386 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,386 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,386 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('printer_deviceid', 'MFG:Canon;MDL:MP530 FAX;DES:Canon MP530 FAX;CMD:MultiPASS 2.1;')
2011-10-29 22:05:51,386 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v000011C1d00005811sv00001043sd00008294bc0Csc00i10')
2011-10-29 22:05:51,387 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,387 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'input:b0003v046Dp0990e0008-e0,1,kD4,ramlsfw')
2011-10-29 22:05:51,387 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,387 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'usb:v062Ap0252d0000dc00dsc00dp00ic03isc01ip02')
2011-10-29 22:05:51,388 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,388 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,388 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v000011ABd00006121sv00001043sd00008212bc01sc01i8f')
2011-10-29 22:05:51,389 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,389 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_marvell', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,389 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001043sd00008311bc04sc03i00')
2011-10-29 22:05:51,392 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,393 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1201:bd08/05/2008:svnSystemmanufacturer:pnP5QDELUXE:pvrSystemVersion:rvnASUSTeKComputerINC.:rnP5QDELUXE:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2011-10-29 22:05:51,408 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'usb:v1A40p0101d0100dc09dsc00dp02ic09isc00ip02')
2011-10-29 22:05:51,408 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-29 22:05:51,409 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'usb:v04A9p1712d0110dc00dsc00dp00ic07isc01ip02')
2011-10-29 22:05:51,409 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usblp', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,409 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-10-29 22:05:51,410 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'option', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,410 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'usb:v046Dp0990d0008dcEFdsc02dp01ic0Eisc01ip00')
2011-10-29 22:05:51,411 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,411 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,411 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'usb:v5678p1234d0100dc00dsc00dp00ic08isc06ip50')
2011-10-29 22:05:51,411 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,412 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,412 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'acpi:PNP0501:')
2011-10-29 22:05:51,412 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-29 22:05:51,412 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'usb:v046Dp0990d0008dcEFdsc02dp01ic0Eisc02ip00')
2011-10-29 22:05:51,413 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,413 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v000011ABd00004320sv00001043sd0000811Abc02sc00i00')
2011-10-29 22:05:51,413 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'skge', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,413 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'usb:v05ACp1294d0001dc00dsc00dp00icFFiscFDip01')
2011-10-29 22:05:51,414 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ipheth', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,414 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001043sd000082D4bc0Csc03i00')
2011-10-29 22:05:51,418 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001043sd000082D4bc06sc04i01')
2011-10-29 22:05:51,421 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001043sd000082D4bc0Csc03i00')
2011-10-29 22:05:51,424 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-10-29 22:05:51,425 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,425 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-29 22:05:51,425 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'usb:v05ACp1294d0001dc00dsc00dp00ic06isc01ip01')
2011-10-29 22:05:51,425 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001043sd000082D4bc0Csc03i00')
2011-10-29 22:05:51,429 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'usb:v046Dp0990d0008dcEFdsc02dp01ic01isc02ip00')
2011-10-29 22:05:51,430 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,430 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-29 22:05:51,430 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'usb:v04A9p1712d0110dc00dsc00dp00icFFisc00ipFF')
2011-10-29 22:05:51,431 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001043sd000082D4bc0Csc03i20')
2011-10-29 22:05:51,434 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'input:b0003v062Ap0252e0110-e0,1,2,4,k110,111,112,113,114,r0,1,6,8,am4,lsfw')
2011-10-29 22:05:51,434 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,434 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-10-29 22:05:51,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001043sd000082D4bc0Csc03i00')
2011-10-29 22:05:51,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001043sd000082D4bc0Csc05i00')
2011-10-29 22:05:51,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v00008086d00003A16sv00001043sd000082D4bc06sc01i00')
2011-10-29 22:05:51,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-29 22:05:51,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'acpi:PNP0800:')
2011-10-29 22:05:51,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001043sd000082D4bc0Csc03i00')
2011-10-29 22:05:51,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-29 22:05:51,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-10-29 22:05:51,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v00008086d00003A26sv00001043sd000082D4bc01sc01i85')
2011-10-29 22:05:51,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-29 22:05:51,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-29 22:05:51,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'platform:pcspkr')
2011-10-29 22:05:51,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001043sd000082D4bc0Csc03i00')
2011-10-29 22:05:51,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'platform:eisa')
2011-10-29 22:05:51,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v00008086d00003A20sv00001043sd000082D4bc01sc01i8a')
2011-10-29 22:05:51,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v000010DEd000006E4sv0000196Esd000005CCbc03sc00i00')
2011-10-29 22:05:51,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'usb:v0C0BpB159d0112dc00dsc00dp00ic08isc06ip50')
2011-10-29 22:05:51,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'usb:v050Dp0307d0000dc09dsc00dp02ic09isc00ip02')
2011-10-29 22:05:51,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-10-29 22:05:51,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-29 22:05:51,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('printer_deviceid', 'MFG:Canon;MDL:MP530;DES:Canon MP530;CMD:BJL,BJRaster3,BSCCe;')
2011-10-29 22:05:51,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v00008086d00002E20sv00001043sd000082D3bc06sc00i00')
2011-10-29 22:05:51,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'acpi:INT0800:')
2011-10-29 22:05:51,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001043sd000082D4bc0Csc03i20')
2011-10-29 22:05:51,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-29 22:05:51,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-29 22:05:51,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'usb:v05ACp1294d0001dc00dsc00dp00icFFiscFEip02')
2011-10-29 22:05:51,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v000011ABd00004364sv00001043sd000081F8bc02sc00i00')
2011-10-29 22:05:51,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'usb:v046Dp0990d0008dcEFdsc02dp01ic01isc01ip00')
2011-10-29 22:05:51,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('printer_deviceid', 'MFG:Canon;MDL:MP530 FAX;DES:Canon MP530 FAX;CMD:MultiPASS 2.1;')
2011-10-29 22:05:51,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v000011C1d00005811sv00001043sd00008294bc0Csc00i10')
2011-10-29 22:05:51,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'input:b0003v046Dp0990e0008-e0,1,kD4,ramlsfw')
2011-10-29 22:05:51,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'usb:v062Ap0252d0000dc00dsc00dp00ic03isc01ip02')
2011-10-29 22:05:51,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v000011ABd00006121sv00001043sd00008212bc01sc01i8f')
2011-10-29 22:05:51,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001043sd00008311bc04sc03i00')
2011-10-29 22:05:51,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1201:bd08/05/2008:svnSystemmanufacturer:pnP5QDELUXE:pvrSystemVersion:rvnASUSTeKComputerINC.:rnP5QDELUXE:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2011-10-29 22:05:51,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'usb:v1A40p0101d0100dc09dsc00dp02ic09isc00ip02')
2011-10-29 22:05:51,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-29 22:05:51,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'usb:v04A9p1712d0110dc00dsc00dp00ic07isc01ip02')
2011-10-29 22:05:51,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-10-29 22:05:51,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'usb:v046Dp0990d0008dcEFdsc02dp01ic0Eisc01ip00')
2011-10-29 22:05:51,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'usb:v5678p1234d0100dc00dsc00dp00ic08isc06ip50')
2011-10-29 22:05:51,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'acpi:PNP0501:')
2011-10-29 22:05:51,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-29 22:05:51,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'usb:v046Dp0990d0008dcEFdsc02dp01ic0Eisc02ip00')
2011-10-29 22:05:51,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v000011ABd00004320sv00001043sd0000811Abc02sc00i00')
2011-10-29 22:05:51,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'usb:v05ACp1294d0001dc00dsc00dp00icFFiscFDip01')
2011-10-29 22:05:51,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001043sd000082D4bc0Csc03i00')
2011-10-29 22:05:51,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001043sd000082D4bc06sc04i01')
2011-10-29 22:05:51,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001043sd000082D4bc0Csc03i00')
2011-10-29 22:05:51,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-10-29 22:05:51,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-29 22:05:51,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'usb:v05ACp1294d0001dc00dsc00dp00ic06isc01ip01')
2011-10-29 22:05:51,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001043sd000082D4bc0Csc03i00')
2011-10-29 22:05:51,440 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'usb:v046Dp0990d0008dcEFdsc02dp01ic01isc02ip00')
2011-10-29 22:05:51,440 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-29 22:05:51,440 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'usb:v04A9p1712d0110dc00dsc00dp00icFFisc00ipFF')
2011-10-29 22:05:51,440 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001043sd000082D4bc0Csc03i20')
2011-10-29 22:05:51,440 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'input:b0003v062Ap0252e0110-e0,1,2,4,k110,111,112,113,114,r0,1,6,8,am4,lsfw')
2011-10-29 22:05:51,440 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-10-29 22:05:51,491 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc>
2011-10-29 22:05:51,496 DEBUG: reading modalias file /lib/modules/2.6.38-12-generic-pae/modules.alias
2011-10-29 22:05:51,619 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2011-10-29 22:05:51,620 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-10-29 22:05:51,654 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2011-10-29 22:05:51,656 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2011-10-29 22:05:51,658 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2011-10-29 22:05:51,659 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2011-10-29 22:05:51,662 DEBUG: updating <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac>
2011-10-29 22:05:51,662 DEBUG: Querying openprinting.org database...
2011-10-29 22:05:51,662 DEBUG:    ... querying for MFG:Canon;CMD:BJL,BJRaster3,BSCCe;SOJ:TXT01;MDL:MP530;CLS:PRINTER;DES:Canon MP530;VER:1.10;STA:10;FSI:02;HRI:OTH;
2011-10-29 22:05:53,022 ERROR:   openprinting.org query failed: (None, None, None)
2011-10-29 22:05:53,022 ERROR:   openprinting.org query failed: (<type 'exceptions.TypeError'>, TypeError('Parse() argument 1 must be string or read-only buffer, not tuple',), <traceback object at 0xa57e694>)
2011-10-29 22:05:53,023 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-10-29 22:05:53,023 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-10-29 22:05:53,024 DEBUG: Firmware for DVB cards not available
2011-10-29 22:05:53,024 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2011-10-29 22:05:53,025 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2011-10-29 22:05:53,025 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2011-10-29 22:05:53,025 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2011-10-29 22:05:53,025 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2011-10-29 22:05:53,025 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-10-29 22:05:53,030 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-10-29 22:05:53,033 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-10-29 22:05:53,033 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-29 22:05:53,035 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-10-29 22:05:53,035 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-29 22:05:53,035 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-10-29 22:05:53,039 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-10-29 22:05:53,041 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-10-29 22:05:53,042 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-29 22:05:53,042 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-10-29 22:05:53,047 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-10-29 22:05:53,047 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-10-29 22:05:53,047 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-10-29 22:05:53,047 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-10-29 22:05:53,052 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-10-29 22:05:53,054 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-10-29 22:05:53,055 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-10-29 22:05:53,055 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-10-29 22:05:53,059 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-10-29 22:05:53,059 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-10-29 22:05:53,059 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-10-29 22:05:53,060 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-10-29 22:05:53,061 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-10-29 22:05:53,069 DEBUG: Software modem not available
2011-10-29 22:05:53,070 DEBUG: all custom handlers loaded
2011-10-29 22:05:53,070 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('printer_deviceid', 'MFG:Canon;CMD:BJL,BJRaster3,BSCCe;SOJ:TXT01;MDL:MP530;CLS:PRINTER;DES:Canon MP530;VER:1.10;STA:10;FSI:02;HRI:OTH;')
2011-10-29 22:05:53,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('printer_deviceid', 'MFG:Canon;CMD:BJL,BJRaster3,BSCCe;SOJ:TXT01;MDL:MP530;CLS:PRINTER;DES:Canon MP530;VER:1.10;STA:10;FSI:02;HRI:OTH;')
```

---

### Post by MAFoElffen on 2011-12-18
> **ray field said:**
> I've been having difficulty with my Lucid installation -- since I upgraded to PAE every time I update the kernel the system throws an graphics config error on reboot, where it's stuck in VGA.  I wonder if this remedy would work for me.  

```
lspci | grep VGA
```returns

```
01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)
```I don't have a jockey.log, but here is /var/log/jockey.log.1:
```

2011-10-29 22:05:48,635 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc>
2011-10-29 22:05:48,644 DEBUG: reading modalias file /lib/modules/2.6.38-12-generic-pae/modules.alias
2011-10-29 22:05:48,827 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2011-10-29 22:05:48,841 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-10-29 22:05:48,876 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2011-10-29 22:05:48,877 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2011-10-29 22:05:48,880 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2011-10-29 22:05:48,890 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2011-10-29 22:05:48,903 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-10-29 22:05:49,157 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-10-29 22:05:49,249 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-10-29 22:05:49,250 DEBUG: Firmware for DVB cards not available
2011-10-29 22:05:49,250 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2011-10-29 22:05:49,312 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2011-10-29 22:05:49,312 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2011-10-29 22:05:49,327 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2011-10-29 22:05:49,327 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2011-10-29 22:05:49,327 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-10-29 22:05:49,369 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-10-29 22:05:49,389 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-10-29 22:05:49,397 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-29 22:05:49,430 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-10-29 22:05:49,438 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-29 22:05:49,439 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-10-29 22:05:49,450 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-10-29 22:05:49,453 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-10-29 22:05:49,460 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-29 22:05:49,460 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-10-29 22:05:49,465 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-10-29 22:05:49,465 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-10-29 22:05:49,465 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-10-29 22:05:49,465 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-10-29 22:05:49,470 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-10-29 22:05:49,473 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-10-29 22:05:49,480 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-10-29 22:05:49,481 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-10-29 22:05:49,493 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-10-29 22:05:49,500 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-10-29 22:05:49,500 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-10-29 22:05:49,500 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-10-29 22:05:49,509 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-10-29 22:05:49,652 DEBUG: Software modem not available
2011-10-29 22:05:49,653 DEBUG: all custom handlers loaded
2011-10-29 22:05:49,653 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001043sd000082D4bc0Csc03i00')
2011-10-29 22:05:49,944 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001043sd000082D4bc0Csc05i00')
2011-10-29 22:05:50,177 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_i801', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:50,177 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v00008086d00003A16sv00001043sd000082D4bc06sc01i00')
2011-10-29 22:05:50,181 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'iTCO_wdt', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:50,181 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-29 22:05:50,181 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'acpi:PNP0800:')
2011-10-29 22:05:50,182 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001043sd000082D4bc0Csc03i00')
2011-10-29 22:05:50,185 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-29 22:05:50,186 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-10-29 22:05:50,211 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v00008086d00003A26sv00001043sd000082D4bc01sc01i85')
2011-10-29 22:05:50,215 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-29 22:05:50,220 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:50,220 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-29 22:05:50,220 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'platform:pcspkr')
2011-10-29 22:05:50,221 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:50,221 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:50,221 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001043sd000082D4bc0Csc03i00')
2011-10-29 22:05:50,225 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'platform:eisa')
2011-10-29 22:05:50,225 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v00008086d00003A20sv00001043sd000082D4bc01sc01i8a')
2011-10-29 22:05:50,229 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v000010DEd000006E4sv0000196Esd000005CCbc03sc00i00')
2011-10-29 22:05:50,562 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:50,562 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:50,564 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, enabled] NVIDIA accelerated graphics driver)
2011-10-29 22:05:51,077 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-10-29 22:05:51,175 DEBUG: nvidia_173 is not the alternative in use
2011-10-29 22:05:51,079 DEBUG: got handler xorg:nvidia_173([NvidiaDriver173, nonfree, disabled] NVIDIA accelerated graphics driver)
2011-10-29 22:05:51,178 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, enabled] NVIDIA accelerated graphics driver)
2011-10-29 22:05:51,275 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'usb:v0C0BpB159d0112dc00dsc00dp00ic08isc06ip50')
2011-10-29 22:05:51,276 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,277 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,277 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'usb:v050Dp0307d0000dc09dsc00dp02ic09isc00ip02')
2011-10-29 22:05:51,293 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-10-29 22:05:51,293 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-29 22:05:51,293 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('printer_deviceid', 'MFG:Canon;MDL:MP530;DES:Canon MP530;CMD:BJL,BJRaster3,BSCCe;')
2011-10-29 22:05:51,294 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v00008086d00002E20sv00001043sd000082D3bc06sc00i00')
2011-10-29 22:05:51,297 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'acpi:INT0800:')
2011-10-29 22:05:51,298 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001043sd000082D4bc0Csc03i20')
2011-10-29 22:05:51,301 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-29 22:05:51,301 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-29 22:05:51,301 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'usb:v05ACp1294d0001dc00dsc00dp00icFFiscFEip02')
2011-10-29 22:05:51,326 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v000011ABd00004364sv00001043sd000081F8bc02sc00i00')
2011-10-29 22:05:51,354 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,354 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'usb:v046Dp0990d0008dcEFdsc02dp01ic01isc01ip00')
2011-10-29 22:05:51,386 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,386 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,386 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('printer_deviceid', 'MFG:Canon;MDL:MP530 FAX;DES:Canon MP530 FAX;CMD:MultiPASS 2.1;')
2011-10-29 22:05:51,386 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v000011C1d00005811sv00001043sd00008294bc0Csc00i10')
2011-10-29 22:05:51,387 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,387 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'input:b0003v046Dp0990e0008-e0,1,kD4,ramlsfw')
2011-10-29 22:05:51,387 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,387 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'usb:v062Ap0252d0000dc00dsc00dp00ic03isc01ip02')
2011-10-29 22:05:51,388 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbhid', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,388 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usbmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,388 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v000011ABd00006121sv00001043sd00008212bc01sc01i8f')
2011-10-29 22:05:51,389 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,389 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_marvell', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,389 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001043sd00008311bc04sc03i00')
2011-10-29 22:05:51,392 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,393 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1201:bd08/05/2008:svnSystemmanufacturer:pnP5QDELUXE:pvrSystemVersion:rvnASUSTeKComputerINC.:rnP5QDELUXE:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2011-10-29 22:05:51,408 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'usb:v1A40p0101d0100dc09dsc00dp02ic09isc00ip02')
2011-10-29 22:05:51,408 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-29 22:05:51,409 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'usb:v04A9p1712d0110dc00dsc00dp00ic07isc01ip02')
2011-10-29 22:05:51,409 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usblp', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,409 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-10-29 22:05:51,410 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'option', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,410 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'usb:v046Dp0990d0008dcEFdsc02dp01ic0Eisc01ip00')
2011-10-29 22:05:51,411 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,411 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,411 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'usb:v5678p1234d0100dc00dsc00dp00ic08isc06ip50')
2011-10-29 22:05:51,411 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uas', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,412 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'usb_storage', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,412 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'acpi:PNP0501:')
2011-10-29 22:05:51,412 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-29 22:05:51,412 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'usb:v046Dp0990d0008dcEFdsc02dp01ic0Eisc02ip00')
2011-10-29 22:05:51,413 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,413 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v000011ABd00004320sv00001043sd0000811Abc02sc00i00')
2011-10-29 22:05:51,413 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'skge', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,413 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'usb:v05ACp1294d0001dc00dsc00dp00icFFiscFDip01')
2011-10-29 22:05:51,414 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ipheth', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,414 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001043sd000082D4bc0Csc03i00')
2011-10-29 22:05:51,418 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001043sd000082D4bc06sc04i01')
2011-10-29 22:05:51,421 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001043sd000082D4bc0Csc03i00')
2011-10-29 22:05:51,424 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-10-29 22:05:51,425 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,425 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-29 22:05:51,425 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'usb:v05ACp1294d0001dc00dsc00dp00ic06isc01ip01')
2011-10-29 22:05:51,425 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001043sd000082D4bc0Csc03i00')
2011-10-29 22:05:51,429 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'usb:v046Dp0990d0008dcEFdsc02dp01ic01isc02ip00')
2011-10-29 22:05:51,430 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_usb_audio', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,430 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-29 22:05:51,430 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'usb:v04A9p1712d0110dc00dsc00dp00icFFisc00ipFF')
2011-10-29 22:05:51,431 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001043sd000082D4bc0Csc03i20')
2011-10-29 22:05:51,434 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'input:b0003v062Ap0252e0110-e0,1,2,4,k110,111,112,113,114,r0,1,6,8,am4,lsfw')
2011-10-29 22:05:51,434 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-10-29 22:05:51,434 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-10-29 22:05:51,434 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v00008086d00003A37sv00001043sd000082D4bc0Csc03i00')
2011-10-29 22:05:51,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v00008086d00003A30sv00001043sd000082D4bc0Csc05i00')
2011-10-29 22:05:51,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v00008086d00003A16sv00001043sd000082D4bc06sc01i00')
2011-10-29 22:05:51,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'acpi:PNP0000:')
2011-10-29 22:05:51,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'acpi:PNP0800:')
2011-10-29 22:05:51,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v00008086d00003A38sv00001043sd000082D4bc0Csc03i00')
2011-10-29 22:05:51,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-10-29 22:05:51,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-10-29 22:05:51,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v00008086d00003A26sv00001043sd000082D4bc01sc01i85')
2011-10-29 22:05:51,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-10-29 22:05:51,435 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'acpi:PNP0103:')
2011-10-29 22:05:51,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'platform:pcspkr')
2011-10-29 22:05:51,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v00008086d00003A36sv00001043sd000082D4bc0Csc03i00')
2011-10-29 22:05:51,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'platform:eisa')
2011-10-29 22:05:51,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v00008086d00003A20sv00001043sd000082D4bc01sc01i8a')
2011-10-29 22:05:51,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v000010DEd000006E4sv0000196Esd000005CCbc03sc00i00')
2011-10-29 22:05:51,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'usb:v0C0BpB159d0112dc00dsc00dp00ic08isc06ip50')
2011-10-29 22:05:51,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'usb:v050Dp0307d0000dc09dsc00dp02ic09isc00ip02')
2011-10-29 22:05:51,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-10-29 22:05:51,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'acpi:PNP0200:')
2011-10-29 22:05:51,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('printer_deviceid', 'MFG:Canon;MDL:MP530;DES:Canon MP530;CMD:BJL,BJRaster3,BSCCe;')
2011-10-29 22:05:51,436 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v00008086d00002E20sv00001043sd000082D3bc06sc00i00')
2011-10-29 22:05:51,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'acpi:INT0800:')
2011-10-29 22:05:51,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v00008086d00003A3Csv00001043sd000082D4bc0Csc03i20')
2011-10-29 22:05:51,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'acpi:PNP0100:')
2011-10-29 22:05:51,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-10-29 22:05:51,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'usb:v05ACp1294d0001dc00dsc00dp00icFFiscFEip02')
2011-10-29 22:05:51,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v000011ABd00004364sv00001043sd000081F8bc02sc00i00')
2011-10-29 22:05:51,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'usb:v046Dp0990d0008dcEFdsc02dp01ic01isc01ip00')
2011-10-29 22:05:51,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('printer_deviceid', 'MFG:Canon;MDL:MP530 FAX;DES:Canon MP530 FAX;CMD:MultiPASS 2.1;')
2011-10-29 22:05:51,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v000011C1d00005811sv00001043sd00008294bc0Csc00i10')
2011-10-29 22:05:51,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'input:b0003v046Dp0990e0008-e0,1,kD4,ramlsfw')
2011-10-29 22:05:51,437 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'usb:v062Ap0252d0000dc00dsc00dp00ic03isc01ip02')
2011-10-29 22:05:51,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v000011ABd00006121sv00001043sd00008212bc01sc01i8f')
2011-10-29 22:05:51,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v00008086d00003A3Esv00001043sd00008311bc04sc03i00')
2011-10-29 22:05:51,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvr1201:bd08/05/2008:svnSystemmanufacturer:pnP5QDELUXE:pvrSystemVersion:rvnASUSTeKComputerINC.:rnP5QDELUXE:rvrRev1.xx:cvnChassisManufacture:ct3:cvrChassisVersion:')
2011-10-29 22:05:51,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'usb:v1A40p0101d0100dc09dsc00dp02ic09isc00ip02')
2011-10-29 22:05:51,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-10-29 22:05:51,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'usb:v04A9p1712d0110dc00dsc00dp00ic07isc01ip02')
2011-10-29 22:05:51,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-10-29 22:05:51,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'usb:v046Dp0990d0008dcEFdsc02dp01ic0Eisc01ip00')
2011-10-29 22:05:51,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'usb:v5678p1234d0100dc00dsc00dp00ic08isc06ip50')
2011-10-29 22:05:51,438 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'acpi:PNP0501:')
2011-10-29 22:05:51,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-10-29 22:05:51,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'usb:v046Dp0990d0008dcEFdsc02dp01ic0Eisc02ip00')
2011-10-29 22:05:51,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v000011ABd00004320sv00001043sd0000811Abc02sc00i00')
2011-10-29 22:05:51,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'usb:v05ACp1294d0001dc00dsc00dp00icFFiscFDip01')
2011-10-29 22:05:51,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v00008086d00003A39sv00001043sd000082D4bc0Csc03i00')
2011-10-29 22:05:51,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v00008086d0000244Esv00001043sd000082D4bc06sc04i01')
2011-10-29 22:05:51,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v00008086d00003A34sv00001043sd000082D4bc0Csc03i00')
2011-10-29 22:05:51,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-10-29 22:05:51,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-10-29 22:05:51,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'usb:v05ACp1294d0001dc00dsc00dp00ic06isc01ip01')
2011-10-29 22:05:51,439 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v00008086d00003A35sv00001043sd000082D4bc0Csc03i00')
2011-10-29 22:05:51,440 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'usb:v046Dp0990d0008dcEFdsc02dp01ic01isc02ip00')
2011-10-29 22:05:51,440 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'platform:reg-dummy')
2011-10-29 22:05:51,440 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'usb:v04A9p1712d0110dc00dsc00dp00icFFisc00ipFF')
2011-10-29 22:05:51,440 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'pci:v00008086d00003A3Asv00001043sd000082D4bc0Csc03i20')
2011-10-29 22:05:51,440 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'input:b0003v062Ap0252e0110-e0,1,2,4,k110,111,112,113,114,r0,1,6,8,am4,lsfw')
2011-10-29 22:05:51,440 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-10-29 22:05:51,491 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc>
2011-10-29 22:05:51,496 DEBUG: reading modalias file /lib/modules/2.6.38-12-generic-pae/modules.alias
2011-10-29 22:05:51,619 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2011-10-29 22:05:51,620 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-10-29 22:05:51,654 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2011-10-29 22:05:51,656 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2011-10-29 22:05:51,658 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2011-10-29 22:05:51,659 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2011-10-29 22:05:51,662 DEBUG: updating <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac>
2011-10-29 22:05:51,662 DEBUG: Querying openprinting.org database...
2011-10-29 22:05:51,662 DEBUG:    ... querying for MFG:Canon;CMD:BJL,BJRaster3,BSCCe;SOJ:TXT01;MDL:MP530;CLS:PRINTER;DES:Canon MP530;VER:1.10;STA:10;FSI:02;HRI:OTH;
2011-10-29 22:05:53,022 ERROR:   openprinting.org query failed: (None, None, None)
2011-10-29 22:05:53,022 ERROR:   openprinting.org query failed: (<type 'exceptions.TypeError'>, TypeError('Parse() argument 1 must be string or read-only buffer, not tuple',), <traceback object at 0xa57e694>)
2011-10-29 22:05:53,023 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-10-29 22:05:53,023 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-10-29 22:05:53,024 DEBUG: Firmware for DVB cards not available
2011-10-29 22:05:53,024 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2011-10-29 22:05:53,025 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2011-10-29 22:05:53,025 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2011-10-29 22:05:53,025 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2011-10-29 22:05:53,025 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2011-10-29 22:05:53,025 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-10-29 22:05:53,030 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-10-29 22:05:53,033 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-10-29 22:05:53,033 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-29 22:05:53,035 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-10-29 22:05:53,035 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-29 22:05:53,035 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-10-29 22:05:53,039 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-10-29 22:05:53,041 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-10-29 22:05:53,042 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-10-29 22:05:53,042 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-10-29 22:05:53,047 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-10-29 22:05:53,047 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-10-29 22:05:53,047 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-10-29 22:05:53,047 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-10-29 22:05:53,052 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-10-29 22:05:53,054 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-10-29 22:05:53,055 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-10-29 22:05:53,055 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-10-29 22:05:53,059 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-10-29 22:05:53,059 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-10-29 22:05:53,059 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-10-29 22:05:53,060 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-10-29 22:05:53,061 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-10-29 22:05:53,069 DEBUG: Software modem not available
2011-10-29 22:05:53,070 DEBUG: all custom handlers loaded
2011-10-29 22:05:53,070 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0xa452bcc> about HardwareID('printer_deviceid', 'MFG:Canon;CMD:BJL,BJRaster3,BSCCe;SOJ:TXT01;MDL:MP530;CLS:PRINTER;DES:Canon MP530;VER:1.10;STA:10;FSI:02;HRI:OTH;')
2011-10-29 22:05:53,070 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa8468ac> about HardwareID('printer_deviceid', 'MFG:Canon;CMD:BJL,BJRaster3,BSCCe;SOJ:TXT01;MDL:MP530;CLS:PRINTER;DES:Canon MP530;VER:1.10;STA:10;FSI:02;HRI:OTH;')
```
Okay... 

Looks like nvidia-173 errored on the install. You know your card's recommened is nvidia current right?[FONT=monospace]

Updated and geared to your errors:
[/FONT]```

sudo apt-get -f install
sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install linux-headers-'uname -r'  
sudo nvidia-installer --uninstall
sudo apt-get remove nvidia-*  
sudo apt-get install nvidia-current    
sudo nvidia-xconfig 
sudo apt-get upgrade

```

---

### Post by ray field on 2011-12-19
> **MAFoElffen said:**
> Okay... 

Looks like nvidia-173 errored on the install. You know your card's recommened is nvidia current right?[FONT=monospace]

Updated and geared to your errors:
[/FONT]```

sudo apt-get -f install
sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install linux-headers-'uname -r'  
sudo nvidia-installer --uninstall
sudo apt-get remove nvidia-*  
sudo apt-get install nvidia-current    
sudo nvidia-xconfig 
sudo apt-get upgrade

```

Alas, no joy -- I'm writing this booted to the 2.6.38-12-generic-pae kernel becuase 2.6.38-13 still returns the video error.  Let me make certain I followed the steps correctly:

1) While booted under 2.6.38-12-generic-pae I edited /etc/modprobe.d/blacklist.conf as you directed above, adding 

blacklist vga16fb 
blacklist rivafb 
blacklist rivatv 
blacklist nouveau 
blacklist lbm-nouveau 
blacklist nvidiafb 
blacklist nvidia-96
blacklist nvidia-173

2) Then I ran each one of those commands.  I should say, 

```
sudo apt-get install linux-headers-'uname -r' 
```

returns

```
E: Couldn't find package linux-headers-uname -r
```

---

### Post by MAFoElffen on 2011-12-19
> **ray field said:**
> Alas, no joy -- I'm writing this booted to the 2.6.38-12-generic-pae kernel becuase 2.6.38-13 still returns the video error.  Let me make certain I followed the steps correctly:

1) While booted under 2.6.38-12-generic-pae I edited /etc/modprobe.d/blacklist.conf as you directed above, adding 

blacklist vga16fb 
blacklist rivafb 
blacklist rivatv 
blacklist nouveau 
blacklist lbm-nouveau 
blacklist nvidiafb 
blacklist nvidia-96
blacklist nvidia-173

2) Then I ran each one of those commands.  I should say, 

```
sudo apt-get install linux-headers-'uname -r' 
```returns

```
E: Couldn't find package linux-headers-uname -r
```
Then run 
```

uname -r

```Then copy the results from that in place of that in that command. For example
```

mafoelffen@precise01:~$ uname -r
[COLOR=Red]3.1.0-1-generic[/COLOR]

```Then ends up as 
```

sudo apt-get linux-headers-[COLOR=Red]3.1.0-1-generic[/COLOR]

```Please post your /var/log/Xorg.0.log file  and results of 
```

dmesg | grep nvidia

```

---

### Post by ray field on 2011-12-20
Tried again, once again booting the latest kernel, I get the popup

[INDENT]Ubuntu is running in low-graphics mode.
The following error was encountered. You may need to update your configuration to solve this.

(EE) NVIDIA: Failed to load the NVIDIA kernel module.  Please check your
(EE) NVIDIA: system's kernel log for additional error messages.
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.[/INDENT]


> Please post your /var/log/Xorg.0.log file  


```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
Current Operating System: Linux Swann-ubuntu 2.6.38-12-generic-pae #51~lucid1-Ubuntu SMP Thu Sep 29 21:44:10 UTC 2011 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-12-generic-pae root=UUID=c9b2fa81-cb35-4f66-92bc-73de7c949bc7 ro quiet splash
Build Date: 20 October 2011  03:05:54PM
xorg-server 2:1.7.6-2ubuntu7.10 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec 20 09:51:05 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:06e4:196e:05cc nVidia Corporation G98 [GeForce 8400 GS] rev 161, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000bc00/128, BIOS @ 0x????????/131072
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 10:38:29 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 09:34:29 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) Dec 20 09:51:05 NVIDIA(0): Enabling RENDER acceleration
(II) Dec 20 09:51:05 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Dec 20 09:51:05 NVIDIA(0):     enabled.
(II) Dec 20 09:51:07 NVIDIA(0): NVIDIA GPU GeForce 8400 GS (G98) at PCI:1:0:0 (GPU-0)
(--) Dec 20 09:51:07 NVIDIA(0): Memory: 524288 kBytes
(--) Dec 20 09:51:07 NVIDIA(0): VideoBIOS: 62.98.29.00.51
(II) Dec 20 09:51:07 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Dec 20 09:51:07 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Dec 20 09:51:07 NVIDIA(0): Connected display device(s) on GeForce 8400 GS at PCI:1:0:0:
(--) Dec 20 09:51:07 NVIDIA(0):     ViewSonic VX2433wm (CRT-1)
(--) Dec 20 09:51:07 NVIDIA(0): ViewSonic VX2433wm (CRT-1): 400.0 MHz maximum pixel clock
(II) Dec 20 09:51:07 NVIDIA(0): Assigned Display Device: CRT-1
(==) Dec 20 09:51:07 NVIDIA(0): 
(==) Dec 20 09:51:07 NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) Dec 20 09:51:07 NVIDIA(0):     will be used as the requested mode.
(==) Dec 20 09:51:07 NVIDIA(0): 
(II) Dec 20 09:51:07 NVIDIA(0): Validated modes:
(II) Dec 20 09:51:07 NVIDIA(0):     "nvidia-auto-select"
(II) Dec 20 09:51:07 NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(--) Dec 20 09:51:07 NVIDIA(0): DPI set to (93, 94); computed from "UseEdidDpi" X config
(--) Dec 20 09:51:07 NVIDIA(0):     option
(==) Dec 20 09:51:07 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Dec 20 09:51:07 NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
(II) Dec 20 09:51:07 NVIDIA(0): Initialized GPU GART.
(II) Dec 20 09:51:07 NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) Dec 20 09:51:07 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Dec 20 09:51:07 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event3)
(**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
(**) Logitech USB Optical Mouse: always reports core events
(**) Logitech USB Optical Mouse: Device: "/dev/input/event3"
(II) Logitech USB Optical Mouse: Found 12 mouse buttons
(II) Logitech USB Optical Mouse: Found scroll wheel(s)
(II) Logitech USB Optical Mouse: Found relative axes
(II) Logitech USB Optical Mouse: Found x and y relative axes
(II) Logitech USB Optical Mouse: Configuring as mouse
(**) Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE)
(II) Logitech USB Optical Mouse: initialized for relative axes.
(II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device UVC Camera (046d:0990) (/dev/input/event4)
(**) UVC Camera (046d:0990): Applying InputClass "evdev keyboard catchall"
(**) UVC Camera (046d:0990): always reports core events
(**) UVC Camera (046d:0990): Device: "/dev/input/event4"
(II) UVC Camera (046d:0990): Found keys
(II) UVC Camera (046d:0990): Configuring as keyboard
(II) XINPUT: Adding extended input device "UVC Camera (046d:0990)" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
```

> and results of 
```

dmesg | grep nvidia

```

```
 dmesg | grep nvidia
[    8.914365] nvidia: module license 'NVIDIA' taints kernel.
[    9.762844] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.762854] nvidia 0000:01:00.0: setting latency timer to 64

```

---

### Post by MAFoElffen on 2011-12-20
> **ray field said:**
> Tried again, once again booting the latest kernel, I get the popup[INDENT]Ubuntu is running in low-graphics mode.
The following error was encountered. You may need to update your configuration to solve this.

(EE) NVIDIA: Failed to load the NVIDIA kernel module.  Please check your
(EE) NVIDIA: system's kernel log for additional error messages.
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.[/INDENT]<<And the Xorg.0.log normal, loaded nvidia kernel module, no errors>>

<<dmesg normal>>

Wait a minute.  By the Xorg.0.log and dmesg, you're saying that the nvidia Kernel module loaded without errors, The syslog showed no errors with the nvidia driver... 

On another astral plane it came up in Low-graphics mode, said it couldn't load the nvidia kernel module and generated an error (That was written to the logs)???

Am I missing something there?

One side, everything looks okay. Other-side, the driver is not even installed....

---

### Post by ray field on 2011-12-20
> **MAFoElffen said:**
> Wait a minute.  By the Xorg.0.log and dmesg, you're saying that the nvidia Kernel module loaded without errors, The syslog showed no errors with the nvidia driver... 

On another astral plane it came up in Low-graphics mode, said it couldn't load the nvidia kernel module and generated an error (That was written to the logs)???

Am I missing something there?

One side, everything looks okay. Other-side, the driver is not even installed....

When I boot 2.6.38-12-generic-pae kernel, as I have now, everything is fine.

Whenever I allow System Update to update to the latest kernel, I get the above message.

Shall I boot to the latest kernel and when I get the popup error, drop down to the terminal logon and

```
sudo apt-get install nvidia-current 
```

then

```
sudo nvidia-xconfig 
```

and if I do and that works, will I be done with this NVIDIA problem?

Sorry if I have caused some confusion, but I just figured installing a new kernel should automatically bring along a correctly-configured display.

---

### Post by MAFoElffen on 2011-12-20
> **ray field said:**
> When I boot 2.6.38-12-generic-pae kernel, as I have now, everything is fine.

Whenever I allow System Update to update to the latest kernel, I get the above message.

Shall I boot to the latest kernel and when I get the popup error, drop down to the terminal logon and

```
sudo apt-get install nvidia-current 
```then

```
sudo nvidia-xconfig 
```and if I do and that works, will I be done with this NVIDIA problem?

Sorry if I have caused some confusion, but I just figured installing a new kernel should automatically bring along a correctly-configured display.
Explaination First- Sometimes a kernel change cause problems with packages that where installed/compiled against an earlier kernel. Graphics drivers seem to be real senstive to this. Usually uninstalling these packages, then installing them... lets them recompile against the newer kernel.  Older kernel will still work with them as the newer kernel may have new capabilities in them, but have regression (or backward compatability) built in.

Having said that- Yes... but add a step before those to uninstall anything previous, such as
```

sudo apt-get remove nvidia*

```
If you don't add that step in, it either says you already have the current package or some people end up with both old and new pieces that don't work.

---

### Post by ray field on 2011-12-20
Maybe we're getting closer to fixing this problem.

I booted to 2.6.38-13-generic-pae, got the error message, dropped down to the terminal, cleaned out the old nvidia drivers, installed nvidia-current, ran nvidia-xconfig. Restarting X did not work, rebooting brought me the same errormessage.  Then I made my way to the "reconfigure graphics" menu selection, which nearly worked -- I got to a decent definition, but could not enable compiz.

Upon rebooting to 2.6.38-12-generic-pae, which had worked, now I found I had the same error message.  I think I selected "reconfigure graphics" & somehow got back to a normal desktop, and then cleaned & reinstalled again & this time I could enable compiz. Is there anything useful in what the process returned?:

```
sudo nvidia-installer --uninstall
[sudo] password for raphael: 
sudo: nvidia-installer: command not found
raphael@Swann-ubuntu:~$ sudo apt-get remove nvidia-*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting nvidia-180-libvdpau-dev for regex 'nvidia-*'
Note, selecting nvidia-185-libvdpau-dev for regex 'nvidia-*'
Note, selecting nvidia-glx-173-dev for regex 'nvidia-*'
Note, selecting nvidia-current for regex 'nvidia-*'
Note, selecting nvidia-libvdpau-ia32 for regex 'nvidia-*'
Note, selecting nvidia-libvdpau1 for regex 'nvidia-*'
Note, selecting nvidia-glx-dev for regex 'nvidia-*'
Note, selecting nvidia-glx-185-dev for regex 'nvidia-*'
Note, selecting nvidia-173 for regex 'nvidia-*'
Note, selecting nvidia-settings for regex 'nvidia-*'
Note, selecting nvidia-185-libvdpau for regex 'nvidia-*'
Note, selecting nvidia-185-kernel-source for regex 'nvidia-*'
Note, selecting nvidia-vdpau-driver for regex 'nvidia-*'
Note, selecting nvidia-96-dev for regex 'nvidia-*'
Note, selecting nvidia-cg-toolkit for regex 'nvidia-*'
Note, selecting nvidia-96 for regex 'nvidia-*'
Note, selecting nvidia-glx-96-dev for regex 'nvidia-*'
Note, selecting nvidia-glx-173 for regex 'nvidia-*'
Note, selecting nvidia-glx-180 for regex 'nvidia-*'
Note, selecting nvidia-glx-185 for regex 'nvidia-*'
Note, selecting nvidia-180-modaliases for regex 'nvidia-*'
Note, selecting nvidia-kernel-common for regex 'nvidia-*'
Note, selecting nvidia-libvdpau for regex 'nvidia-*'
Note, selecting nvidia-current-dev for regex 'nvidia-*'
Note, selecting nvidia-glx-96 for regex 'nvidia-*'
Note, selecting nvidia-glx-180-dev for regex 'nvidia-*'
Note, selecting nvidia-current-modaliases for regex 'nvidia-*'
Note, selecting nvidia-173-modaliases for regex 'nvidia-*'
Note, selecting nvidia-185-modaliases for regex 'nvidia-*'
Note, selecting nvidia-common for regex 'nvidia-*'
Note, selecting nvidia-96-kernel-source for regex 'nvidia-*'
Note, selecting nvidia-173-kernel-source for regex 'nvidia-*'
Note, selecting nvidia-180-kernel-source for regex 'nvidia-*'
Note, selecting nvidia-libvdpau-dev for regex 'nvidia-*'
Note, selecting nvidia-96-modaliases for regex 'nvidia-*'
Note, selecting nvidia-glx for regex 'nvidia-*'
Note, selecting nvidia-173-dev for regex 'nvidia-*'
Note, selecting nvidia-180-libvdpau for regex 'nvidia-*'
The following packages will be REMOVED:
  nvidia-current nvidia-settings
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 74.5MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 315881 files and directories currently installed.)
Removing nvidia-current ...
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/mesa/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
Removing nvidia-settings ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
Processing triggers for python-support ...
raphael@Swann-ubuntu:~$ sudo apt-get install nvidia-current  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  nvidia-settings
The following NEW packages will be installed:
  nvidia-current nvidia-settings
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/24.1MB of archives.
After this operation, 74.5MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Selecting previously deselected package nvidia-current.
(Reading database ... 315755 files and directories currently installed.)
Unpacking nvidia-current (from .../nvidia-current_195.36.24-0ubuntu1~10.04.1_i386.deb) ...
Selecting previously deselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_195.36.08-0ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up nvidia-current (195.36.24-0ubuntu1~10.04.1) ...
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/lib32/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.1 (of link group gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libvdpau_nvidia.so because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so (of link group gl_conf) doesn't exist.
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-2.6.38-12-generic-pae
Loading new nvidia-current-195.36.24 DKMS files...
Building for 2.6.38-12-generic-pae and 2.6.38-13-generic-pae
Building for architecture i686
Building initial module for 2.6.38-12-generic-pae
Done.

nvidia-current.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.38-12-generic-pae/updates/dkms/

depmod.....

DKMS: install Completed.
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.

Setting up nvidia-settings (195.36.08-0ubuntu2) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-37-generic-pae
Processing triggers for python-support ...


```

---

### Post by MAFoElffen on 2011-12-20
> **ray field said:**
> Maybe we're getting closer to fixing this problem.

I booted to 2.6.38-13-generic-pae, got the error message, dropped down to the terminal, cleaned out the old nvidia drivers, installed nvidia-current, ran nvidia-xconfig. Restarting X did not work, rebooting brought me the same errormessage.  Then I made my way to the "reconfigure graphics" menu selection, which nearly worked -- I got to a decent definition, but could not enable compiz.

Upon rebooting to 2.6.38-12-generic-pae, which had worked, now I found I had the same error message.  I think I selected "reconfigure graphics" & somehow got back to a normal desktop, and then cleaned & reinstalled again & this time I could enable compiz. Is there anything useful in what the process returned?:

```
sudo nvidia-installer --uninstall
[sudo] password for raphael: 
sudo: nvidia-installer: command not found
raphael@Swann-ubuntu:~$ sudo apt-get remove nvidia-*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting nvidia-180-libvdpau-dev for regex 'nvidia-*'
Note, selecting nvidia-185-libvdpau-dev for regex 'nvidia-*'
Note, selecting nvidia-glx-173-dev for regex 'nvidia-*'
Note, selecting nvidia-current for regex 'nvidia-*'
Note, selecting nvidia-libvdpau-ia32 for regex 'nvidia-*'
Note, selecting nvidia-libvdpau1 for regex 'nvidia-*'
Note, selecting nvidia-glx-dev for regex 'nvidia-*'
Note, selecting nvidia-glx-185-dev for regex 'nvidia-*'
Note, selecting nvidia-173 for regex 'nvidia-*'
Note, selecting nvidia-settings for regex 'nvidia-*'
Note, selecting nvidia-185-libvdpau for regex 'nvidia-*'
Note, selecting nvidia-185-kernel-source for regex 'nvidia-*'
Note, selecting nvidia-vdpau-driver for regex 'nvidia-*'
Note, selecting nvidia-96-dev for regex 'nvidia-*'
Note, selecting nvidia-cg-toolkit for regex 'nvidia-*'
Note, selecting nvidia-96 for regex 'nvidia-*'
Note, selecting nvidia-glx-96-dev for regex 'nvidia-*'
Note, selecting nvidia-glx-173 for regex 'nvidia-*'
Note, selecting nvidia-glx-180 for regex 'nvidia-*'
Note, selecting nvidia-glx-185 for regex 'nvidia-*'
Note, selecting nvidia-180-modaliases for regex 'nvidia-*'
Note, selecting nvidia-kernel-common for regex 'nvidia-*'
Note, selecting nvidia-libvdpau for regex 'nvidia-*'
Note, selecting nvidia-current-dev for regex 'nvidia-*'
Note, selecting nvidia-glx-96 for regex 'nvidia-*'
Note, selecting nvidia-glx-180-dev for regex 'nvidia-*'
Note, selecting nvidia-current-modaliases for regex 'nvidia-*'
Note, selecting nvidia-173-modaliases for regex 'nvidia-*'
Note, selecting nvidia-185-modaliases for regex 'nvidia-*'
Note, selecting nvidia-common for regex 'nvidia-*'
Note, selecting nvidia-96-kernel-source for regex 'nvidia-*'
Note, selecting nvidia-173-kernel-source for regex 'nvidia-*'
Note, selecting nvidia-180-kernel-source for regex 'nvidia-*'
Note, selecting nvidia-libvdpau-dev for regex 'nvidia-*'
Note, selecting nvidia-96-modaliases for regex 'nvidia-*'
Note, selecting nvidia-glx for regex 'nvidia-*'
Note, selecting nvidia-173-dev for regex 'nvidia-*'
Note, selecting nvidia-180-libvdpau for regex 'nvidia-*'
The following packages will be REMOVED:
  nvidia-current nvidia-settings
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 74.5MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 315881 files and directories currently installed.)
Removing nvidia-current ...
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/mesa/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
Removing nvidia-settings ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
Processing triggers for python-support ...
raphael@Swann-ubuntu:~$ sudo apt-get install nvidia-current  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  nvidia-settings
The following NEW packages will be installed:
  nvidia-current nvidia-settings
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/24.1MB of archives.
After this operation, 74.5MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Selecting previously deselected package nvidia-current.
(Reading database ... 315755 files and directories currently installed.)
Unpacking nvidia-current (from .../nvidia-current_195.36.24-0ubuntu1~10.04.1_i386.deb) ...
Selecting previously deselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_195.36.08-0ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up nvidia-current (195.36.24-0ubuntu1~10.04.1) ...
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/lib32/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.1 (of link group gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libvdpau_nvidia.so because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so (of link group gl_conf) doesn't exist.
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-2.6.38-12-generic-pae
Loading new nvidia-current-195.36.24 DKMS files...
Building for 2.6.38-12-generic-pae and 2.6.38-13-generic-pae
Building for architecture i686
Building initial module for 2.6.38-12-generic-pae
Done.

nvidia-current.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.38-12-generic-pae/updates/dkms/

depmod.....

DKMS: install Completed.
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.

Setting up nvidia-settings (195.36.08-0ubuntu2) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-37-generic-pae
Processing triggers for python-support ...


```
```

sudo apt-get install libvdpau1

```That is the library it's not finding...
Also make sure you have the header file for the running kernel
```

sudo apt-get install kernel-headers-'uname -r'

```If that command error's, do just uname -r and put the results in place of the quotation marks and everything inside it...

Then reinstall and see if the messages are different.

---

### Post by ray field on 2011-12-21
Done, the latest kernel boots just fine. Many thanks, MAFoElffen.

---

