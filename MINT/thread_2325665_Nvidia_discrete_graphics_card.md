---
title: "Nvidia discrete graphics card"
date: 2016-05-24
forum: MINT
---

### Post by Jan_Jindrek on 2016-05-24
Good afternoon, ladies and gentlemen, I hope that some good soul can help me here please.
lspci -nn | grep VGA doesn't find my discrete graphics card, however
lspci -nn | grep 01:00.0 shows some 3D controller nvidia that looks like my graphics card
The problem is, all drivers etc. refuse to work, I have all the typical problems like no direct rendering when I run glxinfo, gdm on my system was just blowing up with every try, so I'm using mdm at the moment - much better debugging options.. cinnamon runs normally.
Important output of glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: Intel Open Source Technology Center
After I have used
prime-select nvidia - I had to uninstall nvidia-prime to get this working, bumblebee shows no errors, already set up it's conf files - I can provide them too if asked

---

### Post by Linuxisfast on 2016-05-24
Do you know the model of your card?

---

### Post by QIII on 2016-05-24
Hello!

Expecting an answer within the hour is a bit demanding.  This is a volunteer forum, populated by users such as yourself.  Perhaps the person with just the right answer has not seen your thread yet.  We ask that users wait 12 hours without a response before bumping their threads.

Just so you know:  Of the views, before you got the answer you did, three had been by users who are logged in.  You, another Staff member and me.  The rest of those views are likely from people looking for an answer and indexing bots.

And, by the way, by bumping so quickly you have removed your thread from the "unanswered posts" query that many of us look at to find posts that need to be answered.

Please be patient and respectful.

Thanks.

---

### Post by Jan_Jindrek on 2016-05-24
I'm so sorry I was just stressed out. Won't happen again I promise.

---

### Post by Bashing-om on 2016-05-24
Jan_Jindrek; Hello'

Let's start by identifying the hardware - and ask the right question of the system.
```

lspci -k | grep -EA2 'VGA|3D'
dpkg -l | grep -i nvidia

```
and see what is installed for a driver(s) .

Maybe next is look at the X log file ?

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-05-25
lspci -k | grep -EA2 'VGA|3D'
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
        Subsystem: Micro-Star International Co., Ltd. [MSI] Device 1112
        Kernel driver in use: i915
--
01:00.0 3D controller: NVIDIA Corporation GM108M [GeForce 840M] (rev a2)
        Subsystem: Micro-Star International Co., Ltd. [MSI] Device 1112
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5249 PCI Express Card Reader (rev 01)


dpkg -l | grep -i nvidia
ii  bbswitch-dkms                                               0.8-2~trustyppa1                                       all          Interface for toggling the power on NVIDIA Optimus video cards
ii  libcg:amd64                                                 3.1.0013-1                                             amd64        Nvidia Cg core runtime library
ii  libcggl:amd64                                               3.1.0013-1                                             amd64        Nvidia Cg Opengl runtime library
rc  libcuda1-304                                                304.131-0ubuntu0.14.04.1                               amd64        NVIDIA CUDA runtime library
rc  libcuda1-340                                                340.96-0ubuntu0.14.04.1                                amd64        NVIDIA CUDA runtime library
rc  libcuda1-346                                                346.47-0ubuntu1~xedgers14.04.1                         i386         NVIDIA CUDA runtime library
ii  libcuda1-352                                                352.63-0ubuntu0.14.04.1                                amd64        NVIDIA CUDA runtime library
rc  libcuda1-352-updates                                        352.63-0ubuntu0.14.04.1                                amd64        NVIDIA CUDA runtime library
rc  libcuinj32-5.5:i386                                         5.5.22-3ubuntu1                                        i386         NVIDIA CUDA INJ runtime library (32-bit)
ii  libcuinj64-5.5:amd64                                        5.5.22-3ubuntu1                                        amd64        NVIDIA CUDA INJ runtime library (64-bit)
rc  nvidia-352                                                  352.63-0ubuntu0.14.04.1                                amd64        NVIDIA binary driver - version 352.63
ii  nvidia-opencl-icd-352                                       352.63-0ubuntu0.14.04.1                                amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                                0.6.2linuxmint1                                        amd64        Tools to enable NVIDIA's Prime
ii  nvidia-profiler                                             5.5.22-3ubuntu1                                        amd64        NVIDIA Profiler for CUDA and OpenCL
ii  nvidia-settings                                             331.20-0ubuntu8                                        amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-visual-profiler                                      5.5.22-3ubuntu1                                        amd64        NVIDIA Visual Profiler

---

### Post by tokyobadger on 2016-05-25
```
dpkg -l | grep -i nvidia
ii  bbswitch-dkms                                                0.8-2~trustyppa1                                       all           Interface for toggling the power on NVIDIA Optimus video cards
ii  libcg:amd64                                                  3.1.0013-1                                             amd64         Nvidia Cg core runtime library
ii  libcggl:amd64                                                3.1.0013-1                                             amd64         Nvidia Cg Opengl runtime library
rc  libcuda1-304                                                 304.131-0ubuntu0.14.04.1                               amd64         NVIDIA CUDA runtime library
rc  libcuda1-340                                                 340.96-0ubuntu0.14.04.1                                amd64         NVIDIA CUDA runtime library
rc  libcuda1-346                                                 346.47-0ubuntu1~xedgers14.04.1                         i386          NVIDIA CUDA runtime library
ii  libcuda1-352                                                 352.63-0ubuntu0.14.04.1                                amd64         NVIDIA CUDA runtime library
rc  libcuda1-352-updates                                         352.63-0ubuntu0.14.04.1                                amd64         NVIDIA CUDA runtime library
rc  libcuinj32-5.5:i386                                          5.5.22-3ubuntu1                                        i386          NVIDIA CUDA INJ runtime library (32-bit)
ii  libcuinj64-5.5:amd64                                         5.5.22-3ubuntu1                                        amd64         NVIDIA CUDA INJ runtime library (64-bit)
rc  nvidia-352                                                   352.63-0ubuntu0.14.04.1                                amd64         NVIDIA binary driver - version 352.63
ii  nvidia-opencl-icd-352                                        352.63-0ubuntu0.14.04.1                                amd64         NVIDIA OpenCL ICD
ii  nvidia-prime                                                 0.6.2linuxmint1                                        amd64         Tools to enable NVIDIA's Prime
ii  nvidia-profiler                                              5.5.22-3ubuntu1                                        amd64         NVIDIA Profiler for CUDA and OpenCL
ii  nvidia-settings                                              331.20-0ubuntu8                                        amd64        Tool  for configuring the NVIDIA graphics driver
ii  nvidia-visual-profiler                                       5.5.22-3ubuntu1                                        amd64         NVIDIA Visual Profiler
```
^^ that's yours - it looks messy and I don't see a gpu driver installed; I also see xedgers (xorg-edgers? it's deprecated) and linuxmint references.

I think you should tell us more about your set-up.

If I run the same command (albeit on a desktop not on a laptop with dual graphics) I get:
```
badger@badgerbox:~$ dpkg -l | grep -i nvidia
ii  bbswitch-dkms                                               0.8-3ubuntu1                                          amd64        Interface for toggling the power on NVIDIA Optimus video cards
ii  libcuda1-364                                                364.19-0ubuntu0~gpu15.10.3                            amd64        NVIDIA CUDA runtime library
rc  nvidia-361                                                  361.28-0ubuntu1                                       amd64        NVIDIA binary driver - version 361.28
ii  nvidia-364                                                  364.19-0ubuntu0~gpu15.10.3                            amd64        NVIDIA binary driver - version 364.19
rc  nvidia-opencl-icd-361                                       361.28-0ubuntu1                                       amd64        NVIDIA OpenCL ICD
ii  nvidia-opencl-icd-364                                       364.19-0ubuntu0~gpu15.10.3                            amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                                0.8.2                                                 amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                             364.15-0ubuntu0~gpu15.10.1                            amd64        Tool for configuring the NVIDIA graphics driver
```
More info from you I think

---

### Post by Bashing-om on 2016-05-25
Jan_Jindrek; Hey;

Making progress, and I do agree with tokyobadger. We need additional info .
What release are you running ? What are you doing with this system ? A gamer ? Heavy duty number crunching ?
How much ram is installed .. enough to handle intensive graphics ?

Nvidia recommends the 361 version driver for your system . Depending, perhaps the 364 will perform better.
We also need to know the Xserver version you have:
show us /// between code tags /// :
```

free -m
lsb_release -a
uname -r
X -version

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And we get this system cleaned up and the proper graphic's driver installed.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-05-27
```
jan@mint ~ $ free -m
             total       used       free     shared    buffers     cached
Mem:          7904       3789       4114        133        262       1782
-/+ buffers/cache:       1743       6160
Swap:            0          0          0
jan@mint ~ $ lsb-release -a
P&#345;íkaz 'lsb-release' nebyl nalezen. M&#283;li jste na mysli:
 P&#345;íkaz 'lsb_release' z balíku 'lsb-release' (main)
lsb-release: p&#345;íkaz nebyl nalezen
jan@mint ~ $ lsb_release -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
Distributor ID: LinuxMint
Description:    Linux Mint 17.1 Rebecca
Release:        17.1
Codename:       rebecca
jan@mint ~ $ uname -r
3.13.0-86-generic
jan@mint ~ $ X -version


X.Org X Server 1.15.1
Release Date: 2014-04-13
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
Current Operating System: Linux mint 3.13.0-86-generic #131-Ubuntu SMP Thu May 12 23:33:13 UTC 2016 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-86-generic root=UUID=05f808d5-075a-4ba8-99e8-bfcfdc0b2807 ro plymouth:debug=1
Build Date: 12 February 2015  02:49:29PM
xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.30.2
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
```

---

### Post by howefield on 2016-05-27
Thread moved to the "*Other Operating Systems*" section.

---

### Post by Bashing-om on 2016-05-27
Jan_Jindrek; Well.

I do not know so much about Mint; We proceed with caution.

I am a believer in taking Nvidia's advise on what version of driver to install . With kernel 3.13.0-86 in 'buntu we have to acquire that driver from our trusted PPA.
Can we do the same for Mint ?
Let's see your sources list to know that out PPA will be compatible and what modules are presently installed.
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*
dpkg -l | grep -i nvidia
lsmod | grep nvidia

```

[INDENT][INDENT]safety is no accident
[/INDENT][/INDENT]

---

### Post by rayhan3 on 2016-05-27
still getting a black screen when to install the Nvidia .. what can do now?

---

### Post by Bashing-om on 2016-05-27
rayhan3; Well ........

Boot to grub's boot menu // 
what results when choosing to boot a recovery kernel ? -> "resume normal boot"
Degraded graphics is acceptable at this point.
Try and install a graphic's driver from Additional Drivers within "soft ware Sources utility ,



[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]many path to an end
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-05-29
```

jan@localhost ~ $ cat -n /etc/apt/sources.list
jan@localhost ~ $ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/alessandrofac93-bumblebee-config-gtk-dev-trusty.list <==
# deb http://ppa.launchpad.net/alessandrofac93/bumblebee-config-gtk-dev/ubuntu trusty main
# deb-src http://ppa.launchpad.net/alessandrofac93/bumblebee-config-gtk-dev/ubuntu trusty main


==> /etc/apt/sources.list.d/apandada1-typhoon-trusty.list <==
deb http://ppa.launchpad.net/apandada1/typhoon/ubuntu trusty main
deb-src http://ppa.launchpad.net/apandada1/typhoon/ubuntu trusty main


==> /etc/apt/sources.list.d/bumblebee-stable-trusty.list <==
deb http://ppa.launchpad.net/bumblebee/stable/ubuntu trusty main
deb-src http://ppa.launchpad.net/bumblebee/stable/ubuntu trusty main


==> /etc/apt/sources.list.d/colingille-freshlight-trusty.list <==
# deb http://ppa.launchpad.net/colingille/freshlight/ubuntu trusty main
# deb-src http://ppa.launchpad.net/colingille/freshlight/ubuntu trusty main


==> /etc/apt/sources.list.d/costales-folder-color-trusty.list <==
deb http://ppa.launchpad.net/costales/folder-color/ubuntu trusty main
deb-src http://ppa.launchpad.net/costales/folder-color/ubuntu trusty main


==> /etc/apt/sources.list.d/crebs-ppa-trusty.list <==
# deb http://ppa.launchpad.net/crebs/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/crebs/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/ffmulticonverter-stable-trusty.list <==
deb http://ppa.launchpad.net/ffmulticonverter/stable/ubuntu trusty main
deb-src http://ppa.launchpad.net/ffmulticonverter/stable/ubuntu trusty main


==> /etc/apt/sources.list.d/getdeb.list <==
# deb http://archive.getdeb.net/ubuntu trusty-getdeb apps 


==> /etc/apt/sources.list.d/google-earth.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb http://dl.google.com/linux/earth/deb/ stable main


==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###                                              
# You may comment out this entry, but any other modifications may be lost.                 
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main                        
                                                                                           
==> /etc/apt/sources.list.d/jtasker-weather-indicator-trusty.list <==
deb http://ppa.launchpad.net/jtasker/weather-indicator/ubuntu trusty main
deb-src http://ppa.launchpad.net/jtasker/weather-indicator/ubuntu trusty main


==> /etc/apt/sources.list.d/mono-xamarin.list <==
deb http://download.mono-project.com/repo/debian wheezy main


==> /etc/apt/sources.list.d/nilarimogard-webupd8-trusty.list <==
deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main
deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main


==> /etc/apt/sources.list.d/official-package-repositories.list <==
deb http://packages.linuxmint.com rebecca main upstream import backport


deb http://extra.linuxmint.com rebecca main


deb http://archive.ubuntu.com/ubuntu trusty main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu trusty-updates main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu/ trusty-security main restricted universe multiverse
deb http://archive.canonical.com/ubuntu/ trusty partner


==> /etc/apt/sources.list.d/playonlinux.list <==
deb http://deb.playonlinux.com/ maverick main


==> /etc/apt/sources.list.d/ravefinity-project-ppa-trusty.list <==
deb http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu trusty main
deb-src http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/rvm-smplayer-trusty.list <==
deb http://ppa.launchpad.net/rvm/smplayer/ubuntu trusty main
deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu trusty main


==> /etc/apt/sources.list.d/strukturag-libde265-trusty.list <==
deb http://ppa.launchpad.net/strukturag/libde265/ubuntu trusty main
deb-src http://ppa.launchpad.net/strukturag/libde265/ubuntu trusty main


==> /etc/apt/sources.list.d/ubuntu-audio-dev-alsa-daily-trusty.list <==
deb http://ppa.launchpad.net/ubuntu-audio-dev/alsa-daily/ubuntu trusty main
deb-src http://ppa.launchpad.net/ubuntu-audio-dev/alsa-daily/ubuntu trusty main


==> /etc/apt/sources.list.d/webupd8team-themes-trusty.list <==
deb http://ppa.launchpad.net/webupd8team/themes/ubuntu trusty main
deb-src http://ppa.launchpad.net/webupd8team/themes/ubuntu trusty main


==> /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list <==
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main
deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main
jan@localhost ~ $ dpkg -l | grep -i nvidia
ii  bbswitch-dkms                                               0.8-2~trustyppa1                                       all          Interface for toggling the power on NVIDIA Optimus video cards
ii  bbswitch-source                                             0.8-2~trustyppa1                                       all          Interface for toggling the power on NVIDIA Optimus video cards
ii  bumblebee                                                   3.2.1-93~trustyppa1                                    amd64        NVIDIA Optimus support
ii  bumblebee-nvidia                                            3.2.1-93~trustyppa1                                    amd64        NVIDIA Optimus support using the proprietary NVIDIA driver
ii  libcg:amd64                                                 3.1.0013-1                                             amd64        Nvidia Cg core runtime library
ii  libcggl:amd64                                               3.1.0013-1                                             amd64        Nvidia Cg Opengl runtime library
rc  libcuda1-304                                                304.131-0ubuntu0.14.04.1                               amd64        NVIDIA CUDA runtime library
rc  libcuda1-340                                                340.96-0ubuntu0.14.04.1                                amd64        NVIDIA CUDA runtime library
rc  libcuda1-346                                                346.47-0ubuntu1~xedgers14.04.1                         i386         NVIDIA CUDA runtime library
ii  libcuda1-352                                                352.63-0ubuntu0.14.04.1                                amd64        NVIDIA CUDA runtime library
rc  libcuda1-352-updates                                        352.63-0ubuntu0.14.04.1                                amd64        NVIDIA CUDA runtime library
rc  libcuinj32-5.5:i386                                         5.5.22-3ubuntu1                                        i386         NVIDIA CUDA INJ runtime library (32-bit)
ii  libcuinj64-5.5:amd64                                        5.5.22-3ubuntu1                                        amd64        NVIDIA CUDA INJ runtime library (64-bit)
ii  nvidia-352                                                  352.63-0ubuntu0.14.04.1                                amd64        NVIDIA binary driver - version 352.63
ii  nvidia-opencl-icd-352                                       352.63-0ubuntu0.14.04.1                                amd64        NVIDIA OpenCL ICD
ii  nvidia-profiler                                             5.5.22-3ubuntu1                                        amd64        NVIDIA Profiler for CUDA and OpenCL
ii  nvidia-settings                                             331.20-0ubuntu8                                        amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-visual-profiler                                      5.5.22-3ubuntu1                                        amd64        NVIDIA Visual Profiler
ii  primus                                                      20150328-1~trustyppa1                                  amd64        client-side GPU offloading for NVIDIA Optimus
jan@localhost ~ $ lsmod | grep nvidia
jan@localhost ~ $ 



```

---

### Post by Bashing-om on 2016-05-29
Jan_Jindrek; Humm ...


Well we can for sure use our trusty repo . No problem there .

I find it strange that dpkg says the 352 version of the driver is installed, but lsmod does not so reflect. Did the driver build ?
show:
```

cat /var/log/Xorg.0.log 

```

Keeping in mind seems that Mint prefers BumbleBee over nvidia-prime for the graphic's controller . Not to sure about that manipulation .

[INDENT][INDENT]sometimes I do wonder
[INDENT][INDENT][INDENT]othertimes, I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-05-29
```
[    28.563] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    28.563] X Protocol Version 11, Revision 0
[    28.563] Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
[    28.563] Current Operating System: Linux localhost 3.13.0-86-generic #131-Ubuntu SMP Thu May 12 23:33:13 UTC 2016 x86_64
[    28.563] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-86-generic root=UUID=05f808d5-075a-4ba8-99e8-bfcfdc0b2807 ro plymouth:debug=1
[    28.563] Build Date: 12 February 2015  02:49:29PM
[    28.563] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support) 
[    28.563] Current version of pixman: 0.30.2
[    28.563]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    28.563] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    28.563] (==) Log file: "/var/log/Xorg.0.log", Time: Sat May 28 02:00:24 2016
[    28.785] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    28.862] (==) No Layout section.  Using the first Screen section.
[    28.862] (==) No screen section available. Using defaults.
[    28.862] (**) |-->Screen "Default Screen Section" (0)
[    28.862] (**) |   |-->Monitor "<default monitor>"
[    28.862] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[    28.862] (==) Automatically adding devices
[    28.862] (==) Automatically enabling devices
[    28.862] (==) Automatically adding GPU devices
[    28.862] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    28.862]    Entry deleted from font path.
[    28.862] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    28.862]    Entry deleted from font path.
[    28.862] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    28.862]    Entry deleted from font path.
[    28.862] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    28.862]    Entry deleted from font path.
[    28.862] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    28.862]    Entry deleted from font path.
[    28.862] (==) FontPath set to:                                                         
        /usr/share/fonts/X11/misc,                                                         
        /usr/share/fonts/X11/Type1,                                                        
        built-ins                                                                          
[    28.862] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    28.862] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    28.862] (II) Loader magic: 0x7f6fdd8c3d40
[    28.862] (II) Module ABI versions:
[    28.862]    X.Org ANSI C Emulation: 0.4
[    28.862]    X.Org Video Driver: 15.0
[    28.862]    X.Org XInput driver : 20.0
[    28.862]    X.Org Server Extension : 8.0
[    28.862] (II) xfree86: Adding drm device (/dev/dri/card0)
[    28.864] (--) PCI:*(0:0:2:0) 8086:0416:1462:1112 rev 6, Mem @ 0xf7400000/4194304, 0xd0000000/268435456, I/O @ 0x0000f000/64
[    28.864] (--) PCI: (0:1:0:0) 10de:1341:1462:1112 rev 162, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    28.864] Initializing built-in extension Generic Event Extension
[    28.864] Initializing built-in extension SHAPE
[    28.864] Initializing built-in extension MIT-SHM
[    28.864] Initializing built-in extension XInputExtension
[    28.864] Initializing built-in extension XTEST
[    28.864] Initializing built-in extension BIG-REQUESTS
[    28.864] Initializing built-in extension SYNC
[    28.864] Initializing built-in extension XKEYBOARD
[    28.864] Initializing built-in extension XC-MISC
[    28.864] Initializing built-in extension SECURITY
[    28.864] Initializing built-in extension XINERAMA
[    28.864] Initializing built-in extension XFIXES
[    28.864] Initializing built-in extension RENDER
[    28.864] Initializing built-in extension RANDR
[    28.864] Initializing built-in extension COMPOSITE
[    28.864] Initializing built-in extension DAMAGE
[    28.864] Initializing built-in extension MIT-SCREEN-SAVER
[    28.864] Initializing built-in extension DOUBLE-BUFFER
[    28.864] Initializing built-in extension RECORD
[    28.864] Initializing built-in extension DPMS
[    28.864] Initializing built-in extension Present
[    28.864] Initializing built-in extension DRI3
[    28.864] Initializing built-in extension X-Resource
[    28.864] Initializing built-in extension XVideo
[    28.864] Initializing built-in extension XVideo-MotionCompensation
[    28.864] Initializing built-in extension SELinux
[    28.864] Initializing built-in extension XFree86-VidModeExtension
[    28.864] Initializing built-in extension XFree86-DGA
[    28.864] Initializing built-in extension XFree86-DRI
[    28.864] Initializing built-in extension DRI2
[    28.864] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    28.864] (II) "glx" will be loaded by default.
[    28.864] (WW) "xmir" is not to be loaded by default. Skipping.
[    28.864] (II) LoadModule: "glx"
[    29.008] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    29.727] (II) Module glx: vendor="NVIDIA Corporation"
[    29.727]    compiled for 4.0.2, module version = 1.0.0
[    29.727]    Module class: X.Org Server Extension
[    29.758] (II) NVIDIA GLX Module  352.63  Sat Nov  7 20:52:00 PST 2015
[    29.758] Loading extension GLX
[    29.758] (==) Matched intel as autoconfigured driver 0
[    29.758] (==) Matched intel as autoconfigured driver 1
[    29.758] (==) Matched modesetting as autoconfigured driver 2
[    29.758] (==) Matched fbdev as autoconfigured driver 3
[    29.758] (==) Matched vesa as autoconfigured driver 4
[    29.758] (==) Assigned the driver to the xf86ConfigLayout
[    29.758] (II) LoadModule: "intel"
[    29.795] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    29.905] (II) Module intel: vendor="X.Org Foundation"
[    29.905]    compiled for 1.15.1, module version = 2.99.917
[    29.905]    Module class: X.Org Video Driver
[    29.905]    ABI class: X.Org Video Driver, version 15.0
[    29.905] (II) LoadModule: "modesetting"
[    29.906] (WW) Warning, couldn't open module modesetting
[    29.906] (II) UnloadModule: "modesetting"
[    29.906] (II) Unloading modesetting
[    29.906] (EE) Failed to load module "modesetting" (module does not exist, 0)
[    29.906] (II) LoadModule: "fbdev"
[    29.906] (WW) Warning, couldn't open module fbdev
[    29.906] (II) UnloadModule: "fbdev"
[    29.906] (II) Unloading fbdev
[    29.906] (EE) Failed to load module "fbdev" (module does not exist, 0)
[    29.906] (II) LoadModule: "vesa"
[    29.906] (WW) Warning, couldn't open module vesa
[    29.906] (II) UnloadModule: "vesa"
[    29.906] (II) Unloading vesa
[    29.906] (EE) Failed to load module "vesa" (module does not exist, 0)
[    29.906] (==) Matched intel as autoconfigured driver 0
[    29.906] (==) Matched intel as autoconfigured driver 1
[    29.906] (==) Matched modesetting as autoconfigured driver 2
[    29.906] (==) Matched fbdev as autoconfigured driver 3
[    29.906] (==) Matched vesa as autoconfigured driver 4
[    29.906] (==) Assigned the driver to the xf86ConfigLayout
[    29.906] (II) LoadModule: "intel"
[    29.906] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    29.906] (II) Module intel: vendor="X.Org Foundation"
[    29.906]    compiled for 1.15.1, module version = 2.99.917
[    29.906]    Module class: X.Org Video Driver
[    29.906]    ABI class: X.Org Video Driver, version 15.0
[    29.906] (II) UnloadModule: "intel"
[    29.906] (II) Unloading intel
[    29.906] (II) Failed to load module "intel" (already loaded, 32623)
[    29.906] (II) LoadModule: "modesetting"
[    29.906] (WW) Warning, couldn't open module modesetting
[    29.906] (II) UnloadModule: "modesetting"
[    29.906] (II) Unloading modesetting
[    29.906] (EE) Failed to load module "modesetting" (module does not exist, 0)
[    29.906] (II) LoadModule: "fbdev"
[    29.906] (WW) Warning, couldn't open module fbdev
[    29.906] (II) UnloadModule: "fbdev"
[    29.906] (II) Unloading fbdev
[    29.906] (EE) Failed to load module "fbdev" (module does not exist, 0)
[    29.906] (II) LoadModule: "vesa"
[    29.907] (WW) Warning, couldn't open module vesa
[    29.907] (II) UnloadModule: "vesa"
[    29.907] (II) Unloading vesa
[    29.907] (EE) Failed to load module "vesa" (module does not exist, 0)
[    29.907] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
        i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
        915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
        Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
        GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    29.907] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    29.907] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    29.907] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    29.907] (++) using VT number 8


[    29.910] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20080730
[    29.910] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20151202.da9ad388-0ubuntu0sarvatt~trusty (Robert Hooker <sarvatt@ubuntu.com>)
[    29.910] (II) intel(0): SNA compiled for use with valgrind
[    29.911] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4600
[    29.911] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2; using a maximum of 2 threads
[    29.911] (II) intel(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[    29.911] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    29.911] (==) intel(0): RGB weight 888
[    29.911] (==) intel(0): Default visual is TrueColor
[    29.911] (II) intel(0): Output eDP1 has no monitor section
[    29.911] (--) intel(0): Found backlight control interface acpi_video0 (type 'firmware') for output eDP1
[    29.911] (II) intel(0): Enabled output eDP1
[    29.911] (II) intel(0): Output VGA1 has no monitor section
[    29.911] (II) intel(0): Enabled output VGA1
[    29.911] (II) intel(0): Output HDMI1 has no monitor section
[    29.911] (II) intel(0): Enabled output HDMI1
[    29.911] (--) intel(0): Using a maximum size of 64x64 for hardware cursors
[    29.911] (II) intel(0): Output VIRTUAL1 has no monitor section
[    29.911] (II) intel(0): Enabled output VIRTUAL1
[    29.911] (--) intel(0): Output eDP1 using initial mode 1920x1080 on pipe 0
[    29.911] (==) intel(0): TearFree disabled
[    29.911] (==) intel(0): DPI set to (96, 96)
[    29.911] (II) Loading sub module "dri2"
[    29.911] (II) LoadModule: "dri2"
[    29.911] (II) Module "dri2" already built-in
[    29.911] (II) Loading sub module "present"
[    29.911] (II) LoadModule: "present"
[    29.911] (WW) Warning, couldn't open module present
[    29.911] (II) UnloadModule: "present"
[    29.911] (II) Unloading present
[    29.911] (EE) intel: Failed to load module "present" (module does not exist, 0)
[    29.914] (==) Depth 24 pixmap format is 32 bpp
[    29.915] (II) intel(0): SNA initialized with Haswell (gen7.5, gt2) backend
[    29.915] (==) intel(0): Backing store enabled
[    29.915] (==) intel(0): Silken mouse enabled
[    29.915] (II) intel(0): HW Cursor enabled
[    29.915] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    29.915] (==) intel(0): DPMS enabled
[    29.915] (==) intel(0): Display hotplug detection enabled
[    29.915] (II) intel(0): [DRI2] Setup complete
[    29.915] (II) intel(0): [DRI2]   DRI driver: i965
[    29.915] (II) intel(0): [DRI2]   VDPAU driver: va_gl
[    29.915] (II) intel(0): direct rendering: DRI2 enabled
[    29.915] (--) RandR disabled
[    29.918] (II) SELinux: Disabled on system
[    29.949] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    29.951] (II) intel(0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    29.951] (II) intel(0): Setting screen physical size to 508 x 285
[    29.955] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    29.956] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    29.956] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.956] (II) LoadModule: "evdev"
[    29.956] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.018] (II) Module evdev: vendor="X.Org Foundation"
[    30.018]    compiled for 1.15.0, module version = 2.8.2
[    30.018]    Module class: X.Org XInput Driver
[    30.018]    ABI class: X.Org XInput driver, version 20.0
[    30.018] (II) Using input driver 'evdev' for 'Power Button'
[    30.018] (**) Power Button: always reports core events
[    30.018] (**) evdev: Power Button: Device: "/dev/input/event3"
[    30.018] (--) evdev: Power Button: Vendor 0 Product 0x1
[    30.018] (--) evdev: Power Button: Found keys
[    30.018] (II) evdev: Power Button: Configuring as keyboard
[    30.018] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    30.018] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    30.018] (**) Option "xkb_rules" "evdev"
[    30.018] (**) Option "xkb_model" "pc105"
[    30.018] (**) Option "xkb_layout" "cz"
[    30.019] (II) XKB: reuse xkmfile /var/lib/xkb/server-583B992BBA3776030BA62AC94FC7F0AE9B04119F.xkm
[    30.020] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[    30.020] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    30.020] (II) Using input driver 'evdev' for 'Video Bus'
[    30.020] (**) Video Bus: always reports core events
[    30.020] (**) evdev: Video Bus: Device: "/dev/input/event8"
[    30.020] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    30.020] (--) evdev: Video Bus: Found keys
[    30.020] (II) evdev: Video Bus: Configuring as keyboard
[    30.020] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input9/event8"
[    30.020] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    30.020] (**) Option "xkb_rules" "evdev"
[    30.020] (**) Option "xkb_model" "pc105"
[    30.020] (**) Option "xkb_layout" "cz"
[    30.020] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    30.020] (II) No input driver specified, ignoring this device.
[    30.020] (II) This device may have been added with another device file.
[    30.020] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    30.020] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    30.020] (II) Using input driver 'evdev' for 'Video Bus'
[    30.020] (**) Video Bus: always reports core events
[    30.020] (**) evdev: Video Bus: Device: "/dev/input/event7"
[    30.020] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    30.020] (--) evdev: Video Bus: Found keys
[    30.020] (II) evdev: Video Bus: Configuring as keyboard
[    30.020] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:45/LNXVIDEO:00/input/input8/event7"
[    30.020] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    30.020] (**) Option "xkb_rules" "evdev"
[    30.020] (**) Option "xkb_model" "pc105"
[    30.020] (**) Option "xkb_layout" "cz"
[    30.020] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    30.020] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    30.020] (II) Using input driver 'evdev' for 'Power Button'
[    30.020] (**) Power Button: always reports core events
[    30.020] (**) evdev: Power Button: Device: "/dev/input/event1"
[    30.020] (--) evdev: Power Button: Vendor 0 Product 0x1
[    30.020] (--) evdev: Power Button: Found keys
[    30.020] (II) evdev: Power Button: Configuring as keyboard
[    30.020] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    30.020] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[    30.021] (**) Option "xkb_rules" "evdev"
[    30.021] (**) Option "xkb_model" "pc105"
[    30.021] (**) Option "xkb_layout" "cz"
[    30.021] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    30.021] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    30.021] (II) Using input driver 'evdev' for 'Sleep Button'
[    30.021] (**) Sleep Button: always reports core events
[    30.021] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    30.021] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    30.021] (--) evdev: Sleep Button: Found keys
[    30.021] (II) evdev: Sleep Button: Configuring as keyboard
[    30.021] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    30.021] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 10)
[    30.021] (**) Option "xkb_rules" "evdev"
[    30.021] (**) Option "xkb_model" "pc105"
[    30.021] (**) Option "xkb_layout" "cz"
[    30.021] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[    30.021] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    30.021] (II) config/udev: Adding input device HDA Intel HDMI HDMI (/dev/input/event12)
[    30.021] (II) No input driver specified, ignoring this device.
[    30.021] (II) This device may have been added with another device file.
[    30.021] (II) config/udev: Adding input device MOSART Semi. 2.4G Wireless Mouse (/dev/input/event5)
[    30.021] (**) MOSART Semi. 2.4G Wireless Mouse: Applying InputClass "evdev pointer catchall"
[    30.021] (II) Using input driver 'evdev' for 'MOSART Semi. 2.4G Wireless Mouse'
[    30.021] (**) MOSART Semi. 2.4G Wireless Mouse: always reports core events
[    30.021] (**) evdev: MOSART Semi. 2.4G Wireless Mouse: Device: "/dev/input/event5"
[    30.021] (--) evdev: MOSART Semi. 2.4G Wireless Mouse: Vendor 0x3938 Product 0x1031
[    30.021] (--) evdev: MOSART Semi. 2.4G Wireless Mouse: Found 9 mouse buttons
[    30.021] (--) evdev: MOSART Semi. 2.4G Wireless Mouse: Found scroll wheel(s)
[    30.021] (--) evdev: MOSART Semi. 2.4G Wireless Mouse: Found relative axes
[    30.021] (--) evdev: MOSART Semi. 2.4G Wireless Mouse: Found x and y relative axes
[    30.021] (--) evdev: MOSART Semi. 2.4G Wireless Mouse: Found absolute axes
[    30.021] (II) evdev: MOSART Semi. 2.4G Wireless Mouse: Forcing absolute x/y axes to exist.
[    30.021] (II) evdev: MOSART Semi. 2.4G Wireless Mouse: Configuring as mouse
[    30.021] (II) evdev: MOSART Semi. 2.4G Wireless Mouse: Adding scrollwheel support
[    30.021] (**) evdev: MOSART Semi. 2.4G Wireless Mouse: YAxisMapping: buttons 4 and 5
[    30.021] (**) evdev: MOSART Semi. 2.4G Wireless Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    30.021] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-6/3-6:1.0/input/input7/event5"
[    30.021] (II) XINPUT: Adding extended input device "MOSART Semi. 2.4G Wireless Mouse" (type: MOUSE, id 11)
[    30.021] (II) evdev: MOSART Semi. 2.4G Wireless Mouse: initialized for relative axes.
[    30.021] (WW) evdev: MOSART Semi. 2.4G Wireless Mouse: ignoring absolute axes.
[    30.021] (**) MOSART Semi. 2.4G Wireless Mouse: (accel) keeping acceleration scheme 1
[    30.021] (**) MOSART Semi. 2.4G Wireless Mouse: (accel) acceleration profile 0
[    30.021] (**) MOSART Semi. 2.4G Wireless Mouse: (accel) acceleration factor: 2.000
[    30.021] (**) MOSART Semi. 2.4G Wireless Mouse: (accel) acceleration threshold: 4
[    30.022] (II) config/udev: Adding input device MOSART Semi. 2.4G Wireless Mouse (/dev/input/mouse0)
[    30.022] (II) No input driver specified, ignoring this device.
[    30.022] (II) This device may have been added with another device file.
[    30.022] (II) config/udev: Adding input device BisonCam, NB Pro (/dev/input/event13)
[    30.022] (**) BisonCam, NB Pro: Applying InputClass "evdev keyboard catchall"
[    30.022] (II) Using input driver 'evdev' for 'BisonCam, NB Pro'
[    30.022] (**) BisonCam, NB Pro: always reports core events
[    30.022] (**) evdev: BisonCam, NB Pro: Device: "/dev/input/event13"
[    30.022] (--) evdev: BisonCam, NB Pro: Vendor 0x5986 Product 0x14c
[    30.022] (--) evdev: BisonCam, NB Pro: Found keys
[    30.022] (II) evdev: BisonCam, NB Pro: Configuring as keyboard
[    30.022] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-8/3-8:1.0/input/input14/event13"
[    30.022] (II) XINPUT: Adding extended input device "BisonCam, NB Pro" (type: KEYBOARD, id 12)
[    30.022] (**) Option "xkb_rules" "evdev"
[    30.022] (**) Option "xkb_model" "pc105"
[    30.022] (**) Option "xkb_layout" "cz"
[    30.022] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event11)
[    30.022] (II) No input driver specified, ignoring this device.
[    30.022] (II) This device may have been added with another device file.
[    30.022] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event10)
[    30.022] (II) No input driver specified, ignoring this device.
[    30.022] (II) This device may have been added with another device file.
[    30.022] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    30.022] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    30.022] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    30.022] (**) AT Translated Set 2 keyboard: always reports core events
[    30.022] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    30.022] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    30.022] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    30.022] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    30.022] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    30.022] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[    30.022] (**) Option "xkb_rules" "evdev"
[    30.022] (**) Option "xkb_model" "pc105"
[    30.022] (**) Option "xkb_layout" "cz"
[    30.022] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event6)
[    30.022] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    30.022] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    30.022] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    30.022] (II) LoadModule: "synaptics"
[    30.023] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    30.023] (II) Module synaptics: vendor="X.Org Foundation"
[    30.023]    compiled for 1.15.0, module version = 1.7.4
[    30.023]    Module class: X.Org XInput Driver
[    30.023]    ABI class: X.Org XInput driver, version 20.0
[    30.023] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    30.023] (**) ETPS/2 Elantech Touchpad: always reports core events
[    30.023] (**) Option "Device" "/dev/input/event6"
[    30.040] (II) synaptics: ETPS/2 Elantech Touchpad: ignoring touch events for semi-multitouch device
[    30.040] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 2356 (res 0)
[    30.040] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 1240 (res 0)
[    30.040] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    30.040] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    30.040] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[    30.040] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    30.040] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    30.040] (**) ETPS/2 Elantech Touchpad: always reports core events
[    30.068] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event6"
[    30.068] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 14)
[    30.068] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    30.068] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[    30.068] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.075
[    30.068] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    30.068] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    30.068] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    30.068] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    30.068] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    30.068] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse1)
[    30.068] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    30.069] (II) config/udev: Adding input device MSI WMI hotkeys (/dev/input/event9)
[    30.069] (**) MSI WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    30.069] (II) Using input driver 'evdev' for 'MSI WMI hotkeys'
[    30.069] (**) MSI WMI hotkeys: always reports core events
[    30.069] (**) evdev: MSI WMI hotkeys: Device: "/dev/input/event9"
[    30.069] (--) evdev: MSI WMI hotkeys: Vendor 0 Product 0
[    30.069] (--) evdev: MSI WMI hotkeys: Found keys
[    30.069] (II) evdev: MSI WMI hotkeys: Configuring as keyboard
[    30.069] (**) Option "config_info" "udev:/sys/devices/virtual/input/input10/event9"
[    30.069] (II) XINPUT: Adding extended input device "MSI WMI hotkeys" (type: KEYBOARD, id 15)
[    30.069] (**) Option "xkb_rules" "evdev"
[    30.069] (**) Option "xkb_model" "pc105"
[    30.069] (**) Option "xkb_layout" "cz"
[    31.912] (II) intel(0): EDID vendor "CMO", prod id 5920
[    31.912] (II) intel(0): Printing DDC gathered Modelines:
[    31.912] (II) intel(0): Modeline "1920x1080"x0.0  138.70  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (66.7 kHz eP)
[    50.393] (II) XKB: reuse xkmfile /var/lib/xkb/server-380215CD03F10668E4B11AD1C12FA19DDFF64277.xkm
[    50.422] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    51.259] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    51.260] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    51.262] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    51.263] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    51.265] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    51.266] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    51.268] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    51.270] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    51.271] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    51.273] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
```

By the way, you are totally right.. there are kernel problems in my system related to latest upgrade.. at which time the drivers and couple of other libraries stopped working too! I'm also including the output of sudo apt-get install nvidia-352 --reinstall here! (sadly, it's in czech, but google translate should be sufficient?

```

&#268;tu seznamy balík&#367;&#8230; Hotovo
Vytvá&#345;í se strom závislostí       
&#268;tu stavové informace&#8230; Hotovo
Následující balík byl nainstalován automaticky a ji&#382; není pot&#345;eba:
  mdm
Pro jeho odstran&#283;ní pou&#382;ijte &#8222;apt-get autoremove&#8220;.
0 aktualizováno, 0 nov&#283; instalováno, 1 p&#345;einstalováno, 0 k odstran&#283;ní a 51 neaktualizováno.
Pot&#345;ebuji stáhnout 60,4 MB archiv&#367;.
Po této operaci bude na disku pou&#382;ito dal&#353;ích 0 B.
Mám:1 http://archive.ubuntu.com/ubuntu/ trusty-updates/restricted nvidia-352 amd64 352.63-0ubuntu0.14.04.1 [60,4 MB]
Sta&#382;eno 60,4 MB za 1min 13s (822 kB/s)                                         
(&#268;tu databázi &#8230; nyní je nainstalováno 484884 soubor&#367; a adresá&#345;&#367;.)
Preparing to unpack &#8230;/nvidia-352_352.63-0ubuntu0.14.04.1_amd64.deb ...
Stopping nvidia-persistenced
nvidia-persistenced: &#382;ádný proces nenalezen
Done.
Removing all DKMS Modules
Done.
Stopping previous nvidia-persistenced
nvidia-persistenced: &#382;ádný proces nenalezen
Done.
Unpacking nvidia-352 (352.63-0ubuntu0.14.04.1) over (352.63-0ubuntu0.14.04.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Nastavuji balík nvidia-352 (352.63-0ubuntu0.14.04.1) &#8230;
INFO:Enable nvidia-352
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
Loading new nvidia-352-352.63 DKMS files...
Building for 3.13.0-86-generic and 3.19.0-32-generic
Building for architecture x86_64
Building initial module for 3.13.0-86-generic
Done.


nvidia_352:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-86-generic/kernel/drivers/char/drm/


nvidia_352_uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-86-generic/kernel/drivers/video/


depmod....


DKMS: install completed.
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.



```

---

### Post by Bashing-om on 2016-05-29
Jan_Jindrek; Ouch !!

Let's put the pieces together:
> 
0 aktualizováno, 0 nov&#283; instalováno, 1 p&#345;einstalováno, 0 k odstran&#283;ní a 51 neaktualizováno.

Translated:
> 
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 51 not upgraded.


and the next :
>  
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.


In small steps, to arrive at booting up with the Nvidia driver rather than Intel - see what we can do to get the driver to build.

1st up is to get this system updated:
```

sudo apt update
sudo apt full-upgrade
sudo apt -f install

```

now did the kernel source files get installed ?

show:
```

dpkg -l | grep linux-

```

and we see what we have to work with and what we must work toward .

[INDENT][INDENT]maybe
[INDENT][INDENT]our work is cut out for us
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-05-30
```

jan@localhost ~ $ sudo apt update && sudo apt full-upgrade && sudo apt-get -f install && dpkg -l | grep linux-
[sudo] password for jan: 
Cíl http://ppa.launchpad.net trusty InRelease
Ign http://dl.google.com stable InRelease                                      
Cíl http://security.ubuntu.com trusty-security InRelease                       
Cíl http://deb.playonlinux.com maverick InRelease                              
Ign http://archive.ubuntu.com trusty InRelease                                 
Ign http://archive.canonical.com trusty InRelease                              
Ign http://ppa.launchpad.net trusty InRelease                                  
Cíl http://dl.google.com stable Release.gpg                                    
Cíl http://security.ubuntu.com trusty-security/main amd64 Packages             
Cíl http://deb.playonlinux.com maverick/main amd64 Packages                    
Mám:1 http://archive.ubuntu.com trusty-updates InRelease [65,9 kB]             
Cíl http://archive.canonical.com trusty Release.gpg                            
Cíl http://ppa.launchpad.net trusty InRelease                                  
Cíl http://deb.playonlinux.com maverick/main i386 Packages                     
Cíl http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Cíl http://dl.google.com stable Release                                        
Cíl http://download.mono-project.com wheezy InRelease                          
Ign http://extra.linuxmint.com rebecca InRelease                               
Cíl http://archive.canonical.com trusty Release                                
Ign http://ppa.launchpad.net trusty InRelease                                  
Cíl http://security.ubuntu.com trusty-security/universe amd64 Packages         
Ign http://packages.linuxmint.com rebecca InRelease                            
Cíl http://dl.google.com stable/main amd64 Packages                            
Cíl http://download.mono-project.com wheezy/main amd64 Packages                
Ign http://ppa.launchpad.net trusty InRelease                                  
Cíl http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Cíl http://archive.canonical.com trusty/partner amd64 Packages                 
Cíl http://download.mono-project.com wheezy/main i386 Packages                 
Cíl http://archive.ubuntu.com trusty Release.gpg                               
Cíl http://ppa.launchpad.net trusty InRelease                                  
Cíl http://extra.linuxmint.com rebecca Release.gpg                             
Cíl http://security.ubuntu.com trusty-security/main i386 Packages              
Cíl http://archive.canonical.com trusty/partner i386 Packages                  
Mám:2 http://archive.ubuntu.com trusty-updates/main amd64 Packages [768 kB]    
Cíl http://packages.linuxmint.com rebecca Release.gpg                          
Cíl http://security.ubuntu.com trusty-security/restricted i386 Packages        
Cíl http://archive.canonical.com trusty/partner Translation-en                 
Cíl http://security.ubuntu.com trusty-security/universe i386 Packages                      
Cíl http://security.ubuntu.com trusty-security/multiverse i386 Packages                    
Cíl http://security.ubuntu.com trusty-security/main Translation-en                         
Cíl http://security.ubuntu.com trusty-security/multiverse Translation-en                   
Cíl http://extra.linuxmint.com rebecca Release                                 
Cíl http://ppa.launchpad.net trusty InRelease                                  
Cíl http://packages.linuxmint.com rebecca Release                              
Cíl http://security.ubuntu.com trusty-security/restricted Translation-en       
Cíl http://ppa.launchpad.net trusty InRelease                                  
Cíl http://security.ubuntu.com trusty-security/universe Translation-en         
Ign http://ppa.launchpad.net trusty InRelease                                  
Mám:3 http://ppa.launchpad.net trusty InRelease [15,5 kB]                      
Cíl http://extra.linuxmint.com rebecca/main amd64 Packages                     
Cíl http://packages.linuxmint.com rebecca/main amd64 Packages                  
Ign http://download.mono-project.com wheezy/main Translation-cs_CZ             
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://download.mono-project.com wheezy/main Translation-cs                
Mám:4 http://archive.ubuntu.com trusty-updates/restricted amd64 Packages [15,9 kB]
Ign http://download.mono-project.com wheezy/main Translation-en                
Cíl http://ppa.launchpad.net trusty InRelease                                  
Mám:5 http://archive.ubuntu.com trusty-updates/universe amd64 Packages [360 kB]
Cíl http://ppa.launchpad.net trusty/main Sources                               
Cíl http://extra.linuxmint.com rebecca/main i386 Packages                      
Cíl http://packages.linuxmint.com rebecca/upstream amd64 Packages              
Cíl http://ppa.launchpad.net trusty/main amd64 Packages                        
Cíl http://ppa.launchpad.net trusty/main i386 Packages                         
Cíl http://ppa.launchpad.net trusty/main Translation-en                        
Cíl http://ppa.launchpad.net trusty Release.gpg                                
Cíl http://ppa.launchpad.net trusty/main Sources                               
Cíl http://packages.linuxmint.com rebecca/import amd64 Packages                
Ign http://deb.playonlinux.com maverick/main Translation-cs_CZ                 
Ign http://deb.playonlinux.com maverick/main Translation-cs                    
Cíl http://ppa.launchpad.net trusty/main amd64 Packages                        
Mám:6 http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages [13,2 kB]
Ign http://deb.playonlinux.com maverick/main Translation-en                    
Cíl http://ppa.launchpad.net trusty/main i386 Packages                         
Mám:7 http://archive.ubuntu.com trusty-updates/main i386 Packages [736 kB]     
Cíl http://ppa.launchpad.net trusty/main Translation-en                        
Cíl http://packages.linuxmint.com rebecca/backport amd64 Packages              
Cíl http://ppa.launchpad.net trusty Release.gpg                                
Ign http://dl.google.com stable/main Translation-cs_CZ                         
Ign http://ppa.launchpad.net trusty Release.gpg                                
Ign http://dl.google.com stable/main Translation-cs                            
Cíl http://ppa.launchpad.net trusty/main Sources                               
Ign http://dl.google.com stable/main Translation-en                            
Cíl http://ppa.launchpad.net trusty/main amd64 Packages                        
Cíl http://packages.linuxmint.com rebecca/main i386 Packages                   
Cíl http://ppa.launchpad.net trusty/main i386 Packages                         
Cíl http://ppa.launchpad.net trusty/main Translation-en                        
Cíl http://ppa.launchpad.net trusty/main Sources                               
Cíl http://ppa.launchpad.net trusty/main amd64 Packages                        
Cíl http://ppa.launchpad.net trusty/main i386 Packages                         
Cíl http://packages.linuxmint.com rebecca/upstream i386 Packages               
Cíl http://ppa.launchpad.net trusty/main Translation-en                        
Cíl http://ppa.launchpad.net trusty/main Sources                               
Cíl http://ppa.launchpad.net trusty/main amd64 Packages                        
Cíl http://ppa.launchpad.net trusty/main i386 Packages                         
Cíl http://ppa.launchpad.net trusty/main Translation-en                        
Cíl http://packages.linuxmint.com rebecca/import i386 Packages                 
Mám:8 http://archive.ubuntu.com trusty-updates/restricted i386 Packages [15,6 kB]
Cíl http://ppa.launchpad.net trusty Release.gpg                                
Mám:9 http://archive.ubuntu.com trusty-updates/universe i386 Packages [361 kB] 
Mám:10 http://ppa.launchpad.net trusty/main Sources [1 780 B]                  
Mám:11 http://ppa.launchpad.net trusty/main amd64 Packages [1 831 B]           
Cíl http://packages.linuxmint.com rebecca/backport i386 Packages               
Mám:12 http://ppa.launchpad.net trusty/main i386 Packages [1 831 B]            
Mám:13 http://ppa.launchpad.net trusty/main Translation-en [251 B]             
Cíl http://ppa.launchpad.net trusty Release.gpg                                
Cíl http://ppa.launchpad.net trusty/main Sources                               
Cíl http://ppa.launchpad.net trusty/main amd64 Packages                        
Cíl http://ppa.launchpad.net trusty/main i386 Packages                         
Mám:14 http://archive.ubuntu.com trusty-updates/multiverse i386 Packages [13,6 kB]
Cíl http://ppa.launchpad.net trusty/main Translation-en                        
Cíl http://ppa.launchpad.net trusty Release                                    
Cíl http://archive.ubuntu.com trusty-updates/main Translation-en               
Cíl http://ppa.launchpad.net trusty Release                                    
Cíl http://archive.ubuntu.com trusty-updates/multiverse Translation-en         
Ign http://ppa.launchpad.net trusty Release                                    
Cíl http://ppa.launchpad.net trusty Release                                    
Cíl http://archive.ubuntu.com trusty-updates/restricted Translation-en         
Cíl http://ppa.launchpad.net trusty Release                                    
Cíl http://archive.ubuntu.com trusty-updates/universe Translation-en           
Cíl http://ppa.launchpad.net trusty/main Sources                               
Cíl http://archive.ubuntu.com trusty Release                                   
Cíl http://ppa.launchpad.net trusty/main amd64 Packages                        
Cíl http://archive.ubuntu.com trusty/main amd64 Packages                       
Cíl http://ppa.launchpad.net trusty/main i386 Packages                         
Cíl http://archive.ubuntu.com trusty/restricted amd64 Packages                 
Cíl http://ppa.launchpad.net trusty/main Translation-en                        
Cíl http://ppa.launchpad.net trusty/main Sources                               
Cíl http://archive.ubuntu.com trusty/universe amd64 Packages                   
Cíl http://ppa.launchpad.net trusty/main amd64 Packages                        
Cíl http://archive.ubuntu.com trusty/multiverse amd64 Packages                 
Cíl http://ppa.launchpad.net trusty/main i386 Packages                         
Cíl http://archive.ubuntu.com trusty/main i386 Packages                        
Ign http://extra.linuxmint.com rebecca/main Translation-cs_CZ                  
Cíl http://archive.ubuntu.com trusty/restricted i386 Packages                  
Cíl http://archive.ubuntu.com trusty/universe i386 Packages                    
Cíl http://archive.ubuntu.com trusty/multiverse i386 Packages                  
Ign http://extra.linuxmint.com rebecca/main Translation-cs                     
Cíl http://archive.ubuntu.com trusty/main Translation-cs                       
Cíl http://archive.ubuntu.com trusty/main Translation-en                       
Ign http://extra.linuxmint.com rebecca/main Translation-en                     
Cíl http://ppa.launchpad.net trusty/main Sources                               
Cíl http://archive.ubuntu.com trusty/multiverse Translation-cs                 
Cíl http://ppa.launchpad.net trusty/main amd64 Packages                        
Cíl http://ppa.launchpad.net trusty/main i386 Packages                 
Cíl http://archive.ubuntu.com trusty/multiverse Translation-en         
Cíl http://ppa.launchpad.net trusty/main Translation-en                
Cíl http://ppa.launchpad.net trusty/main Sources                               
Cíl http://archive.ubuntu.com trusty/restricted Translation-cs                 
Cíl http://ppa.launchpad.net trusty/main amd64 Packages              
Cíl http://archive.ubuntu.com trusty/restricted Translation-en                 
Cíl http://ppa.launchpad.net trusty/main i386 Packages                         
Cíl http://archive.ubuntu.com trusty/universe Translation-cs                   
Cíl http://ppa.launchpad.net trusty/main Translation-en              
Cíl http://archive.ubuntu.com trusty/universe Translation-en         
Ign http://archive.ubuntu.com trusty/main Translation-cs_CZ                    
Ign http://archive.ubuntu.com trusty/multiverse Translation-cs_CZ        
Ign http://archive.ubuntu.com trusty/restricted Translation-cs_CZ
Ign http://archive.ubuntu.com trusty/universe Translation-cs_CZ
Ign http://ppa.launchpad.net trusty/main Translation-cs_CZ
Ign http://ppa.launchpad.net trusty/main Translation-cs                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Err http://ppa.launchpad.net trusty/main Sources                               
  404  Not Found
Err http://ppa.launchpad.net trusty/main amd64 Packages                        
  404  Not Found
Err http://ppa.launchpad.net trusty/main i386 Packages                         
  404  Not Found
Ign http://ppa.launchpad.net trusty/main Translation-cs_CZ                     
Ign http://ppa.launchpad.net trusty/main Translation-cs                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://packages.linuxmint.com rebecca/backport Translation-cs_CZ           
Ign http://packages.linuxmint.com rebecca/backport Translation-cs              
Ign http://packages.linuxmint.com rebecca/backport Translation-en              
Ign http://packages.linuxmint.com rebecca/import Translation-cs_CZ             
Ign http://packages.linuxmint.com rebecca/import Translation-cs                
Ign http://packages.linuxmint.com rebecca/import Translation-en                
Ign http://packages.linuxmint.com rebecca/main Translation-cs_CZ               
Ign http://packages.linuxmint.com rebecca/main Translation-cs                  
Ign http://packages.linuxmint.com rebecca/main Translation-en                  
Ign http://packages.linuxmint.com rebecca/upstream Translation-cs_CZ           
Ign http://packages.linuxmint.com rebecca/upstream Translation-cs              
Ign http://packages.linuxmint.com rebecca/upstream Translation-en              
Sta&#382;eno 2 371 kB za 12s (192 kB/s)
W: Selhalo sta&#382;ení http://ppa.launchpad.net/jtasker/weather-indicator/ubuntu/dists/trusty/main/source/Sources  404  Not Found


W: Selhalo sta&#382;ení http://ppa.launchpad.net/jtasker/weather-indicator/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found


W: Selhalo sta&#382;ení http://ppa.launchpad.net/jtasker/weather-indicator/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found


E: N&#283;které indexové soubory se nepoda&#345;ilo stáhnout. Jsou ignorovány, nebo jsou pou&#382;ity star&#353;í verze.
apt
Usage: apt command [options]
       apt help command [options]


Commands:
autoclean       - Erase old downloaded archive files
autoremove      - Remove automatically all unused packages
build           - Build binary or source packages from sources
build-dep       - Configure build-dependencies for source packages
changelog       - View a package's changelog
check           - Verify that there are no broken dependencies
clean           - Erase downloaded archive files
contains        - List packages containing a file
content         - List files contained in a package
deb             - Install a .deb package
depends         - Show raw dependency information for a package
dist-upgrade    - Perform an upgrade, possibly installing and removing packages
download        - Download the .deb file for a package
dselect-upgrade - Follow dselect selections
held            - List all held packages
help            - Show help for a command
hold            - Hold a package
install         - Install/upgrade packages
policy          - Show policy settings
purge           - Remove packages and their configuration files
rdepends        - Show reverse dependency information for a package
reinstall       - Download and (possibly) reinstall a currently installed package
remove          - Remove packages
search          - Search for a package by name and/or expression
show            - Display detailed information about a package
source          - Download source archives
sources         - Edit /etc/apt/sources.list with nano
unhold          - Unhold a package
update          - Download lists of new/upgradable packages
upgrade         - Perform a safe upgrade
version         - Show the installed version of a package
                        This apt has Super Cow Powers
jan@localhost ~ $ 



```
Included nvidia-352 reinstall.. Thank you so much!

---

### Post by Bashing-om on 2016-05-30
Jan_Jindrek; Hey ...

You are moving to fast for my little mind to follow.

Did you note that this PPA
[http://ppa.launchpad.net/jtasker/weather-indicator/ubuntu/dists/](http://ppa.launchpad.net/jtasker/weather-indicator/ubuntu/dists/)
is no longer supported ?
Remove it from your source list.

Now what have we ?
```

sudo apt update
sudo apt upgrade
sudo apt -f install
dpkg -l | grep linux-

```

[INDENT][INDENT]to install a driver
[INDENT][INDENT][INDENT]we have to make it so
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-05-30
```

jan@localhost ~ $ sudo apt-get upgrade && sudo apt-get -f install && dpkg -l | grep linux-
[sudo] password for jan: 
&#268;tu seznamy balík&#367;&#8230; Hotovo
Vytvá&#345;í se strom závislostí       
&#268;tu stavové informace&#8230; Hotovo
Propo&#269;ítávám aktualizaci&#8230; Hotovo
Následující balík byl nainstalován automaticky a ji&#382; není pot&#345;eba:
  mdm
Pro jeho odstran&#283;ní pou&#382;ijte &#8222;apt-get autoremove&#8220;.
Následující balíky budou aktualizovány:
  apt apt-transport-https apt-utils compiz compiz-core compiz-dev compiz-gnome
  compiz-plugins compiz-plugins-default compiz-plugins-extra
  compiz-plugins-main compiz-plugins-main-default compiz-plugins-main-dev
  compizconfig-backend-gconf compizconfig-settings-manager
  google-chrome-stable libapache2-mod-php5 libapt-inst1.5 libapt-pkg4.12
  libc-bin libc-dev-bin libc6 libc6:i386 libc6-dev libc6-i386 libcompizconfig0
  libcompizconfig0-dev libdecoration0 libdecoration0-dev libsmbclient
  libwbclient0 multiarch-support oem-audio-hda-daily-dkms php-pear php5-cli
  php5-common php5-curl php5-dev php5-gd php5-mysql python-compizconfig
  python-samba python3-apport python3-problem-report samba samba-common
  samba-common-bin samba-dsdb-modules samba-libs smbclient winbind
51 aktualizováno, 0 nov&#283; instalováno, 0 k odstran&#283;ní a 0 neaktualizováno.
Pot&#345;ebuji stáhnout 83,5 MB archiv&#367;.
Po této operaci bude na disku pou&#382;ito dal&#353;ích 3 593 kB.
Chcete pokra&#269;ovat? [Y/n] y
Mám:1 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libc-bin amd64 2.19-0ubuntu6.9 [1 165 kB]
Mám:2 http://ppa.launchpad.net/ubuntu-audio-dev/alsa-daily/ubuntu/ trusty/main oem-audio-hda-daily-dkms all 0.201605300501~ubuntu14.04.1 [267 kB]
Mám:3 http://dl.google.com/linux/chrome/deb/ stable/main google-chrome-stable amd64 51.0.2704.63-1 [49,0 MB]
Mám:4 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libc6-i386 amd64 2.19-0ubuntu6.9 [2 201 kB]
Mám:5 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libc-dev-bin amd64 2.19-0ubuntu6.9 [69,0 kB]
Mám:6 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libc6-dev amd64 2.19-0ubuntu6.9 [1 910 kB]
Mám:7 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libc6 i386 2.19-0ubuntu6.9 [3 988 kB]
Mám:8 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libc6 amd64 2.19-0ubuntu6.9 [4 717 kB]
Mám:9 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libapt-pkg4.12 amd64 1.0.1ubuntu2.14 [638 kB]
Mám:10 http://archive.ubuntu.com/ubuntu/ trusty-updates/main apt amd64 1.0.1ubuntu2.14 [955 kB]
Mám:11 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libapt-inst1.5 amd64 1.0.1ubuntu2.14 [58,6 kB]
Mám:12 http://archive.ubuntu.com/ubuntu/ trusty-updates/main winbind amd64 2:4.3.9+dfsg-0ubuntu0.14.04.3 [411 kB]
Mám:13 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libwbclient0 amd64 2:4.3.9+dfsg-0ubuntu0.14.04.3 [30,9 kB]
Mám:14 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libsmbclient amd64 2:4.3.9+dfsg-0ubuntu0.14.04.3 [53,0 kB]
Mám:15 http://archive.ubuntu.com/ubuntu/ trusty-updates/main smbclient amd64 2:4.3.9+dfsg-0ubuntu0.14.04.3 [312 kB]
Mám:16 http://archive.ubuntu.com/ubuntu/ trusty-updates/main samba amd64 2:4.3.9+dfsg-0ubuntu0.14.04.3 [903 kB]
Mám:17 http://archive.ubuntu.com/ubuntu/ trusty-updates/main samba-common-bin amd64 2:4.3.9+dfsg-0ubuntu0.14.04.3 [508 kB]
Mám:18 http://archive.ubuntu.com/ubuntu/ trusty-updates/main samba-common all 2:4.3.9+dfsg-0ubuntu0.14.04.3 [82,8 kB]
Mám:19 http://archive.ubuntu.com/ubuntu/ trusty-updates/main samba-dsdb-modules amd64 2:4.3.9+dfsg-0ubuntu0.14.04.3 [218 kB]
Mám:20 http://archive.ubuntu.com/ubuntu/ trusty-updates/main python-samba amd64 2:4.3.9+dfsg-0ubuntu0.14.04.3 [1 068 kB]
Mám:21 http://archive.ubuntu.com/ubuntu/ trusty-updates/main samba-libs amd64 2:4.3.9+dfsg-0ubuntu0.14.04.3 [5 144 kB]
Mám:22 http://archive.ubuntu.com/ubuntu/ trusty-updates/main php5-mysql amd64 5.5.9+dfsg-1ubuntu4.17 [63,0 kB]
Mám:23 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libapache2-mod-php5 amd64 5.5.9+dfsg-1ubuntu4.17 [2 212 kB]
Mám:24 http://archive.ubuntu.com/ubuntu/ trusty-updates/main php5-cli amd64 5.5.9+dfsg-1ubuntu4.17 [2 162 kB]
Mám:25 http://archive.ubuntu.com/ubuntu/ trusty-updates/main php5-gd amd64 5.5.9+dfsg-1ubuntu4.17 [27,9 kB]
Mám:26 http://archive.ubuntu.com/ubuntu/ trusty-updates/main php5-curl amd64 5.5.9+dfsg-1ubuntu4.17 [27,3 kB]
Mám:27 http://archive.ubuntu.com/ubuntu/ trusty-updates/main php5-common amd64 5.5.9+dfsg-1ubuntu4.17 [444 kB]
Mám:28 http://archive.ubuntu.com/ubuntu/ trusty-updates/main multiarch-support amd64 2.19-0ubuntu6.9 [4 484 B]
Mám:29 http://archive.ubuntu.com/ubuntu/ trusty-updates/main apt-utils amd64 1.0.1ubuntu2.14 [172 kB]
Mám:30 http://archive.ubuntu.com/ubuntu/ trusty-updates/main apt-transport-https amd64 1.0.1ubuntu2.14 [25,0 kB]
Mám:31 http://archive.ubuntu.com/ubuntu/ trusty-updates/main compiz-gnome amd64 1:0.9.11.3+14.04.20160425-0ubuntu1 [156 kB]
Mám:32 http://archive.ubuntu.com/ubuntu/ trusty-updates/main compiz-dev amd64 1:0.9.11.3+14.04.20160425-0ubuntu1 [76,4 kB]
Mám:33 http://archive.ubuntu.com/ubuntu/ trusty-updates/main compiz-plugins-default amd64 1:0.9.11.3+14.04.20160425-0ubuntu1 [770 kB]
Mám:34 http://archive.ubuntu.com/ubuntu/ trusty-updates/universe compiz-plugins amd64 1:0.9.11.3+14.04.20160425-0ubuntu1 [1 880 kB]
Mám:35 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libdecoration0-dev amd64 1:0.9.11.3+14.04.20160425-0ubuntu1 [6 958 B]
Mám:36 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libdecoration0 amd64 1:0.9.11.3+14.04.20160425-0ubuntu1 [49,2 kB]
Mám:37 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libcompizconfig0-dev amd64 1:0.9.11.3+14.04.20160425-0ubuntu1 [19,8 kB]
Mám:38 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libcompizconfig0 amd64 1:0.9.11.3+14.04.20160425-0ubuntu1 [117 kB]
Mám:39 http://archive.ubuntu.com/ubuntu/ trusty-updates/main compiz-core amd64 1:0.9.11.3+14.04.20160425-0ubuntu1 [296 kB]
Mám:40 http://archive.ubuntu.com/ubuntu/ trusty-updates/main compiz all 1:0.9.11.3+14.04.20160425-0ubuntu1 [4 050 B]
Mám:41 http://archive.ubuntu.com/ubuntu/ trusty-updates/main php-pear all 5.5.9+dfsg-1ubuntu4.17 [267 kB]
Mám:42 http://archive.ubuntu.com/ubuntu/ trusty-updates/main php5-dev amd64 5.5.9+dfsg-1ubuntu4.17 [356 kB]
Mám:43 http://archive.ubuntu.com/ubuntu/ trusty-updates/main python3-problem-report all 2.14.1-0ubuntu3.21 [9 710 B]
Mám:44 http://archive.ubuntu.com/ubuntu/ trusty-updates/main python3-apport all 2.14.1-0ubuntu3.21 [75,3 kB]
Mám:45 http://archive.ubuntu.com/ubuntu/ trusty-updates/universe compiz-plugins-extra all 1:0.9.11.3+14.04.20160425-0ubuntu1 [3 436 B]
Mám:46 http://archive.ubuntu.com/ubuntu/ trusty-updates/universe compiz-plugins-main all 1:0.9.11.3+14.04.20160425-0ubuntu1 [3 432 B]
Mám:47 http://archive.ubuntu.com/ubuntu/ trusty-updates/universe compiz-plugins-main-default all 1:0.9.11.3+14.04.20160425-0ubuntu1 [3 446 B]
Mám:48 http://archive.ubuntu.com/ubuntu/ trusty-updates/main compiz-plugins-main-dev all 1:0.9.11.3+14.04.20160425-0ubuntu1 [3 438 B]
Mám:49 http://archive.ubuntu.com/ubuntu/ trusty-updates/universe compizconfig-backend-gconf all 1:0.9.11.3+14.04.20160425-0ubuntu1 [5 946 B]
Mám:50 http://archive.ubuntu.com/ubuntu/ trusty-updates/universe python-compizconfig amd64 1:0.9.11.3+14.04.20160425-0ubuntu1 [37,1 kB]
Mám:51 http://archive.ubuntu.com/ubuntu/ trusty-updates/universe compizconfig-settings-manager all 1:0.9.11.3+14.04.20160425-0ubuntu1 [574 kB]
Sta&#382;eno 83,5 MB za 1min 9s (1 196 kB/s)                                        
Extrahuji z balík&#367; &#353;ablony: 100%
P&#345;ednastavuji balíky&#8230;
(&#268;tu databázi &#8230; nyní je nainstalováno 509845 soubor&#367; a adresá&#345;&#367;.)
Preparing to unpack &#8230;/libc-bin_2.19-0ubuntu6.9_amd64.deb ...
Unpacking libc-bin (2.19-0ubuntu6.9) over (2.19-0ubuntu6.7) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Nastavuji balík libc-bin (2.19-0ubuntu6.9) &#8230;
(&#268;tu databázi &#8230; nyní je nainstalováno 509844 soubor&#367; a adresá&#345;&#367;.)
Preparing to unpack &#8230;/libc6-i386_2.19-0ubuntu6.9_amd64.deb ...
Unpacking libc6-i386 (2.19-0ubuntu6.9) over (2.19-0ubuntu6.7) ...
Replaced by files in installed package libc6:i386 (2.19-0ubuntu6.7) ...
Preparing to unpack &#8230;/libc-dev-bin_2.19-0ubuntu6.9_amd64.deb ...
Unpacking libc-dev-bin (2.19-0ubuntu6.9) over (2.19-0ubuntu6.7) ...
Preparing to unpack &#8230;/libc6-dev_2.19-0ubuntu6.9_amd64.deb ...
Unpacking libc6-dev:amd64 (2.19-0ubuntu6.9) over (2.19-0ubuntu6.7) ...
Preparing to unpack &#8230;/libc6_2.19-0ubuntu6.9_amd64.deb ...
De-configuring libc6:i386 (2.19-0ubuntu6.7) ...
Unpacking libc6:amd64 (2.19-0ubuntu6.9) over (2.19-0ubuntu6.7) ...
Preparing to unpack &#8230;/libc6_2.19-0ubuntu6.9_i386.deb ...
Unpacking libc6:i386 (2.19-0ubuntu6.9) over (2.19-0ubuntu6.7) ...
Preparing to unpack &#8230;/libapt-pkg4.12_1.0.1ubuntu2.14_amd64.deb ...
Unpacking libapt-pkg4.12:amd64 (1.0.1ubuntu2.14) over (1.0.1ubuntu2.13) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Nastavuji balík libc6:amd64 (2.19-0ubuntu6.9) &#8230;
Nastavuji balík libc6:i386 (2.19-0ubuntu6.9) &#8230;
Nastavuji balík libapt-pkg4.12:amd64 (1.0.1ubuntu2.14) &#8230;
Processing triggers for libc-bin (2.19-0ubuntu6.9) ...
(&#268;tu databázi &#8230; nyní je nainstalováno 509844 soubor&#367; a adresá&#345;&#367;.)
Preparing to unpack &#8230;/apt_1.0.1ubuntu2.14_amd64.deb ...
Unpacking apt (1.0.1ubuntu2.14) over (1.0.1ubuntu2.13) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Nastavuji balík apt (1.0.1ubuntu2.14) &#8230;
Processing triggers for libc-bin (2.19-0ubuntu6.9) ...
(&#268;tu databázi &#8230; nyní je nainstalováno 509844 soubor&#367; a adresá&#345;&#367;.)
Preparing to unpack &#8230;/libapt-inst1.5_1.0.1ubuntu2.14_amd64.deb ...
Unpacking libapt-inst1.5:amd64 (1.0.1ubuntu2.14) over (1.0.1ubuntu2.13) ...
Nastavuji balík libapt-inst1.5:amd64 (1.0.1ubuntu2.14) &#8230;
Processing triggers for libc-bin (2.19-0ubuntu6.9) ...
(&#268;tu databázi &#8230; nyní je nainstalováno 509844 soubor&#367; a adresá&#345;&#367;.)
Preparing to unpack &#8230;/google-chrome-stable_51.0.2704.63-1_amd64.deb ...
Unpacking google-chrome-stable (51.0.2704.63-1) over (50.0.2661.102-1) ...
Preparing to unpack &#8230;/winbind_2%3a4.3.9+dfsg-0ubuntu0.14.04.3_amd64.deb ...
winbind stop/waiting
Unpacking winbind (2:4.3.9+dfsg-0ubuntu0.14.04.3) over (2:4.3.9+dfsg-0ubuntu0.14.04.1) ...
Preparing to unpack &#8230;/libwbclient0_2%3a4.3.9+dfsg-0ubuntu0.14.04.3_amd64.deb ...
Unpacking libwbclient0:amd64 (2:4.3.9+dfsg-0ubuntu0.14.04.3) over (2:4.3.9+dfsg-0ubuntu0.14.04.1) ...
Preparing to unpack &#8230;/libsmbclient_2%3a4.3.9+dfsg-0ubuntu0.14.04.3_amd64.deb ...
Unpacking libsmbclient:amd64 (2:4.3.9+dfsg-0ubuntu0.14.04.3) over (2:4.3.9+dfsg-0ubuntu0.14.04.1) ...
Preparing to unpack &#8230;/smbclient_2%3a4.3.9+dfsg-0ubuntu0.14.04.3_amd64.deb ...
Unpacking smbclient (2:4.3.9+dfsg-0ubuntu0.14.04.3) over (2:4.3.9+dfsg-0ubuntu0.14.04.1) ...
Preparing to unpack &#8230;/samba_2%3a4.3.9+dfsg-0ubuntu0.14.04.3_amd64.deb ...
nmbd stop/waiting
smbd stop/waiting
Unpacking samba (2:4.3.9+dfsg-0ubuntu0.14.04.3) over (2:4.3.9+dfsg-0ubuntu0.14.04.1) ...
Preparing to unpack &#8230;/samba-common-bin_2%3a4.3.9+dfsg-0ubuntu0.14.04.3_amd64.deb ...
Unpacking samba-common-bin (2:4.3.9+dfsg-0ubuntu0.14.04.3) over (2:4.3.9+dfsg-0ubuntu0.14.04.1) ...
Preparing to unpack &#8230;/samba-common_2%3a4.3.9+dfsg-0ubuntu0.14.04.3_all.deb ...
Unpacking samba-common (2:4.3.9+dfsg-0ubuntu0.14.04.3) over (2:4.3.9+dfsg-0ubuntu0.14.04.1) ...
Preparing to unpack &#8230;/samba-dsdb-modules_2%3a4.3.9+dfsg-0ubuntu0.14.04.3_amd64.deb ...
Unpacking samba-dsdb-modules (2:4.3.9+dfsg-0ubuntu0.14.04.3) over (2:4.3.9+dfsg-0ubuntu0.14.04.1) ...
Preparing to unpack &#8230;/python-samba_2%3a4.3.9+dfsg-0ubuntu0.14.04.3_amd64.deb ...
Unpacking python-samba (2:4.3.9+dfsg-0ubuntu0.14.04.3) over (2:4.3.9+dfsg-0ubuntu0.14.04.1) ...
Preparing to unpack &#8230;/samba-libs_2%3a4.3.9+dfsg-0ubuntu0.14.04.3_amd64.deb ...
Unpacking samba-libs:amd64 (2:4.3.9+dfsg-0ubuntu0.14.04.3) over (2:4.3.9+dfsg-0ubuntu0.14.04.1) ...
Preparing to unpack &#8230;/php5-mysql_5.5.9+dfsg-1ubuntu4.17_amd64.deb ...
Unpacking php5-mysql (5.5.9+dfsg-1ubuntu4.17) over (5.5.9+dfsg-1ubuntu4.16) ...
Preparing to unpack &#8230;/libapache2-mod-php5_5.5.9+dfsg-1ubuntu4.17_amd64.deb ...
Unpacking libapache2-mod-php5 (5.5.9+dfsg-1ubuntu4.17) over (5.5.9+dfsg-1ubuntu4.16) ...
Preparing to unpack &#8230;/php5-cli_5.5.9+dfsg-1ubuntu4.17_amd64.deb ...
Unpacking php5-cli (5.5.9+dfsg-1ubuntu4.17) over (5.5.9+dfsg-1ubuntu4.16) ...
Preparing to unpack &#8230;/php5-gd_5.5.9+dfsg-1ubuntu4.17_amd64.deb ...
Unpacking php5-gd (5.5.9+dfsg-1ubuntu4.17) over (5.5.9+dfsg-1ubuntu4.16) ...
Preparing to unpack &#8230;/php5-curl_5.5.9+dfsg-1ubuntu4.17_amd64.deb ...
Unpacking php5-curl (5.5.9+dfsg-1ubuntu4.17) over (5.5.9+dfsg-1ubuntu4.16) ...
Preparing to unpack &#8230;/php5-common_5.5.9+dfsg-1ubuntu4.17_amd64.deb ...
Unpacking php5-common (5.5.9+dfsg-1ubuntu4.17) over (5.5.9+dfsg-1ubuntu4.16) ...
Preparing to unpack &#8230;/multiarch-support_2.19-0ubuntu6.9_amd64.deb ...
Unpacking multiarch-support (2.19-0ubuntu6.9) over (2.19-0ubuntu6.7) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for menu (2.1.46ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for ufw (0.34~rc-0ubuntu2) ...
Nastavuji balík multiarch-support (2.19-0ubuntu6.9) &#8230;
(&#268;tu databázi &#8230; nyní je nainstalováno 509844 soubor&#367; a adresá&#345;&#367;.)
Preparing to unpack &#8230;/apt-utils_1.0.1ubuntu2.14_amd64.deb ...
Unpacking apt-utils (1.0.1ubuntu2.14) over (1.0.1ubuntu2.13) ...
Preparing to unpack &#8230;/apt-transport-https_1.0.1ubuntu2.14_amd64.deb ...
Unpacking apt-transport-https (1.0.1ubuntu2.14) over (1.0.1ubuntu2.13) ...
Preparing to unpack &#8230;/compiz-gnome_1%3a0.9.11.3+14.04.20160425-0ubuntu1_amd64.deb ...
Unpacking compiz-gnome (1:0.9.11.3+14.04.20160425-0ubuntu1) over (1:0.9.11.3+14.04.20150313-0ubuntu1) ...
Preparing to unpack &#8230;/compiz-dev_1%3a0.9.11.3+14.04.20160425-0ubuntu1_amd64.deb ...
Unpacking compiz-dev (1:0.9.11.3+14.04.20160425-0ubuntu1) over (1:0.9.11.3+14.04.20150313-0ubuntu1) ...
Preparing to unpack &#8230;/compiz-plugins-default_1%3a0.9.11.3+14.04.20160425-0ubuntu1_amd64.deb ...
Unpacking compiz-plugins-default (1:0.9.11.3+14.04.20160425-0ubuntu1) over (1:0.9.11.3+14.04.20150313-0ubuntu1) ...
Preparing to unpack &#8230;/compiz-plugins_1%3a0.9.11.3+14.04.20160425-0ubuntu1_amd64.deb ...
Unpacking compiz-plugins (1:0.9.11.3+14.04.20160425-0ubuntu1) over (1:0.9.11.3+14.04.20150313-0ubuntu1) ...
Preparing to unpack &#8230;/libdecoration0-dev_1%3a0.9.11.3+14.04.20160425-0ubuntu1_amd64.deb ...
Unpacking libdecoration0-dev (1:0.9.11.3+14.04.20160425-0ubuntu1) over (1:0.9.11.3+14.04.20150313-0ubuntu1) ...
Preparing to unpack &#8230;/libdecoration0_1%3a0.9.11.3+14.04.20160425-0ubuntu1_amd64.deb ...
Unpacking libdecoration0 (1:0.9.11.3+14.04.20160425-0ubuntu1) over (1:0.9.11.3+14.04.20150313-0ubuntu1) ...
Preparing to unpack &#8230;/libcompizconfig0-dev_1%3a0.9.11.3+14.04.20160425-0ubuntu1_amd64.deb ...
Unpacking libcompizconfig0-dev (1:0.9.11.3+14.04.20160425-0ubuntu1) over (1:0.9.11.3+14.04.20150313-0ubuntu1) ...
Preparing to unpack &#8230;/libcompizconfig0_1%3a0.9.11.3+14.04.20160425-0ubuntu1_amd64.deb ...
Unpacking libcompizconfig0 (1:0.9.11.3+14.04.20160425-0ubuntu1) over (1:0.9.11.3+14.04.20150313-0ubuntu1) ...
Preparing to unpack &#8230;/compiz-core_1%3a0.9.11.3+14.04.20160425-0ubuntu1_amd64.deb ...
Unpacking compiz-core (1:0.9.11.3+14.04.20160425-0ubuntu1) over (1:0.9.11.3+14.04.20150313-0ubuntu1) ...
Preparing to unpack &#8230;/compiz_1%3a0.9.11.3+14.04.20160425-0ubuntu1_all.deb ...
Unpacking compiz (1:0.9.11.3+14.04.20160425-0ubuntu1) over (1:0.9.11.3+14.04.20150313-0ubuntu1) ...
Preparing to unpack &#8230;/php-pear_5.5.9+dfsg-1ubuntu4.17_all.deb ...
Unpacking php-pear (5.5.9+dfsg-1ubuntu4.17) over (5.5.9+dfsg-1ubuntu4.16) ...
Preparing to unpack &#8230;/php5-dev_5.5.9+dfsg-1ubuntu4.17_amd64.deb ...
Unpacking php5-dev (5.5.9+dfsg-1ubuntu4.17) over (5.5.9+dfsg-1ubuntu4.16) ...
Preparing to unpack &#8230;/python3-problem-report_2.14.1-0ubuntu3.21_all.deb ...
Unpacking python3-problem-report (2.14.1-0ubuntu3.21) over (2.14.1-0ubuntu3.20) ...
Preparing to unpack &#8230;/python3-apport_2.14.1-0ubuntu3.21_all.deb ...
Unpacking python3-apport (2.14.1-0ubuntu3.21) over (2.14.1-0ubuntu3.20) ...
Preparing to unpack &#8230;/compiz-plugins-extra_1%3a0.9.11.3+14.04.20160425-0ubuntu1_all.deb ...
Unpacking compiz-plugins-extra (1:0.9.11.3+14.04.20160425-0ubuntu1) over (1:0.9.11.3+14.04.20150313-0ubuntu1) ...
Preparing to unpack &#8230;/compiz-plugins-main_1%3a0.9.11.3+14.04.20160425-0ubuntu1_all.deb ...
Unpacking compiz-plugins-main (1:0.9.11.3+14.04.20160425-0ubuntu1) over (1:0.9.11.3+14.04.20150313-0ubuntu1) ...
Preparing to unpack &#8230;/compiz-plugins-main-default_1%3a0.9.11.3+14.04.20160425-0ubuntu1_all.deb ...
Unpacking compiz-plugins-main-default (1:0.9.11.3+14.04.20160425-0ubuntu1) over (1:0.9.11.3+14.04.20150313-0ubuntu1) ...
Preparing to unpack &#8230;/compiz-plugins-main-dev_1%3a0.9.11.3+14.04.20160425-0ubuntu1_all.deb ...
Unpacking compiz-plugins-main-dev (1:0.9.11.3+14.04.20160425-0ubuntu1) over (1:0.9.11.3+14.04.20150313-0ubuntu1) ...
Preparing to unpack &#8230;/compizconfig-backend-gconf_1%3a0.9.11.3+14.04.20160425-0ubuntu1_all.deb ...
Unpacking compizconfig-backend-gconf (1:0.9.11.3+14.04.20160425-0ubuntu1) over (1:0.9.11.3+14.04.20150313-0ubuntu1) ...
Preparing to unpack &#8230;/python-compizconfig_1%3a0.9.11.3+14.04.20160425-0ubuntu1_amd64.deb ...
Unpacking python-compizconfig (1:0.9.11.3+14.04.20160425-0ubuntu1) over (1:0.9.11.3+14.04.20150313-0ubuntu1) ...
Preparing to unpack &#8230;/compizconfig-settings-manager_1%3a0.9.11.3+14.04.20160425-0ubuntu1_all.deb ...
Unpacking compizconfig-settings-manager (1:0.9.11.3+14.04.20160425-0ubuntu1) over (1:0.9.11.3+14.04.20150313-0ubuntu1) ...
Preparing to unpack &#8230;/oem-audio-hda-daily-dkms_0.201605300501~ubuntu14.04.1_all.deb ...


-------- Uninstall Beginning --------
Module:  oem-audio-hda-daily
Version: 0.201605230501~ubuntu14.04.1
Kernel:  3.13.0-37-generic (amd64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


snd-hda-codec-idt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-37-generic/updates/kernel//
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/3.13.0-37-generic/updates/kernel//


snd-hda-codec-analog.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-37-generic/updates/kernel//
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/3.13.0-37-generic/updates/kernel//


snd-hda-codec.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-37-generic/updates/kernel//
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/3.13.0-37-generic/updates/kernel//


snd-hda-codec-cirrus.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-37-generic/updates/kernel//
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/3.13.0-37-generic/updates/kernel//


snd-hda-codec-conexant.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-37-generic/updates/kernel//
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/3.13.0-37-generic/updates/kernel//


snd-hda-intel.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-37-generic/updates/kernel//
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/3.13.0-37-generic/updates/kernel//


snd-hda-core.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-37-generic/updates/kernel//
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




snd-hda-codec-ca0132.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-37-generic/updates/kernel//
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/3.13.0-37-generic/updates/kernel//


snd-hda-codec-via.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-37-generic/updates/kernel//
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/3.13.0-37-generic/updates/kernel//


snd-hda-codec-si3054.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-37-generic/updates/kernel//
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/3.13.0-37-generic/updates/kernel//


snd-hda-codec-realtek.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-37-generic/updates/kernel//
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/3.13.0-37-generic/updates/kernel//


snd-hda-codec-hdmi.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-37-generic/updates/kernel//
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/3.13.0-37-generic/updates/kernel//


snd-hda-codec-ca0110.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-37-generic/updates/kernel//
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/3.13.0-37-generic/updates/kernel//


snd-hda-codec-cmedia.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-37-generic/updates/kernel//
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/3.13.0-37-generic/updates/kernel//


snd-hda-codec-generic.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-37-generic/updates/kernel//
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod...........


Removing original_module from DKMS tree for kernel 3.13.0-37-generic (amd64)


DKMS: uninstall completed.


-------- Uninstall Beginning --------
Module:  oem-audio-hda-daily
Version: 0.201605230501~ubuntu14.04.1
Kernel:  3.13.0-86-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


snd-hda-codec-idt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-86-generic/updates/kernel//
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/3.13.0-86-generic/updates/kernel//


snd-hda-codec-analog.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-86-generic/updates/kernel//
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/3.13.0-86-generic/updates/kernel//


snd-hda-codec.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-86-generic/updates/kernel//
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/3.13.0-86-generic/updates/kernel//


snd-hda-codec-cirrus.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-86-generic/updates/kernel//
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/3.13.0-86-generic/updates/kernel//


snd-hda-codec-conexant.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-86-generic/updates/kernel//
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/3.13.0-86-generic/updates/kernel//


snd-hda-intel.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-86-generic/updates/kernel//
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/3.13.0-86-generic/updates/kernel//


snd-hda-core.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-86-generic/updates/kernel//
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.




snd-hda-codec-ca0132.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-86-generic/updates/kernel//
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/3.13.0-86-generic/updates/kernel//


snd-hda-codec-via.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-86-generic/updates/kernel//
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/3.13.0-86-generic/updates/kernel//


snd-hda-codec-si3054.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-86-generic/updates/kernel//
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/3.13.0-86-generic/updates/kernel//


snd-hda-codec-realtek.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-86-generic/updates/kernel//
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/3.13.0-86-generic/updates/kernel//


snd-hda-codec-hdmi.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-86-generic/updates/kernel//
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/3.13.0-86-generic/updates/kernel//


snd-hda-codec-ca0110.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-86-generic/updates/kernel//
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/3.13.0-86-generic/updates/kernel//


snd-hda-codec-cmedia.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-86-generic/updates/kernel//
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/3.13.0-86-generic/updates/kernel//


snd-hda-codec-generic.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.13.0-86-generic/updates/kernel//
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod........


Removing original_module from DKMS tree for kernel 3.13.0-86-generic (x86_64)


DKMS: uninstall completed.


------------------------------
Deleting module version: 0.201605230501~ubuntu14.04.1
completely from the DKMS tree.
------------------------------
Done.
Unpacking oem-audio-hda-daily-dkms (0.201605300501~ubuntu14.04.1) over (0.201605230501~ubuntu14.04.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Processing triggers for libglib2.0-0:amd64 (2.40.2-0ubuntu1) ...
Processing triggers for libglib2.0-0:i386 (2.40.2-0ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for doc-base (0.10.5) ...
Zpracování 1 zm&#283;n&#283;ný doc-base soubor...
Registrace dokument&#367; s scrollkeeper...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Nastavuji balík libc6-i386 (2.19-0ubuntu6.9) &#8230;
Nastavuji balík libc-dev-bin (2.19-0ubuntu6.9) &#8230;
Nastavuji balík libc6-dev:amd64 (2.19-0ubuntu6.9) &#8230;
Nastavuji balík google-chrome-stable (51.0.2704.63-1) &#8230;
Nastavuji balík libwbclient0:amd64 (2:4.3.9+dfsg-0ubuntu0.14.04.3) &#8230;
Nastavuji balík samba-libs:amd64 (2:4.3.9+dfsg-0ubuntu0.14.04.3) &#8230;
Nastavuji balík python-samba (2:4.3.9+dfsg-0ubuntu0.14.04.3) &#8230;
Nastavuji balík samba-common (2:4.3.9+dfsg-0ubuntu0.14.04.3) &#8230;
Nastavuji balík samba-common-bin (2:4.3.9+dfsg-0ubuntu0.14.04.3) &#8230;
Nastavuji balík samba (2:4.3.9+dfsg-0ubuntu0.14.04.3) &#8230;
smbd start/running, process 6006
nmbd start/running, process 6044
samba-ad-dc start/running, process 6083
Nastavuji balík winbind (2:4.3.9+dfsg-0ubuntu0.14.04.3) &#8230;
winbind start/running, process 6133
Nastavuji balík libsmbclient:amd64 (2:4.3.9+dfsg-0ubuntu0.14.04.3) &#8230;
Nastavuji balík smbclient (2:4.3.9+dfsg-0ubuntu0.14.04.3) &#8230;
Nastavuji balík samba-dsdb-modules (2:4.3.9+dfsg-0ubuntu0.14.04.3) &#8230;
Nastavuji balík php5-common (5.5.9+dfsg-1ubuntu4.17) &#8230;
php5_invoke pdo: already enabled for apache2 SAPI
php5_invoke pdo: already enabled for cli SAPI
php5_invoke opcache: already enabled for apache2 SAPI
php5_invoke opcache: already enabled for cli SAPI
Nastavuji balík php5-mysql (5.5.9+dfsg-1ubuntu4.17) &#8230;
php5_invoke mysql: already enabled for apache2 SAPI
php5_invoke mysql: already enabled for cli SAPI
php5_invoke mysqli: already enabled for apache2 SAPI
php5_invoke mysqli: already enabled for cli SAPI
php5_invoke pdo_mysql: already enabled for apache2 SAPI
php5_invoke pdo_mysql: already enabled for cli SAPI
Nastavuji balík libapache2-mod-php5 (5.5.9+dfsg-1ubuntu4.17) &#8230;
php5_invoke mysql: already enabled for apache2 SAPI
php5_invoke curl: already enabled for apache2 SAPI
php5_invoke pdo: already enabled for apache2 SAPI
php5_invoke gd: already enabled for apache2 SAPI
php5_invoke json: already enabled for apache2 SAPI
php5_invoke opcache: already enabled for apache2 SAPI
php5_invoke pdo_mysql: already enabled for apache2 SAPI
php5_invoke mysqli: already enabled for apache2 SAPI
apache2_invoke php5: already enabled
 * Restarting web server apache2                                                           AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1. Set the 'ServerName' directive globally to suppress this message
                                                                                    [ OK ]
Nastavuji balík php5-cli (5.5.9+dfsg-1ubuntu4.17) &#8230;
php5_invoke mysql: already enabled for cli SAPI
php5_invoke curl: already enabled for cli SAPI
php5_invoke pdo: already enabled for cli SAPI
php5_invoke gd: already enabled for cli SAPI
php5_invoke json: already enabled for cli SAPI
php5_invoke opcache: already enabled for cli SAPI
php5_invoke pdo_mysql: already enabled for cli SAPI
php5_invoke mysqli: already enabled for cli SAPI
Nastavuji balík php5-gd (5.5.9+dfsg-1ubuntu4.17) &#8230;
php5_invoke gd: already enabled for apache2 SAPI
php5_invoke gd: already enabled for cli SAPI
Nastavuji balík php5-curl (5.5.9+dfsg-1ubuntu4.17) &#8230;
php5_invoke curl: already enabled for apache2 SAPI
php5_invoke curl: already enabled for cli SAPI
Nastavuji balík apt-utils (1.0.1ubuntu2.14) &#8230;
Nastavuji balík apt-transport-https (1.0.1ubuntu2.14) &#8230;
Nastavuji balík compiz-core (1:0.9.11.3+14.04.20160425-0ubuntu1) &#8230;
Nastavuji balík libcompizconfig0 (1:0.9.11.3+14.04.20160425-0ubuntu1) &#8230;
Nastavuji balík libdecoration0 (1:0.9.11.3+14.04.20160425-0ubuntu1) &#8230;
Nastavuji balík compiz-plugins-default (1:0.9.11.3+14.04.20160425-0ubuntu1) &#8230;
Nastavuji balík compiz-gnome (1:0.9.11.3+14.04.20160425-0ubuntu1) &#8230;
Nastavuji balík libdecoration0-dev (1:0.9.11.3+14.04.20160425-0ubuntu1) &#8230;
Nastavuji balík compiz-dev (1:0.9.11.3+14.04.20160425-0ubuntu1) &#8230;
Nastavuji balík compiz-plugins (1:0.9.11.3+14.04.20160425-0ubuntu1) &#8230;
Nastavuji balík libcompizconfig0-dev (1:0.9.11.3+14.04.20160425-0ubuntu1) &#8230;
Nastavuji balík compiz (1:0.9.11.3+14.04.20160425-0ubuntu1) &#8230;
Nastavuji balík php-pear (5.5.9+dfsg-1ubuntu4.17) &#8230;
Instaluji novou verzi konfigura&#269;ního souboru /etc/pear/pear.conf &#8230;
Nastavuji balík php5-dev (5.5.9+dfsg-1ubuntu4.17) &#8230;
Nastavuji balík python3-problem-report (2.14.1-0ubuntu3.21) &#8230;
Nastavuji balík python3-apport (2.14.1-0ubuntu3.21) &#8230;
Nastavuji balík compiz-plugins-extra (1:0.9.11.3+14.04.20160425-0ubuntu1) &#8230;
Nastavuji balík compiz-plugins-main (1:0.9.11.3+14.04.20160425-0ubuntu1) &#8230;
Nastavuji balík compiz-plugins-main-default (1:0.9.11.3+14.04.20160425-0ubuntu1) &#8230;
Nastavuji balík compiz-plugins-main-dev (1:0.9.11.3+14.04.20160425-0ubuntu1) &#8230;
Nastavuji balík compizconfig-backend-gconf (1:0.9.11.3+14.04.20160425-0ubuntu1) &#8230;
Nastavuji balík python-compizconfig (1:0.9.11.3+14.04.20160425-0ubuntu1) &#8230;
Nastavuji balík compizconfig-settings-manager (1:0.9.11.3+14.04.20160425-0ubuntu1) &#8230;
Nastavuji balík oem-audio-hda-daily-dkms (0.201605300501~ubuntu14.04.1) &#8230;
Loading new oem-audio-hda-daily-0.201605300501~ubuntu14.04.1 DKMS files...
First Installation: checking all kernels...
Building for 3.13.0-86-generic and 3.19.0-32-generic
Building for architecture amd64
Building initial module for 3.13.0-86-generic
Done.


snd-hda-codec-idt:
Running module version sanity check.
 - Original module
   - Found /lib/modules/3.13.0-86-generic/updates/kernel//snd-hda-codec-idt.ko
   - Storing in /var/lib/dkms/oem-audio-hda-daily/original_module/3.13.0-86-generic/amd64/
   - Archiving for uninstallation purposes
 - Installation
   - Installing to /lib/modules/3.13.0-86-generic/updates/kernel//


snd-hda-codec-analog.ko:
Running module version sanity check.
 - Original module
   - Found /lib/modules/3.13.0-86-generic/updates/kernel//snd-hda-codec-analog.ko
   - Storing in /var/lib/dkms/oem-audio-hda-daily/original_module/3.13.0-86-generic/amd64/
   - Archiving for uninstallation purposes
 - Installation
   - Installing to /lib/modules/3.13.0-86-generic/updates/kernel//


snd-hda-codec.ko:
Running module version sanity check.
 - Original module
   - Found /lib/modules/3.13.0-86-generic/updates/kernel//snd-hda-codec.ko
   - Storing in /var/lib/dkms/oem-audio-hda-daily/original_module/3.13.0-86-generic/amd64/
   - Archiving for uninstallation purposes
 - Installation
   - Installing to /lib/modules/3.13.0-86-generic/updates/kernel//


snd-hda-codec-cirrus.ko:
Running module version sanity check.
 - Original module
   - Found /lib/modules/3.13.0-86-generic/updates/kernel//snd-hda-codec-cirrus.ko
   - Storing in /var/lib/dkms/oem-audio-hda-daily/original_module/3.13.0-86-generic/amd64/
   - Archiving for uninstallation purposes
 - Installation
   - Installing to /lib/modules/3.13.0-86-generic/updates/kernel//


snd-hda-codec-conexant.ko:
Running module version sanity check.
 - Original module
   - Found /lib/modules/3.13.0-86-generic/updates/kernel//snd-hda-codec-conexant.ko
   - Storing in /var/lib/dkms/oem-audio-hda-daily/original_module/3.13.0-86-generic/amd64/
   - Archiving for uninstallation purposes
 - Installation
   - Installing to /lib/modules/3.13.0-86-generic/updates/kernel//


snd-hda-intel.ko:
Running module version sanity check.
 - Original module
   - Found /lib/modules/3.13.0-86-generic/updates/kernel//snd-hda-intel.ko
   - Storing in /var/lib/dkms/oem-audio-hda-daily/original_module/3.13.0-86-generic/amd64/
   - Archiving for uninstallation purposes
 - Installation
   - Installing to /lib/modules/3.13.0-86-generic/updates/kernel//


snd-hda-core.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/3.13.0-86-generic/updates/kernel//


snd-hda-codec-ca0132.ko:
Running module version sanity check.
 - Original module
   - Found /lib/modules/3.13.0-86-generic/updates/kernel//snd-hda-codec-ca0132.ko
   - Storing in /var/lib/dkms/oem-audio-hda-daily/original_module/3.13.0-86-generic/amd64/
   - Archiving for uninstallation purposes
 - Installation
   - Installing to /lib/modules/3.13.0-86-generic/updates/kernel//


snd-hda-codec-via.ko:
Running module version sanity check.
 - Original module
   - Found /lib/modules/3.13.0-86-generic/updates/kernel//snd-hda-codec-via.ko
   - Storing in /var/lib/dkms/oem-audio-hda-daily/original_module/3.13.0-86-generic/amd64/
   - Archiving for uninstallation purposes
 - Installation
   - Installing to /lib/modules/3.13.0-86-generic/updates/kernel//


snd-hda-codec-si3054.ko:
Running module version sanity check.
 - Original module
   - Found /lib/modules/3.13.0-86-generic/updates/kernel//snd-hda-codec-si3054.ko
   - Storing in /var/lib/dkms/oem-audio-hda-daily/original_module/3.13.0-86-generic/amd64/
   - Archiving for uninstallation purposes
 - Installation
   - Installing to /lib/modules/3.13.0-86-generic/updates/kernel//


snd-hda-codec-realtek.ko:
Running module version sanity check.
 - Original module
   - Found /lib/modules/3.13.0-86-generic/updates/kernel//snd-hda-codec-realtek.ko
   - Storing in /var/lib/dkms/oem-audio-hda-daily/original_module/3.13.0-86-generic/amd64/
   - Archiving for uninstallation purposes
 - Installation
   - Installing to /lib/modules/3.13.0-86-generic/updates/kernel//


snd-hda-codec-hdmi.ko:
Running module version sanity check.
 - Original module
   - Found /lib/modules/3.13.0-86-generic/updates/kernel//snd-hda-codec-hdmi.ko
   - Storing in /var/lib/dkms/oem-audio-hda-daily/original_module/3.13.0-86-generic/amd64/
   - Archiving for uninstallation purposes
 - Installation
   - Installing to /lib/modules/3.13.0-86-generic/updates/kernel//


snd-hda-codec-ca0110.ko:
Running module version sanity check.
 - Original module
   - Found /lib/modules/3.13.0-86-generic/updates/kernel//snd-hda-codec-ca0110.ko
   - Storing in /var/lib/dkms/oem-audio-hda-daily/original_module/3.13.0-86-generic/amd64/
   - Archiving for uninstallation purposes
 - Installation
   - Installing to /lib/modules/3.13.0-86-generic/updates/kernel//


snd-hda-codec-cmedia.ko:
Running module version sanity check.
 - Original module
   - Found /lib/modules/3.13.0-86-generic/updates/kernel//snd-hda-codec-cmedia.ko
   - Storing in /var/lib/dkms/oem-audio-hda-daily/original_module/3.13.0-86-generic/amd64/
   - Archiving for uninstallation purposes
 - Installation
   - Installing to /lib/modules/3.13.0-86-generic/updates/kernel//


snd-hda-codec-generic.ko:
Running module version sanity check.
 - Original module
 - Installation
   - Installing to /lib/modules/3.13.0-86-generic/updates/kernel//


depmod....


DKMS: install completed.
Building initial module for 3.19.0-32-generic
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
Done.
Processing triggers for libc-bin (2.19-0ubuntu6.9) ...
Processing triggers for menu (2.1.46ubuntu1) ...
Processing triggers for libapache2-mod-php5 (5.5.9+dfsg-1ubuntu4.17) ...
&#268;tu seznamy balík&#367;&#8230; Hotovo
Vytvá&#345;í se strom závislostí       
&#268;tu stavové informace&#8230; Hotovo
Následující balík byl nainstalován automaticky a ji&#382; není pot&#345;eba:
  mdm
Pro jeho odstran&#283;ní pou&#382;ijte &#8222;apt-get autoremove&#8220;.
0 aktualizováno, 0 nov&#283; instalováno, 0 k odstran&#283;ní a 0 neaktualizováno.
ii  binutils-aarch64-linux-gnu                                  2.24-5ubuntu14cross0.11.2                              amd64        GNU binary utilities, for aarch64-linux-gnu target
ii  binutils-arm-linux-gnueabi                                  2.24-5ubuntu13cross1.97.1                              amd64        GNU binary utilities, for arm-linux-gnueabi target
ii  binutils-powerpc-linux-gnu                                  2.24-5ubuntu13cross0.10.1                              amd64        GNU binary utilities, for powerpc-linux-gnu target
ii  binutils-powerpc64le-linux-gnu                              2.24-5ubuntu13cross0.4.1                               amd64        GNU binary utilities, for powerpc64le-linux-gnu target
ii  cpp-4.7-arm-linux-gnueabi                                   4.7.3-12ubuntu1cross1.85                               amd64        GNU C preprocessor
ii  cpp-4.8-aarch64-linux-gnu                                   4.8.4-2ubuntu1~14.04.1cross0.11.2                      amd64        GNU C preprocessor
ii  cpp-4.8-powerpc-linux-gnu                                   4.8.4-2ubuntu1~14.04.1cross0.11.2                      amd64        GNU C preprocessor
ii  cpp-4.8-powerpc64le-linux-gnu                               4.8.4-2ubuntu1~14.04.1cross0.4.2                       amd64        GNU C preprocessor
ii  cpp-arm-linux-gnueabi                                       4:4.7.2-1                                              amd64        The GNU C preprocessor (cpp) for armel architecture
ii  g++-4.7-arm-linux-gnueabi                                   4.7.3-12ubuntu1cross1.85                               amd64        GNU C++ compiler
ii  g++-arm-linux-gnueabi                                       4:4.7.2-1                                              amd64        The GNU C++ compiler for armel architecture
ii  gcc-4.7-arm-linux-gnueabi                                   4.7.3-12ubuntu1cross1.85                               amd64        GNU C compiler
ii  gcc-4.7-arm-linux-gnueabi-base                              4.7.3-12ubuntu1cross1.85                               amd64        GCC, the GNU Compiler Collection (base package)
ii  gcc-4.8-aarch64-linux-gnu                                   4.8.4-2ubuntu1~14.04.1cross0.11.2                      amd64        GNU C compiler
ii  gcc-4.8-aarch64-linux-gnu-base                              4.8.4-2ubuntu1~14.04.1cross0.11.2                      amd64        GCC, the GNU Compiler Collection (base package)
ii  gcc-4.8-powerpc-linux-gnu                                   4.8.4-2ubuntu1~14.04.1cross0.11.2                      amd64        GNU C compiler
ii  gcc-4.8-powerpc-linux-gnu-base                              4.8.4-2ubuntu1~14.04.1cross0.11.2                      amd64        GCC, the GNU Compiler Collection (base package)
ii  gcc-4.8-powerpc64le-linux-gnu                               4.8.4-2ubuntu1~14.04.1cross0.4.2                       amd64        GNU C compiler
ii  gcc-4.8-powerpc64le-linux-gnu-base                          4.8.4-2ubuntu1~14.04.1cross0.4.2                       amd64        GCC, the GNU Compiler Collection (base package)
ii  gcc-arm-linux-gnueabi                                       4:4.7.2-1                                              amd64        The GNU C compiler for armel architecture
ii  gobjc++-4.7-arm-linux-gnueabi                               4.7.3-12ubuntu1cross1.85                               amd64        GNU Objective-C++ compiler
ii  gobjc-4.7-arm-linux-gnueabi                                 4.7.3-12ubuntu1cross1.85                               amd64        GNU Objective-C compiler
ii  gobjc-4.8-aarch64-linux-gnu                                 4.8.4-2ubuntu1~14.04.1cross0.11.2                      amd64        GNU Objective-C compiler
ii  gobjc-4.8-powerpc-linux-gnu                                 4.8.4-2ubuntu1~14.04.1cross0.11.2                      amd64        GNU Objective-C compiler
ii  gobjc-4.8-powerpc64le-linux-gnu                             4.8.4-2ubuntu1~14.04.1cross0.4.2                       amd64        GNU Objective-C compiler
ii  linux-firmware                                              1.127.22                                               all          Firmware for Linux kernel drivers
ii  linux-generic                                               3.13.0.86.92                                           amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-24                                     3.13.0-24.47                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-24-generic                             3.13.0-24.47                                           amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-37                                     3.13.0-37.64                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-37-generic                             3.13.0-37.64                                           amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-83                                     3.13.0-83.127                                          all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-83-generic                             3.13.0-83.127                                          amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-85                                     3.13.0-85.129                                          all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-85-generic                             3.13.0-85.129                                          amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-86                                     3.13.0-86.131                                          all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-86-generic                             3.13.0-86.131                                          amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-32                                     3.19.0-32.37~14.04.1                                   all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-32-generic                             3.19.0-32.37~14.04.1                                   amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       3.13.0.86.92                                           amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-24-generic                               3.13.0-24.47                                           amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-37-generic                               3.13.0-37.64                                           amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-86-generic                               3.13.0-86.131                                          amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic                         3.13.0-24.47                                           amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic                         3.13.0-37.64                                           amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-86-generic                         3.13.0-86.131                                          amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                         3.13.0.86.92                                           amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                        3.13.0-86.131                                          amd64        Linux Kernel Headers for development
ii  linux-libc-dev-arm64-cross                                  3.13.0-12.32cross0.10                                  all          Linux Kernel Headers for development (for cross-compiling)
ii  linux-libc-dev-armel-cross                                  3.13.0-12.32cross1.104                                 all          Linux Kernel Headers for development (for cross-compiling)
ii  linux-libc-dev-powerpc-cross                                3.13.0-13.33cross1.1                                   all          Linux Kernel Headers for development (for cross-compiling)
ii  linux-libc-dev-ppc64el-cross                                3.13.0-13.33cross0.2                                   all          Linux Kernel Headers for development (for cross-compiling)
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu4                                   all          base package for ALSA and OSS sound systems
ii  mlton-runtime-x86-64-linux-gnu                              20100608-5.1                                           amd64        Optimizing compiler for Standard ML - amd64 runtime libraries
ii  syslinux-common                                             3:4.05+dfsg-6+deb8u1                                   all          collection of boot loaders (common files)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu5                                   amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  syslinux-themes-linuxmint-cinnamon                          1.0.7                                                  all          collection of boot loaders (theme metapackage)
ii  syslinux-themes-linuxmint-cinnamon-rebecca                  1.0.7                                                  all          collection of boot loaders (linuxmint-rebecca theme)
jan@localhost ~ $ 



```
Here is the output (except update)

---

### Post by Bashing-om on 2016-05-30
Jan_Jindrek; So far.

So good; Maybe ?

These:
> 
Installing to /lib/modules/3.13.0-86-generic/updates/kernel//

Huh ?? WHY ! when kernel linux-headers-3.19.0-32-generic ...........

And ouch !
> 
DKMS: install completed.
Building initial module for 3.19.0-32-generic
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.


UH OH Now I see !
the headers are installed for the -32 kernel .. BUT linux-image and linux-image-extra for that latest kernel are not installed .

Tell me what have you been doing to be in this situation ? So I have some idea of what to do to climb back up out of this hole.
Are you trying to opt in for Hardware Enablement ?
see:
[http://askubuntu.com/questions/248914/what-is-hwe-hardware-enablement](http://askubuntu.com/questions/248914/what-is-hwe-hardware-enablement)
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Presently before proceeding I need to know that we have the operating head room for the package manager to work in conjunction with apt to try and get the latest kernel installed and functional.

what returns:
```

df -h
df -i

```

we do indeed
[INDENT][INDENT]have our work cut out for us
[/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-05-30
I pressed yes twice on "sudo apt-get upgrade". Yes, they ****ed up official update. So badly in fact, that multiple people including me had the pleasure of meeting the command line that runs when nothing else does.. very fun.
```

jan@localhost ~ $ df -h
Souborový systém   Velikost U&#382;ito Volno U&#382;i% P&#345;ipojeno do
udev                   3,9G  4,0K  3,9G   1% /dev
tmpfs                  791M  1,5M  789M   1% /run
/dev/sda1              909G  478G  386G  56% /
none                   4,0K     0  4,0K   0% /sys/fs/cgroup
none                   5,0M     0  5,0M   0% /run/lock
none                   3,9G  219M  3,7G   6% /run/shm
none                   100M   28K  100M   1% /run/user
/home/jan/.Private     909G  478G  386G  56% /home/jan
jan@localhost ~ $ df -i
Souborový systém     I-uzl&#367; IU&#382;ito   IVolno IU&#382;i% P&#345;ipojeno do
udev                1007898    523  1007375    1% /dev
tmpfs               1011747    595  1011152    1% /run
/dev/sda1          60530688 914811 59615877    2% /
none                1011747      2  1011745    1% /sys/fs/cgroup
none                1011747      4  1011743    1% /run/lock
none                1011747    197  1011550    1% /run/shm
none                1011747     20  1011727    1% /run/user
/home/jan/.Private 60530688 914811 59615877    2% /home/jan

```
Sorry for the czech.. but thanks for help!!!!

---

### Post by Bashing-om on 2016-05-30
Jan_Jindrek; OK, 

We have head room, so we can operate .

Operate might be the operative word here . But this is 'buntu and it is always fixable given the time and effort.

Now the question remains:
why is 3.19.0-32 (vivid) on this system ?
A) You installed after the 14.04.2 release such that HWE was the default
B) You opted in to HWE and for some reason the enablement failed
C) You attempted a manual install of the vivid kernels
D) You are trying to build something for vivid, installed the headers and messed up the system ?

As I do not find vivid's linux-firmware I do not know what path was taken to arrive here .. and sorta in a quandry how to proceed.
What returns:
```

dpkg -l '*vivid*'

```

see if we get some direction to proceed.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-05-30
```

jan@localhost ~ $ dpkg -l '*vivid*'
dpkg-query: *vivid* nevyhovuje &#382;ádný balík
jan@localhost ~ $ dpkg -l *vivid*
dpkg-query: *vivid* nevyhovuje &#382;ádný balík
jan@localhost ~ $ dpkg -l vivid
dpkg-query: vivid nevyhovuje &#382;ádný balík



```
Nothing found? By the way, I think I attempted a manual install..

---

### Post by Bashing-om on 2016-05-30
Jan_Jindrek; K;

Let's begin the process of cleaning up.
We must not mess with the booting kernel !
show:
```

uname -r

```

So we know what not to do .

[INDENT][INDENT]maybe yes here
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-06-01
```
3.13.0-86-generic
```

---

### Post by Bashing-om on 2016-06-01
Jan_Jindrek; K;

Here goes a 1st stab at getting the images correct with kernel/headers:
```

sudo dpkg -P linux-headers-3.13.0-83-generic
sudo dpkg -P linux-headers-3.13.0-83
sudo dpkg -P linux-headers-3.13.0-85-generic
sudo dpkg -P linux-headers-3.13.0-85
sudo dpkg -P linux-headers-3.19.0-32-generic
sudo dpkg -P linux-headers-3.19.0-32

```

IF that goes well .. we next want to see if we can pull in the new 3.13.0-87 kernel.
What do we get now with :
```

sudo apt update
sudo apt full-upgrade

```

And when that goes well .. and IF then I would want to see that all supporting files for the kernels are in place . Will await that look when the above completes .

[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-06-01
```

jan@localhost ~ $ sudo dpkg -P linux-headers-3.13.0-83-generic
[sudo] password for jan: 
Zkuste to znovu, prosím.
[sudo] password for jan: 
(&#268;tu databázi &#8230; nyní je nainstalováno 509843 soubor&#367; a adresá&#345;&#367;.)
Removing linux-headers-3.13.0-83-generic (3.13.0-83.127) ...
dpkg: varování: p&#345;i odstra&#328;ování linux-headers-3.13.0-83-generic není adresá&#345; &#8222;/lib/modules/3.13.0-83-generic&#8220; prázdný, proto nebude odstran&#283;n
jan@localhost ~ $ sudo dpkg -P linux-headers-3.13.0-83-generic
dpkg: varování: ignoruji po&#382;adavek na odstran&#283;ní nenainstalovaného balíku linux-headers-3.13.0-83-generic
jan@localhost ~ $ sudo dpkg -P linux-headers-3.13.0-83
(&#268;tu databázi &#8230; nyní je nainstalováno 500275 soubor&#367; a adresá&#345;&#367;.)
Removing linux-headers-3.13.0-83 (3.13.0-83.127) ...
jan@localhost ~ $ sudo dpkg -P linux-headers-3.13.0-85-generic
(&#268;tu databázi &#8230; nyní je nainstalováno 485018 soubor&#367; a adresá&#345;&#367;.)
Removing linux-headers-3.13.0-85-generic (3.13.0-85.129) ...
dpkg: varování: p&#345;i odstra&#328;ování linux-headers-3.13.0-85-generic není adresá&#345; &#8222;/lib/modules/3.13.0-85-generic&#8220; prázdný, proto nebude odstran&#283;n
jan@localhost ~ $ sudo dpkg -P linux-headers-3.13.0-85
(&#268;tu databázi &#8230; nyní je nainstalováno 475450 soubor&#367; a adresá&#345;&#367;.)
Removing linux-headers-3.13.0-85 (3.13.0-85.129) ...
jan@localhost ~ $ sudo dpkg -P linux-headers-3.19.0-32-generic
(&#268;tu databázi &#8230; nyní je nainstalováno 460193 soubor&#367; a adresá&#345;&#367;.)
Removing linux-headers-3.19.0-32-generic (3.19.0-32.37~14.04.1) ...
dpkg: varování: p&#345;i odstra&#328;ování linux-headers-3.19.0-32-generic není adresá&#345; &#8222;/lib/modules/3.19.0-32-generic&#8220; prázdný, proto nebude odstran&#283;n
jan@localhost ~ $ sudo dpkg -P linux-headers-3.19.0-32
(&#268;tu databázi &#8230; nyní je nainstalováno 451055 soubor&#367; a adresá&#345;&#367;.)
Removing linux-headers-3.19.0-32 (3.19.0-32.37~14.04.1) ...
jan@localhost ~ $ sudo apt-get update && sudo apt-get full-upgrade
Ign http://archive.ubuntu.com trusty InRelease
Cíl http://ppa.launchpad.net trusty InRelease                                  
Ign http://archive.canonical.com trusty InRelease                              
Mám:1 http://security.ubuntu.com trusty-security InRelease [65,9 kB]           
Ign http://dl.google.com stable InRelease                                      
Mám:2 http://archive.ubuntu.com trusty-updates InRelease [65,9 kB]             
Cíl http://archive.canonical.com trusty Release.gpg                            
Ign http://ppa.launchpad.net trusty InRelease                                  
Cíl http://archive.canonical.com trusty Release                                
Cíl http://ppa.launchpad.net trusty InRelease                                              
Cíl http://dl.google.com stable Release.gpg                                                
Cíl http://deb.playonlinux.com maverick InRelease                                          
Cíl http://download.mono-project.com wheezy InRelease                                      
Cíl http://archive.canonical.com trusty/partner amd64 Packages                 
Ign http://ppa.launchpad.net trusty InRelease                                  
Cíl http://dl.google.com stable Release                                        
Cíl http://download.mono-project.com wheezy/main amd64 Packages                
Ign http://packages.linuxmint.com rebecca InRelease                            
Ign http://extra.linuxmint.com rebecca InRelease                               
Cíl http://archive.ubuntu.com trusty Release.gpg                               
Mám:3 http://security.ubuntu.com trusty-security/main amd64 Packages [483 kB]  
Ign http://ppa.launchpad.net trusty InRelease                                  
Cíl http://download.mono-project.com wheezy/main i386 Packages                 
Cíl http://archive.canonical.com trusty/partner i386 Packages                  
Mám:4 http://archive.ubuntu.com trusty-updates/main amd64 Packages [771 kB]    
Cíl http://dl.google.com stable/main amd64 Packages                            
Cíl http://ppa.launchpad.net trusty InRelease                                  
Cíl http://archive.canonical.com trusty/partner Translation-en                 
Cíl http://packages.linuxmint.com rebecca Release.gpg                          
Cíl http://extra.linuxmint.com rebecca Release.gpg                             
Cíl http://ppa.launchpad.net trusty InRelease                                  
Cíl http://deb.playonlinux.com maverick/main amd64 Packages                    
Cíl http://ppa.launchpad.net trusty InRelease                                  
Cíl http://deb.playonlinux.com maverick/main i386 Packages                     
Ign http://ppa.launchpad.net trusty InRelease                                  
Cíl http://ppa.launchpad.net trusty InRelease                                  
Cíl http://extra.linuxmint.com rebecca Release                                 
Cíl http://packages.linuxmint.com rebecca Release                              
Ign http://ppa.launchpad.net trusty InRelease                                  
Mám:5 http://security.ubuntu.com trusty-security/restricted amd64 Packages [13,0 kB]
Cíl http://ppa.launchpad.net trusty InRelease                                  
Cíl http://ppa.launchpad.net trusty/main Sources                               
Mám:6 http://security.ubuntu.com trusty-security/universe amd64 Packages [130 kB]
Cíl http://ppa.launchpad.net trusty/main amd64 Packages                        
Cíl http://ppa.launchpad.net trusty/main i386 Packages                         
Cíl http://ppa.launchpad.net trusty/main Translation-en                        
Cíl http://packages.linuxmint.com rebecca/main amd64 Packages                  
Cíl http://extra.linuxmint.com rebecca/main amd64 Packages                     
Cíl http://ppa.launchpad.net trusty Release.gpg                                
Mám:7 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [4 978 B]
Cíl http://ppa.launchpad.net trusty/main Sources                               
Mám:8 http://security.ubuntu.com trusty-security/main i386 Packages [456 kB]   
Cíl http://ppa.launchpad.net trusty/main amd64 Packages                        
Ign http://deb.playonlinux.com maverick/main Translation-cs_CZ                 
Ign http://deb.playonlinux.com maverick/main Translation-cs                    
Cíl http://ppa.launchpad.net trusty/main i386 Packages                         
Cíl http://packages.linuxmint.com rebecca/upstream amd64 Packages              
Cíl http://extra.linuxmint.com rebecca/main i386 Packages                      
Ign http://deb.playonlinux.com maverick/main Translation-en                    
Cíl http://ppa.launchpad.net trusty/main Translation-en                        
Cíl http://ppa.launchpad.net trusty Release.gpg                                
Mám:9 http://archive.ubuntu.com trusty-updates/restricted amd64 Packages [15,9 kB]
Ign http://ppa.launchpad.net trusty Release.gpg                                
Cíl http://ppa.launchpad.net trusty/main Sources                               
Ign http://dl.google.com stable/main Translation-cs_CZ                         
Mám:10 http://archive.ubuntu.com trusty-updates/universe amd64 Packages [361 kB]
Cíl http://packages.linuxmint.com rebecca/import amd64 Packages                
Cíl http://ppa.launchpad.net trusty/main amd64 Packages                        
Ign http://dl.google.com stable/main Translation-cs                            
Cíl http://ppa.launchpad.net trusty/main i386 Packages                         
Cíl http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://dl.google.com stable/main Translation-en                            
Ign http://download.mono-project.com wheezy/main Translation-cs_CZ             
Cíl http://ppa.launchpad.net trusty/main Sources                               
Mám:11 http://security.ubuntu.com trusty-security/restricted i386 Packages [12,7 kB]
Cíl http://ppa.launchpad.net trusty/main amd64 Packages                        
Mám:12 http://security.ubuntu.com trusty-security/universe i386 Packages [130 kB]
Cíl http://packages.linuxmint.com rebecca/backport amd64 Packages              
Cíl http://ppa.launchpad.net trusty/main i386 Packages                         
Ign http://download.mono-project.com wheezy/main Translation-cs                
Cíl http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://download.mono-project.com wheezy/main Translation-en                
Cíl http://ppa.launchpad.net trusty/main Sources                               
Mám:13 http://security.ubuntu.com trusty-security/multiverse i386 Packages [5 168 B]
Cíl http://ppa.launchpad.net trusty/main amd64 Packages                        
Mám:14 http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages [13,2 kB]
Cíl http://ppa.launchpad.net trusty/main i386 Packages                         
Cíl http://security.ubuntu.com trusty-security/main Translation-en             
Mám:15 http://archive.ubuntu.com trusty-updates/main i386 Packages [738 kB]    
Cíl http://ppa.launchpad.net trusty/main Translation-en                        
Cíl http://packages.linuxmint.com rebecca/main i386 Packages                   
Cíl http://security.ubuntu.com trusty-security/multiverse Translation-en       
Cíl http://ppa.launchpad.net trusty Release.gpg                                
Cíl http://security.ubuntu.com trusty-security/restricted Translation-en       
Cíl http://security.ubuntu.com trusty-security/universe Translation-en         
Cíl http://ppa.launchpad.net trusty/main Sources                               
Cíl http://ppa.launchpad.net trusty/main amd64 Packages                        
Cíl http://ppa.launchpad.net trusty/main i386 Packages                         
Cíl http://packages.linuxmint.com rebecca/upstream i386 Packages               
Cíl http://ppa.launchpad.net trusty/main Translation-en                        
Cíl http://ppa.launchpad.net trusty Release.gpg                                
Cíl http://ppa.launchpad.net trusty/main Sources                               
Cíl http://ppa.launchpad.net trusty/main amd64 Packages                        
Cíl http://ppa.launchpad.net trusty/main i386 Packages                         
Cíl http://ppa.launchpad.net trusty/main Translation-en                        
Cíl http://packages.linuxmint.com rebecca/import i386 Packages                 
Cíl http://ppa.launchpad.net trusty Release                                    
Cíl http://ppa.launchpad.net trusty Release                                    
Ign http://ppa.launchpad.net trusty Release                                    
Cíl http://ppa.launchpad.net trusty Release                                    
Cíl http://ppa.launchpad.net trusty Release                                    
Cíl http://ppa.launchpad.net trusty/main Sources                               
Cíl http://ppa.launchpad.net trusty/main amd64 Packages                        
Cíl http://packages.linuxmint.com rebecca/backport i386 Packages               
Mám:16 http://archive.ubuntu.com trusty-updates/restricted i386 Packages [15,6 kB]
Cíl http://ppa.launchpad.net trusty/main i386 Packages                         
Mám:17 http://archive.ubuntu.com trusty-updates/universe i386 Packages [363 kB]
Cíl http://ppa.launchpad.net trusty/main Translation-en                        
Cíl http://ppa.launchpad.net trusty/main Sources                               
Cíl http://ppa.launchpad.net trusty/main amd64 Packages                        
Cíl http://ppa.launchpad.net trusty/main i386 Packages                         
Mám:18 http://archive.ubuntu.com trusty-updates/multiverse i386 Packages [13,6 kB]
Cíl http://archive.ubuntu.com trusty-updates/main Translation-en               
Cíl http://archive.ubuntu.com trusty-updates/multiverse Translation-en         
Cíl http://archive.ubuntu.com trusty-updates/restricted Translation-en         
Cíl http://archive.ubuntu.com trusty-updates/universe Translation-en           
Ign http://extra.linuxmint.com rebecca/main Translation-cs_CZ                  
Cíl http://archive.ubuntu.com trusty Release                                   
Cíl http://archive.ubuntu.com trusty/main amd64 Packages                       
Cíl http://archive.ubuntu.com trusty/restricted amd64 Packages                 
Cíl http://ppa.launchpad.net trusty/main Sources                               
Ign http://extra.linuxmint.com rebecca/main Translation-cs                     
Cíl http://ppa.launchpad.net trusty/main amd64 Packages                        
Cíl http://ppa.launchpad.net trusty/main i386 Packages                         
Cíl http://archive.ubuntu.com trusty/universe amd64 Packages                   
Cíl http://ppa.launchpad.net trusty/main Translation-en                        
Cíl http://archive.ubuntu.com trusty/multiverse amd64 Packages                 
Ign http://extra.linuxmint.com rebecca/main Translation-en                     
Cíl http://ppa.launchpad.net trusty/main Sources                               
Cíl http://archive.ubuntu.com trusty/main i386 Packages                        
Cíl http://ppa.launchpad.net trusty/main amd64 Packages                        
Cíl http://archive.ubuntu.com trusty/restricted i386 Packages                  
Cíl http://ppa.launchpad.net trusty/main i386 Packages                         
Cíl http://archive.ubuntu.com trusty/universe i386 Packages                    
Cíl http://archive.ubuntu.com trusty/multiverse i386 Packages                  
Cíl http://archive.ubuntu.com trusty/main Translation-cs                       
Cíl http://archive.ubuntu.com trusty/main Translation-en                       
Cíl http://archive.ubuntu.com trusty/multiverse Translation-cs                 
Cíl http://archive.ubuntu.com trusty/multiverse Translation-en                 
Cíl http://ppa.launchpad.net trusty/main Translation-en                        
Cíl http://archive.ubuntu.com trusty/restricted Translation-cs                 
Cíl http://archive.ubuntu.com trusty/restricted Translation-en                 
Cíl http://archive.ubuntu.com trusty/universe Translation-cs                   
Cíl http://archive.ubuntu.com trusty/universe Translation-en                   
Ign http://archive.ubuntu.com trusty/main Translation-cs_CZ                    
Ign http://archive.ubuntu.com trusty/multiverse Translation-cs_CZ        
Ign http://archive.ubuntu.com trusty/restricted Translation-cs_CZ
Ign http://archive.ubuntu.com trusty/universe Translation-cs_CZ
Ign http://ppa.launchpad.net trusty/main Translation-cs_CZ
Ign http://ppa.launchpad.net trusty/main Translation-cs                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Err http://ppa.launchpad.net trusty/main Sources                               
  404  Not Found
Err http://ppa.launchpad.net trusty/main amd64 Packages                        
  404  Not Found
Err http://ppa.launchpad.net trusty/main i386 Packages                         
  404  Not Found
Ign http://ppa.launchpad.net trusty/main Translation-cs_CZ                     
Ign http://ppa.launchpad.net trusty/main Translation-cs                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://packages.linuxmint.com rebecca/backport Translation-cs_CZ           
Ign http://packages.linuxmint.com rebecca/backport Translation-cs              
Ign http://packages.linuxmint.com rebecca/backport Translation-en              
Ign http://packages.linuxmint.com rebecca/import Translation-cs_CZ             
Ign http://packages.linuxmint.com rebecca/import Translation-cs                
Ign http://packages.linuxmint.com rebecca/import Translation-en                
Ign http://packages.linuxmint.com rebecca/main Translation-cs_CZ               
Ign http://packages.linuxmint.com rebecca/main Translation-cs
Ign http://packages.linuxmint.com rebecca/main Translation-en
Ign http://packages.linuxmint.com rebecca/upstream Translation-cs_CZ
Ign http://packages.linuxmint.com rebecca/upstream Translation-cs
Ign http://packages.linuxmint.com rebecca/upstream Translation-en
Sta&#382;eno 3 657 kB za 13s (275 kB/s)
W: Selhalo sta&#382;ení http://ppa.launchpad.net/jtasker/weather-indicator/ubuntu/dists/trusty/main/source/Sources  404  Not Found


W: Selhalo sta&#382;ení http://ppa.launchpad.net/jtasker/weather-indicator/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found


W: Selhalo sta&#382;ení http://ppa.launchpad.net/jtasker/weather-indicator/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found


E: N&#283;které indexové soubory se nepoda&#345;ilo stáhnout. Jsou ignorovány, nebo jsou pou&#382;ity star&#353;í verze.
jan@localhost ~ $ sudo apt-get -f upgrade  
&#268;tu seznamy balík&#367;&#8230; Hotovo
Vytvá&#345;í se strom závislostí       
&#268;tu stavové informace&#8230; Hotovo
Propo&#269;ítávám aktualizaci&#8230; Hotovo
Následující balík byl nainstalován automaticky a ji&#382; není pot&#345;eba:
  mdm
Pro jeho odstran&#283;ní pou&#382;ijte &#8222;apt-get autoremove&#8220;.
Následující balíky jsou podr&#382;eny v aktuální verzi:
  linux-generic linux-headers-generic linux-image-generic
Následující balíky budou aktualizovány:
  dosfstools libgd-dev libgd2-xpm-dev libgd3 libgd3:i386 linux-libc-dev
6 aktualizováno, 0 nov&#283; instalováno, 0 k odstran&#283;ní a 3 neaktualizováno.
Pot&#345;ebuji stáhnout 1 327 kB archiv&#367;.
Po této operaci bude na disku pou&#382;ito dal&#353;ích 0 B.
Chcete pokra&#269;ovat? [Y/n] y
Mám:1 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libgd-dev amd64 2.1.0-3ubuntu0.1 [250 kB]
Mám:2 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libgd3 i386 2.1.0-3ubuntu0.1 [118 kB]
Mám:3 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libgd3 amd64 2.1.0-3ubuntu0.1 [121 kB]
Mám:4 http://archive.ubuntu.com/ubuntu/ trusty-updates/main dosfstools amd64 3.0.26-1ubuntu0.1 [60,1 kB]
Mám:5 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libgd2-xpm-dev all 2.1.0-3ubuntu0.1 [1 198 B]
Mám:6 http://archive.ubuntu.com/ubuntu/ trusty-updates/main linux-libc-dev amd64 3.13.0-87.133 [777 kB]
Sta&#382;eno 1 327 kB za 1s (750 kB/s)        
(&#268;tu databázi &#8230; nyní je nainstalováno 435233 soubor&#367; a adresá&#345;&#367;.)
Preparing to unpack &#8230;/libgd-dev_2.1.0-3ubuntu0.1_amd64.deb ...
Unpacking libgd-dev:amd64 (2.1.0-3ubuntu0.1) over (2.1.0-3) ...
Preparing to unpack &#8230;/libgd3_2.1.0-3ubuntu0.1_i386.deb ...
De-configuring libgd3:amd64 (2.1.0-3) ...
Unpacking libgd3:i386 (2.1.0-3ubuntu0.1) over (2.1.0-3) ...
Preparing to unpack &#8230;/libgd3_2.1.0-3ubuntu0.1_amd64.deb ...
Unpacking libgd3:amd64 (2.1.0-3ubuntu0.1) over (2.1.0-3) ...
Preparing to unpack &#8230;/dosfstools_3.0.26-1ubuntu0.1_amd64.deb ...
Unpacking dosfstools (3.0.26-1ubuntu0.1) over (3.0.26-1) ...
Preparing to unpack &#8230;/libgd2-xpm-dev_2.1.0-3ubuntu0.1_all.deb ...
Unpacking libgd2-xpm-dev (2.1.0-3ubuntu0.1) over (2.1.0-3) ...
Preparing to unpack &#8230;/linux-libc-dev_3.13.0-87.133_amd64.deb ...
Unpacking linux-libc-dev:amd64 (3.13.0-87.133) over (3.13.0-86.131) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Nastavuji balík libgd3:amd64 (2.1.0-3ubuntu0.1) &#8230;
Nastavuji balík libgd3:i386 (2.1.0-3ubuntu0.1) &#8230;
Nastavuji balík libgd-dev:amd64 (2.1.0-3ubuntu0.1) &#8230;
Nastavuji balík dosfstools (3.0.26-1ubuntu0.1) &#8230;
Nastavuji balík libgd2-xpm-dev (2.1.0-3ubuntu0.1) &#8230;
Nastavuji balík linux-libc-dev:amd64 (3.13.0-87.133) &#8230;
Processing triggers for libc-bin (2.19-0ubuntu6.9) ...




```
This is full output - I have not removed some of the stuff from the update list.. I will get to it soon.

---

### Post by Bashing-om on 2016-06-01
Jan_Jindrek; Welp:

1) " W: Selhalo stažení [http://ppa.launchpad.net/jtasker/weather-indicator/ubuntu/dists/trusty/main/source/Sources](http://ppa.launchpad.net/jtasker/weather-indicator/ubuntu/dists/trusty/main/source/Sources)  404  Not Found"
Back up in the thread and see to remove this PPA / Remove this PPA .

2) " p&#345;i odstra&#328;ování linux-headers-3.13.0-83-generic není adresá&#345; „/lib/modules/3.13.0-83-generic“ prázdný, proto nebude odstran&#283;n "
We best deal with this now rather than later.
post back:
```

ls -al /usr/src/
ls -al /lib/modules/
dpkg -l |grep linux-
ls -al /boot
ls -al /vmlinuz*
ls -al /initrd.img*

```

3) I had expected the new kernel .. Your mirror has not caught up with current ?
What returns:
```

apt-cache policy linux-image-generic

```

[INDENT][INDENT]a lot going on
[INDENT][INDENT][INDENT]reduce to simplest terms
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-06-01
```

jan@localhost ~ $ ls -al /usr/src
celkem 68
drwxr-xr-x 13 root root  4096 &#269;en  1 20:06 .
drwxr-xr-x 19 root root  4096 dub 26  2015 ..
-rw-r--r--  1 root root  7218 &#269;ec 26  2015 bbswitch.tar.bz2
drwxr-xr-x  2 root root  4096 kv&#283; 25 12:54 bbswitch-0.8
drwxr-xr-x  3 root root  4096 dub  3  2015 dsp
drwxr-xr-x 24 root root  4096 b&#345;e 26  2015 linux-headers-3.13.0-24
drwxr-xr-x  7 root root  4096 b&#345;e  7  2015 linux-headers-3.13.0-24-generic
drwxr-xr-x 24 root root  4096 b&#345;e 24 23:19 linux-headers-3.13.0-37
drwxr-xr-x  7 root root  4096 b&#345;e 24 23:19 linux-headers-3.13.0-37-generic
drwxr-xr-x 24 root root  4096 kv&#283; 22 19:39 linux-headers-3.13.0-86
drwxr-xr-x  7 root root  4096 kv&#283; 30 02:08 linux-headers-3.13.0-86-generic
drwxr-xr-x  4 root root 12288 kv&#283; 30 12:57 nvidia-352-352.63
drwxr-xr-x  6 root root  4096 kv&#283; 30 23:27 oem-audio-hda-daily-0.201605300501~ubuntu14.04.1
lrwxrwxrwx  1 root root    32 srp 13  2015 vboxhost-5.0.2 -> ../share/virtualbox/src/vboxhost
drwxr-xr-x  7 root root  4096 b&#345;e 26  2015 virtualbox-guest-4.3.18
jan@localhost ~ $ ls -al /lib/modules
celkem 36
drwxr-xr-x  9 root root 4096 kv&#283; 23 17:14 .
drwxr-xr-x 27 root root 4096 kv&#283; 30 23:25 ..
drwxr-xr-x  5 root root 4096 dub 22 23:09 3.13.0-24-generic
drwxr-xr-x  6 root root 4096 kv&#283; 30 23:27 3.13.0-37-generic
drwxr-xr-x  3 root root 4096 kv&#283; 22 19:38 3.13.0-53-generic
drwxr-xr-x  3 root root 4096 &#269;en  1 20:05 3.13.0-83-generic
drwxr-xr-x  3 root root 4096 &#269;en  1 20:05 3.13.0-85-generic
drwxr-xr-x  6 root root 4096 kv&#283; 30 23:29 3.13.0-86-generic
drwxr-xr-x  3 root root 4096 &#269;en  1 20:06 3.19.0-32-generic
jan@localhost ~ $ dpkg -l | grep linux-
ii  binutils-aarch64-linux-gnu                                  2.24-5ubuntu14cross0.11.2                              amd64        GNU binary utilities, for aarch64-linux-gnu target
ii  binutils-arm-linux-gnueabi                                  2.24-5ubuntu13cross1.97.1                              amd64        GNU binary utilities, for arm-linux-gnueabi target
ii  binutils-powerpc-linux-gnu                                  2.24-5ubuntu13cross0.10.1                              amd64        GNU binary utilities, for powerpc-linux-gnu target
ii  binutils-powerpc64le-linux-gnu                              2.24-5ubuntu13cross0.4.1                               amd64        GNU binary utilities, for powerpc64le-linux-gnu target
ii  cpp-4.7-arm-linux-gnueabi                                   4.7.3-12ubuntu1cross1.85                               amd64        GNU C preprocessor                                
ii  cpp-4.8-aarch64-linux-gnu                                   4.8.4-2ubuntu1~14.04.1cross0.11.2                      amd64        GNU C preprocessor                                
ii  cpp-4.8-powerpc-linux-gnu                                   4.8.4-2ubuntu1~14.04.1cross0.11.2                      amd64        GNU C preprocessor
ii  cpp-4.8-powerpc64le-linux-gnu                               4.8.4-2ubuntu1~14.04.1cross0.4.2                       amd64        GNU C preprocessor
ii  cpp-arm-linux-gnueabi                                       4:4.7.2-1                                              amd64        The GNU C preprocessor (cpp) for armel architecture
ii  g++-4.7-arm-linux-gnueabi                                   4.7.3-12ubuntu1cross1.85                               amd64        GNU C++ compiler
ii  g++-arm-linux-gnueabi                                       4:4.7.2-1                                              amd64        The GNU C++ compiler for armel architecture
ii  gcc-4.7-arm-linux-gnueabi                                   4.7.3-12ubuntu1cross1.85                               amd64        GNU C compiler
ii  gcc-4.7-arm-linux-gnueabi-base                              4.7.3-12ubuntu1cross1.85                               amd64        GCC, the GNU Compiler Collection (base package)
ii  gcc-4.8-aarch64-linux-gnu                                   4.8.4-2ubuntu1~14.04.1cross0.11.2                      amd64        GNU C compiler
ii  gcc-4.8-aarch64-linux-gnu-base                              4.8.4-2ubuntu1~14.04.1cross0.11.2                      amd64        GCC, the GNU Compiler Collection (base package)
ii  gcc-4.8-powerpc-linux-gnu                                   4.8.4-2ubuntu1~14.04.1cross0.11.2                      amd64        GNU C compiler
ii  gcc-4.8-powerpc-linux-gnu-base                              4.8.4-2ubuntu1~14.04.1cross0.11.2                      amd64        GCC, the GNU Compiler Collection (base package)
ii  gcc-4.8-powerpc64le-linux-gnu                               4.8.4-2ubuntu1~14.04.1cross0.4.2                       amd64        GNU C compiler
ii  gcc-4.8-powerpc64le-linux-gnu-base                          4.8.4-2ubuntu1~14.04.1cross0.4.2                       amd64        GCC, the GNU Compiler Collection (base package)
ii  gcc-arm-linux-gnueabi                                       4:4.7.2-1                                              amd64        The GNU C compiler for armel architecture
ii  gobjc++-4.7-arm-linux-gnueabi                               4.7.3-12ubuntu1cross1.85                               amd64        GNU Objective-C++ compiler
ii  gobjc-4.7-arm-linux-gnueabi                                 4.7.3-12ubuntu1cross1.85                               amd64        GNU Objective-C compiler
ii  gobjc-4.8-aarch64-linux-gnu                                 4.8.4-2ubuntu1~14.04.1cross0.11.2                      amd64        GNU Objective-C compiler
ii  gobjc-4.8-powerpc-linux-gnu                                 4.8.4-2ubuntu1~14.04.1cross0.11.2                      amd64        GNU Objective-C compiler
ii  gobjc-4.8-powerpc64le-linux-gnu                             4.8.4-2ubuntu1~14.04.1cross0.4.2                       amd64        GNU Objective-C compiler
ii  linux-firmware                                              1.127.22                                               all          Firmware for Linux kernel drivers
ii  linux-generic                                               3.13.0.86.92                                           amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-24                                     3.13.0-24.47                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-24-generic                             3.13.0-24.47                                           amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-37                                     3.13.0-37.64                                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-37-generic                             3.13.0-37.64                                           amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-86                                     3.13.0-86.131                                          all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-86-generic                             3.13.0-86.131                                          amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       3.13.0.86.92                                           amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-24-generic                               3.13.0-24.47                                           amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-37-generic                               3.13.0-37.64                                           amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-86-generic                               3.13.0-86.131                                          amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic                         3.13.0-24.47                                           amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic                         3.13.0-37.64                                           amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-86-generic                         3.13.0-86.131                                          amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                         3.13.0.86.92                                           amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                        3.13.0-87.133                                          amd64        Linux Kernel Headers for development
ii  linux-libc-dev-arm64-cross                                  3.13.0-12.32cross0.10                                  all          Linux Kernel Headers for development (for cross-compiling)
ii  linux-libc-dev-armel-cross                                  3.13.0-12.32cross1.104                                 all          Linux Kernel Headers for development (for cross-compiling)
ii  linux-libc-dev-powerpc-cross                                3.13.0-13.33cross1.1                                   all          Linux Kernel Headers for development (for cross-compiling)
ii  linux-libc-dev-ppc64el-cross                                3.13.0-13.33cross0.2                                   all          Linux Kernel Headers for development (for cross-compiling)
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu4                                   all          base package for ALSA and OSS sound systems
ii  mlton-runtime-x86-64-linux-gnu                              20100608-5.1                                           amd64        Optimizing compiler for Standard ML - amd64 runtime libraries
ii  syslinux-common                                             3:4.05+dfsg-6+deb8u1                                   all          collection of boot loaders (common files)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu5                                   amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  syslinux-themes-linuxmint-cinnamon                          1.0.7                                                  all          collection of boot loaders (theme metapackage)
ii  syslinux-themes-linuxmint-cinnamon-rebecca                  1.0.7                                                  all          collection of boot loaders (linuxmint-rebecca theme)
jan@localhost ~ $ ls -al /boot
celkem 132208
drwxr-xr-x  4 root root     4096 kv&#283; 27 13:36 .
drwxr-xr-x 29 root root     4096 kv&#283; 23 20:43 ..
-rw-r--r--  1 root root  1158016 kv&#283;  3  2014 abi-3.13.0-24-generic
-rw-r--r--  1 root root  1164489 zá&#345; 23  2014 abi-3.13.0-37-generic
-rw-r--r--  1 root root  1166060 kv&#283; 13 04:15 abi-3.13.0-86-generic
-rw-r--r--  1 root root   165510 kv&#283;  3  2014 config-3.13.0-24-generic
-rw-r--r--  1 root root   165712 zá&#345; 23  2014 config-3.13.0-37-generic
-rw-r--r--  1 root root   165918 kv&#283; 13 04:15 config-3.13.0-86-generic
drwxr-xr-x  2 root root     4096 kv&#283; 23 17:18 config-3.19.0-32-generic
drwxr-xr-x  5 root root     4096 kv&#283; 30 12:57 grub
-rw-r--r--  1 root root  8248624 kv&#283; 22 18:29 initrd.img-3.13.0.24-generic
-rw-r--r--  1 root root 28400618 b&#345;e 23 23:10 initrd.img-3.13.0-24-generic
-rw-r--r--  1 root root 28577374 kv&#283; 23 20:46 initrd.img-3.13.0-37-generic
-rw-r--r--  1 root root 28682434 kv&#283; 25 14:56 initrd.img-3.13.0-86-generic
-rw-r--r--  1 root root  8249113 kv&#283; 27 13:36 initrd.img-3.19.0-32-generic
-rw-r--r--  1 root root   729120 led 14  2015 ipxe.efi
-rw-r--r--  1 root root   342498 led 14  2015 ipxe.lkrn
-rw-r--r--  1 root root   176500 b&#345;e 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 b&#345;e 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 b&#345;e 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  3372643 kv&#283;  3  2014 System.map-3.13.0-24-generic
-rw-------  1 root root  3386945 zá&#345; 23  2014 System.map-3.13.0-37-generic
-rw-------  1 root root  3393573 kv&#283; 13 04:15 System.map-3.13.0-86-generic
-rw-------  1 root root  5776416 kv&#283;  3  2014 vmlinuz-3.13.0-24-generic
-rw-------  1 root root  5808832 zá&#345; 23  2014 vmlinuz-3.13.0-37-generic
-rw-------  1 root root  5834048 kv&#283; 13 04:15 vmlinuz-3.13.0-86-generic
jan@localhost ~ $ ls -al /vmlinuz*
lrwxrwxrwx 1 root root 30 kv&#283; 23 20:43 /vmlinuz -> boot/vmlinuz-3.13.0-86-generic
lrwxrwxrwx 1 root root 30 b&#345;e 24 23:20 /vmlinuz.old -> boot/vmlinuz-3.13.0-37-generic
jan@localhost ~ $ ls -al /initrd.img*
lrwxrwxrwx 1 root root 33 kv&#283; 23 20:43 /initrd.img -> boot/initrd.img-3.13.0-86-generic
lrwxrwxrwx 1 root root 33 b&#345;e 24 23:20 /initrd.img.old -> boot/initrd.img-3.13.0-37-generic
jan@localhost ~ $ sudo apt-cache policy linux-image-generic
[sudo] password for jan: 
linux-image-generic:
  Instalovaná verze: 3.13.0.86.92
  Kandidát:          3.13.0.87.93
  Tabulka verzí:
     3.13.0.87.93 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
 *** 3.13.0.86.92 0
        100 /var/lib/dpkg/status
     3.13.0.24.28 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages





```
This is all

---

### Post by Bashing-om on 2016-06-01
Jan_Jindrek; Yukkie;

We do this the hard way.

OK, as a last resort .. others beware NOT a good thing to do ! - we get down and real dirty
```

sudo rm -rf /lib/modules/3.13.0-{53,83,85}*
sudo rm -rf /lib/modules/3.19.0-32*
sudo rm /boot/*-3.19.0-32-generic

```
The above goes behind the package manager's back and breaks the package management system.
Copy and paste for best results, note the use of the wild card character '*" is required and an error here will be very difficult to recover from.

Now let's try and put the package manager back together:
If we have all our ducks in a row, should work.
```

sudo apt -f install
sudo update-grub

```

This. however, does make me pause:
> 
-rw-r--r--  1 root root  8248624 kv&#283; 22 18:29 initrd.img-3.13.0.24-generic
-rw-r--r--  1 root root 28400618 b&#345;e 23 23:10 initrd.img-3.13.0-24-generic
-
and consider ... Why OH why are there 2 "initrd.img-3.13.0-24-generic" files in existence ? How can this even happen ? Note the difference in the sizes of the files .. Something is real real bad here .
I do think we get stable and consistent .. we should focus on removing this kernel also .

And that -87 kernel is there, so why did it not install ?
Let's try again:
```

sudo apt update
sudo apt full-upgrade

```

Not, yet - are we ready
[INDENT][INDENT]to try and install a graphic's driver
[/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-06-01
Okay, it seems to work, no depmod problems when reinstalling nvidia driver, trying to remove all other nvidia related stuff, especially bumblebee and install nvidia-prime and finally get the driver working! If you are a girl, I wanna marry you!!! Thank you thousand times!

---

### Post by Bashing-om on 2016-06-01
Jan_Jindrek; Hey ...

Sounds like we have made good progress.
I Do not know how Mint will work out with Nvidia-prime;
Keep me advised on the status of what you have done.

Does the driver install, and nvidia-prime is functional ?

----------------------

Marry Me ....
Have to ask my other half for approval :) .


[INDENT][INDENT]it is a good thing
[INDENT][INDENT]when a plan works out
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-06-01
So I installed prime, picked nvidia-352, rebooted, however startx stops at LOADING NV-CONTROL and all I get is a black screen...

---

### Post by Bashing-om on 2016-06-01
Jan_Jindrek; Welp;

Not real surprised . Did you purge BumbleBee ? And I seem to recall that Mint has incorporated the functionality to Re-install BumbleBee. We may have a lot of homework to do in this respect to discover how and what one must do to make the system not do this !

However,
Let's look and see what the status is now.
```

cat /var/log/Xorg.0.log
cat /var/log/gpu-manager.log
dpkg -l | grep -i nvidia
lsmod | grep nvidia

```
get us a hint of what we are going to do.

[INDENT][INDENT]not over 'til
[INDENT][INDENT]it is over
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-06-01
```

jan@localhost ~ $ cat /var/log/Xorg.0.log
[    28.219] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    28.219] X Protocol Version 11, Revision 0
[    28.219] Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
[    28.219] Current Operating System: Linux localhost 3.13.0-87-generic #133-Ubuntu SMP Tue May 24 18:32:09 UTC 2016 x86_64
[    28.219] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-87-generic root=UUID=05f808d5-075a-4ba8-99e8-bfcfdc0b2807 ro plymouth:debug=1
[    28.219] Build Date: 12 February 2015  02:49:29PM
[    28.219] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support) 
[    28.219] Current version of pixman: 0.30.2
[    28.219]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    28.219] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    28.219] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun  2 00:02:33 2016
[    28.330] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    28.346] (==) No Layout section.  Using the first Screen section.
[    28.346] (==) No screen section available. Using defaults.
[    28.346] (**) |-->Screen "Default Screen Section" (0)
[    28.346] (**) |   |-->Monitor "<default monitor>"
[    28.346] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[    28.346] (==) Automatically adding devices
[    28.346] (==) Automatically enabling devices
[    28.346] (==) Automatically adding GPU devices
[    28.346] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    28.346]    Entry deleted from font path.
[    28.346] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    28.346]    Entry deleted from font path.
[    28.346] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    28.346]    Entry deleted from font path.
[    28.346] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    28.346]    Entry deleted from font path.
[    28.346] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    28.346]    Entry deleted from font path.
[    28.346] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[    28.347] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    28.347] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    28.347] (II) Loader magic: 0x7fbe54e97d40
[    28.347] (II) Module ABI versions:
[    28.347]    X.Org ANSI C Emulation: 0.4
[    28.347]    X.Org Video Driver: 15.0
[    28.347]    X.Org XInput driver : 20.0
[    28.347]    X.Org Server Extension : 8.0
[    28.347] (II) xfree86: Adding drm device (/dev/dri/card0)
[    28.348] (--) PCI:*(0:0:2:0) 8086:0416:1462:1112 rev 6, Mem @ 0xf7400000/4194304, 0xd0000000/268435456, I/O @ 0x0000f000/64
[    28.348] (--) PCI: (0:1:0:0) 10de:1341:1462:1112 rev 162, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    28.348] Initializing built-in extension Generic Event Extension
[    28.348] Initializing built-in extension SHAPE
[    28.348] Initializing built-in extension MIT-SHM
[    28.348] Initializing built-in extension XInputExtension
[    28.348] Initializing built-in extension XTEST
[    28.348] Initializing built-in extension BIG-REQUESTS
[    28.348] Initializing built-in extension SYNC
[    28.348] Initializing built-in extension XKEYBOARD
[    28.348] Initializing built-in extension XC-MISC
[    28.348] Initializing built-in extension SECURITY
[    28.348] Initializing built-in extension XINERAMA
[    28.348] Initializing built-in extension XFIXES
[    28.348] Initializing built-in extension RENDER
[    28.348] Initializing built-in extension RANDR
[    28.348] Initializing built-in extension COMPOSITE
[    28.348] Initializing built-in extension DAMAGE
[    28.348] Initializing built-in extension MIT-SCREEN-SAVER
[    28.348] Initializing built-in extension DOUBLE-BUFFER
[    28.348] Initializing built-in extension RECORD
[    28.348] Initializing built-in extension DPMS
[    28.348] Initializing built-in extension Present
[    28.348] Initializing built-in extension DRI3
[    28.348] Initializing built-in extension X-Resource
[    28.348] Initializing built-in extension XVideo
[    28.348] Initializing built-in extension XVideo-MotionCompensation
[    28.348] Initializing built-in extension SELinux
[    28.348] Initializing built-in extension XFree86-VidModeExtension
[    28.348] Initializing built-in extension XFree86-DGA
[    28.348] Initializing built-in extension XFree86-DRI
[    28.348] Initializing built-in extension DRI2
[    28.348] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    28.348] (II) "glx" will be loaded by default.
[    28.348] (WW) "xmir" is not to be loaded by default. Skipping.
[    28.348] (II) LoadModule: "glx"
[    28.399] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    29.428] (II) Module glx: vendor="NVIDIA Corporation"
[    29.428]    compiled for 4.0.2, module version = 1.0.0
[    29.428]    Module class: X.Org Server Extension
[    29.480] (II) NVIDIA GLX Module  352.63  Sat Nov  7 20:52:00 PST 2015
[    29.481] Loading extension GLX
[    29.481] (==) Matched intel as autoconfigured driver 0
[    29.481] (==) Matched intel as autoconfigured driver 1
[    29.481] (==) Matched modesetting as autoconfigured driver 2
[    29.481] (==) Matched fbdev as autoconfigured driver 3
[    29.481] (==) Matched vesa as autoconfigured driver 4
[    29.481] (==) Assigned the driver to the xf86ConfigLayout
[    29.481] (II) LoadModule: "intel"
[    29.517] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    29.595] (II) Module intel: vendor="X.Org Foundation"
[    29.595]    compiled for 1.15.1, module version = 2.99.917
[    29.595]    Module class: X.Org Video Driver
[    29.595]    ABI class: X.Org Video Driver, version 15.0
[    29.595] (II) LoadModule: "modesetting"
[    29.595] (WW) Warning, couldn't open module modesetting
[    29.595] (II) UnloadModule: "modesetting"
[    29.595] (II) Unloading modesetting
[    29.595] (EE) Failed to load module "modesetting" (module does not exist, 0)
[    29.595] (II) LoadModule: "fbdev"
[    29.595] (WW) Warning, couldn't open module fbdev
[    29.595] (II) UnloadModule: "fbdev"
[    29.595] (II) Unloading fbdev
[    29.595] (EE) Failed to load module "fbdev" (module does not exist, 0)
[    29.595] (II) LoadModule: "vesa"
[    29.595] (WW) Warning, couldn't open module vesa
[    29.595] (II) UnloadModule: "vesa"
[    29.595] (II) Unloading vesa
[    29.595] (EE) Failed to load module "vesa" (module does not exist, 0)
[    29.595] (==) Matched intel as autoconfigured driver 0
[    29.595] (==) Matched intel as autoconfigured driver 1
[    29.595] (==) Matched modesetting as autoconfigured driver 2
[    29.595] (==) Matched fbdev as autoconfigured driver 3
[    29.595] (==) Matched vesa as autoconfigured driver 4
[    29.595] (==) Assigned the driver to the xf86ConfigLayout
[    29.595] (II) LoadModule: "intel"
[    29.595] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    29.595] (II) Module intel: vendor="X.Org Foundation"
[    29.595]    compiled for 1.15.1, module version = 2.99.917
[    29.595]    Module class: X.Org Video Driver
[    29.595]    ABI class: X.Org Video Driver, version 15.0
[    29.595] (II) UnloadModule: "intel"
[    29.595] (II) Unloading intel
[    29.595] (II) Failed to load module "intel" (already loaded, 32702)
[    29.595] (II) LoadModule: "modesetting"
[    29.596] (WW) Warning, couldn't open module modesetting
[    29.596] (II) UnloadModule: "modesetting"
[    29.596] (II) Unloading modesetting
[    29.596] (EE) Failed to load module "modesetting" (module does not exist, 0)
[    29.596] (II) LoadModule: "fbdev"
[    29.596] (WW) Warning, couldn't open module fbdev
[    29.596] (II) UnloadModule: "fbdev"
[    29.596] (II) Unloading fbdev
[    29.596] (EE) Failed to load module "fbdev" (module does not exist, 0)
[    29.596] (II) LoadModule: "vesa"
[    29.596] (WW) Warning, couldn't open module vesa
[    29.596] (II) UnloadModule: "vesa"
[    29.596] (II) Unloading vesa
[    29.596] (EE) Failed to load module "vesa" (module does not exist, 0)
[    29.596] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
        i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
        915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
        Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
        GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    29.596] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    29.596] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    29.596] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    29.596] (++) using VT number 8


[    29.599] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20080730
[    29.599] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20151202.da9ad388-0ubuntu0sarvatt~trusty (Robert Hooker <sarvatt@ubuntu.com>)
[    29.599] (II) intel(0): SNA compiled for use with valgrind
[    29.600] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4600
[    29.600] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2; using a maximum of 2 threads
[    29.600] (II) intel(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[    29.600] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    29.600] (==) intel(0): RGB weight 888
[    29.600] (==) intel(0): Default visual is TrueColor
[    29.600] (II) intel(0): Output eDP1 has no monitor section
[    29.600] (--) intel(0): Found backlight control interface acpi_video0 (type 'firmware') for output eDP1
[    29.600] (II) intel(0): Enabled output eDP1
[    29.600] (II) intel(0): Output VGA1 has no monitor section
[    29.600] (II) intel(0): Enabled output VGA1
[    29.600] (II) intel(0): Output HDMI1 has no monitor section
[    29.600] (II) intel(0): Enabled output HDMI1
[    29.600] (--) intel(0): Using a maximum size of 64x64 for hardware cursors
[    29.600] (II) intel(0): Output VIRTUAL1 has no monitor section
[    29.600] (II) intel(0): Enabled output VIRTUAL1
[    29.600] (--) intel(0): Output eDP1 using initial mode 1920x1080 on pipe 0
[    29.600] (==) intel(0): TearFree disabled
[    29.600] (==) intel(0): DPI set to (96, 96)
[    29.600] (II) Loading sub module "dri2"
[    29.600] (II) LoadModule: "dri2"
[    29.600] (II) Module "dri2" already built-in
[    29.600] (II) Loading sub module "present"
[    29.600] (II) LoadModule: "present"
[    29.600] (WW) Warning, couldn't open module present
[    29.600] (II) UnloadModule: "present"
[    29.600] (II) Unloading present
[    29.600] (EE) intel: Failed to load module "present" (module does not exist, 0)
[    29.604] (==) Depth 24 pixmap format is 32 bpp
[    29.604] (II) intel(0): SNA initialized with Haswell (gen7.5, gt2) backend
[    29.604] (==) intel(0): Backing store enabled
[    29.604] (==) intel(0): Silken mouse enabled
[    29.604] (II) intel(0): HW Cursor enabled
[    29.604] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    29.604] (==) intel(0): DPMS enabled
[    29.604] (==) intel(0): Display hotplug detection enabled
[    29.604] (II) intel(0): [DRI2] Setup complete
[    29.604] (II) intel(0): [DRI2]   DRI driver: i965
[    29.604] (II) intel(0): [DRI2]   VDPAU driver: va_gl
[    29.604] (II) intel(0): direct rendering: DRI2 enabled
[    29.604] (--) RandR disabled
[    29.607] (II) SELinux: Disabled on system
[    29.638] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    29.640] (II) intel(0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    29.640] (II) intel(0): Setting screen physical size to 508 x 285
[    29.644] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    29.646] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    29.646] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.646] (II) LoadModule: "evdev"
[    29.646] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.685] (II) Module evdev: vendor="X.Org Foundation"
[    29.685]    compiled for 1.15.0, module version = 2.8.2
[    29.685]    Module class: X.Org XInput Driver
[    29.685]    ABI class: X.Org XInput driver, version 20.0
[    29.685] (II) Using input driver 'evdev' for 'Power Button'
[    29.685] (**) Power Button: always reports core events
[    29.685] (**) evdev: Power Button: Device: "/dev/input/event3"
[    29.685] (--) evdev: Power Button: Vendor 0 Product 0x1
[    29.685] (--) evdev: Power Button: Found keys
[    29.685] (II) evdev: Power Button: Configuring as keyboard
[    29.685] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    29.685] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    29.685] (**) Option "xkb_rules" "evdev"
[    29.685] (**) Option "xkb_model" "pc105"
[    29.685] (**) Option "xkb_layout" "cz"
[    29.687] (II) XKB: reuse xkmfile /var/lib/xkb/server-583B992BBA3776030BA62AC94FC7F0AE9B04119F.xkm
[    29.687] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[    29.687] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    29.687] (II) Using input driver 'evdev' for 'Video Bus'
[    29.687] (**) Video Bus: always reports core events
[    29.687] (**) evdev: Video Bus: Device: "/dev/input/event8"
[    29.687] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    29.687] (--) evdev: Video Bus: Found keys
[    29.687] (II) evdev: Video Bus: Configuring as keyboard
[    29.687] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input9/event8"
[    29.687] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    29.687] (**) Option "xkb_rules" "evdev"
[    29.687] (**) Option "xkb_model" "pc105"
[    29.687] (**) Option "xkb_layout" "cz"
[    29.687] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    29.687] (II) No input driver specified, ignoring this device.
[    29.687] (II) This device may have been added with another device file.
[    29.688] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    29.688] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    29.688] (II) Using input driver 'evdev' for 'Video Bus'
[    29.688] (**) Video Bus: always reports core events
[    29.688] (**) evdev: Video Bus: Device: "/dev/input/event7"
[    29.688] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    29.688] (--) evdev: Video Bus: Found keys
[    29.688] (II) evdev: Video Bus: Configuring as keyboard
[    29.688] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:45/LNXVIDEO:00/input/input8/event7"
[    29.688] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    29.688] (**) Option "xkb_rules" "evdev"
[    29.688] (**) Option "xkb_model" "pc105"
[    29.688] (**) Option "xkb_layout" "cz"
[    29.688] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    29.688] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.688] (II) Using input driver 'evdev' for 'Power Button'
[    29.688] (**) Power Button: always reports core events
[    29.688] (**) evdev: Power Button: Device: "/dev/input/event1"
[    29.688] (--) evdev: Power Button: Vendor 0 Product 0x1
[    29.688] (--) evdev: Power Button: Found keys
[    29.688] (II) evdev: Power Button: Configuring as keyboard
[    29.688] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    29.688] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[    29.688] (**) Option "xkb_rules" "evdev"
[    29.688] (**) Option "xkb_model" "pc105"
[    29.688] (**) Option "xkb_layout" "cz"
[    29.688] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    29.688] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    29.688] (II) Using input driver 'evdev' for 'Sleep Button'
[    29.688] (**) Sleep Button: always reports core events
[    29.688] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    29.688] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    29.688] (--) evdev: Sleep Button: Found keys
[    29.688] (II) evdev: Sleep Button: Configuring as keyboard
[    29.688] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    29.688] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 10)
[    29.688] (**) Option "xkb_rules" "evdev"
[    29.688] (**) Option "xkb_model" "pc105"
[    29.688] (**) Option "xkb_layout" "cz"
[    29.688] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[    29.688] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    29.688] (II) config/udev: Adding input device HDA Intel HDMI HDMI (/dev/input/event11)
[    29.688] (II) No input driver specified, ignoring this device.
[    29.688] (II) This device may have been added with another device file.
[    29.689] (II) config/udev: Adding input device MOSART Semi. 2.4G Wireless Mouse (/dev/input/event5)
[    29.689] (**) MOSART Semi. 2.4G Wireless Mouse: Applying InputClass "evdev pointer catchall"
[    29.689] (II) Using input driver 'evdev' for 'MOSART Semi. 2.4G Wireless Mouse'
[    29.689] (**) MOSART Semi. 2.4G Wireless Mouse: always reports core events
[    29.689] (**) evdev: MOSART Semi. 2.4G Wireless Mouse: Device: "/dev/input/event5"
[    29.689] (--) evdev: MOSART Semi. 2.4G Wireless Mouse: Vendor 0x3938 Product 0x1031
[    29.689] (--) evdev: MOSART Semi. 2.4G Wireless Mouse: Found 9 mouse buttons
[    29.689] (--) evdev: MOSART Semi. 2.4G Wireless Mouse: Found scroll wheel(s)
[    29.689] (--) evdev: MOSART Semi. 2.4G Wireless Mouse: Found relative axes
[    29.689] (--) evdev: MOSART Semi. 2.4G Wireless Mouse: Found x and y relative axes
[    29.689] (--) evdev: MOSART Semi. 2.4G Wireless Mouse: Found absolute axes
[    29.689] (II) evdev: MOSART Semi. 2.4G Wireless Mouse: Forcing absolute x/y axes to exist.
[    29.689] (II) evdev: MOSART Semi. 2.4G Wireless Mouse: Configuring as mouse
[    29.689] (II) evdev: MOSART Semi. 2.4G Wireless Mouse: Adding scrollwheel support
[    29.689] (**) evdev: MOSART Semi. 2.4G Wireless Mouse: YAxisMapping: buttons 4 and 5
[    29.689] (**) evdev: MOSART Semi. 2.4G Wireless Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    29.689] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-6/3-6:1.0/input/input7/event5"
[    29.689] (II) XINPUT: Adding extended input device "MOSART Semi. 2.4G Wireless Mouse" (type: MOUSE, id 11)
[    29.689] (II) evdev: MOSART Semi. 2.4G Wireless Mouse: initialized for relative axes.
[    29.689] (WW) evdev: MOSART Semi. 2.4G Wireless Mouse: ignoring absolute axes.
[    29.689] (**) MOSART Semi. 2.4G Wireless Mouse: (accel) keeping acceleration scheme 1
[    29.689] (**) MOSART Semi. 2.4G Wireless Mouse: (accel) acceleration profile 0
[    29.689] (**) MOSART Semi. 2.4G Wireless Mouse: (accel) acceleration factor: 2.000
[    29.689] (**) MOSART Semi. 2.4G Wireless Mouse: (accel) acceleration threshold: 4
[    29.689] (II) config/udev: Adding input device MOSART Semi. 2.4G Wireless Mouse (/dev/input/mouse0)
[    29.689] (II) No input driver specified, ignoring this device.
[    29.689] (II) This device may have been added with another device file.
[    29.689] (II) config/udev: Adding input device BisonCam, NB Pro (/dev/input/event13)
[    29.689] (**) BisonCam, NB Pro: Applying InputClass "evdev keyboard catchall"
[    29.689] (II) Using input driver 'evdev' for 'BisonCam, NB Pro'
[    29.689] (**) BisonCam, NB Pro: always reports core events
[    29.689] (**) evdev: BisonCam, NB Pro: Device: "/dev/input/event13"
[    29.689] (--) evdev: BisonCam, NB Pro: Vendor 0x5986 Product 0x14c
[    29.689] (--) evdev: BisonCam, NB Pro: Found keys
[    29.689] (II) evdev: BisonCam, NB Pro: Configuring as keyboard
[    29.689] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-8/3-8:1.0/input/input14/event13"
[    29.689] (II) XINPUT: Adding extended input device "BisonCam, NB Pro" (type: KEYBOARD, id 12)
[    29.689] (**) Option "xkb_rules" "evdev"
[    29.689] (**) Option "xkb_model" "pc105"
[    29.689] (**) Option "xkb_layout" "cz"
[    29.689] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
[    29.689] (II) No input driver specified, ignoring this device.
[    29.689] (II) This device may have been added with another device file.
[    29.689] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event9)
[    29.689] (II) No input driver specified, ignoring this device.
[    29.689] (II) This device may have been added with another device file.
[    29.690] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    29.690] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    29.690] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    29.690] (**) AT Translated Set 2 keyboard: always reports core events
[    29.690] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    29.690] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    29.690] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    29.690] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    29.690] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    29.690] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[    29.690] (**) Option "xkb_rules" "evdev"
[    29.690] (**) Option "xkb_model" "pc105"
[    29.690] (**) Option "xkb_layout" "cz"
[    29.690] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event6)
[    29.690] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    29.690] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    29.690] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    29.690] (II) LoadModule: "synaptics"
[    29.690] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    29.690] (II) Module synaptics: vendor="X.Org Foundation"
[    29.690]    compiled for 1.15.0, module version = 1.7.4
[    29.690]    Module class: X.Org XInput Driver
[    29.690]    ABI class: X.Org XInput driver, version 20.0
[    29.690] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    29.690] (**) ETPS/2 Elantech Touchpad: always reports core events
[    29.690] (**) Option "Device" "/dev/input/event6"
[    29.704] (II) synaptics: ETPS/2 Elantech Touchpad: ignoring touch events for semi-multitouch device
[    29.704] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 2356 (res 0)
[    29.704] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 1240 (res 0)
[    29.704] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    29.704] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    29.704] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[    29.704] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    29.704] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    29.704] (**) ETPS/2 Elantech Touchpad: always reports core events
[    29.712] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event6"
[    29.712] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 14)
[    29.712] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    29.712] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[    29.712] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.075
[    29.712] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    29.712] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    29.712] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    29.712] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    29.712] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    29.712] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse1)
[    29.712] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    29.713] (II) config/udev: Adding input device MSI WMI hotkeys (/dev/input/event12)
[    29.713] (**) MSI WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    29.713] (II) Using input driver 'evdev' for 'MSI WMI hotkeys'
[    29.713] (**) MSI WMI hotkeys: always reports core events
[    29.713] (**) evdev: MSI WMI hotkeys: Device: "/dev/input/event12"
[    29.713] (--) evdev: MSI WMI hotkeys: Vendor 0 Product 0
[    29.713] (--) evdev: MSI WMI hotkeys: Found keys
[    29.713] (II) evdev: MSI WMI hotkeys: Configuring as keyboard
[    29.713] (**) Option "config_info" "udev:/sys/devices/virtual/input/input13/event12"
[    29.713] (II) XINPUT: Adding extended input device "MSI WMI hotkeys" (type: KEYBOARD, id 15)
[    29.713] (**) Option "xkb_rules" "evdev"
[    29.713] (**) Option "xkb_model" "pc105"
[    29.713] (**) Option "xkb_layout" "cz"
[    31.601] (II) intel(0): EDID vendor "CMO", prod id 5920
[    31.601] (II) intel(0): Printing DDC gathered Modelines:
[    31.601] (II) intel(0): Modeline "1920x1080"x0.0  138.70  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (66.7 kHz eP)
[    47.270] (II) XKB: reuse xkmfile /var/lib/xkb/server-380215CD03F10668E4B11AD1C12FA19DDFF64277.xkm
[    47.323] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    48.167] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    48.169] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    48.171] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    48.172] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    48.174] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    48.175] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    48.177] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    48.178] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    48.180] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    48.181] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
jan@localhost ~ $ cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
Found "/dev/dri/card0", driven by "i915"
output 0:
        eDP connector
Number of connected outputs for /dev/dri/card0: 1
Does it require offloading? yes
grep dmesg status 256
dmesg status 256 == 0? No
grep dmesg status 256
dmesg status 256 == 0? No
Is nvidia loaded? no
Was nvidia unloaded? no
Is fglrx loaded? no
Was fglrx unloaded? no
Is intel loaded? yes
Is radeon loaded? no
Is nouveau loaded? no
Vendor/Device Id: 8086:416
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 10de:1341
BusID "PCI:1@0:0:0"
Is boot vga? no
Error: can't access /sys/bus/pci/devices/0000:01:00.0/driver
The device is not bound to any driver. Skipping...
last cards number = 1
Has amd? no
Has intel? yes
Has nvidia? no
How many cards? 1
Has the system changed? No
main_arch_path x86_64-linux-gnu, other_arch_path i386-linux-gnu
Current alternative: /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf
Is nvidia enabled? no
Is fglrx enabled? no
Is mesa enabled? yes
Is pxpress enabled? no
Is prime enabled? no
Is nvidia available? yes
Is fglrx available? no
Is mesa available? yes
Is pxpress available? no
Is prime available? yes
Single card detected
Nothing to do
No change - nothing to do
jan@localhost ~ $ dpkg -l | grep -i nvidia
ii  bbswitch-dkms                                               0.8-2~trustyppa1                                       all          Interface for toggling the power on NVIDIA Optimus video cards
ii  bumblebee                                                   3.2.1-93~trustyppa1                                    amd64        NVIDIA Optimus support
ii  bumblebee-nvidia                                            3.2.1-93~trustyppa1                                    amd64        NVIDIA Optimus support using the proprietary NVIDIA driver
ii  libcg:amd64                                                 3.1.0013-1                                             amd64        Nvidia Cg core runtime library
ii  libcggl:amd64                                               3.1.0013-1                                             amd64        Nvidia Cg Opengl runtime library
rc  libcuda1-304                                                304.131-0ubuntu0.14.04.1                               amd64        NVIDIA CUDA runtime library
rc  libcuda1-340                                                340.96-0ubuntu0.14.04.1                                amd64        NVIDIA CUDA runtime library
rc  libcuda1-346                                                346.47-0ubuntu1~xedgers14.04.1                         i386         NVIDIA CUDA runtime library
ii  libcuda1-352                                                352.63-0ubuntu0.14.04.1                                amd64        NVIDIA CUDA runtime library
rc  libcuda1-352-updates                                        352.63-0ubuntu0.14.04.1                                amd64        NVIDIA CUDA runtime library
rc  libcuinj32-5.5:i386                                         5.5.22-3ubuntu1                                        i386         NVIDIA CUDA INJ runtime library (32-bit)
ii  libcuinj64-5.5:amd64                                        5.5.22-3ubuntu1                                        amd64        NVIDIA CUDA INJ runtime library (64-bit)
ii  nvidia-352                                                  352.63-0ubuntu0.14.04.1                                amd64        NVIDIA binary driver - version 352.63
ii  nvidia-opencl-icd-352                                       352.63-0ubuntu0.14.04.1                                amd64        NVIDIA OpenCL ICD
ii  nvidia-settings                                             331.20-0ubuntu8                                        amd64        Tool for configuring the NVIDIA graphics driver
jan@localhost ~ $ lsmod | grep nvidia
jan@localhost ~ $ 




```
btw. tried prime-select nvidia, seems to work, doesn't change anything

---

### Post by Bashing-om on 2016-06-01
Jan_Jindrek; Yuk !

What in the world is going on here ? No driver is loading, and several modules fail to load .
Makes me wonder what config file is presently in use booting up with the Intel driver.
I note that you have obtained BumbleBee from a PPA . I recon that should work fine with a repo install of the Nvidia driver.
show:
```

ls -al /etc/X11/
ls -al /etc/X11/xorg.conf
cat /etc/X11/xorg.conf 

```

See if there are problems in the config files.

Good news is that you are booting the latest -87 kernel, and I only see BumbleBee installed, so no conflict with nvidia-prime.

[INDENT][INDENT]cause and effect
[INDENT][INDENT][INDENT]cause and effect
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-06-01
```

jan@localhost ~ $ ls -al /etc/X11/
celkem 128
drwxrwxrwx  11 jan  jan   4096 &#269;en  1 23:53 .
drwxr-xr-x 188 root root 12288 &#269;en  2 00:06 ..
drwxrwxrwx   2 root root  4096 kv&#283; 23  2015 app-defaults
drwxrwxrwx   2 root root  4096 dub  3  2015 cursors
-rw-rw-rw-   1 root root    14 kv&#283; 24 13:54 default-display-manager
drwxrwxrwx   4 root root  4096 &#269;en 24  2014 fonts
lrwxrwxrwx   1 root root    14 pro 22  2013 openbox -> ../xdg/openbox
-rw-rw-rw-   1 root root 17394 pro  3  2009 rgb.txt
lrwxrwxrwx   1 root root    13 úno 14  2015 X -> /usr/bin/Xorg
drwxrwxrwx   3 root root  4096 b&#345;e 23 20:55 xinit
drwxrwxrwx   2 root root  4096 led 15  2014 xkb
-rw-rw-rw-   1 root root   884 lis 11  2013 Xloadimage
-rw-r--r--   1 jan  jan    568 kv&#283; 25 14:13 xorg.conf.backup
-rw-r--r--   1 jan  jan      0 kv&#283; 25 14:53 xorg.conf.nvidia-xconfig-original
-rw-rw-rw-   1 root root 12288 kv&#283; 23 23:47 .xorg.conf.swp
-rw-rw-rw-   1 root root   592 kv&#283; 23 23:48 xorg.conf.05232016
-rw-rw-rw-   1 root root  1332 kv&#283; 24 18:16 xorg.conf.05242016
-rw-r--r--   1 jan  jan   1325 kv&#283; 25 14:53 xorg.conf.05252016
-rw-r--r--   1 root root   568 &#269;en  1 23:40 xorg.conf.06012016
-rwxrwxrwx   1 root root   709 dub  1  2010 Xreset
drwxrwxrwx   2 root root  4096 b&#345;e 23 20:55 Xreset.d
drwxrwxrwx   2 root root  4096 b&#345;e 23 20:55 Xresources
-rwxrwxrwx   1 root root  3730 led 29  2014 Xsession
drwxrwxrwx   2 root root  4096 kv&#283; 30 23:28 Xsession.d
-rw-rw-rw-   1 root root   265 &#269;ec  1  2008 Xsession.options
drwxrwxrwx   2 root root  4096 &#269;en 24  2014 xsm
-rw-rw-rw-   1 root root   601 &#269;en 24  2014 Xwrapper.config
jan@localhost ~ $ ls -al /etc/X11/xorg.conf
ls: nelze p&#345;istoupit k /etc/X11/xorg.conf: Adresá&#345; nebo soubor neexistuje
jan@localhost ~ $ cat /etc/X11/xorg.conf
cat: /etc/X11/xorg.conf: Adresá&#345; nebo soubor neexistuje


```

Should I create the missing directories?

---

### Post by Bashing-om on 2016-06-01
Jan_Jindrek; Uh Huh .
> 
Should I create the missing directories?


I am undecided on a best means to generate the config file.

Can you reboot with the Nvidia card in use ? I am the more comfortable working from Nvidia ,
verify that Nvidia is in use:
```

sudo lshw -C display

```
If we can boot up Nvidia .. we can have the system generate the file for us:
```

sudo nvidia-xconfig

```
reboot to see the effect.

The hope here is that we can get the proper config files in place for the respective video cards and then all else will fall into place.

[INDENT][INDENT]hey it could happen
[/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-06-01
Before reboot:
```

jan@localhost ~ $ sudo lshw -C display
[sudo] password for jan: 
Zkuste to znovu, prosím.
[sudo] password for jan: 
  *-display               
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:50 memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64)
jan@localhost ~ $ sudo nvidia-xconfig


WARNING: Unable to locate/open X configuration file.


New X configuration file written to '/etc/X11/xorg.conf'

```


When I'm done rebooting I will report new results!

EDIT: Done rebooting, results:
```

jan@localhost ~ $ sudo lshw -C display
[sudo] password for jan: 
  *-display               
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:50 memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64)
jan@localhost ~ $ sudo nvidia-xconfig
sudo: nvidia-xconfig: command not found

```

Ok, I'm completely mindfuc!<ed at this point.. sorry?

---

### Post by Bashing-om on 2016-06-01
Jan_Jindrek; Hummm ...

I am blown away also that " sudo nvidia-xconfig " is not found . I assure you it is valid in 'buntu .
AND I do not see the card in the outputs .. Is it by some chance turned OFF in bios ?

However, on a good note:
> 

WARNING: Unable to locate/open X configuration file.


New X configuration file written to '/etc/X11/xorg.conf'

I was totally unaware that " sudo lshw -C display " could or would generate the X file !

Let's examine that file and see what was built !
```

cat /etc/X11/xorg.conf

```

see if that file is usable .


[INDENT]for every action
[INDENT][INDENT]there is an equal and opposite reaction -> leads to a broken system
[/INDENT][/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-06-01
The file doesn't exist at all.. It's like my operating system has become Jaden Smith.

---

### Post by Bashing-om on 2016-06-01
Jan_Jindrek; Hummm ...

Nvidia card died ?
Does Bios pass it on to the system and what now does the system see:
```

lspci -k | grep -EA2 'VGA|3D'

```

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT]other times we do not know
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-06-01
```

jan@localhost ~ $ lspci -k | grep -EA2 'VGA|3D'
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
        Subsystem: Micro-Star International Co., Ltd. [MSI] Device 1112
        Kernel driver in use: i915
--
01:00.0 3D controller: NVIDIA Corporation GM108M [GeForce 840M] (rev ff)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5249 PCI Express Card Reader (rev 01)
        Subsystem: Micro-Star International Co., Ltd. [MSI] Device 1112

```
if it helps, I started using mdm instead of gdm, because gdm is so much worse at debugging any problem.

---

### Post by Bashing-om on 2016-06-01
Jan_Jindrek; Well ..


Yeah, let us use the native display manager mdm, I am not much into mixing DMs .. config files can really get crossed up .. maybe that is the situation here ?
The card is there ,, and the system does see it . 
If we can just get the system to build the driver and use it .

I got an idea, 
what returns:
```

sudo ubuntu-drivers devices
sudo ubuntu-drivers list

```

See if we can find another avenue
[INDENT][INDENT][INDENT]forward
[/INDENT][/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-06-02
```

jan@localhost ~ $ sudo ubuntu-drivers devices
[sudo] password for jan: 
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00001341sv00001462sd00001112bc03sc02i00
vendor   : NVIDIA Corporation
driver   : nvidia-340-updates - distro non-free
driver   : nvidia-352 - distro non-free recommended
driver   : nvidia-352-updates - distro non-free
driver   : nvidia-340 - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin


== /sys/devices/pci0000:00/0000:00:1b.0 ==
modalias : pci:v00008086d00008C20sv00001462sd00001112bc04sc03i00
model    : Lynx Point High Definition Audio Controller
vendor   : Intel Corporation
driver   : oem-audio-hda-daily-lts-wily-dkms - third-party free
driver   : oem-audio-hda-daily-lts-utopic-dkms - third-party free
driver   : oem-audio-hda-daily-dkms - third-party free
driver   : oem-audio-hda-daily-lts-xenial-dkms - third-party free
driver   : oem-audio-hda-daily-lts-vivid-dkms - third-party free


jan@localhost ~ $ sudo ubuntu-drivers list
nvidia-340
nvidia-340-updates
oem-audio-hda-daily-lts-xenial-dkms
nvidia-352
oem-audio-hda-daily-lts-wily-dkms
nvidia-352-updates
oem-audio-hda-daily-dkms
oem-audio-hda-daily-lts-utopic-dkms
oem-audio-hda-daily-lts-vivid-dkms

```
Here is the output! Sorry I responded so late.. had to sleep

---

### Post by Bashing-om on 2016-06-02
Jan_Jindrek; Hey ..

I too must sleep sometimes .. no help for that .. gotta .

That last says what I have in mind , to have the system install the graphic's driver for us - should work .
1st, however, maybe the driver has built, and what we now have is a config issue in your DE profile ??

What results booting with mdm and choosing the guest session ? If you have a functional GUI in the guest session that pretty much points to a config issue in your normal profile.

Else, well .. I have in mind to purge BumbleBee and the Nvidia driver .. and have the system install what it thinks best .

[INDENT][INDENT]ain't no quit'n
[/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-06-02
so I should purge bumblebee and reboot, then install what mintdriver reccommends me?

---

### Post by Bashing-om on 2016-06-02
Jan_Jindrek; Not /

Sorry if I was unclear .
What results booting mdm to the guest session ? If the GUI is functional in the guest session .. not a driver issue is what I am saying.

[INDENT][INDENT]we do need to know
[INDENT][INDENT][INDENT]what is
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-06-02
Strangely enough, mdm does not have guest session according to linuxmint forum. I am however, trying to boot GNOME. Also, logging as root and using startx does not work out.

EDIT: GNOME is just a black screen with a cursor

---

### Post by Bashing-om on 2016-06-02
Jan_Jindrek; Hummmm ...

Can not boot the recovery console is not a good sign .. that is before a graphics driver is loaded when booting that environment.

Can you boot to terminal TTY1 from the grub boot menu ?
e for edit .. and in the linux line substitute 'text' for "quiet splash" . key combo ctl+x to boot to TTY1.

Login here with user name and password .. then we can take a look around .

[INDENT][INDENT]sometimes I wonder
[/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-06-02
Oh sorry, recovery console is working with mdm, but a bug in gdm stops it from working sadly.. and I already disabled quiet splash..
EDIT: startx stops at NV_CONTROL.. I don't know what other info you want, however, I am an open book

---

### Post by Bashing-om on 2016-06-02
Jan_Jindrek; K;

Then, let us take a look at the log file for the driver and X.
```

cat /var/log/Xorg.0.log
cat /var/log/gpu-manager.log

```

If these still looks good , we consider what results with re-configuring mdm .
As another thought /// access rights will also cause this issue .
Do you have the rights to access your desktop ?
```

ls -al /home/<username>

```
where of particular interest are the files .ICEauthority and .Xauthority .

[INDENT][INDENT]try'n to make things right
[/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-06-02
```

jan@localhost ~ $ cat /var/log/Xorg.0.log
[    25.551] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    25.551] X Protocol Version 11, Revision 0
[    25.551] Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
[    25.551] Current Operating System: Linux localhost 3.13.0-87-generic #133-Ubuntu SMP Tue May 24 18:32:09 UTC 2016 x86_64
[    25.551] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-87-generic root=UUID=05f808d5-075a-4ba8-99e8-bfcfdc0b2807 ro plymouth:debug=1
[    25.551] Build Date: 12 February 2015  02:49:29PM
[    25.551] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support) 
[    25.551] Current version of pixman: 0.30.2
[    25.551]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    25.551] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    25.551] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun  2 22:20:26 2016
[    25.629] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    25.659] (==) No Layout section.  Using the first Screen section.
[    25.659] (==) No screen section available. Using defaults.
[    25.659] (**) |-->Screen "Default Screen Section" (0)
[    25.659] (**) |   |-->Monitor "<default monitor>"
[    25.659] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[    25.659] (==) Automatically adding devices
[    25.659] (==) Automatically enabling devices
[    25.659] (==) Automatically adding GPU devices
[    25.659] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    25.659]    Entry deleted from font path.
[    25.659] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    25.659]    Entry deleted from font path.
[    25.659] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    25.659]    Entry deleted from font path.
[    25.659] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    25.659]    Entry deleted from font path.
[    25.659] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    25.659]    Entry deleted from font path.
[    25.659] (==) FontPath set to:                                                         
        /usr/share/fonts/X11/misc,                                                         
        /usr/share/fonts/X11/Type1,                                                        
        built-ins                                                                          
[    25.659] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    25.659] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    25.659] (II) Loader magic: 0x7fd0ef1f3d40
[    25.659] (II) Module ABI versions:
[    25.659]    X.Org ANSI C Emulation: 0.4
[    25.659]    X.Org Video Driver: 15.0
[    25.659]    X.Org XInput driver : 20.0
[    25.659]    X.Org Server Extension : 8.0
[    25.659] (II) xfree86: Adding drm device (/dev/dri/card0)
[    25.661] (--) PCI:*(0:0:2:0) 8086:0416:1462:1112 rev 6, Mem @ 0xf7400000/4194304, 0xd0000000/268435456, I/O @ 0x0000f000/64
[    25.661] (--) PCI: (0:1:0:0) 10de:1341:1462:1112 rev 162, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    25.661] Initializing built-in extension Generic Event Extension
[    25.661] Initializing built-in extension SHAPE
[    25.661] Initializing built-in extension MIT-SHM
[    25.661] Initializing built-in extension XInputExtension
[    25.661] Initializing built-in extension XTEST
[    25.661] Initializing built-in extension BIG-REQUESTS
[    25.661] Initializing built-in extension SYNC
[    25.661] Initializing built-in extension XKEYBOARD
[    25.661] Initializing built-in extension XC-MISC
[    25.661] Initializing built-in extension SECURITY
[    25.661] Initializing built-in extension XINERAMA
[    25.661] Initializing built-in extension XFIXES
[    25.661] Initializing built-in extension RENDER
[    25.661] Initializing built-in extension RANDR
[    25.661] Initializing built-in extension COMPOSITE
[    25.661] Initializing built-in extension DAMAGE
[    25.661] Initializing built-in extension MIT-SCREEN-SAVER
[    25.661] Initializing built-in extension DOUBLE-BUFFER
[    25.661] Initializing built-in extension RECORD
[    25.661] Initializing built-in extension DPMS
[    25.661] Initializing built-in extension Present
[    25.661] Initializing built-in extension DRI3
[    25.661] Initializing built-in extension X-Resource
[    25.661] Initializing built-in extension XVideo
[    25.661] Initializing built-in extension XVideo-MotionCompensation
[    25.661] Initializing built-in extension SELinux
[    25.661] Initializing built-in extension XFree86-VidModeExtension
[    25.661] Initializing built-in extension XFree86-DGA
[    25.661] Initializing built-in extension XFree86-DRI
[    25.661] Initializing built-in extension DRI2
[    25.661] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    25.661] (II) "glx" will be loaded by default.
[    25.661] (WW) "xmir" is not to be loaded by default. Skipping.
[    25.661] (II) LoadModule: "glx"
[    25.731] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    26.682] (II) Module glx: vendor="NVIDIA Corporation"
[    26.682]    compiled for 4.0.2, module version = 1.0.0
[    26.682]    Module class: X.Org Server Extension
[    26.746] (II) NVIDIA GLX Module  352.63  Sat Nov  7 20:52:00 PST 2015
[    26.746] Loading extension GLX
[    26.746] (==) Matched intel as autoconfigured driver 0
[    26.746] (==) Matched intel as autoconfigured driver 1
[    26.746] (==) Matched modesetting as autoconfigured driver 2
[    26.746] (==) Matched fbdev as autoconfigured driver 3
[    26.746] (==) Matched vesa as autoconfigured driver 4
[    26.746] (==) Assigned the driver to the xf86ConfigLayout
[    26.746] (II) LoadModule: "intel"
[    26.794] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    26.949] (II) Module intel: vendor="X.Org Foundation"
[    26.949]    compiled for 1.15.1, module version = 2.99.917
[    26.949]    Module class: X.Org Video Driver
[    26.949]    ABI class: X.Org Video Driver, version 15.0
[    26.949] (II) LoadModule: "modesetting"
[    26.949] (WW) Warning, couldn't open module modesetting
[    26.949] (II) UnloadModule: "modesetting"
[    26.949] (II) Unloading modesetting
[    26.949] (EE) Failed to load module "modesetting" (module does not exist, 0)
[    26.949] (II) LoadModule: "fbdev"
[    26.949] (WW) Warning, couldn't open module fbdev
[    26.949] (II) UnloadModule: "fbdev"
[    26.949] (II) Unloading fbdev
[    26.949] (EE) Failed to load module "fbdev" (module does not exist, 0)
[    26.949] (II) LoadModule: "vesa"
[    26.950] (WW) Warning, couldn't open module vesa
[    26.950] (II) UnloadModule: "vesa"
[    26.950] (II) Unloading vesa
[    26.950] (EE) Failed to load module "vesa" (module does not exist, 0)
[    26.950] (==) Matched intel as autoconfigured driver 0
[    26.950] (==) Matched intel as autoconfigured driver 1
[    26.950] (==) Matched modesetting as autoconfigured driver 2
[    26.950] (==) Matched fbdev as autoconfigured driver 3
[    26.950] (==) Matched vesa as autoconfigured driver 4
[    26.950] (==) Assigned the driver to the xf86ConfigLayout
[    26.950] (II) LoadModule: "intel"
[    26.950] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    26.950] (II) Module intel: vendor="X.Org Foundation"
[    26.950]    compiled for 1.15.1, module version = 2.99.917
[    26.950]    Module class: X.Org Video Driver
[    26.950]    ABI class: X.Org Video Driver, version 15.0
[    26.950] (II) UnloadModule: "intel"
[    26.950] (II) Unloading intel
[    26.950] (II) Failed to load module "intel" (already loaded, 32720)
[    26.950] (II) LoadModule: "modesetting"
[    26.950] (WW) Warning, couldn't open module modesetting
[    26.950] (II) UnloadModule: "modesetting"
[    26.950] (II) Unloading modesetting
[    26.950] (EE) Failed to load module "modesetting" (module does not exist, 0)
[    26.950] (II) LoadModule: "fbdev"
[    26.950] (WW) Warning, couldn't open module fbdev
[    26.950] (II) UnloadModule: "fbdev"
[    26.950] (II) Unloading fbdev
[    26.950] (EE) Failed to load module "fbdev" (module does not exist, 0)
[    26.950] (II) LoadModule: "vesa"
[    26.950] (WW) Warning, couldn't open module vesa
[    26.950] (II) UnloadModule: "vesa"
[    26.950] (II) Unloading vesa
[    26.950] (EE) Failed to load module "vesa" (module does not exist, 0)
[    26.950] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
        i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
        915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
        Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
        GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    26.950] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    26.950] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    26.950] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    26.950] (++) using VT number 8


[    26.954] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20080730
[    26.954] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20151202.da9ad388-0ubuntu0sarvatt~trusty (Robert Hooker <sarvatt@ubuntu.com>)
[    26.954] (II) intel(0): SNA compiled for use with valgrind
[    26.954] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4600
[    26.954] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2; using a maximum of 2 threads
[    26.954] (II) intel(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[    26.954] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    26.954] (==) intel(0): RGB weight 888
[    26.954] (==) intel(0): Default visual is TrueColor
[    26.954] (II) intel(0): Output eDP1 has no monitor section
[    26.954] (--) intel(0): Found backlight control interface acpi_video0 (type 'firmware') for output eDP1
[    26.954] (II) intel(0): Enabled output eDP1
[    26.954] (II) intel(0): Output VGA1 has no monitor section
[    26.954] (II) intel(0): Enabled output VGA1
[    26.954] (II) intel(0): Output HDMI1 has no monitor section
[    26.954] (II) intel(0): Enabled output HDMI1
[    26.954] (--) intel(0): Using a maximum size of 64x64 for hardware cursors
[    26.954] (II) intel(0): Output VIRTUAL1 has no monitor section
[    26.954] (II) intel(0): Enabled output VIRTUAL1
[    26.954] (--) intel(0): Output eDP1 using initial mode 1920x1080 on pipe 0
[    26.954] (==) intel(0): TearFree disabled
[    26.954] (==) intel(0): DPI set to (96, 96)
[    26.954] (II) Loading sub module "dri2"
[    26.954] (II) LoadModule: "dri2"
[    26.954] (II) Module "dri2" already built-in
[    26.954] (II) Loading sub module "present"
[    26.954] (II) LoadModule: "present"
[    26.954] (WW) Warning, couldn't open module present
[    26.955] (II) UnloadModule: "present"
[    26.955] (II) Unloading present
[    26.955] (EE) intel: Failed to load module "present" (module does not exist, 0)
[    26.958] (==) Depth 24 pixmap format is 32 bpp
[    26.958] (II) intel(0): SNA initialized with Haswell (gen7.5, gt2) backend
[    26.958] (==) intel(0): Backing store enabled
[    26.958] (==) intel(0): Silken mouse enabled
[    26.958] (II) intel(0): HW Cursor enabled
[    26.958] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    26.958] (==) intel(0): DPMS enabled
[    26.958] (==) intel(0): Display hotplug detection enabled
[    26.958] (II) intel(0): [DRI2] Setup complete
[    26.958] (II) intel(0): [DRI2]   DRI driver: i965
[    26.958] (II) intel(0): [DRI2]   VDPAU driver: va_gl
[    26.958] (II) intel(0): direct rendering: DRI2 enabled
[    26.958] (--) RandR disabled
[    26.961] (II) SELinux: Disabled on system
[    27.037] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    27.038] (II) intel(0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    27.039] (II) intel(0): Setting screen physical size to 508 x 285
[    27.043] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    27.044] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    27.044] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.044] (II) LoadModule: "evdev"
[    27.044] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.072] (II) Module evdev: vendor="X.Org Foundation"
[    27.072]    compiled for 1.15.0, module version = 2.8.2
[    27.072]    Module class: X.Org XInput Driver
[    27.072]    ABI class: X.Org XInput driver, version 20.0
[    27.072] (II) Using input driver 'evdev' for 'Power Button'
[    27.072] (**) Power Button: always reports core events
[    27.072] (**) evdev: Power Button: Device: "/dev/input/event3"
[    27.072] (--) evdev: Power Button: Vendor 0 Product 0x1
[    27.072] (--) evdev: Power Button: Found keys
[    27.072] (II) evdev: Power Button: Configuring as keyboard
[    27.072] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    27.072] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    27.072] (**) Option "xkb_rules" "evdev"
[    27.072] (**) Option "xkb_model" "pc105"
[    27.072] (**) Option "xkb_layout" "cz"
[    27.074] (II) XKB: reuse xkmfile /var/lib/xkb/server-583B992BBA3776030BA62AC94FC7F0AE9B04119F.xkm
[    27.074] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[    27.074] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    27.074] (II) Using input driver 'evdev' for 'Video Bus'
[    27.074] (**) Video Bus: always reports core events
[    27.074] (**) evdev: Video Bus: Device: "/dev/input/event8"
[    27.074] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    27.074] (--) evdev: Video Bus: Found keys
[    27.074] (II) evdev: Video Bus: Configuring as keyboard
[    27.074] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input9/event8"
[    27.074] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    27.074] (**) Option "xkb_rules" "evdev"
[    27.074] (**) Option "xkb_model" "pc105"
[    27.074] (**) Option "xkb_layout" "cz"
[    27.075] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    27.075] (II) No input driver specified, ignoring this device.
[    27.075] (II) This device may have been added with another device file.
[    27.075] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    27.075] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    27.075] (II) Using input driver 'evdev' for 'Video Bus'
[    27.075] (**) Video Bus: always reports core events
[    27.075] (**) evdev: Video Bus: Device: "/dev/input/event7"
[    27.075] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    27.075] (--) evdev: Video Bus: Found keys
[    27.075] (II) evdev: Video Bus: Configuring as keyboard
[    27.075] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:45/LNXVIDEO:00/input/input8/event7"
[    27.075] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    27.075] (**) Option "xkb_rules" "evdev"
[    27.075] (**) Option "xkb_model" "pc105"
[    27.075] (**) Option "xkb_layout" "cz"
[    27.075] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    27.075] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.075] (II) Using input driver 'evdev' for 'Power Button'
[    27.075] (**) Power Button: always reports core events
[    27.075] (**) evdev: Power Button: Device: "/dev/input/event1"
[    27.075] (--) evdev: Power Button: Vendor 0 Product 0x1
[    27.075] (--) evdev: Power Button: Found keys
[    27.075] (II) evdev: Power Button: Configuring as keyboard
[    27.075] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    27.075] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[    27.075] (**) Option "xkb_rules" "evdev"
[    27.075] (**) Option "xkb_model" "pc105"
[    27.075] (**) Option "xkb_layout" "cz"
[    27.076] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    27.076] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    27.076] (II) Using input driver 'evdev' for 'Sleep Button'
[    27.076] (**) Sleep Button: always reports core events
[    27.076] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    27.076] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    27.076] (--) evdev: Sleep Button: Found keys
[    27.076] (II) evdev: Sleep Button: Configuring as keyboard
[    27.076] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    27.076] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 10)
[    27.076] (**) Option "xkb_rules" "evdev"
[    27.076] (**) Option "xkb_model" "pc105"
[    27.076] (**) Option "xkb_layout" "cz"
[    27.076] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[    27.076] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    27.076] (II) config/udev: Adding input device HDA Intel HDMI HDMI (/dev/input/event11)
[    27.076] (II) No input driver specified, ignoring this device.
[    27.076] (II) This device may have been added with another device file.
[    27.076] (II) config/udev: Adding input device MOSART Semi. 2.4G Wireless Mouse (/dev/input/event5)
[    27.076] (**) MOSART Semi. 2.4G Wireless Mouse: Applying InputClass "evdev pointer catchall"
[    27.076] (II) Using input driver 'evdev' for 'MOSART Semi. 2.4G Wireless Mouse'
[    27.076] (**) MOSART Semi. 2.4G Wireless Mouse: always reports core events
[    27.076] (**) evdev: MOSART Semi. 2.4G Wireless Mouse: Device: "/dev/input/event5"
[    27.076] (--) evdev: MOSART Semi. 2.4G Wireless Mouse: Vendor 0x3938 Product 0x1031
[    27.076] (--) evdev: MOSART Semi. 2.4G Wireless Mouse: Found 9 mouse buttons
[    27.076] (--) evdev: MOSART Semi. 2.4G Wireless Mouse: Found scroll wheel(s)
[    27.076] (--) evdev: MOSART Semi. 2.4G Wireless Mouse: Found relative axes
[    27.076] (--) evdev: MOSART Semi. 2.4G Wireless Mouse: Found x and y relative axes
[    27.076] (--) evdev: MOSART Semi. 2.4G Wireless Mouse: Found absolute axes
[    27.076] (II) evdev: MOSART Semi. 2.4G Wireless Mouse: Forcing absolute x/y axes to exist.
[    27.076] (II) evdev: MOSART Semi. 2.4G Wireless Mouse: Configuring as mouse
[    27.076] (II) evdev: MOSART Semi. 2.4G Wireless Mouse: Adding scrollwheel support
[    27.076] (**) evdev: MOSART Semi. 2.4G Wireless Mouse: YAxisMapping: buttons 4 and 5
[    27.077] (**) evdev: MOSART Semi. 2.4G Wireless Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    27.077] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-6/3-6:1.0/input/input7/event5"
[    27.077] (II) XINPUT: Adding extended input device "MOSART Semi. 2.4G Wireless Mouse" (type: MOUSE, id 11)
[    27.077] (II) evdev: MOSART Semi. 2.4G Wireless Mouse: initialized for relative axes.
[    27.077] (WW) evdev: MOSART Semi. 2.4G Wireless Mouse: ignoring absolute axes.
[    27.077] (**) MOSART Semi. 2.4G Wireless Mouse: (accel) keeping acceleration scheme 1
[    27.077] (**) MOSART Semi. 2.4G Wireless Mouse: (accel) acceleration profile 0
[    27.077] (**) MOSART Semi. 2.4G Wireless Mouse: (accel) acceleration factor: 2.000
[    27.077] (**) MOSART Semi. 2.4G Wireless Mouse: (accel) acceleration threshold: 4
[    27.077] (II) config/udev: Adding input device MOSART Semi. 2.4G Wireless Mouse (/dev/input/mouse0)
[    27.077] (II) No input driver specified, ignoring this device.
[    27.077] (II) This device may have been added with another device file.
[    27.077] (II) config/udev: Adding input device BisonCam, NB Pro (/dev/input/event13)
[    27.077] (**) BisonCam, NB Pro: Applying InputClass "evdev keyboard catchall"
[    27.077] (II) Using input driver 'evdev' for 'BisonCam, NB Pro'
[    27.077] (**) BisonCam, NB Pro: always reports core events
[    27.077] (**) evdev: BisonCam, NB Pro: Device: "/dev/input/event13"
[    27.077] (--) evdev: BisonCam, NB Pro: Vendor 0x5986 Product 0x14c
[    27.077] (--) evdev: BisonCam, NB Pro: Found keys
[    27.077] (II) evdev: BisonCam, NB Pro: Configuring as keyboard
[    27.077] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-8/3-8:1.0/input/input14/event13"
[    27.077] (II) XINPUT: Adding extended input device "BisonCam, NB Pro" (type: KEYBOARD, id 12)
[    27.077] (**) Option "xkb_rules" "evdev"
[    27.077] (**) Option "xkb_model" "pc105"
[    27.077] (**) Option "xkb_layout" "cz"
[    27.078] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
[    27.078] (II) No input driver specified, ignoring this device.
[    27.078] (II) This device may have been added with another device file.
[    27.078] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event9)
[    27.078] (II) No input driver specified, ignoring this device.
[    27.078] (II) This device may have been added with another device file.
[    27.078] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    27.078] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    27.078] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    27.078] (**) AT Translated Set 2 keyboard: always reports core events
[    27.078] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    27.078] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    27.078] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    27.078] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    27.078] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    27.078] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[    27.078] (**) Option "xkb_rules" "evdev"
[    27.078] (**) Option "xkb_model" "pc105"
[    27.078] (**) Option "xkb_layout" "cz"
[    27.078] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event6)
[    27.078] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    27.078] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    27.078] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    27.078] (II) LoadModule: "synaptics"
[    27.078] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    27.079] (II) Module synaptics: vendor="X.Org Foundation"
[    27.079]    compiled for 1.15.0, module version = 1.7.4
[    27.079]    Module class: X.Org XInput Driver
[    27.079]    ABI class: X.Org XInput driver, version 20.0
[    27.079] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    27.079] (**) ETPS/2 Elantech Touchpad: always reports core events
[    27.079] (**) Option "Device" "/dev/input/event6"
[    27.164] (II) synaptics: ETPS/2 Elantech Touchpad: ignoring touch events for semi-multitouch device
[    27.164] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 2356 (res 0)
[    27.164] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 1240 (res 0)
[    27.164] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    27.164] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    27.164] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[    27.164] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    27.164] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    27.164] (**) ETPS/2 Elantech Touchpad: always reports core events
[    27.176] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event6"
[    27.176] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 14)
[    27.176] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    27.176] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[    27.176] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.075
[    27.176] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    27.176] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    27.176] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    27.176] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    27.176] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    27.176] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse1)
[    27.176] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    27.177] (II) config/udev: Adding input device MSI WMI hotkeys (/dev/input/event12)
[    27.177] (**) MSI WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    27.177] (II) Using input driver 'evdev' for 'MSI WMI hotkeys'
[    27.177] (**) MSI WMI hotkeys: always reports core events
[    27.177] (**) evdev: MSI WMI hotkeys: Device: "/dev/input/event12"
[    27.177] (--) evdev: MSI WMI hotkeys: Vendor 0 Product 0
[    27.177] (--) evdev: MSI WMI hotkeys: Found keys
[    27.177] (II) evdev: MSI WMI hotkeys: Configuring as keyboard
[    27.177] (**) Option "config_info" "udev:/sys/devices/virtual/input/input13/event12"
[    27.177] (II) XINPUT: Adding extended input device "MSI WMI hotkeys" (type: KEYBOARD, id 15)
[    27.177] (**) Option "xkb_rules" "evdev"
[    27.177] (**) Option "xkb_model" "pc105"
[    27.177] (**) Option "xkb_layout" "cz"
[    28.954] (II) intel(0): EDID vendor "CMO", prod id 5920
[    28.954] (II) intel(0): Printing DDC gathered Modelines:
[    28.954] (II) intel(0): Modeline "1920x1080"x0.0  138.70  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (66.7 kHz eP)
[    57.604] (II) XKB: reuse xkmfile /var/lib/xkb/server-380215CD03F10668E4B11AD1C12FA19DDFF64277.xkm
[    58.438] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    59.502] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    59.503] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    59.505] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    59.506] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    59.507] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    59.509] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    59.510] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    59.511] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    59.513] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    59.514] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
jan@localhost ~ $ cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
Found "/dev/dri/card0", driven by "i915"
output 0:
        eDP connector
Number of connected outputs for /dev/dri/card0: 1
Does it require offloading? yes
grep dmesg status 256
dmesg status 256 == 0? No
grep dmesg status 256
dmesg status 256 == 0? No
Is nvidia loaded? no
Was nvidia unloaded? no
Is fglrx loaded? no
Was fglrx unloaded? no
Is intel loaded? yes
Is radeon loaded? no
Is nouveau loaded? no
Vendor/Device Id: 8086:416
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 10de:1341
BusID "PCI:1@0:0:0"
Is boot vga? no
Error: can't access /sys/bus/pci/devices/0000:01:00.0/driver
The device is not bound to any driver. Skipping...
last cards number = 1
Has amd? no
Has intel? yes
Has nvidia? no
How many cards? 1
Has the system changed? No
main_arch_path x86_64-linux-gnu, other_arch_path i386-linux-gnu
Current alternative: /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf
Is nvidia enabled? no
Is fglrx enabled? no
Is mesa enabled? yes
Is pxpress enabled? no
Is prime enabled? no
Is nvidia available? yes
Is fglrx available? no
Is mesa available? yes
Is pxpress available? no
Is prime available? yes
Single card detected
Nothing to do
No change - nothing to do
jan@localhost ~ $ ls -al /home/jan
celkem 4658248
drwx------ 117 jan  jan       28672 &#269;en  2 22:20 .
drwxr-xr-x   5 root root       4096 dub 16 19:56 ..
drwx------   3 root root       4096 kv&#283;  2  2015 .adobe
drwxr-x---   3 jan  jan        4096 &#269;en 30  2015 .android
-rw-------   1 root root      12288 b&#345;e  6 02:36 .apache2.conf.swp
-rw-r--r--   1 jan  jan    16038580 pro 17  2013 A Song About An Anglerfish by Hank Green - Video LP-Ek_wCaBZTCg.mp4
drwxr-xr-x  11 jan  jan        4096 kv&#283; 14 01:20 .azureus
drwxr-xr-x   5 jan  jan        4096 b&#345;e 31  2015 Azureus Downloads
-rw-------   1 jan  jan       13652 &#269;en  2 22:19 .bash_history
-rw-r--r--   1 jan  jan         220 úno 14  2015 .bash_logout
drwxr-xr-x   3 jan  jan        4096 b&#345;e 22  2015 Bioshock
drwxr-xr-x   3 jan  jan        4096 dub  6  2015 BioWare
drwxr-xr-x   4 jan  jan        4096 &#269;en  2 16:32 .bluefish
drwxrwxr-x   5 jan  jan        4096 kv&#283; 23 21:22 bumblebee-ui
drwx------  43 jan  jan       16384 &#269;en  2 22:21 .cache
-rw-------   1 jan  jan          34 kv&#283; 10 18:44 .calc_history
-rw-r--r--   1 jan  jan  4310695936 zá&#345;  7  2015 CentOS-7-x86_64-DVD-1503-01.iso
drwxrwxr-x   6 jan  jan        4096 &#269;en  1 23:43 .cinnamon
drwxr-xr-x   2 jan  jan        4096 lis 17  2015 codex-fallout_4_iso
drwxrwxr-x   2 jan  jan        4096 dub 17 14:44 .composer
-rwxr-xr-x   1 jan  jan     1592980 dub 17 14:45 composer.phar
drwxr-xr-x  70 jan  jan       12288 kv&#283; 30 15:00 .config
drwx------   3 jan  jan        4096 úno 14  2015 .dbus
drwxr-xr-x  10 jan  jan        4096 úno 24  2015 .dbvis
drwxr-xr-x   8 jan  jan        4096 úno 24  2015 DbVisualizer
-rw-r--r--   1 jan  jan         144 lis 14  2015 dead.letter
-rw-r--r--   1 jan  jan    35167551 led 26  2015 DFTBA by Hank Green - Video LP-oPUxnpIWt6E.mp4
-rw-------   1 jan  jan          50 &#269;en  2 22:20 .dmrc
-rw-r--r--   1 jan  jan     5093324 kv&#283; 30  2015 Dokument.xcf
drwxr-xr-x  12 jan  jan        4096 kv&#283; 21 21:30 Dokumenty
-rw-r--r--   1 jan  jan     1238562 dub  3  2015 Downloader.exe
drwx------   5 jan  jan        4096 &#269;en  2 22:22 .dropbox
drwx------   3 jan  jan        4096 &#269;en  2 22:22 Dropbox
drwxr-xr-x   3 jan  jan        4096 kv&#283;  7 00:30 .dropbox-dist
drwxr-xr-x   3 jan  jan        4096 dub  4  2015 .dvdcss
drwxr-xr-x   6 jan  jan        4096 lis 11  2015 .eclipse
lrwxrwxrwx   1 jan  jan          29 úno 14  2015 .ecryptfs -> /home/.ecryptfs/jan/.ecryptfs
drwxr-xr-x   3 jan  jan        4096 úno 26  2015 Editor
-rw-r--r--   1 jan  jan    66593510 &#269;ec 16  2015 Ed sheeran - The orange room(FULL ALBUM)   No. 5 Collaborations Project-FS5zuLz9ms0.mp4
-rw-r--r--   1 jan  jan        2621 zá&#345; 13  2015 .face
drwxr-xr-x   2 jan  jan        4096 zá&#345; 19  2015 Fallout3
drwxr-xr-x   2 jan  jan        4096 lis 14  2015 Fallout.4-CODEX
drwxr-xr-x   2 jan  jan        4096 &#269;ec 18  2015 .FBReader
drwx------   2 root root       4096 led  8 18:26 .filezilla
drwxr-xr-x   2 jan  jan        4096 kv&#283; 25 00:44 .furiusisomount
drwx------   4 jan  jan        4096 &#269;en  2 22:21 .gconf
drwxr-xr-x   2 jan  jan        4096 úno 14  2015 .gervill
drwxr-xr-x   3 jan  jan        4096 dub  7  2015 .get_flash_videos
-rw-r--r--   1 jan  jan       80910 pro  1  2010 get-flash-videos_1.24-1_all.deb
-rw-rw-r--   1 jan  jan           0 kv&#283; 23 01:42 ge3.ini
drwxr-xr-x  24 jan  jan        4096 kv&#283; 28 14:00 .gimp-2.8
drwxr-xr-x   2 root root       4096 kv&#283; 23 21:13 git
-rw-r-----   1 jan  jan           0 &#269;en  2 16:17 .gksu.lock
drwxr-xr-x  70 jan  jan       20480 b&#345;e  6 02:08 glibc
drwx------   3 jan  jan        4096 úno 14  2015 .gnome
drwxr-xr-x   5 jan  jan        4096 kv&#283; 13 18:05 .gnome2
drwx------   2 jan  jan        4096 úno 14  2015 .gnome2_private
drwxr-xr-x   4 jan  jan        4096 led  8 16:14 GNUstep
drwx------   5 jan  jan        4096 kv&#283; 13 19:16 .googleearth
drwx------   2 jan  jan        4096 &#269;en 27  2015 .gphoto
drwxr-xr-x   2 jan  jan        4096 kv&#283; 24 00:13 .gstreamer-0.10
drwx------   2 root root       4096 b&#345;e 24 18:41 .gvfs
-rw-r--r--   1 jan  jan    62055530 pro  8  2014 HANK GREEN  -  INCONGRUENT(Full  2014)-cuOas7wwg8U.mp4
-rw-r-----   1 jan  jan     6567183 &#269;ec 26  2015 helicockter.gif
drwxr-xr-x   2 jan  jan        4096 led 28 00:29 Hellgate_London_[PCDVD][MULTi5][DVD9]_By_josvila_iso
drwxr-xr-x   2 jan  jan        4096 zá&#345;  8  2015 Hry
-rw-r--r--   1 jan  jan      131366 lis  6  2015 hs_err_pid21322.log
-rw-r--r--   1 jan  jan      131421 lis 14  2015 hs_err_pid4382.log
-rw-r--r--   1 root root          0 b&#345;e  6 02:36 httpd.conf
drwxr-xr-x   3 jan  jan        4096 pro  1  2015 Hudba
-rw-r--r--   1 jan  jan         418 b&#345;e 10  2015 .chromium-bsu
-rw-------   1 jan  jan       88868 &#269;en  2 22:20 .ICEauthority
drwxr-xr-x  30 jan  jan        4096 b&#345;e 22  2015 .icons
-rw-rw-r--   1 jan  jan          43 úno 24  2015 .install4j
drwxr-xr-x   5 jan  jan        4096 zá&#345;  7  2015 ipxe
-rw-r--r--   1 jan  jan    71376603 b&#345;e 29  2015 I_Shall_BLOW_YOUR_MIND.mp4
drwxrwxrwx   4 jan  jan        4096 úno 24  2015 .java
drwx------   4 jan  jan        4096 kv&#283; 28 01:58 .kde
drwxr-xr-x   3 jan  jan        4096 b&#345;e 28  2015 Larian Studios
drwxr-xr-x   5 jan  jan        4096 kv&#283; 24 12:57 .linuxmint
drwxr-xr-x   4 jan  jan        4096 úno 24  2015 .local
drwxr-xr-x   6 root root       4096 b&#345;e  4  2015 .luckyBackup
drwx------   3 root root       4096 kv&#283;  2  2015 .macromedia
drwxr-xr-x   6 jan  jan        4096 úno 27  2015 make
-rw-r--r--   1 jan  jan    33642004 úno  4 21:26 Mandrage Na dlani.
-rw-r--r--   1 jan  jan    49875388 úno  4 21:25 Mandrage Tan&#269;i dokud m&#367;&#382;e&#353;.
drwxrwxr-x   2 jan  jan        4096 dub 16 20:20 .me-tv
drwxr-xr-x   2 jan  jan        4096 srp 15  2015 Mount&Blade Warband
drwxr-xr-x   3 jan  jan        4096 srp 15  2015 Mount&Blade Warband Savegames
drwx------   4 jan  jan        4096 b&#345;e 26 18:46 .mozilla
drwxr-xr-x   2 jan  jan        4096 dub 12  2015 .mplayer
-rw-r--r--   1 jan  jan         150 srp 17  2015 .mtab.fuseiso
drwxr-xr-x   6 jan  jan        4096 zá&#345;  7  2015 .multibootusb
drwxr-xr-x   2 jan  jan        4096 &#269;en  6  2015 .MultiGet
-rw-r--r--   1 jan  jan         648 pro 17 22:49 mwf_config
drwxr-xr-x   6 jan  jan        4096 úno 27  2015 mwf-designer
drwxr-xr-x   7 jan  jan        4096 led 20 15:56 My Games
drwxr-xr-x   3 jan  root       4096 úno 15  2015 .netbeans
drwx------   3 jan  jan        4096 b&#345;e 21  2015 .nv
-rw-rw-r--   1 jan  jan    68367946 b&#345;e 25 00:20 nvidia.run
-rw-r--r--   1 jan  jan         492 kv&#283; 25 14:53 .nvidia-settings-rc
drwxr-xr-x   4 jan  jan       36864 kv&#283; 28 19:36 Obrázky
-rw-r--r--   1 jan  jan           0 b&#345;e  7  2015 .odbc.ini
lrwxrwxrwx   1 jan  jan          17 úno 27 20:38 Odkaz na Dropbox -> /home/jan/Dropbox
-rw-------   1 jan  jan         551 led  4 18:59 .pagekite.rc
drwxr-xr-x   2 jan  jan        4096 led  8 15:48 .PeaZip
drwxr-xr-x   9 jan  jan       20480 úno 24  2015 phpMyAdmin-4.3.10-english
drwxr-xr-x   2 jan  jan        4096 b&#345;e 22  2015 Pictures
-rw-r--r--   1 jan  jan           0 &#269;en 29  2015 Pitty.pit
drwx------   3 jan  jan        4096 úno 14  2015 .pki
drwxr-xr-x  15 jan  jan        4096 kv&#283; 25 01:21 .PlayOnLinux
drwxr-xr-x   3 jan  jan        4096 dub  6  2015 PlayOnLinux's user directories
lrwxrwxrwx   1 jan  jan          35 úno 19  2015 PlayOnLinux's virtual drives -> /home/jan/.PlayOnLinux//wineprefix/
drwxr-xr-x   9 jan  jan       20480 kv&#283; 31 02:05 Plocha
drwxrwxr-x   8 jan  jan        4096 kv&#283; 15 23:05 .pokemmo
drwxr-xr-x   2 jan  jan        4096 lis  6  2015 Police Academy (1984) [1080p]
-rw-r--r--   1 root root          0 zá&#345; 20  2015 popup.js
lrwxrwxrwx   1 jan  jan          28 úno 14  2015 .Private -> /home/.ecryptfs/jan/.Private
-rw-r--r--   1 jan  jan         675 úno 14  2015 .profile
drwxr-xr-x   6 jan  jan        4096 b&#345;e  5 21:37 Propel
drwxrwxr-x   2 jan  jan        4096 dub 22 20:22 Prototype_iso
drwx------   5 jan  jan        4096 zá&#345; 19  2015 .purple
-rw-r--r--   1 root root     122453 kv&#283; 23 21:28 pygtk
drwxr-xr-x   9 jan  jan        4096 úno 24  2015 .razorsql
-rw-r--r--   1 jan  jan        2018 dub 12  2015 .recently-used
-rw-r-----   1 jan  jan     4093952 &#269;ec  1  2015 recovery.img
drwxr-xr-x   3 jan  jan        4096 kv&#283; 27  2015 Rockstar Games
drwxr-xr-x   2 jan  jan        4096 kv&#283; 10  2015 .rpmdb
drwxr-xr-x   2 jan  jan        4096 úno 24  2015 .rs
drwxr-xr--   2 jan  jan        4096 b&#345;e 31  2015 scalpel-output
drwxrwxr-x   4 jan  jan        4096 dub 17 15:00 sdk-core-php-master
-rw-r--r--   1 jan  jan          66 pro 13 14:40 .selected_editor
drwxr-xr-x   2 jan  jan        4096 kv&#283;  4  2015 School-Work
drwx------   6 jan  jan        4096 srp 20  2015 .Skype
drwxr-xr-x  44 jan  jan       77824 &#269;en  1 19:01 Sta&#382;ené
drwxr-xr-x   5 jan  jan        4096 dub 19  2015 .stellarium
-rw-r--r--   1 jan  jan    35465108 b&#345;e  8  2014 Strange Charm - A Song about Quarks-U0kXkWXSXRA.mp4
drwxr-xr-x   3 jan  jan        4096 úno 15  2015 .swt
drwx------   2 jan  jan        4096 b&#345;e 25  2015 .synaptic
drwxr-xr-x   2 jan  jan        4096 úno 14  2015 &#352;ablony
drwxr-xr-x   2 jan  jan        4096 kv&#283; 25 00:44 TESVSLE_LL_iso
drwxr-xr-x   3 jan  jan        4096 lis  6  2015 The Big Lebowski (1998)
drwxr-xr-x  58 jan  jan       12288 b&#345;e 22  2015 .themes
drwxr-xr-x   3 jan  jan        4096 dub  2  2015 The Witcher
drwxr-xr-x   2 jan  jan        4096 lis 12  2015 The Wolf of Wall Street (2013) [1080p]
drwx------   3 jan  jan        4096 b&#345;e 25  2015 .thumbnails
drwx------   4 jan  jan        4096 dub  5  2015 .thunderbird
drwx------   3 jan  jan        4096 srp 26  2015 tor-browser_en-US
drwxr-xr-x  14 jan  jan        4096 kv&#283; 20 21:07 TrackMania
drwx------   4 root root       4096 úno 15  2015 .Trash-0
drwxrwxr-x   3 jan  jan        4096 dub 22 18:49 usr
drwxr-xr-x   2 jan  jan        4096 b&#345;e 28  2015 Ve&#345;ejné
drwxr-xr-x   4 jan  jan        4096 led 20 21:37 Videa
drwxr-xr-x   4 jan  jan        4096 úno 26  2015 VirtualBox VMs
drwxrwxr-x   2 jan  jan        4096 dub 22 18:39 .wfrog
drwxr-xr-x   4 jan  jan        4096 kv&#283; 21 19:44 .wine
drwxr-xr-x   2 jan  jan        4096 úno  4 23:55 .winff
-rw-r--r--   1 jan  jan      177698 pro  6  2013 winusb_1.0.11+saucy1_amd64.deb
drwxr-xr-x   8 jan  jan        4096 &#345;íj 26  2015 workspace
-rw-------   1 root root         98 &#269;en  1 23:43 .Xauthority
drwxr-xr-x   2 jan  jan        4096 &#345;íj 22  2015 x (Deluxe Edition)
drwx------   4 jan  jan        4096 b&#345;e 13 21:45 .xchat2
-rw-rw-r--   1 jan  jan        1744 kv&#283; 25 14:14 xorg.conf
-rw-r--r--   1 jan  jan        1744 kv&#283; 25 14:14 xorg.conf.backup
-rw-r--r--   1 jan  jan        1744 kv&#283; 25 14:14 xorg.conf.nvidia-xconfig-original
-rw-r--r--   1 jan  jan       46283 &#269;en  3 00:44 .xsession-errors
-rw-r--r--   1 jan  jan       45384 &#269;ec 17  2015 Youtube
drwxr-xr-x   2 jan  jan        4096 b&#345;e 16 18:41 .yumi
drwxr-xr-x   6 jan  jan        4096 b&#345;e 22  2015 .zoncolor
drwxrwxr-x   3 jan  jan        4096 dub 22 18:49 .zygrib
-rw-rw-r--   1 jan  jan       33647 dub 22 18:50 20160422_185035_.grb.bz2
-rw-r--r--   1 jan  jan         611 úno 10  2015 300.html

```

---

### Post by Bashing-om on 2016-06-02
Jan_Jindrek; Yuk, and ouch !

yuk:
"YOU" do not have authority to access your desktop .. that is but one issue ,however .
> 
-rw-------   1 root root         98 &#269;en  1 23:43 .Xauthority

root does but you do not ! We will fix that before returning to the driver installation.

ouch:
And then we have the biggy:
> 
BusID "PCI:1@0:0:0"
Is boot vga? no
Error: can't access /sys/bus/pci/devices/0000:01:00.0/driver
The device is not bound to any driver. Skipping...


I do not know the why here yet .. taking some time to read the log file . I will be back soonest.

[INDENT][INDENT]If I know everything I would not be me
[/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-06-02
Thank you so much for taking your time.. if you need something done in PHP or Javascript, I will do the work pro bono. I'm also not too shabby in C# or Java. Anything for you, you amazing stranger.

---

### Post by Bashing-om on 2016-06-02
Jan_Jindrek; Hey !

I have not a clue why the Nvidia driver did not build.

However, I must question the boot parameter " plymouth:debug=1 " . What is this all about ?
I do not find it as a valid boot option at all .
[https://www.kernel.org/doc/Documentation/kernel-parameters.txt](https://www.kernel.org/doc/Documentation/kernel-parameters.txt)

1) remove plymouth:debug=1 as it might be a big hindrance - unless you KNOW what you are doing here,  I sure do not .
2) we fix your access to your /home:
```

sudo chown jan:jan .Xauthority

```

3) BumbleBee :
Looks to be installed from a PPA [ add-apt-repository ppa:bumblebee/stable ??] Let's look at the sources and make sure we do not import this tool when we re-install the driver;
what is in your sources ?
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

4) in the log file is :
> 
Enabled output eDP1
Enabled output VGA1
Enabled output HDMI1
Enabled output VIRTUAL1
Output eDP1 using initial mode 1920x1080 on pipe 0
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)Enabled output eDP1

More than the 1 monitor attached ?? If so reduce to simplest terms .. to only one display .


When these are done. next is to purge all the BumbleBee and Nvidia files.

See what results when we have the system choose and install the driver for us .

[INDENT][INDENT]what does it take to keep a display like you
[INDENT][INDENT][INDENT]satisfied
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-06-03
I removed the "ro" before it too.. is it okay?

```

jan@localhost ~ $ cat -n /etc/apt/sources.list
jan@localhost ~ $ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/alessandrofac93-bumblebee-config-gtk-dev-trusty.list <==
# deb http://ppa.launchpad.net/alessandrofac93/bumblebee-config-gtk-dev/ubuntu trusty main
# deb-src http://ppa.launchpad.net/alessandrofac93/bumblebee-config-gtk-dev/ubuntu trusty main


==> /etc/apt/sources.list.d/apandada1-typhoon-trusty.list <==
deb http://ppa.launchpad.net/apandada1/typhoon/ubuntu trusty main
deb-src http://ppa.launchpad.net/apandada1/typhoon/ubuntu trusty main


==> /etc/apt/sources.list.d/bumblebee-stable-trusty.list <==
deb http://ppa.launchpad.net/bumblebee/stable/ubuntu trusty main
deb-src http://ppa.launchpad.net/bumblebee/stable/ubuntu trusty main


==> /etc/apt/sources.list.d/colingille-freshlight-trusty.list <==
# deb http://ppa.launchpad.net/colingille/freshlight/ubuntu trusty main
# deb-src http://ppa.launchpad.net/colingille/freshlight/ubuntu trusty main


==> /etc/apt/sources.list.d/costales-folder-color-trusty.list <==
deb http://ppa.launchpad.net/costales/folder-color/ubuntu trusty main
deb-src http://ppa.launchpad.net/costales/folder-color/ubuntu trusty main


==> /etc/apt/sources.list.d/crebs-ppa-trusty.list <==
# deb http://ppa.launchpad.net/crebs/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/crebs/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/ffmulticonverter-stable-trusty.list <==
deb http://ppa.launchpad.net/ffmulticonverter/stable/ubuntu trusty main
deb-src http://ppa.launchpad.net/ffmulticonverter/stable/ubuntu trusty main


==> /etc/apt/sources.list.d/getdeb.list <==
# deb http://archive.getdeb.net/ubuntu trusty-getdeb apps 


==> /etc/apt/sources.list.d/google-earth.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb http://dl.google.com/linux/earth/deb/ stable main


==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main


==> /etc/apt/sources.list.d/mono-xamarin.list <==
deb http://download.mono-project.com/repo/debian wheezy main


==> /etc/apt/sources.list.d/nilarimogard-webupd8-trusty.list <==
deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main
deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main


==> /etc/apt/sources.list.d/official-package-repositories.list <==
deb http://packages.linuxmint.com rebecca main upstream import backport


deb http://extra.linuxmint.com rebecca main


deb http://archive.ubuntu.com/ubuntu trusty main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu trusty-updates main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu/ trusty-security main restricted universe multiverse
deb http://archive.canonical.com/ubuntu/ trusty partner


==> /etc/apt/sources.list.d/playonlinux.list <==
deb http://deb.playonlinux.com/ maverick main


==> /etc/apt/sources.list.d/ravefinity-project-ppa-trusty.list <==
deb http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu trusty main
deb-src http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/rvm-smplayer-trusty.list <==
deb http://ppa.launchpad.net/rvm/smplayer/ubuntu trusty main
deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu trusty main


==> /etc/apt/sources.list.d/strukturag-libde265-trusty.list <==
deb http://ppa.launchpad.net/strukturag/libde265/ubuntu trusty main
deb-src http://ppa.launchpad.net/strukturag/libde265/ubuntu trusty main


==> /etc/apt/sources.list.d/ubuntu-audio-dev-alsa-daily-trusty.list <==
deb http://ppa.launchpad.net/ubuntu-audio-dev/alsa-daily/ubuntu trusty main
deb-src http://ppa.launchpad.net/ubuntu-audio-dev/alsa-daily/ubuntu trusty main


==> /etc/apt/sources.list.d/webupd8team-themes-trusty.list <==
deb http://ppa.launchpad.net/webupd8team/themes/ubuntu trusty main
deb-src http://ppa.launchpad.net/webupd8team/themes/ubuntu trusty main


==> /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list <==
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main
deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main

```
The output you wanted to see. Only one monotor attached. Probably preemptive enabling?

---

### Post by Bashing-om on 2016-06-03
Jan_Jindrek; Wow !

Does not Mint utilize the configuration file "  /etc/apt/sources.list " for it's package management ??? I see that your response is a null output .. blows me away .

I am at a loss for a way to express the shape of the sources, and what it may have done to the system . Upfront, I do not know that there is a recovery .
This one:
> 
deb [http://packages.linuxmint.com](http://packages.linuxmint.com) rebecca main upstream import backport

stops me dead in my tracks - I have no foundation to base anything on. We Have access also to ubuntu trusty repo . A conflict in kernels ?
Working through it:
I find:
[http://ubuntuforums.org/showthread.php?t=2279468](http://ubuntuforums.org/showthread.php?t=2279468)
> 
They're all Ubuntu kernels released for the 14.04 series, so it's pretty unlikely you'll see issues. When I use Mint, I routinely enable all 5 sections of its update scheme and install the latest available kernel. I do that specifically to get a kernel + Nouveau driver combination that works with my Nvidia card, as well as allow a working proprietary drive{r} to be installed. Plus, they're all the same updates Ubuntu users routinely pull down.

the good news here is that the codebase for 'rebecca' is ubuntu 14.04 . Maybe same same kernel is in use ? It is the ubuntu repositories that you have added that causes me concern as to what kernel and it's headers the system should be using .
---------------
# deb [http://ppa.launchpad.net/alessandrofac93/bumblebee-config-gtk-dev/ubuntu](http://ppa.launchpad.net/alessandrofac93/bumblebee-config-gtk-dev/ubuntu) trusty main
This PPA is unsupported since 2013, as such I am uncertain as to the results of attempting to remove the files that have been installed. We can try and see what results:
Activate this PPA and let's see what results with terminal command:
```

sudo add-apt-repository -r ppa:alessandrofac93/bumblebee-config-gtk-dev

```
And once completed .. let us make sure that the source is gone gone .. I do not recall IF " add-apt-repository -r" will remove this source or if the system depends on us to remove it.
verify that it is gone .. if not manually delete it if the add-apt command upon completion does not remove the source .

-----------

deb [http://ppa.launchpad.net/bumblebee/stable/ubuntu](http://ppa.launchpad.net/bumblebee/stable/ubuntu) trusty main
Let us do the same here as for ppa:alessandrofac93/ .
```

sudo add-apt-repository -r ppa:bumblebee/stable 

```
As we are cleaning up here and we want ALL BumbleBee files removed.
BumbleBee is availabale in the ubuntu repo as version /trusty 3.2.1-5  if and when it gets re-installed.
-------------------

deb [http://deb.playonlinux.com/](http://deb.playonlinux.com/) maverick main
This source needs to be removed as "maverick" is End_Of_Life and that resposiroty no longer exists.
-----------------------

deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) trusty main
This PPA is depreciated:
> 
 Proprietary graphics drivers are now in [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

remove it also:
```

sudo ppa-purge ppa:xorg-edgers/ppa

```
And remove this source also when completed.
let's see now if the Nvidia driver is removed.... and the nouveau driver  loaded instead.

However, we are also going to now explicitly remove any vestiges that might still be hanging around.
run terminal commands:
```

sudo apt purge bumblebee*
sudo apt purge nvidia*
sudo rm /etc/X11/xorg.conf

```

OK ??? still breathing ?
Let's reboot and see what results .. I do expect that the nouveau driver is loaded for nvidia .. make sure that the card is turned on in bios.
```

sudo shutdown -r now

```

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-06-03
```

jan@localhost ~ $ sudo add-apt-repository -r ppa:alessandrofac93/bumblebee-config-gtk-dev
[sudo] password for jan: 
Usage: add-apt-repository [options] repository


add-apt-repository: error: no such option: -r
jan@localhost ~ $ sudo add-apt-repository ppa:alessandrofac93/bumblebee-config-gtk-dev
Chystáte se do svého systému p&#345;idat následující PPA repozitá&#345;:
 Bumblebee Configurator Gui Development PPA.
To add this PPA to your system, open a terminal and execute this command:
sudo add-apt-repository ppa:alessandrofac93/bumblebee-config-gtk-dev && sudo apt-get update


For reporting issues, go to the official launchpad page of the project.
https://launchpad.net/bumblebee-config-gtk
 Více informací: https://launchpad.net/~alessandrofac93/+archive/ubuntu/bumblebee-config-gtk-dev
Stiskn&#283;te [ENTER] pro pokra&#269;ování nebo ctrl-c pro zru&#353;ení jeho p&#345;idání


Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --homedir /tmp/tmp.ESNsf12AkR --no-auto-check-trustdb --trust-model always --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys ECF83153
gpg: po&#382;aduji klí&#269; ECF83153 ze hkp server keyserver.ubuntu.com
gpg: klí&#269; ECF83153: "Launchpad PPA for Alessandro Facciorusso" beze zm&#283;n
gpg: Celkový po&#269;et zpracovaných klí&#269;&#367;: 1
gpg:              beze zm&#283;n: 1

```
Result of the second command
```

jan@localhost ~ $ sudo ppa-purge ppa:xorg-edgers/ppa
Updating packages lists
W: Selhalo sta&#382;ení http://ppa.launchpad.net/alessandrofac93/bumblebee-config-gtk-dev/ubuntu/dists/trusty/main/source/Sources  404  Not Found


W: Selhalo sta&#382;ení http://ppa.launchpad.net/alessandrofac93/bumblebee-config-gtk-dev/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found


W: Selhalo sta&#382;ení http://ppa.launchpad.net/alessandrofac93/bumblebee-config-gtk-dev/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found


E: N&#283;které indexové soubory se nepoda&#345;ilo stáhnout. Jsou ignorovány, nebo jsou pou&#382;ity star&#353;í verze.
Warning:  apt-get update failed for some reason

```
Removing the first repository since it isn't found...
```

jan@localhost ~ $ sudo apt-get remove --purge bumblebee* nvidia* && sudo rm /etc/X11/xorg.conf
&#268;tu seznamy balík&#367;&#8230; Hotovo
Vytvá&#345;í se strom závislostí       
&#268;tu stavové informace&#8230; Hotovo
E: Nelze najít balík bumblebee-ui
E: Nelze najít balík nvidia.run
E: Nelze najít balík vyhovující regulárnímu výrazu &#8222;nvidia.run&#8220;

```
This is so bizzare, but I think we found the problem perhaps? I tried to install nvidia drivers through nvidia.run file from nvidia webpage

---

### Post by Bashing-om on 2016-06-03
Jan_Jindrek; Ouch !!

add-apt-repository: error: no such option: -r
We get deeper and deeper in what is and what is not on this system :
That command should work as given unless :
> 
 I'm currently running Ubuntu 14.04 and it still has options -r and --remove on apt-add-repository command. Thus I think you're using a modified or outdated version of apt-add-repository. This utility is provided by the python-software-properties package, maybe you're using a locked version of it. You can check its source code here: bazaar.launchpad.net/~ubuntu-branches/ubuntu/trusty/… Those removing options was introduced on revision 47, on late 2010. So they exist since 10.10 and never get changed, as you can see in the source


This too adds to the possibility we are beating a horse that has no recovery .


We want these sources removed from the system  ..such that the files they have installed are also removed. Then these sources are no longer a part of a bad equation.

Installing a driver direct from Nvidia is not to be considered yet . You have enough problems on this system without the head ache of maintaining a external driver that the system can not maintain for you .

I do advocate we try and get this system stable on the open source driver ( nouveau) and then install the proprietary driver from repo .. ( or if we must the 361 version driver from our trusted PPA ) .

We must get the sources.list consistent and fully functional before we can even think of adding anything else to this system .

When the sources are functional, we get the system updated and in a consistent state with these sources.

[INDENT][INDENT]and again;
[INDENT][INDENT][INDENT]possible, I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jeremy31 on 2016-06-03
Jan_Jindrek

Go into Linux Mint Program menu, Administration, Software Sources, then click PPA on the left, then click the ppa:alessandrofac93/bumblebee-config-gtk-dev and there should be a button on the bottom of the window to remove.  See if this works

Bashing_om, the add-apt-repository: error: no such option: -r occurred on my LM17.3 laptop.  I don't have Nvidia graphics on anything so I will leave this alone

---

### Post by Bashing-om on 2016-06-03
@jeremy31; Thanks

For that ... As said .. I have no Mint knowledge .
Another looking over this is a good thing !

[INDENT][INDENT]3 heads are better than 1
[/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-06-03
It appears that what you wanted was possible through synaptic - removed nvidia packages, removed bumblebee, removed sources you wanted me to remove, now it's just a matter of time till everything is done and I can reboot - I will keep you posted.
EDIT: Synaptic is also installing some more libraries..
EDIT_2: No changes, still in fallback
EDIT_3: If I do prime-select nvidia, mdm fails to start, prime-select intel brings me back to fallback

---

### Post by Bashing-om on 2016-06-04
Jan_Jindrek; K

So, what driver did you attempt to install and from where ?
What do the log files relate as to what the state of X is ?
```

cat /var/log/Xorg.0.log
cat /var/log/gpu-manager.log
cat .xsession-errors

```

Still we do not know how much is a driver issue and/or a user profile config issue.

[INDENT][INDENT]we seek to find
[/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-06-04
First
```

jan@localhost ~ $ cat /var/log/Xorg.0.log
[    26.879] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    26.879] X Protocol Version 11, Revision 0
[    26.879] Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
[    26.879] Current Operating System: Linux localhost 3.13.0-87-generic #133-Ubuntu SMP Tue May 24 18:32:09 UTC 2016 x86_64
[    26.879] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-87-generic root=UUID=05f808d5-075a-4ba8-99e8-bfcfdc0b2807 ro plymouth:debug=1
[    26.879] Build Date: 12 February 2015  02:49:29PM
[    26.879] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support) 
[    26.879] Current version of pixman: 0.30.2
[    26.879]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    26.879] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    26.879] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jun  4 12:24:53 2016
[    26.935] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    26.935] (==) No Layout section.  Using the first Screen section.
[    26.935] (==) No screen section available. Using defaults.
[    26.935] (**) |-->Screen "Default Screen Section" (0)
[    26.935] (**) |   |-->Monitor "<default monitor>"
[    26.935] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[    26.935] (==) Automatically adding devices
[    26.935] (==) Automatically enabling devices
[    26.935] (==) Automatically adding GPU devices
[    26.935] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    26.935]    Entry deleted from font path.
[    26.935] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    26.935]    Entry deleted from font path.
[    26.935] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    26.935]    Entry deleted from font path.
[    26.935] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    26.935]    Entry deleted from font path.
[    26.935] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    26.935]    Entry deleted from font path.
[    26.935] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[    26.935] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    26.935] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    26.935] (II) Loader magic: 0x7fa5819f2d40
[    26.935] (II) Module ABI versions:
[    26.935]    X.Org ANSI C Emulation: 0.4
[    26.935]    X.Org Video Driver: 15.0
[    26.935]    X.Org XInput driver : 20.0
[    26.935]    X.Org Server Extension : 8.0
[    26.935] (II) xfree86: Adding drm device (/dev/dri/card0)
[    26.937] (--) PCI:*(0:0:2:0) 8086:0416:1462:1112 rev 6, Mem @ 0xf7400000/4194304, 0xd0000000/268435456, I/O @ 0x0000f000/64
[    26.937] (--) PCI: (0:1:0:0) 10de:1341:1462:1112 rev 162, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    26.937] Initializing built-in extension Generic Event Extension
[    26.937] Initializing built-in extension SHAPE
[    26.937] Initializing built-in extension MIT-SHM
[    26.937] Initializing built-in extension XInputExtension
[    26.937] Initializing built-in extension XTEST
[    26.937] Initializing built-in extension BIG-REQUESTS
[    26.937] Initializing built-in extension SYNC
[    26.937] Initializing built-in extension XKEYBOARD
[    26.937] Initializing built-in extension XC-MISC
[    26.937] Initializing built-in extension SECURITY
[    26.937] Initializing built-in extension XINERAMA
[    26.937] Initializing built-in extension XFIXES
[    26.937] Initializing built-in extension RENDER
[    26.937] Initializing built-in extension RANDR
[    26.937] Initializing built-in extension COMPOSITE
[    26.937] Initializing built-in extension DAMAGE
[    26.937] Initializing built-in extension MIT-SCREEN-SAVER
[    26.937] Initializing built-in extension DOUBLE-BUFFER
[    26.937] Initializing built-in extension RECORD
[    26.937] Initializing built-in extension DPMS
[    26.937] Initializing built-in extension Present
[    26.937] Initializing built-in extension DRI3
[    26.937] Initializing built-in extension X-Resource
[    26.937] Initializing built-in extension XVideo
[    26.937] Initializing built-in extension XVideo-MotionCompensation
[    26.937] Initializing built-in extension SELinux
[    26.937] Initializing built-in extension XFree86-VidModeExtension
[    26.937] Initializing built-in extension XFree86-DGA
[    26.937] Initializing built-in extension XFree86-DRI
[    26.937] Initializing built-in extension DRI2
[    26.937] (II) LoadModule: "glx"
[    26.937] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    28.066] (II) Module glx: vendor="NVIDIA Corporation"
[    28.066]    compiled for 4.0.2, module version = 1.0.0
[    28.066]    Module class: X.Org Server Extension
[    28.118] (II) NVIDIA GLX Module  352.63  Sat Nov  7 20:52:00 PST 2015
[    28.118] Loading extension GLX
[    28.118] (==) Matched intel as autoconfigured driver 0
[    28.118] (==) Matched intel as autoconfigured driver 1
[    28.118] (==) Matched modesetting as autoconfigured driver 2
[    28.118] (==) Matched fbdev as autoconfigured driver 3
[    28.118] (==) Matched vesa as autoconfigured driver 4
[    28.118] (==) Assigned the driver to the xf86ConfigLayout
[    28.118] (II) LoadModule: "intel"
[    28.133] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    28.177] (II) Module intel: vendor="X.Org Foundation"
[    28.177]    compiled for 1.15.1, module version = 2.99.917
[    28.177]    Module class: X.Org Video Driver
[    28.177]    ABI class: X.Org Video Driver, version 15.0
[    28.177] (II) LoadModule: "modesetting"
[    28.185] (WW) Warning, couldn't open module modesetting
[    28.185] (II) UnloadModule: "modesetting"
[    28.185] (II) Unloading modesetting
[    28.185] (EE) Failed to load module "modesetting" (module does not exist, 0)
[    28.185] (II) LoadModule: "fbdev"
[    28.185] (WW) Warning, couldn't open module fbdev
[    28.186] (II) UnloadModule: "fbdev"
[    28.186] (II) Unloading fbdev
[    28.186] (EE) Failed to load module "fbdev" (module does not exist, 0)
[    28.186] (II) LoadModule: "vesa"
[    28.186] (WW) Warning, couldn't open module vesa
[    28.186] (II) UnloadModule: "vesa"
[    28.186] (II) Unloading vesa
[    28.186] (EE) Failed to load module "vesa" (module does not exist, 0)
[    28.186] (==) Matched intel as autoconfigured driver 0
[    28.186] (==) Matched intel as autoconfigured driver 1
[    28.186] (==) Matched modesetting as autoconfigured driver 2
[    28.186] (==) Matched fbdev as autoconfigured driver 3
[    28.186] (==) Matched vesa as autoconfigured driver 4
[    28.186] (==) Assigned the driver to the xf86ConfigLayout
[    28.186] (II) LoadModule: "intel"
[    28.186] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    28.186] (II) Module intel: vendor="X.Org Foundation"
[    28.186]    compiled for 1.15.1, module version = 2.99.917
[    28.186]    Module class: X.Org Video Driver
[    28.186]    ABI class: X.Org Video Driver, version 15.0
[    28.186] (II) UnloadModule: "intel"
[    28.186] (II) Unloading intel
[    28.186] (II) Failed to load module "intel" (already loaded, 32677)
[    28.186] (II) LoadModule: "modesetting"
[    28.186] (WW) Warning, couldn't open module modesetting
[    28.186] (II) UnloadModule: "modesetting"
[    28.186] (II) Unloading modesetting
[    28.186] (EE) Failed to load module "modesetting" (module does not exist, 0)
[    28.186] (II) LoadModule: "fbdev"
[    28.186] (WW) Warning, couldn't open module fbdev
[    28.186] (II) UnloadModule: "fbdev"
[    28.186] (II) Unloading fbdev
[    28.186] (EE) Failed to load module "fbdev" (module does not exist, 0)
[    28.186] (II) LoadModule: "vesa"
[    28.187] (WW) Warning, couldn't open module vesa
[    28.187] (II) UnloadModule: "vesa"
[    28.187] (II) Unloading vesa
[    28.187] (EE) Failed to load module "vesa" (module does not exist, 0)
[    28.187] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
        i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
        915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
        Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
        GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    28.187] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    28.187] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    28.187] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    28.187] (++) using VT number 8


[    28.191] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20080730
[    28.191] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20151202.da9ad388-0ubuntu0sarvatt~trusty (Robert Hooker <sarvatt@ubuntu.com>)
[    28.191] (II) intel(0): SNA compiled for use with valgrind
[    28.191] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4600
[    28.191] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2; using a maximum of 2 threads
[    28.191] (II) intel(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[    28.191] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    28.191] (==) intel(0): RGB weight 888
[    28.191] (==) intel(0): Default visual is TrueColor
[    28.191] (II) intel(0): Output eDP1 has no monitor section
[    28.191] (--) intel(0): Found backlight control interface acpi_video0 (type 'firmware') for output eDP1
[    28.191] (II) intel(0): Enabled output eDP1
[    28.191] (II) intel(0): Output VGA1 has no monitor section
[    28.191] (II) intel(0): Enabled output VGA1
[    28.191] (II) intel(0): Output HDMI1 has no monitor section
[    28.191] (II) intel(0): Enabled output HDMI1
[    28.191] (--) intel(0): Using a maximum size of 64x64 for hardware cursors
[    28.191] (II) intel(0): Output VIRTUAL1 has no monitor section
[    28.191] (II) intel(0): Enabled output VIRTUAL1
[    28.191] (--) intel(0): Output eDP1 using initial mode 1920x1080 on pipe 0
[    28.191] (==) intel(0): TearFree disabled
[    28.191] (==) intel(0): DPI set to (96, 96)
[    28.191] (II) Loading sub module "dri2"
[    28.191] (II) LoadModule: "dri2"
[    28.191] (II) Module "dri2" already built-in
[    28.191] (II) Loading sub module "present"
[    28.191] (II) LoadModule: "present"
[    28.192] (WW) Warning, couldn't open module present
[    28.192] (II) UnloadModule: "present"
[    28.192] (II) Unloading present
[    28.192] (EE) intel: Failed to load module "present" (module does not exist, 0)
[    28.195] (==) Depth 24 pixmap format is 32 bpp
[    28.195] (II) intel(0): SNA initialized with Haswell (gen7.5, gt2) backend
[    28.195] (==) intel(0): Backing store enabled
[    28.195] (==) intel(0): Silken mouse enabled
[    28.195] (II) intel(0): HW Cursor enabled
[    28.195] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    28.195] (==) intel(0): DPMS enabled
[    28.195] (==) intel(0): Display hotplug detection enabled
[    28.195] (II) intel(0): [DRI2] Setup complete
[    28.195] (II) intel(0): [DRI2]   DRI driver: i965
[    28.195] (II) intel(0): [DRI2]   VDPAU driver: va_gl
[    28.195] (II) intel(0): direct rendering: DRI2 enabled
[    28.195] (--) RandR disabled
[    28.198] (II) SELinux: Disabled on system
[    28.254] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    28.317] (II) intel(0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    28.317] (II) intel(0): Setting screen physical size to 508 x 285
[    28.369] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    28.370] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    28.370] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    28.370] (II) LoadModule: "evdev"
[    28.371] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.411] (II) Module evdev: vendor="X.Org Foundation"
[    28.411]    compiled for 1.15.0, module version = 2.8.2
[    28.411]    Module class: X.Org XInput Driver
[    28.411]    ABI class: X.Org XInput driver, version 20.0
[    28.411] (II) Using input driver 'evdev' for 'Power Button'
[    28.411] (**) Power Button: always reports core events
[    28.411] (**) evdev: Power Button: Device: "/dev/input/event3"
[    28.411] (--) evdev: Power Button: Vendor 0 Product 0x1
[    28.411] (--) evdev: Power Button: Found keys
[    28.411] (II) evdev: Power Button: Configuring as keyboard
[    28.411] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    28.411] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    28.411] (**) Option "xkb_rules" "evdev"
[    28.411] (**) Option "xkb_model" "pc105"
[    28.411] (**) Option "xkb_layout" "cz"
[    28.413] (II) XKB: reuse xkmfile /var/lib/xkb/server-583B992BBA3776030BA62AC94FC7F0AE9B04119F.xkm
[    28.413] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[    28.413] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    28.413] (II) Using input driver 'evdev' for 'Video Bus'
[    28.413] (**) Video Bus: always reports core events
[    28.413] (**) evdev: Video Bus: Device: "/dev/input/event8"
[    28.413] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    28.413] (--) evdev: Video Bus: Found keys
[    28.413] (II) evdev: Video Bus: Configuring as keyboard
[    28.413] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input9/event8"
[    28.413] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    28.413] (**) Option "xkb_rules" "evdev"
[    28.413] (**) Option "xkb_model" "pc105"
[    28.414] (**) Option "xkb_layout" "cz"
[    28.414] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    28.414] (II) No input driver specified, ignoring this device.
[    28.414] (II) This device may have been added with another device file.
[    28.414] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    28.414] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    28.414] (II) Using input driver 'evdev' for 'Video Bus'
[    28.414] (**) Video Bus: always reports core events
[    28.414] (**) evdev: Video Bus: Device: "/dev/input/event7"
[    28.414] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    28.414] (--) evdev: Video Bus: Found keys
[    28.414] (II) evdev: Video Bus: Configuring as keyboard
[    28.414] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:45/LNXVIDEO:00/input/input8/event7"
[    28.414] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    28.414] (**) Option "xkb_rules" "evdev"
[    28.414] (**) Option "xkb_model" "pc105"
[    28.414] (**) Option "xkb_layout" "cz"
[    28.414] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    28.414] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    28.414] (II) Using input driver 'evdev' for 'Power Button'
[    28.414] (**) Power Button: always reports core events
[    28.414] (**) evdev: Power Button: Device: "/dev/input/event1"
[    28.414] (--) evdev: Power Button: Vendor 0 Product 0x1
[    28.414] (--) evdev: Power Button: Found keys
[    28.414] (II) evdev: Power Button: Configuring as keyboard
[    28.414] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    28.414] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[    28.414] (**) Option "xkb_rules" "evdev"
[    28.414] (**) Option "xkb_model" "pc105"
[    28.414] (**) Option "xkb_layout" "cz"
[    28.414] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    28.414] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    28.414] (II) Using input driver 'evdev' for 'Sleep Button'
[    28.414] (**) Sleep Button: always reports core events
[    28.414] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    28.414] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    28.414] (--) evdev: Sleep Button: Found keys
[    28.414] (II) evdev: Sleep Button: Configuring as keyboard
[    28.414] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    28.414] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 10)
[    28.414] (**) Option "xkb_rules" "evdev"
[    28.414] (**) Option "xkb_model" "pc105"
[    28.414] (**) Option "xkb_layout" "cz"
[    28.415] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[    28.415] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    28.415] (II) config/udev: Adding input device HDA Intel HDMI HDMI (/dev/input/event11)
[    28.415] (II) No input driver specified, ignoring this device.
[    28.415] (II) This device may have been added with another device file.
[    28.415] (II) config/udev: Adding input device MOSART Semi. 2.4G Wireless Mouse (/dev/input/event5)
[    28.415] (**) MOSART Semi. 2.4G Wireless Mouse: Applying InputClass "evdev pointer catchall"
[    28.415] (II) Using input driver 'evdev' for 'MOSART Semi. 2.4G Wireless Mouse'
[    28.415] (**) MOSART Semi. 2.4G Wireless Mouse: always reports core events
[    28.415] (**) evdev: MOSART Semi. 2.4G Wireless Mouse: Device: "/dev/input/event5"
[    28.415] (--) evdev: MOSART Semi. 2.4G Wireless Mouse: Vendor 0x3938 Product 0x1031
[    28.415] (--) evdev: MOSART Semi. 2.4G Wireless Mouse: Found 9 mouse buttons
[    28.415] (--) evdev: MOSART Semi. 2.4G Wireless Mouse: Found scroll wheel(s)
[    28.415] (--) evdev: MOSART Semi. 2.4G Wireless Mouse: Found relative axes
[    28.415] (--) evdev: MOSART Semi. 2.4G Wireless Mouse: Found x and y relative axes
[    28.415] (--) evdev: MOSART Semi. 2.4G Wireless Mouse: Found absolute axes
[    28.415] (II) evdev: MOSART Semi. 2.4G Wireless Mouse: Forcing absolute x/y axes to exist.
[    28.415] (II) evdev: MOSART Semi. 2.4G Wireless Mouse: Configuring as mouse
[    28.415] (II) evdev: MOSART Semi. 2.4G Wireless Mouse: Adding scrollwheel support
[    28.415] (**) evdev: MOSART Semi. 2.4G Wireless Mouse: YAxisMapping: buttons 4 and 5
[    28.415] (**) evdev: MOSART Semi. 2.4G Wireless Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    28.415] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-6/3-6:1.0/input/input7/event5"
[    28.415] (II) XINPUT: Adding extended input device "MOSART Semi. 2.4G Wireless Mouse" (type: MOUSE, id 11)
[    28.415] (II) evdev: MOSART Semi. 2.4G Wireless Mouse: initialized for relative axes.
[    28.415] (WW) evdev: MOSART Semi. 2.4G Wireless Mouse: ignoring absolute axes.
[    28.415] (**) MOSART Semi. 2.4G Wireless Mouse: (accel) keeping acceleration scheme 1
[    28.415] (**) MOSART Semi. 2.4G Wireless Mouse: (accel) acceleration profile 0
[    28.415] (**) MOSART Semi. 2.4G Wireless Mouse: (accel) acceleration factor: 2.000
[    28.415] (**) MOSART Semi. 2.4G Wireless Mouse: (accel) acceleration threshold: 4
[    28.415] (II) config/udev: Adding input device MOSART Semi. 2.4G Wireless Mouse (/dev/input/mouse0)
[    28.415] (II) No input driver specified, ignoring this device.
[    28.415] (II) This device may have been added with another device file.
[    28.415] (II) config/udev: Adding input device BisonCam, NB Pro (/dev/input/event13)
[    28.415] (**) BisonCam, NB Pro: Applying InputClass "evdev keyboard catchall"
[    28.415] (II) Using input driver 'evdev' for 'BisonCam, NB Pro'
[    28.415] (**) BisonCam, NB Pro: always reports core events
[    28.415] (**) evdev: BisonCam, NB Pro: Device: "/dev/input/event13"
[    28.415] (--) evdev: BisonCam, NB Pro: Vendor 0x5986 Product 0x14c
[    28.415] (--) evdev: BisonCam, NB Pro: Found keys
[    28.415] (II) evdev: BisonCam, NB Pro: Configuring as keyboard
[    28.415] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-8/3-8:1.0/input/input14/event13"
[    28.415] (II) XINPUT: Adding extended input device "BisonCam, NB Pro" (type: KEYBOARD, id 12)
[    28.415] (**) Option "xkb_rules" "evdev"
[    28.415] (**) Option "xkb_model" "pc105"
[    28.415] (**) Option "xkb_layout" "cz"
[    28.416] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
[    28.416] (II) No input driver specified, ignoring this device.
[    28.416] (II) This device may have been added with another device file.
[    28.416] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event9)
[    28.416] (II) No input driver specified, ignoring this device.
[    28.416] (II) This device may have been added with another device file.
[    28.416] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    28.416] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    28.416] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    28.416] (**) AT Translated Set 2 keyboard: always reports core events
[    28.416] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    28.416] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    28.416] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    28.416] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    28.416] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    28.416] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[    28.416] (**) Option "xkb_rules" "evdev"
[    28.416] (**) Option "xkb_model" "pc105"
[    28.416] (**) Option "xkb_layout" "cz"
[    28.416] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event6)
[    28.416] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    28.416] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    28.416] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    28.416] (II) LoadModule: "synaptics"
[    28.416] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    28.416] (II) Module synaptics: vendor="X.Org Foundation"
[    28.416]    compiled for 1.15.0, module version = 1.7.4
[    28.416]    Module class: X.Org XInput Driver
[    28.416]    ABI class: X.Org XInput driver, version 20.0
[    28.416] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    28.416] (**) ETPS/2 Elantech Touchpad: always reports core events
[    28.416] (**) Option "Device" "/dev/input/event6"
[    28.444] (II) synaptics: ETPS/2 Elantech Touchpad: ignoring touch events for semi-multitouch device
[    28.444] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 2356 (res 0)
[    28.444] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 1240 (res 0)
[    28.444] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    28.444] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    28.444] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[    28.444] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    28.444] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    28.444] (**) ETPS/2 Elantech Touchpad: always reports core events
[    28.452] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event6"
[    28.452] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 14)
[    28.452] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    28.452] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[    28.452] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.075
[    28.452] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    28.452] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    28.452] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    28.452] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    28.452] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    28.452] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse1)
[    28.452] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    28.453] (II) config/udev: Adding input device MSI WMI hotkeys (/dev/input/event12)
[    28.453] (**) MSI WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    28.453] (II) Using input driver 'evdev' for 'MSI WMI hotkeys'
[    28.453] (**) MSI WMI hotkeys: always reports core events
[    28.453] (**) evdev: MSI WMI hotkeys: Device: "/dev/input/event12"
[    28.453] (--) evdev: MSI WMI hotkeys: Vendor 0 Product 0
[    28.453] (--) evdev: MSI WMI hotkeys: Found keys
[    28.453] (II) evdev: MSI WMI hotkeys: Configuring as keyboard
[    28.453] (**) Option "config_info" "udev:/sys/devices/virtual/input/input13/event12"
[    28.453] (II) XINPUT: Adding extended input device "MSI WMI hotkeys" (type: KEYBOARD, id 15)
[    28.453] (**) Option "xkb_rules" "evdev"
[    28.453] (**) Option "xkb_model" "pc105"
[    28.453] (**) Option "xkb_layout" "cz"
[    30.192] (II) intel(0): EDID vendor "CMO", prod id 5920
[    30.192] (II) intel(0): Printing DDC gathered Modelines:
[    30.192] (II) intel(0): Modeline "1920x1080"x0.0  138.70  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (66.7 kHz eP)
[    80.624] (II) XKB: reuse xkmfile /var/lib/xkb/server-380215CD03F10668E4B11AD1C12FA19DDFF64277.xkm
[    82.448] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    83.302] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    83.304] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    83.305] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    83.307] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    83.308] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    83.309] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    83.311] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    83.312] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    83.314] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm
[    83.315] (II) XKB: reuse xkmfile /var/lib/xkb/server-C62F447E1AD0D6FCB0B4ED695A145D696DD333C5.xkm

```
Second
```

jan@localhost ~ $ cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
Found "/dev/dri/card0", driven by "i915"
output 0:
        eDP connector
Number of connected outputs for /dev/dri/card0: 1
Does it require offloading? yes
grep dmesg status 256
dmesg status 256 == 0? No
grep dmesg status 256
dmesg status 256 == 0? No
Is nvidia loaded? no
Was nvidia unloaded? no
Is fglrx loaded? no
Was fglrx unloaded? no
Is intel loaded? yes
Is radeon loaded? no
Is nouveau loaded? yes
Vendor/Device Id: 8086:416
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 10de:1341
BusID "PCI:1@0:0:0"
Is boot vga? no
Error: can't access /sys/bus/pci/devices/0000:01:00.0/driver
The device is not bound to any driver. Skipping...
last cards number = 1
Has amd? no
Has intel? yes
Has nvidia? no
How many cards? 1
Has the system changed? No
main_arch_path x86_64-linux-gnu, other_arch_path i386-linux-gnu
Current alternative: /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf
Is nvidia enabled? no
Is fglrx enabled? no
Is mesa enabled? yes
Is pxpress enabled? no
Is prime enabled? no
Is nvidia available? no
Is fglrx available? no
Is mesa available? yes
Is pxpress available? no
Is prime available? no
Single card detected
Nothing to do
No change - nothing to do

```
Third
```

/etc/mdm/Xsession: Beginning session setup...
localuser:jan being added to access control list
Failed to connect to the VirtualBox kernel service
Failed to connect to the VirtualBox kernel service
Failed to connect to the VirtualBox kernel service
Failed to connect to the VirtualBox kernel service
Failed to connect to the VirtualBox kernel service
GNOME_KEYRING_CONTROL=/run/user/1000/keyring-RGYpMe
GNOME_KEYRING_CONTROL=/run/user/1000/keyring-RGYpMe
SSH_AUTH_SOCK=/run/user/1000/keyring-RGYpMe/ssh
GNOME_KEYRING_CONTROL=/run/user/1000/keyring-RGYpMe
SSH_AUTH_SOCK=/run/user/1000/keyring-RGYpMe/ssh
GNOME_KEYRING_CONTROL=/run/user/1000/keyring-RGYpMe
SSH_AUTH_SOCK=/run/user/1000/keyring-RGYpMe/ssh
GPG_AGENT_INFO=/run/user/1000/keyring-RGYpMe/gpg:0:1
cinnamon-session[2482]: WARNING: Application 'cinnamon-settings-daemon.desktop' failed to register before timeout
cinnamon-session[2482]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Xlib:  extension "GLX" missing on display ":0".


(cinnamon:2893): Clutter-CRITICAL **: Unable to initialize Clutter: Failed to connected to any renderer due to constraints
Window manager error: Unable to initialize Clutter.
Starting Dropbox...nm-applet-Message: using fallback from indicator to GtkStatusIcon
apache2: Could not open configuration file /usr/share/gnome-user-share/dav_user_2.4.conf: No such file or directory
spawning httpd failed
Creating Bluetooth ObexPush server failed: Could not create server socket
Creating Bluetooth ObexFTP server failed: Could not create server socket
Creating Bluetooth ObexPush server failed: Could not create server socket
Creating Bluetooth ObexFTP server failed: Could not create server socket
mintUpdate: žádný proces nenalezen


(mintUpdate.py:2972): libglade-WARNING **: unknown attribute `swapped' for <signal>.


(mintUpdate.py:2972): libglade-WARNING **: unknown attribute `swapped' for <signal>.


(mintUpdate.py:2972): libglade-WARNING **: unknown attribute `swapped' for <signal>.


(mintUpdate.py:2972): libglade-WARNING **: unknown attribute `swapped' for <signal>.
Could not register the application: &#268;asový limit vypršel
Dropbox isn't running!
Done!
Intializing nemo-pastebin extension...
2016-06-04 12:26:38,376 [DEBUG] nemo-pastebin(53): Intializing nemo-pastebin extension...
[Nemo Terminal] I: Initializing the Nemo extension
Initializing folder-color-switcher extension...
Initializing nemo-image-converter extension
Initializing nemo-dropbox 2.4.0


** (nemo:2926): CRITICAL **: nemo_menu_provider_get_background_items: assertion 'NEMO_IS_MENU_PROVIDER (provider)' failed
2926
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Got bus address:  "unix:abstract=/tmp/dbus-bcrTNMRUj0,guid=02882cf7b7f7c2168828db715752ac86" 
Connected to accessibility bus at:  "unix:abstract=/tmp/dbus-bcrTNMRUj0,guid=02882cf7b7f7c2168828db715752ac86" 
Registered DEC:  true 
Registered event listener change listener:  true 
Varování správce oken: Log level 8: Source ID 61 was not found when attempting to remove it
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
[3250:3250:0604/122828:ERROR:gl_surface_glx.cc(381)] glxQueryVersion failed
[3250:3250:0604/122828:ERROR:gl_surface_x11.cc(62)] GLSurfaceGLX::InitializeOneOff failed.
[3250:3250:0604/122828:ERROR:gpu_child_thread.cc(397)] Exiting GPU process due to errors during initialization
Varování správce oken: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x3a00001 (Nová kart)
Varování správce oken: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
[3209:3242:0604/122835:ERROR:browser_gpu_channel_host_factory.cc(119)] Failed to launch GPU process.
[3209:3242:0604/122836:ERROR:browser_gpu_channel_host_factory.cc(119)] Failed to launch GPU process.
[3209:3242:0604/123016:ERROR:browser_gpu_channel_host_factory.cc(119)] Failed to launch GPU process.
[3209:3242:0604/123016:ERROR:browser_gpu_channel_host_factory.cc(119)] Failed to launch GPU process.
[WARNING:flash/platform/pepper/pep_module.cpp(63)] SANDBOXED
Vector smash protection is enabled.
[1:1:0604/123325:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[3209:3242:0604/123325:ERROR:browser_gpu_channel_host_factory.cc(119)] Failed to launch GPU process.
[3209:3242:0604/123325:ERROR:browser_gpu_channel_host_factory.cc(119)] Failed to launch GPU process.
[1:1:0604/123924:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/124826:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/124826:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/130703:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[3209:3242:0604/131853:ERROR:browser_gpu_channel_host_factory.cc(119)] Failed to launch GPU process.
[3209:3242:0604/131853:ERROR:browser_gpu_channel_host_factory.cc(119)] Failed to launch GPU process.
[3209:3242:0604/131853:ERROR:browser_gpu_channel_host_factory.cc(119)] Failed to launch GPU process.
[3209:3242:0604/131853:ERROR:browser_gpu_channel_host_factory.cc(119)] Failed to launch GPU process.
[3209:3242:0604/132136:ERROR:browser_gpu_channel_host_factory.cc(119)] Failed to launch GPU process.
[3209:3242:0604/132136:ERROR:browser_gpu_channel_host_factory.cc(119)] Failed to launch GPU process.
[3209:3242:0604/132136:ERROR:browser_gpu_channel_host_factory.cc(119)] Failed to launch GPU process.
[3209:3242:0604/132136:ERROR:browser_gpu_channel_host_factory.cc(119)] Failed to launch GPU process.
[1:1:0604/132258:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132258:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132259:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132259:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132300:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132306:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132306:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132329:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132329:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132339:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132340:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132410:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132411:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132629:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132629:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132630:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132630:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132631:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132631:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132717:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132719:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132719:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132720:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132721:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132723:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132723:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132741:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132741:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132743:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132743:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132744:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132744:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132752:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132758:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132758:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132847:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132848:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132853:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132858:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132859:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132907:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132919:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132919:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132922:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132923:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132930:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132931:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132943:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132944:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()
[1:1:0604/132945:ERROR:PlatformKeyboardEvent.cpp(117)] Not implemented reached in static PlatformEvent::Modifiers blink::PlatformKeyboardEvent::getCurrentModifierState()


** (nemo:2926): CRITICAL **: nemo_menu_provider_get_background_items: assertion 'NEMO_IS_MENU_PROVIDER (provider)' failed


** (nemo:2926): CRITICAL **: nemo_menu_provider_get_background_items: assertion 'NEMO_IS_MENU_PROVIDER (provider)' failed


** (nemo:2926): CRITICAL **: nemo_menu_provider_get_background_items: assertion 'NEMO_IS_MENU_PROVIDER (provider)' failed


** (nemo:2926): CRITICAL **: nemo_menu_provider_get_background_items: assertion 'NEMO_IS_MENU_PROVIDER (provider)' failed


** (nemo:2926): CRITICAL **: nemo_menu_provider_get_background_items: assertion 'NEMO_IS_MENU_PROVIDER (provider)' failed


** (nemo:2926): CRITICAL **: nemo_menu_provider_get_background_items: assertion 'NEMO_IS_MENU_PROVIDER (provider)' failed


** (nemo:2926): CRITICAL **: nemo_menu_provider_get_background_items: assertion 'NEMO_IS_MENU_PROVIDER (provider)' failed


** (nemo:2926): CRITICAL **: nemo_menu_provider_get_background_items: assertion 'NEMO_IS_MENU_PROVIDER (provider)' failed


** (nemo:2926): CRITICAL **: nemo_menu_provider_get_background_items: assertion 'NEMO_IS_MENU_PROVIDER (provider)' failed


** (nemo:2926): CRITICAL **: nemo_menu_provider_get_background_items: assertion 'NEMO_IS_MENU_PROVIDER (provider)' failed
Varování správce oken: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1a00007 (Ov&#283;&#345;ení)
Varování správce oken: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.


(polkit-gnome-authentication-agent-1:2913): GLib-WARNING **: GChildWatchSource: Exit status of a child process was requested but ECHILD was received by waitpid(). Most likely the process is ignoring SIGCHLD, or some other thread is invoking waitpid() with a nonpositive first argument; either behavior can break applications that use g_child_watch_add()/g_spawn_sync() either directly or indirectly.
Intializing nemo-pastebin extension...
2016-06-04 13:44:18,062 [DEBUG] nemo-pastebin(53): Intializing nemo-pastebin extension...
[Nemo Terminal] I: Initializing the Nemo extension
Initializing folder-color-switcher extension...
Initializing nemo-image-converter extension
Initializing nemo-dropbox 2.4.0


** (nemo:4240): CRITICAL **: nemo_menu_provider_get_background_items: assertion 'NEMO_IS_MENU_PROVIDER (provider)' failed


** (nemo:4240): CRITICAL **: nemo_menu_provider_get_background_items: assertion 'NEMO_IS_MENU_PROVIDER (provider)' failed


** (nemo:4240): CRITICAL **: nemo_menu_provider_get_background_items: assertion 'NEMO_IS_MENU_PROVIDER (provider)' failed


** (nemo:4240): CRITICAL **: nemo_menu_provider_get_background_items: assertion 'NEMO_IS_MENU_PROVIDER (provider)' failed
Varování správce oken: Log level 8: Source ID 194 was not found when attempting to remove it
Varování správce oken: Log level 8: Source ID 320 was not found when attempting to remove it


(nemo:2926): Gtk-CRITICAL **: gtk_container_foreach: assertion 'GTK_IS_CONTAINER (container)' failed


(nemo:2926): Gtk-CRITICAL **: gtk_container_foreach: assertion 'GTK_IS_CONTAINER (container)' failed


(nemo:2926): Gtk-CRITICAL **: gtk_container_foreach: assertion 'GTK_IS_CONTAINER (container)' failed


(nemo:2926): Gtk-CRITICAL **: gtk_container_foreach: assertion 'GTK_IS_CONTAINER (container)' failed


(nemo:2926): Gtk-CRITICAL **: gtk_container_foreach: assertion 'GTK_IS_CONTAINER (container)' failed


(nemo:2926): Gtk-CRITICAL **: gtk_container_foreach: assertion 'GTK_IS_CONTAINER (container)' failed


(nemo:2926): Gtk-CRITICAL **: gtk_container_foreach: assertion 'GTK_IS_CONTAINER (container)' failed


(nemo:2926): Gtk-CRITICAL **: gtk_container_foreach: assertion 'GTK_IS_CONTAINER (container)' failed


(nemo:2926): Gtk-CRITICAL **: gtk_container_foreach: assertion 'GTK_IS_CONTAINER (container)' failed


(nemo:2926): Gtk-CRITICAL **: gtk_container_foreach: assertion 'GTK_IS_CONTAINER (container)' failed
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
Language statistics for Javascript from /usr/share/bluefish/bflang//javascript.bflang2
reference size            0,00 Kbytes
largest table  4372 (  1093,00 Kbytes)
total tables   4414 (  1103,50 Kbytes)
contexts         10 (     0,47 Kbytes)
matches         784 (    36,75 Kbytes)
blocks            3 (     0,09 Kbytes)
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
Possible error in language file, id - / pattern } has ends_context=2, but has only 1 parent contexts
Language statistics for CSS from /usr/share/bluefish/bflang//css.bflang2
reference size            0,00 Kbytes
largest table  1032 (   258,00 Kbytes)
total tables   7690 (  1922,50 Kbytes)
contexts        119 (     5,58 Kbytes)
matches        1147 (    53,77 Kbytes)
blocks            1 (     0,03 Kbytes)
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
Possible error in language file, id - / pattern </script> has ends_context=3, but has only 3 parent contexts
Possible error in language file, id - / pattern </script> has ends_context=3, but has only 3 parent contexts
Possible error in language file: id </script> already exists
Possible error in language file, id - / pattern } has ends_context=2, but has only 2 parent contexts
Possible error in language file, id - / pattern </style> has ends_context=3, but has only 3 parent contexts
Possible error in language file: id </style> already exists
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
Language statistics for PHP from /usr/share/bluefish/bflang//php.bflang2
reference size            0,00 Kbytes
largest table 32354 (  8088,50 Kbytes)
total tables  89857 ( 22464,25 Kbytes)
contexts        248 (    11,62 Kbytes)
matches       14768 (   692,25 Kbytes)
blocks           14 (     0,44 Kbytes)
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb
scanning run 1 (5 ms): 0, 0, 0, 5; from 0-2775, loops=3461,chars=2775,blocks 178/178 (0) contexts 65/65 (0) scancache 368
memory scancache 368(8Kb+14Kb) found 178(5Kb) fcontext 65(1Kb) = 30Kb
average 555000 chars/s 2775 chars/run
scancache integrity check done in 0,042000 ms.
cleanup_scanner, memory scancache 368(8Kb+14Kb) found 178(5Kb) fcontext 65(1Kb) = 30Kb
cleanup_scanner, memory scancache 368(8Kb+14Kb) found 178(5Kb) fcontext 65(1Kb) = 30Kb
scanning run 2 (3 ms): 0, 0, 0, 3; from 0-4140, loops=4832,chars=4140,blocks 118/118 (0) contexts 118/118 (0) scancache 236
memory scancache 604(14Kb+23Kb) found 296(9Kb) fcontext 183(4Kb) = 51Kb
average 864375 chars/s 3457 chars/run
scancache integrity check done in 0,058000 ms.
scanning run 3 (100 ms): 0, 0, 1, 100; from 0-77000, loops=93000,chars=77000,blocks 3329/3326 (0) contexts 1213/1211 (0) scancache 6777
memory scancache 7381(172Kb+288Kb) found 3625(113Kb) fcontext 1396(32Kb) = 607Kb
average 776990 chars/s 27971 chars/run
scanning run 4 (23 ms): 0, 0, 0, 23; from 76995-91560, loops=17702,chars=14565,blocks 713/716 (0) contexts 235/237 (0) scancache 8246
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 751755 chars/s 24620 chars/run
scancache integrity check done in 1,025001 ms.
scanning run 5 (0 ms): 0, 0, 0, 0; from 62589-62702, loops=132,chars=113,blocks 0/0 (0) contexts 0/0 (0) scancache 8246
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 752618 chars/s 19718 chars/run
Nothing to scan anymore, total run timer took 62742 ms
scanning run 6 (0 ms): 0, 0, 0, 0; from 62589-62703, loops=133,chars=114,blocks 0/0 (0) contexts 0/0 (0) scancache 8246
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 753488 chars/s 16451 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 7 (0 ms): 0, 0, 0, 0; from 62487-62704, loops=265,chars=217,blocks 0/0 (0) contexts 0/0 (0) scancache 8246
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 755145 chars/s 14132 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 8 (0 ms): 0, 0, 0, 0; from 62487-62705, loops=266,chars=218,blocks 0/0 (0) contexts 0/0 (0) scancache 8246
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 756809 chars/s 12392 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 9 (0 ms): 0, 0, 0, 0; from 62951-62989, loops=50,chars=38,blocks 0/0 (0) contexts 0/0 (0) scancache 8246
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 757099 chars/s 11020 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 10 (0 ms): 0, 0, 0, 0; from 4135-4138, loops=4,chars=3,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 757122 chars/s 9918 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 11 (0 ms): 0, 0, 0, 0; from 4137-4140, loops=5,chars=3,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 757145 chars/s 9016 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 12 (0 ms): 0, 0, 0, 0; from 4137-4141, loops=6,chars=4,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 757175 chars/s 8265 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 13 (0 ms): 0, 0, 0, 0; from 4137-4142, loops=7,chars=5,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 757213 chars/s 7630 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 14 (0 ms): 0, 0, 0, 0; from 4137-4143, loops=8,chars=6,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 757259 chars/s 7085 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 15 (0 ms): 0, 0, 0, 0; from 4137-4144, loops=9,chars=7,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 757312 chars/s 6613 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 16 (0 ms): 0, 0, 0, 0; from 4135-4145, loops=12,chars=10,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 757389 chars/s 6201 chars/run
scancache integrity check done in 0,085000 ms.
scanning run 17 (0 ms): 0, 0, 0, 0; from 4135-4144, loops=11,chars=9,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 757458 chars/s 5836 chars/run
scancache integrity check done in 0,085000 ms.
scanning run 18 (0 ms): 0, 0, 0, 0; from 4135-4143, loops=10,chars=8,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 757519 chars/s 5513 chars/run
scancache integrity check done in 0,083000 ms.
scanning run 19 (0 ms): 0, 0, 0, 0; from 4135-4142, loops=9,chars=7,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 757572 chars/s 5223 chars/run
scancache integrity check done in 0,089000 ms.
scanning run 20 (0 ms): 0, 0, 0, 0; from 4135-4141, loops=8,chars=6,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 757618 chars/s 4962 chars/run
scancache integrity check done in 0,090000 ms.
scanning run 21 (0 ms): 0, 0, 0, 0; from 4137-4140, loops=5,chars=3,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 757641 chars/s 4726 chars/run
Nothing to scan anymore, total run timer took 1625 ms
scanning run 22 (0 ms): 0, 0, 0, 0; from 4137-4141, loops=6,chars=4,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 757671 chars/s 4511 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 23 (0 ms): 0, 0, 0, 0; from 4137-4142, loops=7,chars=5,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 757709 chars/s 4315 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 24 (0 ms): 0, 0, 0, 0; from 4137-4143, loops=8,chars=6,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 757755 chars/s 4136 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 25 (0 ms): 0, 0, 0, 0; from 4135-4144, loops=11,chars=9,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 757824 chars/s 3971 chars/run
scancache integrity check done in 0,091000 ms.
scanning run 26 (0 ms): 0, 0, 0, 0; from 4135-4143, loops=10,chars=8,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 757885 chars/s 3818 chars/run
scancache integrity check done in 0,088000 ms.
scanning run 27 (0 ms): 0, 0, 0, 0; from 4137-4142, loops=7,chars=5,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 757923 chars/s 3677 chars/run
Nothing to scan anymore, total run timer took 844 ms
scanning run 28 (0 ms): 0, 0, 0, 0; from 4137-4143, loops=8,chars=6,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 757969 chars/s 3546 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 29 (0 ms): 0, 0, 0, 0; from 4137-4144, loops=9,chars=7,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 758022 chars/s 3424 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 30 (0 ms): 0, 0, 0, 0; from 4137-4145, loops=10,chars=8,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 758083 chars/s 3310 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 31 (0 ms): 0, 0, 0, 0; from 4137-4146, loops=11,chars=9,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 758152 chars/s 3203 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 32 (0 ms): 0, 0, 0, 0; from 4137-4147, loops=12,chars=10,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 758229 chars/s 3104 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 33 (0 ms): 0, 0, 0, 0; from 4135-4148, loops=15,chars=13,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 758328 chars/s 3010 chars/run
scancache integrity check done in 0,100000 ms.
scanning run 34 (0 ms): 0, 0, 0, 0; from 4135-4147, loops=14,chars=12,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 758419 chars/s 2922 chars/run
scancache integrity check done in 0,100000 ms.
scanning run 35 (0 ms): 0, 0, 0, 0; from 4135-4146, loops=13,chars=11,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 758503 chars/s 2838 chars/run
scancache integrity check done in 0,088000 ms.
scanning run 36 (0 ms): 0, 0, 0, 0; from 4135-4145, loops=12,chars=10,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 758580 chars/s 2760 chars/run
scancache integrity check done in 0,092000 ms.
scanning run 37 (0 ms): 0, 0, 0, 0; from 4135-4144, loops=11,chars=9,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 758648 chars/s 2686 chars/run
scancache integrity check done in 0,090000 ms.
scanning run 38 (0 ms): 0, 0, 0, 0; from 4137-4143, loops=8,chars=6,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 758694 chars/s 2615 chars/run
Nothing to scan anymore, total run timer took 838 ms
scanning run 39 (0 ms): 0, 0, 0, 0; from 4137-4144, loops=9,chars=7,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 758748 chars/s 2548 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 40 (0 ms): 0, 0, 0, 0; from 4137-4145, loops=10,chars=8,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 758809 chars/s 2485 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 41 (0 ms): 0, 0, 0, 0; from 4137-4146, loops=11,chars=9,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 758877 chars/s 2424 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 42 (0 ms): 0, 0, 0, 0; from 4137-4147, loops=12,chars=10,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 758954 chars/s 2367 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 43 (0 ms): 0, 0, 0, 0; from 4137-4148, loops=13,chars=11,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 759038 chars/s 2312 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 44 (0 ms): 0, 0, 0, 0; from 4137-4149, loops=14,chars=12,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 759129 chars/s 2260 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 45 (0 ms): 0, 0, 0, 0; from 4137-4150, loops=15,chars=13,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 759229 chars/s 2210 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 46 (0 ms): 0, 0, 0, 0; from 4137-4151, loops=16,chars=14,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 759335 chars/s 2162 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 47 (0 ms): 0, 0, 0, 0; from 4137-4152, loops=17,chars=15,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 759450 chars/s 2116 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 48 (0 ms): 0, 0, 0, 0; from 4137-4153, loops=18,chars=16,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 759572 chars/s 2073 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 49 (0 ms): 0, 0, 0, 0; from 4137-4154, loops=19,chars=17,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 759702 chars/s 2031 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 50 (0 ms): 0, 0, 0, 0; from 4137-4155, loops=20,chars=18,blocks 0/0 (0) contexts 0/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4338(135Kb) fcontext 1631(38Kb) = 726Kb
average 759839 chars/s 1990 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 51 (0 ms): 0, 0, 0, 0; from 4137-4158, loops=25,chars=21,blocks 1/0 (0) contexts 1/0 (0) scancache 236
memory scancache 8850(207Kb+345Kb) found 4339(135Kb) fcontext 1632(38Kb) = 726Kb
average 760000 chars/s 1952 chars/run
scancache integrity check done in 0,091000 ms.
scanning run 52 (0 ms): 0, 0, 0, 0; from 4137-4159, loops=26,chars=22,blocks 0/2 (0) contexts 0/2 (0) scancache 238
memory scancache 8852(207Kb+345Kb) found 4339(135Kb) fcontext 1632(38Kb) = 727Kb
average 760167 chars/s 1915 chars/run
scancache integrity check done in 0,090000 ms.
scanning run 53 (0 ms): 0, 0, 0, 0; from 4137-4213, loops=91,chars=76,blocks 0/0 (0) contexts 0/0 (0) scancache 238
memory scancache 8852(207Kb+345Kb) found 4339(135Kb) fcontext 1632(38Kb) = 727Kb
average 760748 chars/s 1880 chars/run
Nothing to scan anymore, total run timer took 642 ms
scanning run 54 (0 ms): 0, 0, 0, 0; from 4155-4214, loops=72,chars=59,blocks 0/0 (0) contexts 0/0 (0) scancache 238
memory scancache 8852(207Kb+345Kb) found 4339(135Kb) fcontext 1632(38Kb) = 727Kb
average 761198 chars/s 1846 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 55 (29 ms): 0, 0, 0, 29; from 62951-91509, loops=32073,chars=28558,blocks 759/762 (0) contexts 320/322 (0) scancache 7055
memory scancache 7661(179Kb+299Kb) found 3764(117Kb) fcontext 1523(35Kb) = 632Kb
average 801718 chars/s 2332 chars/run
scancache integrity check done in 0,990000 ms.
scanning run 56 (43 ms): 0, 0, 0, 43; from 62951-91510, loops=34617,chars=28559,blocks 1335/1338 (0) contexts 430/431 (0) scancache 8248
memory scancache 8854(207Kb+345Kb) found 4340(135Kb) fcontext 1633(38Kb) = 727Kb
average 772581 chars/s 2800 chars/run
scancache integrity check done in 1,101999 ms.
scanning run 57 (0 ms): 0, 0, 0, 0; from 62951-62992, loops=56,chars=41,blocks 0/0 (0) contexts 0/0 (0) scancache 8248
memory scancache 8854(207Kb+345Kb) found 4340(135Kb) fcontext 1633(38Kb) = 727Kb
average 772783 chars/s 2752 chars/run
Nothing to scan anymore, total run timer took 715 ms
scanning run 58 (0 ms): 0, 0, 0, 0; from 62975-62993, loops=28,chars=18,blocks 0/0 (0) contexts 0/0 (0) scancache 8248
memory scancache 8854(207Kb+345Kb) found 4340(135Kb) fcontext 1633(38Kb) = 727Kb
average 772871 chars/s 2705 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 59 (0 ms): 0, 0, 0, 0; from 62975-62994, loops=31,chars=19,blocks 0/0 (0) contexts 0/0 (0) scancache 8248
memory scancache 8854(207Kb+345Kb) found 4340(135Kb) fcontext 1633(38Kb) = 727Kb
average 772965 chars/s 2659 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 60 (0 ms): 0, 0, 0, 0; from 62975-62995, loops=32,chars=20,blocks 0/0 (0) contexts 0/0 (0) scancache 8248
memory scancache 8854(207Kb+345Kb) found 4340(135Kb) fcontext 1633(38Kb) = 727Kb
average 773064 chars/s 2615 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 61 (0 ms): 0, 0, 0, 0; from 62975-62996, loops=33,chars=21,blocks 0/0 (0) contexts 0/0 (0) scancache 8248
memory scancache 8854(207Kb+345Kb) found 4340(135Kb) fcontext 1633(38Kb) = 727Kb
average 773167 chars/s 2573 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 62 (0 ms): 0, 0, 0, 0; from 62975-62997, loops=34,chars=22,blocks 0/0 (0) contexts 0/0 (0) scancache 8248
memory scancache 8854(207Kb+345Kb) found 4340(135Kb) fcontext 1633(38Kb) = 727Kb
average 773275 chars/s 2531 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 63 (0 ms): 0, 0, 0, 0; from 62975-62998, loops=35,chars=23,blocks 0/0 (0) contexts 0/0 (0) scancache 8248
memory scancache 8854(207Kb+345Kb) found 4340(135Kb) fcontext 1633(38Kb) = 727Kb
average 773389 chars/s 2492 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 64 (0 ms): 0, 0, 0, 0; from 62975-62999, loops=36,chars=24,blocks 0/0 (0) contexts 0/0 (0) scancache 8248
memory scancache 8854(207Kb+345Kb) found 4340(135Kb) fcontext 1633(38Kb) = 727Kb
average 773507 chars/s 2453 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 65 (0 ms): 0, 0, 0, 0; from 62975-63000, loops=37,chars=25,blocks 0/0 (0) contexts 0/0 (0) scancache 8248
memory scancache 8854(207Kb+345Kb) found 4340(135Kb) fcontext 1633(38Kb) = 727Kb
average 773630 chars/s 2416 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 66 (0 ms): 0, 0, 0, 0; from 62975-63001, loops=38,chars=26,blocks 0/0 (0) contexts 0/0 (0) scancache 8248
memory scancache 8854(207Kb+345Kb) found 4340(135Kb) fcontext 1633(38Kb) = 727Kb
average 773758 chars/s 2379 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 67 (45 ms): 0, 0, 0, 45; from 62975-91521, loops=34603,chars=28546,blocks 1336/1338 (0) contexts 430/431 (0) scancache 8249
memory scancache 8855(207Kb+345Kb) found 4341(135Kb) fcontext 1633(38Kb) = 727Kb
average 748463 chars/s 2770 chars/run
scancache integrity check done in 1,064998 ms.
scanning run 68 (45 ms): 0, 0, 0, 45; from 62975-91522, loops=34605,chars=28547,blocks 1335/1339 (0) contexts 430/431 (0) scancache 8250
memory scancache 8856(207Kb+345Kb) found 4341(135Kb) fcontext 1633(38Kb) = 727Kb
average 730941 chars/s 3149 chars/run
scancache integrity check done in 1,157000 ms.
scanning run 69 (30 ms): 0, 0, 0, 30; from 62975-91523, loops=32064,chars=28548,blocks 760/762 (0) contexts 321/322 (0) scancache 7058
memory scancache 7664(179Kb+299Kb) found 3766(117Kb) fcontext 1524(35Kb) = 632Kb
average 751436 chars/s 3517 chars/run
scancache integrity check done in 0,936999 ms.
scanning run 70 (42 ms): 0, 0, 0, 42; from 62985-91524, loops=34596,chars=28539,blocks 1335/1340 (0) contexts 430/432 (0) scancache 8252
memory scancache 8858(207Kb+346Kb) found 4342(135Kb) fcontext 1634(38Kb) = 727Kb
average 743158 chars/s 3875 chars/run
scancache integrity check done in 1,074999 ms.
scanning run 71 (0 ms): 0, 0, 0, 0; from 62985-63006, loops=35,chars=21,blocks 0/0 (0) contexts 0/0 (0) scancache 8252
memory scancache 8858(207Kb+346Kb) found 4342(135Kb) fcontext 1634(38Kb) = 727Kb
average 743216 chars/s 3820 chars/run
Nothing to scan anymore, total run timer took 1413 ms
scanning run 72 (0 ms): 0, 0, 0, 0; from 62986-63007, loops=34,chars=21,blocks 0/0 (0) contexts 0/0 (0) scancache 8252
memory scancache 8858(207Kb+346Kb) found 4342(135Kb) fcontext 1634(38Kb) = 727Kb
average 743273 chars/s 3767 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 73 (0 ms): 0, 0, 0, 0; from 62986-63008, loops=35,chars=22,blocks 0/0 (0) contexts 0/0 (0) scancache 8252
memory scancache 8858(207Kb+346Kb) found 4342(135Kb) fcontext 1634(38Kb) = 727Kb
average 743334 chars/s 3716 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 74 (0 ms): 0, 0, 0, 0; from 62986-63009, loops=36,chars=23,blocks 0/0 (0) contexts 0/0 (0) scancache 8252
memory scancache 8858(207Kb+346Kb) found 4342(135Kb) fcontext 1634(38Kb) = 727Kb
average 743397 chars/s 3666 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 75 (0 ms): 0, 0, 0, 0; from 62986-63010, loops=37,chars=24,blocks 0/0 (0) contexts 0/0 (0) scancache 8252
memory scancache 8858(207Kb+346Kb) found 4342(135Kb) fcontext 1634(38Kb) = 727Kb
average 743463 chars/s 3618 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 76 (0 ms): 0, 0, 0, 0; from 62986-63011, loops=38,chars=25,blocks 0/0 (0) contexts 0/0 (0) scancache 8252
memory scancache 8858(207Kb+346Kb) found 4342(135Kb) fcontext 1634(38Kb) = 727Kb
average 743531 chars/s 3570 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 77 (0 ms): 0, 0, 0, 0; from 62986-63012, loops=39,chars=26,blocks 0/0 (0) contexts 0/0 (0) scancache 8252
memory scancache 8858(207Kb+346Kb) found 4342(135Kb) fcontext 1634(38Kb) = 727Kb
average 743602 chars/s 3524 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 78 (0 ms): 0, 0, 0, 0; from 62986-63013, loops=40,chars=27,blocks 0/0 (0) contexts 0/0 (0) scancache 8252
memory scancache 8858(207Kb+346Kb) found 4342(135Kb) fcontext 1634(38Kb) = 727Kb
average 743676 chars/s 3480 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 79 (0 ms): 0, 0, 0, 0; from 62986-63014, loops=41,chars=28,blocks 0/0 (0) contexts 0/0 (0) scancache 8252
memory scancache 8858(207Kb+346Kb) found 4342(135Kb) fcontext 1634(38Kb) = 727Kb
average 743753 chars/s 3436 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 80 (0 ms): 0, 0, 0, 0; from 62986-63015, loops=42,chars=29,blocks 0/0 (0) contexts 0/0 (0) scancache 8252
memory scancache 8858(207Kb+346Kb) found 4342(135Kb) fcontext 1634(38Kb) = 727Kb
average 743832 chars/s 3393 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 81 (0 ms): 0, 0, 0, 0; from 62986-63016, loops=43,chars=30,blocks 0/0 (0) contexts 0/0 (0) scancache 8252
memory scancache 8858(207Kb+346Kb) found 4342(135Kb) fcontext 1634(38Kb) = 727Kb
average 743915 chars/s 3352 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 82 (0 ms): 0, 0, 0, 0; from 62986-63017, loops=44,chars=31,blocks 0/0 (0) contexts 0/0 (0) scancache 8252
memory scancache 8858(207Kb+346Kb) found 4342(135Kb) fcontext 1634(38Kb) = 727Kb
average 744000 chars/s 3311 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 83 (0 ms): 0, 0, 0, 0; from 62986-63018, loops=45,chars=32,blocks 0/0 (0) contexts 0/0 (0) scancache 8252
memory scancache 8858(207Kb+346Kb) found 4342(135Kb) fcontext 1634(38Kb) = 727Kb
average 744087 chars/s 3272 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 84 (43 ms): 0, 0, 0, 43; from 63260-91536, loops=34085,chars=28276,blocks 1254/1258 (0) contexts 480/482 (0) scancache 8112
memory scancache 8718(204Kb+340Kb) found 4275(133Kb) fcontext 1690(39Kb) = 718Kb
average 734970 chars/s 3569 chars/run
scancache integrity check done in 1,115001 ms.
scanning run 85 (44 ms): 0, 0, 0, 44; from 63262-91537, loops=34263,chars=28275,blocks 1322/1325 (0) contexts 425/426 (0) scancache 8254
memory scancache 8860(207Kb+346Kb) found 4343(135Kb) fcontext 1635(38Kb) = 727Kb
average 725980 chars/s 3860 chars/run
scancache integrity check done in 1,114999 ms.
scanning run 86 (0 ms): 0, 0, 0, 0; from 63262-63281, loops=25,chars=19,blocks 0/0 (0) contexts 0/0 (0) scancache 8254
memory scancache 8860(207Kb+346Kb) found 4343(135Kb) fcontext 1635(38Kb) = 727Kb
average 726022 chars/s 3815 chars/run
Nothing to scan anymore, total run timer took 823 ms
scanning run 87 (0 ms): 0, 0, 0, 0; from 63264-63282, loops=23,chars=18,blocks 0/0 (0) contexts 0/0 (0) scancache 8254
memory scancache 8860(207Kb+346Kb) found 4343(135Kb) fcontext 1635(38Kb) = 727Kb
average 726061 chars/s 3772 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 88 (0 ms): 0, 0, 0, 0; from 63264-63283, loops=26,chars=19,blocks 0/0 (0) contexts 0/0 (0) scancache 8254
memory scancache 8860(207Kb+346Kb) found 4343(135Kb) fcontext 1635(38Kb) = 727Kb
average 726103 chars/s 3729 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 89 (0 ms): 0, 0, 0, 0; from 63264-63284, loops=27,chars=20,blocks 0/0 (0) contexts 0/0 (0) scancache 8254
memory scancache 8860(207Kb+346Kb) found 4343(135Kb) fcontext 1635(38Kb) = 727Kb
average 726148 chars/s 3687 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 90 (0 ms): 0, 0, 0, 0; from 63264-63285, loops=28,chars=21,blocks 0/0 (0) contexts 0/0 (0) scancache 8254
memory scancache 8860(207Kb+346Kb) found 4343(135Kb) fcontext 1635(38Kb) = 727Kb
average 726194 chars/s 3647 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 91 (0 ms): 0, 0, 0, 0; from 63264-63286, loops=29,chars=22,blocks 0/0 (0) contexts 0/0 (0) scancache 8254
memory scancache 8860(207Kb+346Kb) found 4343(135Kb) fcontext 1635(38Kb) = 727Kb
average 726243 chars/s 3607 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 92 (0 ms): 0, 0, 0, 0; from 63264-63287, loops=30,chars=23,blocks 0/0 (0) contexts 0/0 (0) scancache 8254
memory scancache 8860(207Kb+346Kb) found 4343(135Kb) fcontext 1635(38Kb) = 727Kb
average 726294 chars/s 3568 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 93 (0 ms): 0, 0, 0, 0; from 63264-63288, loops=31,chars=24,blocks 0/0 (0) contexts 0/0 (0) scancache 8254
memory scancache 8860(207Kb+346Kb) found 4343(135Kb) fcontext 1635(38Kb) = 727Kb
average 726347 chars/s 3530 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 94 (0 ms): 0, 0, 0, 0; from 63264-63289, loops=32,chars=25,blocks 0/0 (0) contexts 0/0 (0) scancache 8254
memory scancache 8860(207Kb+346Kb) found 4343(135Kb) fcontext 1635(38Kb) = 727Kb
average 726402 chars/s 3492 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 95 (0 ms): 0, 0, 0, 0; from 63264-63290, loops=33,chars=26,blocks 0/0 (0) contexts 0/0 (0) scancache 8254
memory scancache 8860(207Kb+346Kb) found 4343(135Kb) fcontext 1635(38Kb) = 727Kb
average 726460 chars/s 3456 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 96 (45 ms): 0, 0, 0, 45; from 63264-91548, loops=34275,chars=28284,blocks 1323/1325 (0) contexts 425/426 (0) scancache 8255
memory scancache 8861(207Kb+346Kb) found 4344(135Kb) fcontext 1635(38Kb) = 727Kb
average 717593 chars/s 3715 chars/run
scancache integrity check done in 1,103999 ms.
scanning run 97 (44 ms): 0, 0, 0, 44; from 63264-91549, loops=34277,chars=28285,blocks 1322/1326 (0) contexts 425/426 (0) scancache 8256
memory scancache 8862(207Kb+346Kb) found 4344(135Kb) fcontext 1635(38Kb) = 727Kb
average 711513 chars/s 3968 chars/run
scancache integrity check done in 1,102000 ms.
scanning run 98 (46 ms): 0, 0, 0, 46; from 63264-91550, loops=34098,chars=28286,blocks 1255/1258 (0) contexts 481/482 (0) scancache 8115
memory scancache 8721(204Kb+340Kb) found 4277(133Kb) fcontext 1691(39Kb) = 718Kb
average 703943 chars/s 4216 chars/run
scancache integrity check done in 1,123000 ms.
scanning run 99 (44 ms): 0, 0, 0, 44; from 63274-91551, loops=34268,chars=28277,blocks 1322/1327 (0) contexts 425/427 (0) scancache 8258
memory scancache 8864(207Kb+346Kb) found 4345(135Kb) fcontext 1636(38Kb) = 728Kb
average 699670 chars/s 4459 chars/run
scancache integrity check done in 1,119001 ms.
scanning run 100 (0 ms): 0, 0, 0, 0; from 63274-63295, loops=30,chars=21,blocks 0/0 (0) contexts 0/0 (0) scancache 8258
memory scancache 8864(207Kb+346Kb) found 4345(135Kb) fcontext 1636(38Kb) = 728Kb
average 699703 chars/s 4415 chars/run
Nothing to scan anymore, total run timer took 1659 ms
scanning run 101 (0 ms): 0, 0, 0, 0; from 63275-63296, loops=29,chars=21,blocks 0/0 (0) contexts 0/0 (0) scancache 8258
memory scancache 8864(207Kb+346Kb) found 4345(135Kb) fcontext 1636(38Kb) = 728Kb
average 699736 chars/s 4371 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 102 (0 ms): 0, 0, 0, 0; from 63275-63297, loops=30,chars=22,blocks 0/0 (0) contexts 0/0 (0) scancache 8258
memory scancache 8864(207Kb+346Kb) found 4345(135Kb) fcontext 1636(38Kb) = 728Kb
average 699771 chars/s 4328 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 103 (0 ms): 0, 0, 0, 0; from 63275-63298, loops=31,chars=23,blocks 0/0 (0) contexts 0/0 (0) scancache 8258
memory scancache 8864(207Kb+346Kb) found 4345(135Kb) fcontext 1636(38Kb) = 728Kb
average 699808 chars/s 4287 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 104 (0 ms): 0, 0, 0, 0; from 4212-4214, loops=3,chars=2,blocks 0/0 (0) contexts 0/0 (0) scancache 238
memory scancache 8864(207Kb+346Kb) found 4345(135Kb) fcontext 1636(38Kb) = 728Kb
average 699811 chars/s 4245 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 105 (0 ms): 0, 0, 0, 0; from 4212-4215, loops=4,chars=3,blocks 0/0 (0) contexts 0/0 (0) scancache 238
memory scancache 8864(207Kb+346Kb) found 4345(135Kb) fcontext 1636(38Kb) = 728Kb
average 699816 chars/s 4205 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 106 (0 ms): 0, 0, 0, 0; from 4212-4217, loops=6,chars=5,blocks 0/0 (0) contexts 0/0 (0) scancache 238
memory scancache 8864(207Kb+346Kb) found 4345(135Kb) fcontext 1636(38Kb) = 728Kb
average 699824 chars/s 4165 chars/run
scancache integrity check done in 0,084000 ms.
scanning run 107 (0 ms): 0, 0, 0, 0; from 4212-4215, loops=4,chars=3,blocks 0/0 (0) contexts 0/0 (0) scancache 238
memory scancache 8864(207Kb+346Kb) found 4345(135Kb) fcontext 1636(38Kb) = 728Kb
average 699828 chars/s 4127 chars/run
Nothing to scan anymore, total run timer took 879 ms
scanning run 108 (0 ms): 0, 0, 0, 0; from 4212-4217, loops=6,chars=5,blocks 0/0 (0) contexts 0/0 (0) scancache 238
memory scancache 8864(207Kb+346Kb) found 4345(135Kb) fcontext 1636(38Kb) = 728Kb
average 699836 chars/s 4088 chars/run
scancache integrity check done in 0,079000 ms.
scanning run 109 (0 ms): 0, 0, 0, 0; from 4212-4215, loops=4,chars=3,blocks 0/0 (0) contexts 0/0 (0) scancache 238
memory scancache 8864(207Kb+346Kb) found 4345(135Kb) fcontext 1636(38Kb) = 728Kb
average 699841 chars/s 4051 chars/run
Nothing to scan anymore, total run timer took 453 ms
scanning run 110 (0 ms): 0, 0, 0, 0; from 4214-4217, loops=5,chars=3,blocks 0/0 (0) contexts 0/0 (0) scancache 238
memory scancache 8864(207Kb+346Kb) found 4345(135Kb) fcontext 1636(38Kb) = 728Kb
average 699846 chars/s 4014 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 111 (0 ms): 0, 0, 0, 0; from 4214-4218, loops=6,chars=4,blocks 0/0 (0) contexts 0/0 (0) scancache 238
memory scancache 8864(207Kb+346Kb) found 4345(135Kb) fcontext 1636(38Kb) = 728Kb
average 699852 chars/s 3978 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 112 (0 ms): 0, 0, 0, 0; from 4214-4219, loops=7,chars=5,blocks 0/0 (0) contexts 0/0 (0) scancache 238
memory scancache 8864(207Kb+346Kb) found 4345(135Kb) fcontext 1636(38Kb) = 728Kb
average 699860 chars/s 3942 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 113 (0 ms): 0, 0, 0, 0; from 4214-4220, loops=8,chars=6,blocks 0/0 (0) contexts 0/0 (0) scancache 238
memory scancache 8864(207Kb+346Kb) found 4345(135Kb) fcontext 1636(38Kb) = 728Kb
average 699870 chars/s 3908 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 114 (0 ms): 0, 0, 0, 0; from 4214-4221, loops=9,chars=7,blocks 0/0 (0) contexts 0/0 (0) scancache 238
memory scancache 8864(207Kb+346Kb) found 4345(135Kb) fcontext 1636(38Kb) = 728Kb
average 699881 chars/s 3873 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 115 (0 ms): 0, 0, 0, 0; from 4214-4222, loops=10,chars=8,blocks 0/0 (0) contexts 0/0 (0) scancache 238
memory scancache 8864(207Kb+346Kb) found 4345(135Kb) fcontext 1636(38Kb) = 728Kb
average 699893 chars/s 3840 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 116 (0 ms): 0, 0, 0, 0; from 4214-4223, loops=11,chars=9,blocks 0/0 (0) contexts 0/0 (0) scancache 238
memory scancache 8864(207Kb+346Kb) found 4345(135Kb) fcontext 1636(38Kb) = 728Kb
average 699908 chars/s 3807 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 117 (0 ms): 0, 0, 0, 0; from 4214-4226, loops=16,chars=12,blocks 1/0 (0) contexts 1/0 (0) scancache 238
memory scancache 8864(207Kb+346Kb) found 4346(135Kb) fcontext 1637(38Kb) = 728Kb
average 699927 chars/s 3774 chars/run
scancache integrity check done in 0,121000 ms.
scanning run 118 (0 ms): 0, 0, 0, 0; from 4214-4227, loops=17,chars=13,blocks 0/2 (0) contexts 0/2 (0) scancache 240
memory scancache 8866(207Kb+346Kb) found 4346(135Kb) fcontext 1637(38Kb) = 728Kb
average 699947 chars/s 3742 chars/run
scancache integrity check done in 0,087000 ms.
scanning run 119 (0 ms): 0, 0, 0, 0; from 4214-4226, loops=17,chars=12,blocks 0/0 (0) contexts 0/0 (0) scancache 240
memory scancache 8866(207Kb+346Kb) found 4346(135Kb) fcontext 1637(38Kb) = 728Kb
average 699966 chars/s 3711 chars/run
Nothing to scan anymore, total run timer took 489 ms
scanning run 120 (0 ms): 0, 0, 0, 0; from 4223-4227, loops=7,chars=4,blocks 0/0 (0) contexts 0/0 (0) scancache 240
memory scancache 8866(207Kb+346Kb) found 4346(135Kb) fcontext 1637(38Kb) = 728Kb
average 699973 chars/s 3680 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 121 (0 ms): 0, 0, 0, 0; from 4223-4228, loops=8,chars=5,blocks 0/0 (0) contexts 0/0 (0) scancache 240
memory scancache 8866(207Kb+346Kb) found 4346(135Kb) fcontext 1637(38Kb) = 728Kb
average 699980 chars/s 3650 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 122 (0 ms): 0, 0, 0, 0; from 63744-63811, loops=89,chars=67,blocks 3/4 (0) contexts 2/3 (0) scancache 8264
memory scancache 8872(207Kb+346Kb) found 4349(135Kb) fcontext 1639(38Kb) = 728Kb
average 700087 chars/s 3620 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 123 (0 ms): 0, 0, 0, 0; from 4137-4214, loops=91,chars=77,blocks 0/0 (0) contexts 0/0 (0) scancache 240
memory scancache 8872(207Kb+346Kb) found 4349(135Kb) fcontext 1639(38Kb) = 728Kb
average 700209 chars/s 3592 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 124 (0 ms): 0, 0, 0, 0; from 4137-4214, loops=90,chars=77,blocks 0/0 (0) contexts 0/0 (0) scancache 240
memory scancache 8872(207Kb+346Kb) found 4349(135Kb) fcontext 1639(38Kb) = 728Kb
average 700331 chars/s 3563 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 125 (0 ms): 0, 0, 0, 0; from 4137-4214, loops=89,chars=77,blocks 0/0 (0) contexts 0/0 (0) scancache 240
memory scancache 8872(207Kb+346Kb) found 4349(135Kb) fcontext 1639(38Kb) = 728Kb
average 700453 chars/s 3535 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 126 (0 ms): 0, 0, 0, 0; from 4137-4214, loops=88,chars=77,blocks 0/0 (0) contexts 0/0 (0) scancache 240
memory scancache 8872(207Kb+346Kb) found 4349(135Kb) fcontext 1639(38Kb) = 728Kb
average 700575 chars/s 3508 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 127 (0 ms): 0, 0, 0, 0; from 4137-4214, loops=87,chars=77,blocks 0/0 (0) contexts 0/0 (0) scancache 240
memory scancache 8872(207Kb+346Kb) found 4349(135Kb) fcontext 1639(38Kb) = 728Kb
average 700697 chars/s 3481 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 128 (0 ms): 0, 0, 0, 0; from 4137-4214, loops=86,chars=77,blocks 0/0 (0) contexts 0/0 (0) scancache 240
memory scancache 8872(207Kb+346Kb) found 4349(135Kb) fcontext 1639(38Kb) = 728Kb
average 700819 chars/s 3454 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 129 (0 ms): 0, 0, 0, 0; from 4137-4214, loops=85,chars=77,blocks 0/0 (0) contexts 0/0 (0) scancache 240
memory scancache 8872(207Kb+346Kb) found 4349(135Kb) fcontext 1639(38Kb) = 728Kb
average 700941 chars/s 3428 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 130 (0 ms): 0, 0, 0, 0; from 4155-4214, loops=64,chars=59,blocks 0/0 (0) contexts 0/0 (0) scancache 240
memory scancache 8872(207Kb+346Kb) found 4349(135Kb) fcontext 1639(38Kb) = 728Kb
average 701034 chars/s 3402 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 131 (0 ms): 0, 0, 0, 0; from 4155-4214, loops=63,chars=59,blocks 0/0 (0) contexts 0/0 (0) scancache 240
memory scancache 8872(207Kb+346Kb) found 4349(135Kb) fcontext 1639(38Kb) = 728Kb
average 701128 chars/s 3377 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 132 (0 ms): 0, 0, 0, 0; from 4155-4214, loops=62,chars=59,blocks 0/0 (0) contexts 0/0 (0) scancache 240
memory scancache 8872(207Kb+346Kb) found 4349(135Kb) fcontext 1639(38Kb) = 728Kb
average 701221 chars/s 3352 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 133 (0 ms): 0, 0, 0, 0; from 64053-64237, loops=219,chars=184,blocks 3/4 (0) contexts 2/3 (0) scancache 8270
memory scancache 8878(208Kb+346Kb) found 4352(136Kb) fcontext 1641(38Kb) = 729Kb
average 701513 chars/s 3328 chars/run
Nothing to scan anymore, total run timer took 3 ms
scanning run 134 (0 ms): 0, 0, 0, 0; from 64927-65065, loops=162,chars=138,blocks 0/0 (0) contexts 0/0 (0) scancache 8270
memory scancache 8878(208Kb+346Kb) found 4352(136Kb) fcontext 1641(38Kb) = 729Kb
average 701732 chars/s 3304 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 135 (0 ms): 0, 0, 0, 0; from 4226-4228, loops=3,chars=2,blocks 0/0 (0) contexts 0/0 (0) scancache 240
memory scancache 8878(208Kb+346Kb) found 4352(136Kb) fcontext 1641(38Kb) = 729Kb
average 701735 chars/s 3279 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 136 (0 ms): 0, 0, 0, 0; from 4226-4229, loops=4,chars=3,blocks 0/0 (0) contexts 0/0 (0) scancache 240
memory scancache 8878(208Kb+346Kb) found 4352(136Kb) fcontext 1641(38Kb) = 729Kb
average 701740 chars/s 3255 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 137 (0 ms): 0, 0, 0, 0; from 4228-4231, loops=5,chars=3,blocks 0/0 (0) contexts 0/0 (0) scancache 240
memory scancache 8878(208Kb+346Kb) found 4352(136Kb) fcontext 1641(38Kb) = 729Kb
average 701744 chars/s 3232 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 138 (0 ms): 0, 0, 0, 0; from 4228-4232, loops=6,chars=4,blocks 0/0 (0) contexts 0/0 (0) scancache 240
memory scancache 8878(208Kb+346Kb) found 4352(136Kb) fcontext 1641(38Kb) = 729Kb
average 701751 chars/s 3208 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 139 (0 ms): 0, 0, 0, 0; from 4228-4233, loops=7,chars=5,blocks 0/0 (0) contexts 0/0 (0) scancache 240
memory scancache 8878(208Kb+346Kb) found 4352(136Kb) fcontext 1641(38Kb) = 729Kb
average 701759 chars/s 3185 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 140 (0 ms): 0, 0, 0, 0; from 4228-4234, loops=8,chars=6,blocks 0/0 (0) contexts 0/0 (0) scancache 240
memory scancache 8878(208Kb+346Kb) found 4352(136Kb) fcontext 1641(38Kb) = 729Kb
average 701768 chars/s 3162 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 141 (0 ms): 0, 0, 0, 0; from 4228-4235, loops=9,chars=7,blocks 0/0 (0) contexts 0/0 (0) scancache 240
memory scancache 8878(208Kb+346Kb) found 4352(136Kb) fcontext 1641(38Kb) = 729Kb
average 701779 chars/s 3140 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 142 (0 ms): 0, 0, 0, 0; from 4228-4236, loops=10,chars=8,blocks 0/0 (0) contexts 0/0 (0) scancache 240
memory scancache 8878(208Kb+346Kb) found 4352(136Kb) fcontext 1641(38Kb) = 729Kb
average 701792 chars/s 3118 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 143 (0 ms): 0, 0, 0, 0; from 4228-4237, loops=11,chars=9,blocks 0/0 (0) contexts 0/0 (0) scancache 240
memory scancache 8878(208Kb+346Kb) found 4352(136Kb) fcontext 1641(38Kb) = 729Kb
average 701806 chars/s 3096 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 144 (0 ms): 0, 0, 0, 0; from 4228-4238, loops=12,chars=10,blocks 0/0 (0) contexts 0/0 (0) scancache 240
memory scancache 8878(208Kb+346Kb) found 4352(136Kb) fcontext 1641(38Kb) = 729Kb
average 701822 chars/s 3075 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 145 (0 ms): 0, 0, 0, 0; from 4228-4239, loops=13,chars=11,blocks 0/0 (0) contexts 0/0 (0) scancache 240
memory scancache 8878(208Kb+346Kb) found 4352(136Kb) fcontext 1641(38Kb) = 729Kb
average 701839 chars/s 3054 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 146 (0 ms): 0, 0, 0, 0; from 4228-4240, loops=14,chars=12,blocks 0/0 (0) contexts 0/0 (0) scancache 240
memory scancache 8878(208Kb+346Kb) found 4352(136Kb) fcontext 1641(38Kb) = 729Kb
average 701858 chars/s 3033 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 147 (0 ms): 0, 0, 0, 0; from 4228-4241, loops=15,chars=13,blocks 0/0 (0) contexts 0/0 (0) scancache 240
memory scancache 8878(208Kb+346Kb) found 4352(136Kb) fcontext 1641(38Kb) = 729Kb
average 701879 chars/s 3012 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 148 (0 ms): 0, 0, 0, 0; from 4228-4242, loops=16,chars=14,blocks 0/0 (0) contexts 0/0 (0) scancache 240
memory scancache 8878(208Kb+346Kb) found 4352(136Kb) fcontext 1641(38Kb) = 729Kb
average 701901 chars/s 2992 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 149 (0 ms): 0, 0, 0, 0; from 4228-4243, loops=17,chars=15,blocks 0/0 (0) contexts 0/0 (0) scancache 240
memory scancache 8878(208Kb+346Kb) found 4352(136Kb) fcontext 1641(38Kb) = 729Kb
average 701925 chars/s 2972 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 150 (0 ms): 0, 0, 0, 0; from 4228-4244, loops=18,chars=16,blocks 0/0 (0) contexts 0/0 (0) scancache 240
memory scancache 8878(208Kb+346Kb) found 4352(136Kb) fcontext 1641(38Kb) = 729Kb
average 701950 chars/s 2952 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 151 (0 ms): 0, 0, 0, 0; from 4228-4247, loops=23,chars=19,blocks 1/0 (0) contexts 1/0 (0) scancache 240
memory scancache 8878(208Kb+346Kb) found 4353(136Kb) fcontext 1642(38Kb) = 729Kb
average 701980 chars/s 2933 chars/run
scancache integrity check done in 0,083000 ms.
scanning run 152 (0 ms): 0, 0, 0, 0; from 4228-4248, loops=24,chars=20,blocks 0/2 (0) contexts 0/2 (0) scancache 242
memory scancache 8880(208Kb+346Kb) found 4353(136Kb) fcontext 1642(38Kb) = 729Kb
average 702012 chars/s 2914 chars/run
scancache integrity check done in 0,104000 ms.
scanning run 153 (0 ms): 0, 0, 0, 0; from 4228-4272, loops=52,chars=44,blocks 0/0 (0) contexts 0/0 (0) scancache 242
memory scancache 8880(208Kb+346Kb) found 4353(136Kb) fcontext 1642(38Kb) = 729Kb
average 702082 chars/s 2895 chars/run
Nothing to scan anymore, total run timer took 795 ms
scanning run 154 (0 ms): 0, 0, 0, 0; from 4244-4273, loops=35,chars=29,blocks 0/0 (0) contexts 0/0 (0) scancache 242
memory scancache 8880(208Kb+346Kb) found 4353(136Kb) fcontext 1642(38Kb) = 729Kb
average 702128 chars/s 2876 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 155 (42 ms): 0, 0, 0, 42; from 64927-91521, loops=32144,chars=26594,blocks 1214/1218 (0) contexts 440/442 (0) scancache 8128
memory scancache 8738(204Kb+341Kb) found 4284(133Kb) fcontext 1675(39Kb) = 719Kb
average 697826 chars/s 3029 chars/run
scancache integrity check done in 1,116999 ms.
scanning run 156 (7 ms): 0, 0, 0, 7; from 64927-69851, loops=5932,chars=4924,blocks 190/192 (0) contexts 78/78 (0) scancache 8272
memory scancache 8882(208Kb+346Kb) found 4354(136Kb) fcontext 1643(38Kb) = 729Kb
average 697883 chars/s 3042 chars/run
Nothing to scan anymore, total run timer took 132 ms
scanning run 157 (0 ms): 0, 0, 0, 0; from 64927-65068, loops=168,chars=141,blocks 0/0 (0) contexts 0/0 (0) scancache 8272
memory scancache 8882(208Kb+346Kb) found 4354(136Kb) fcontext 1643(38Kb) = 729Kb
average 698091 chars/s 3023 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 158 (0 ms): 0, 0, 0, 0; from 65052-65069, loops=23,chars=17,blocks 0/0 (0) contexts 0/0 (0) scancache 8272
memory scancache 8882(208Kb+346Kb) found 4354(136Kb) fcontext 1643(38Kb) = 729Kb
average 698116 chars/s 3004 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 159 (0 ms): 0, 0, 0, 0; from 65052-65070, loops=26,chars=18,blocks 0/0 (0) contexts 0/0 (0) scancache 8272
memory scancache 8882(208Kb+346Kb) found 4354(136Kb) fcontext 1643(38Kb) = 729Kb
average 698142 chars/s 2985 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 160 (0 ms): 0, 0, 0, 0; from 65052-65071, loops=27,chars=19,blocks 0/0 (0) contexts 0/0 (0) scancache 8272
memory scancache 8882(208Kb+346Kb) found 4354(136Kb) fcontext 1643(38Kb) = 729Kb
average 698170 chars/s 2967 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 161 (0 ms): 0, 0, 0, 0; from 65052-65072, loops=28,chars=20,blocks 0/0 (0) contexts 0/0 (0) scancache 8272
memory scancache 8882(208Kb+346Kb) found 4354(136Kb) fcontext 1643(38Kb) = 729Kb
average 698200 chars/s 2948 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 162 (0 ms): 0, 0, 0, 0; from 65052-65073, loops=29,chars=21,blocks 0/0 (0) contexts 0/0 (0) scancache 8272
memory scancache 8882(208Kb+346Kb) found 4354(136Kb) fcontext 1643(38Kb) = 729Kb
average 698230 chars/s 2930 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 163 (0 ms): 0, 0, 0, 0; from 65052-65074, loops=30,chars=22,blocks 0/0 (0) contexts 0/0 (0) scancache 8272
memory scancache 8882(208Kb+346Kb) found 4354(136Kb) fcontext 1643(38Kb) = 729Kb
average 698263 chars/s 2913 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 164 (0 ms): 0, 0, 0, 0; from 65052-65075, loops=31,chars=23,blocks 0/0 (0) contexts 0/0 (0) scancache 8272
memory scancache 8882(208Kb+346Kb) found 4354(136Kb) fcontext 1643(38Kb) = 729Kb
average 698297 chars/s 2895 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 165 (0 ms): 0, 0, 0, 0; from 65052-65076, loops=32,chars=24,blocks 0/0 (0) contexts 0/0 (0) scancache 8272
memory scancache 8882(208Kb+346Kb) found 4354(136Kb) fcontext 1643(38Kb) = 729Kb
average 698332 chars/s 2877 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 166 (0 ms): 0, 0, 0, 0; from 65052-65077, loops=33,chars=25,blocks 0/0 (0) contexts 0/0 (0) scancache 8272
memory scancache 8882(208Kb+346Kb) found 4354(136Kb) fcontext 1643(38Kb) = 729Kb
average 698369 chars/s 2860 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 167 (43 ms): 0, 0, 0, 43; from 65052-91533, loops=32151,chars=26481,blocks 1285/1287 (0) contexts 408/409 (0) scancache 8273
memory scancache 8883(208Kb+346Kb) found 4355(136Kb) fcontext 1643(38Kb) = 729Kb
average 693460 chars/s 3002 chars/run
scancache integrity check done in 1,082002 ms.
scanning run 168 (43 ms): 0, 0, 0, 43; from 65052-91534, loops=32153,chars=26482,blocks 1284/1288 (0) contexts 408/409 (0) scancache 8274
memory scancache 8884(208Kb+347Kb) found 4355(136Kb) fcontext 1643(38Kb) = 729Kb
average 689104 chars/s 3141 chars/run
scancache integrity check done in 1,226000 ms.
scanning run 169 (41 ms): 0, 0, 0, 41; from 65052-91535, loops=32018,chars=26483,blocks 1215/1218 (0) contexts 441/442 (0) scancache 8131
memory scancache 8741(204Kb+341Kb) found 4286(133Kb) fcontext 1676(39Kb) = 719Kb
average 686910 chars/s 3280 chars/run
scancache integrity check done in 1,098001 ms.
scanning run 170 (43 ms): 0, 0, 0, 43; from 65062-91536, loops=32144,chars=26474,blocks 1284/1289 (0) contexts 408/410 (0) scancache 8276
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 683307 chars/s 3416 chars/run
scancache integrity check done in 1,167001 ms.
scanning run 171 (0 ms): 0, 0, 0, 0; from 65062-65082, loops=30,chars=20,blocks 0/0 (0) contexts 0/0 (0) scancache 8276
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 683330 chars/s 3396 chars/run
Nothing to scan anymore, total run timer took 1241 ms
scanning run 172 (0 ms): 0, 0, 0, 0; from 65063-65083, loops=29,chars=20,blocks 0/0 (0) contexts 0/0 (0) scancache 8276
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 683354 chars/s 3377 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 173 (0 ms): 0, 0, 0, 0; from 65063-65084, loops=30,chars=21,blocks 0/0 (0) contexts 0/0 (0) scancache 8276
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 683378 chars/s 3357 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 174 (0 ms): 0, 0, 0, 0; from 65063-65085, loops=31,chars=22,blocks 0/0 (0) contexts 0/0 (0) scancache 8276
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 683404 chars/s 3338 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 175 (0 ms): 0, 0, 0, 0; from 65063-65086, loops=32,chars=23,blocks 0/0 (0) contexts 0/0 (0) scancache 8276
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 683431 chars/s 3319 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 176 (0 ms): 0, 0, 0, 0; from 65063-65087, loops=33,chars=24,blocks 0/0 (0) contexts 0/0 (0) scancache 8276
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 683460 chars/s 3300 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 177 (0 ms): 0, 0, 0, 0; from 65063-65088, loops=34,chars=25,blocks 0/0 (0) contexts 0/0 (0) scancache 8276
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 683489 chars/s 3282 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 178 (0 ms): 0, 0, 0, 0; from 65063-65089, loops=35,chars=26,blocks 0/0 (0) contexts 0/0 (0) scancache 8276
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 683520 chars/s 3264 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 179 (0 ms): 0, 0, 0, 0; from 65063-65090, loops=36,chars=27,blocks 0/0 (0) contexts 0/0 (0) scancache 8276
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 683551 chars/s 3245 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 180 (0 ms): 0, 0, 0, 0; from 65063-65091, loops=37,chars=28,blocks 0/0 (0) contexts 0/0 (0) scancache 8276
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 683584 chars/s 3228 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 181 (0 ms): 0, 0, 0, 0; from 65063-65092, loops=38,chars=29,blocks 0/0 (0) contexts 0/0 (0) scancache 8276
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 683618 chars/s 3210 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 182 (0 ms): 0, 0, 0, 0; from 4271-4273, loops=3,chars=2,blocks 0/0 (0) contexts 0/0 (0) scancache 242
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 683621 chars/s 3192 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 183 (0 ms): 0, 0, 0, 0; from 4271-4274, loops=4,chars=3,blocks 0/0 (0) contexts 0/0 (0) scancache 242
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 683624 chars/s 3175 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 184 (0 ms): 0, 0, 0, 0; from 4273-4276, loops=5,chars=3,blocks 0/0 (0) contexts 0/0 (0) scancache 242
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 683628 chars/s 3158 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 185 (0 ms): 0, 0, 0, 0; from 4273-4277, loops=6,chars=4,blocks 0/0 (0) contexts 0/0 (0) scancache 242
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 683632 chars/s 3141 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 186 (0 ms): 0, 0, 0, 0; from 4273-4278, loops=7,chars=5,blocks 0/0 (0) contexts 0/0 (0) scancache 242
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 683638 chars/s 3124 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 187 (0 ms): 0, 0, 0, 0; from 4273-4279, loops=8,chars=6,blocks 0/0 (0) contexts 0/0 (0) scancache 242
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 683645 chars/s 3107 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 188 (0 ms): 0, 0, 0, 0; from 4273-4280, loops=9,chars=7,blocks 0/0 (0) contexts 0/0 (0) scancache 242
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 683654 chars/s 3090 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 189 (0 ms): 0, 0, 0, 0; from 4273-4281, loops=10,chars=8,blocks 0/0 (0) contexts 0/0 (0) scancache 242
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 683663 chars/s 3074 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 190 (0 ms): 0, 0, 0, 0; from 4273-4282, loops=11,chars=9,blocks 0/0 (0) contexts 0/0 (0) scancache 242
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 683674 chars/s 3058 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 191 (0 ms): 0, 0, 0, 0; from 4273-4283, loops=12,chars=10,blocks 0/0 (0) contexts 0/0 (0) scancache 242
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 683685 chars/s 3042 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 192 (0 ms): 0, 0, 0, 0; from 4273-4284, loops=13,chars=11,blocks 0/0 (0) contexts 0/0 (0) scancache 242
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 683698 chars/s 3026 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 193 (0 ms): 0, 0, 0, 0; from 4273-4285, loops=14,chars=12,blocks 0/0 (0) contexts 0/0 (0) scancache 242
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 683712 chars/s 3011 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 194 (0 ms): 0, 0, 0, 0; from 4273-4286, loops=15,chars=13,blocks 0/0 (0) contexts 0/0 (0) scancache 242
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 683728 chars/s 2995 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 195 (0 ms): 0, 0, 0, 0; from 4273-4287, loops=16,chars=14,blocks 0/0 (0) contexts 0/0 (0) scancache 242
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 683744 chars/s 2980 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 196 (0 ms): 0, 0, 0, 0; from 4273-4288, loops=17,chars=15,blocks 0/0 (0) contexts 0/0 (0) scancache 242
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 683762 chars/s 2965 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 197 (0 ms): 0, 0, 0, 0; from 4273-4289, loops=18,chars=16,blocks 0/0 (0) contexts 0/0 (0) scancache 242
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 683781 chars/s 2950 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 198 (0 ms): 0, 0, 0, 0; from 4273-4292, loops=23,chars=19,blocks 1/0 (0) contexts 1/0 (0) scancache 242
memory scancache 8886(208Kb+347Kb) found 4357(136Kb) fcontext 1645(38Kb) = 730Kb
average 683803 chars/s 2935 chars/run
scancache integrity check done in 0,087000 ms.
scanning run 199 (0 ms): 0, 0, 0, 0; from 4273-4293, loops=24,chars=20,blocks 0/2 (0) contexts 0/2 (0) scancache 244
memory scancache 8888(208Kb+347Kb) found 4357(136Kb) fcontext 1645(38Kb) = 730Kb
average 683827 chars/s 2920 chars/run
scancache integrity check done in 0,087000 ms.
Nothing to scan anymore, total run timer took 2213 ms
scanning run 200 (0 ms): 0, 0, 0, 0; from 66245-66489, loops=287,chars=244,blocks 0/0 (0) contexts 0/0 (0) scancache 8274
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 684114 chars/s 2907 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 201 (0 ms): 0, 0, 0, 0; from 66287-66490, loops=241,chars=203,blocks 0/0 (0) contexts 0/0 (0) scancache 8274
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 684352 chars/s 2894 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 202 (0 ms): 0, 0, 0, 0; from 66300-66491, loops=227,chars=191,blocks 0/0 (0) contexts 0/0 (0) scancache 8274
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 684577 chars/s 2880 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 203 (0 ms): 0, 0, 0, 0; from 66300-66492, loops=228,chars=192,blocks 0/0 (0) contexts 0/0 (0) scancache 8274
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 684803 chars/s 2867 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 204 (0 ms): 0, 0, 0, 0; from 66262-66491, loops=271,chars=229,blocks 0/0 (0) contexts 0/0 (0) scancache 8274
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 685072 chars/s 2854 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 205 (0 ms): 0, 0, 0, 0; from 66300-66492, loops=228,chars=192,blocks 0/0 (0) contexts 0/0 (0) scancache 8274
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 685298 chars/s 2841 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 206 (0 ms): 0, 0, 0, 0; from 66300-66493, loops=229,chars=193,blocks 0/0 (0) contexts 0/0 (0) scancache 8274
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 685525 chars/s 2828 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 207 (0 ms): 0, 0, 0, 0; from 66300-66494, loops=230,chars=194,blocks 0/0 (0) contexts 0/0 (0) scancache 8274
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 685754 chars/s 2815 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 208 (0 ms): 0, 0, 0, 0; from 66300-66495, loops=231,chars=195,blocks 0/0 (0) contexts 0/0 (0) scancache 8274
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 685983 chars/s 2803 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 209 (0 ms): 0, 0, 0, 0; from 66300-66496, loops=232,chars=196,blocks 0/0 (0) contexts 0/0 (0) scancache 8274
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 686214 chars/s 2790 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 210 (0 ms): 0, 0, 0, 0; from 66300-66497, loops=233,chars=197,blocks 0/0 (0) contexts 0/0 (0) scancache 8274
memory scancache 8886(208Kb+347Kb) found 4356(136Kb) fcontext 1644(38Kb) = 730Kb
average 686445 chars/s 2778 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 211 (0 ms): 0, 0, 0, 0; from 66300-66498, loops=235,chars=198,blocks 2/2 (0) contexts 1/1 (0) scancache 8275
memory scancache 8887(208Kb+347Kb) found 4357(136Kb) fcontext 1644(38Kb) = 730Kb
average 686678 chars/s 2766 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 212 (0 ms): 0, 0, 0, 0; from 66300-66499, loops=237,chars=199,blocks 1/3 (0) contexts 1/1 (0) scancache 8276
memory scancache 8888(208Kb+347Kb) found 4357(136Kb) fcontext 1644(38Kb) = 730Kb
average 686912 chars/s 2754 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 213 (27 ms): 0, 0, 0, 27; from 66300-91518, loops=28442,chars=25218,blocks 709/712 (0) contexts 282/283 (0) scancache 7241
memory scancache 7853(184Kb+306Kb) found 3861(120Kb) fcontext 1547(36Kb) = 647Kb
average 694519 chars/s 2859 chars/run
scancache integrity check done in 0,977000 ms.
scanning run 214 (40 ms): 0, 0, 0, 40; from 66309-91519, loops=30586,chars=25210,blocks 1205/1214 (0) contexts 379/381 (0) scancache 8278
memory scancache 8890(208Kb+347Kb) found 4358(136Kb) fcontext 1645(38Kb) = 730Kb
average 691716 chars/s 2964 chars/run
scancache integrity check done in 1,117001 ms.
scanning run 215 (0 ms): 0, 0, 0, 0; from 66309-66502, loops=232,chars=193,blocks 0/0 (0) contexts 0/0 (0) scancache 8278
memory scancache 8890(208Kb+347Kb) found 4358(136Kb) fcontext 1645(38Kb) = 730Kb
average 691926 chars/s 2951 chars/run
Nothing to scan anymore, total run timer took 478 ms
scanning run 216 (0 ms): 0, 0, 0, 0; from 66310-66503, loops=231,chars=193,blocks 0/0 (0) contexts 0/0 (0) scancache 8278
memory scancache 8890(208Kb+347Kb) found 4358(136Kb) fcontext 1645(38Kb) = 730Kb
average 692137 chars/s 2938 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 217 (0 ms): 0, 0, 0, 0; from 66310-66504, loops=232,chars=194,blocks 0/0 (0) contexts 0/0 (0) scancache 8278
memory scancache 8890(208Kb+347Kb) found 4358(136Kb) fcontext 1645(38Kb) = 730Kb
average 692348 chars/s 2925 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 218 (0 ms): 0, 0, 0, 0; from 66310-66505, loops=233,chars=195,blocks 0/0 (0) contexts 0/0 (0) scancache 8278
memory scancache 8890(208Kb+347Kb) found 4358(136Kb) fcontext 1645(38Kb) = 730Kb
average 692561 chars/s 2913 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 219 (0 ms): 0, 0, 0, 0; from 66310-66506, loops=234,chars=196,blocks 0/0 (0) contexts 0/0 (0) scancache 8278
memory scancache 8890(208Kb+347Kb) found 4358(136Kb) fcontext 1645(38Kb) = 730Kb
average 692775 chars/s 2900 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 220 (0 ms): 0, 0, 0, 0; from 66310-66507, loops=235,chars=197,blocks 0/0 (0) contexts 0/0 (0) scancache 8278
memory scancache 8890(208Kb+347Kb) found 4358(136Kb) fcontext 1645(38Kb) = 730Kb
average 692990 chars/s 2888 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 221 (0 ms): 0, 0, 0, 0; from 66310-66508, loops=236,chars=198,blocks 0/0 (0) contexts 0/0 (0) scancache 8278
memory scancache 8890(208Kb+347Kb) found 4358(136Kb) fcontext 1645(38Kb) = 730Kb
average 693206 chars/s 2876 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 222 (0 ms): 0, 0, 0, 0; from 66310-66509, loops=237,chars=199,blocks 0/0 (0) contexts 0/0 (0) scancache 8278
memory scancache 8890(208Kb+347Kb) found 4358(136Kb) fcontext 1645(38Kb) = 730Kb
average 693423 chars/s 2864 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 223 (0 ms): 0, 0, 0, 0; from 66310-66510, loops=238,chars=200,blocks 0/0 (0) contexts 0/0 (0) scancache 8278
memory scancache 8890(208Kb+347Kb) found 4358(136Kb) fcontext 1645(38Kb) = 730Kb
average 693641 chars/s 2852 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 224 (0 ms): 0, 0, 0, 0; from 66310-66511, loops=239,chars=201,blocks 0/0 (0) contexts 0/0 (0) scancache 8278
memory scancache 8890(208Kb+347Kb) found 4358(136Kb) fcontext 1645(38Kb) = 730Kb
average 693860 chars/s 2840 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 225 (0 ms): 0, 0, 0, 0; from 66310-66512, loops=240,chars=202,blocks 0/0 (0) contexts 0/0 (0) scancache 8278
memory scancache 8890(208Kb+347Kb) found 4358(136Kb) fcontext 1645(38Kb) = 730Kb
average 694080 chars/s 2828 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 226 (0 ms): 0, 0, 0, 0; from 4273-4331, loops=69,chars=58,blocks 1/1 (0) contexts 1/1 (0) scancache 244
memory scancache 8890(208Kb+347Kb) found 4358(136Kb) fcontext 1645(38Kb) = 730Kb
average 694143 chars/s 2816 chars/run
scancache integrity check done in 0,081000 ms.
scanning run 227 (0 ms): 0, 0, 0, 0; from 4289-4330, loops=50,chars=41,blocks 0/0 (0) contexts 0/0 (0) scancache 244
memory scancache 8890(208Kb+347Kb) found 4358(136Kb) fcontext 1645(38Kb) = 730Kb
average 694188 chars/s 2804 chars/run
Nothing to scan anymore, total run timer took 449 ms
scanning run 228 (0 ms): 0, 0, 0, 0; from 4328-4330, loops=3,chars=2,blocks 0/0 (0) contexts 0/0 (0) scancache 244
memory scancache 8890(208Kb+347Kb) found 4358(136Kb) fcontext 1645(38Kb) = 730Kb
average 694190 chars/s 2791 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 229 (43 ms): 0, 0, 0, 43; from 66354-91525, loops=30449,chars=25171,blocks 1185/1189 (0) contexts 411/413 (0) scancache 8239
memory scancache 8851(207Kb+345Kb) found 4342(135Kb) fcontext 1679(39Kb) = 728Kb
average 689316 chars/s 2889 chars/run
scancache integrity check done in 1,158001 ms.
scanning run 230 (42 ms): 0, 0, 0, 42; from 66354-91526, loops=30533,chars=25172,blocks 1202/1208 (0) contexts 378/379 (0) scancache 8280
memory scancache 8892(208Kb+347Kb) found 4359(136Kb) fcontext 1646(38Kb) = 730Kb
average 685544 chars/s 2986 chars/run
scancache integrity check done in 1,249999 ms.
scanning run 231 (0 ms): 0, 0, 0, 0; from 66354-66509, loops=179,chars=155,blocks 0/0 (0) contexts 0/0 (0) scancache 8280
memory scancache 8892(208Kb+347Kb) found 4359(136Kb) fcontext 1646(38Kb) = 730Kb
average 685699 chars/s 2974 chars/run
Nothing to scan anymore, total run timer took 949 ms
scanning run 232 (0 ms): 0, 0, 0, 0; from 66402-66510, loops=124,chars=108,blocks 0/0 (0) contexts 0/0 (0) scancache 8280
memory scancache 8892(208Kb+347Kb) found 4359(136Kb) fcontext 1646(38Kb) = 730Kb
average 685807 chars/s 2961 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 233 (0 ms): 0, 0, 0, 0; from 66402-66511, loops=127,chars=109,blocks 0/0 (0) contexts 0/0 (0) scancache 8280
memory scancache 8892(208Kb+347Kb) found 4359(136Kb) fcontext 1646(38Kb) = 730Kb
average 685916 chars/s 2949 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 234 (0 ms): 0, 0, 0, 0; from 66402-66512, loops=128,chars=110,blocks 0/0 (0) contexts 0/0 (0) scancache 8280
memory scancache 8892(208Kb+347Kb) found 4359(136Kb) fcontext 1646(38Kb) = 730Kb
average 686025 chars/s 2937 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 235 (0 ms): 0, 0, 0, 0; from 66402-66513, loops=129,chars=111,blocks 0/0 (0) contexts 0/0 (0) scancache 8280
memory scancache 8892(208Kb+347Kb) found 4359(136Kb) fcontext 1646(38Kb) = 730Kb
average 686136 chars/s 2925 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 236 (0 ms): 0, 0, 0, 0; from 66402-66514, loops=130,chars=112,blocks 0/0 (0) contexts 0/0 (0) scancache 8280
memory scancache 8892(208Kb+347Kb) found 4359(136Kb) fcontext 1646(38Kb) = 730Kb
average 686248 chars/s 2913 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 237 (0 ms): 0, 0, 0, 0; from 66402-66515, loops=131,chars=113,blocks 0/0 (0) contexts 0/0 (0) scancache 8280
memory scancache 8892(208Kb+347Kb) found 4359(136Kb) fcontext 1646(38Kb) = 730Kb
average 686361 chars/s 2901 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 238 (0 ms): 0, 0, 0, 0; from 66402-66516, loops=132,chars=114,blocks 0/0 (0) contexts 0/0 (0) scancache 8280
memory scancache 8892(208Kb+347Kb) found 4359(136Kb) fcontext 1646(38Kb) = 730Kb
average 686475 chars/s 2890 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 239 (0 ms): 0, 0, 0, 0; from 66402-66517, loops=133,chars=115,blocks 0/0 (0) contexts 0/0 (0) scancache 8280
memory scancache 8892(208Kb+347Kb) found 4359(136Kb) fcontext 1646(38Kb) = 730Kb
average 686589 chars/s 2878 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 240 (0 ms): 0, 0, 0, 0; from 66402-66518, loops=134,chars=116,blocks 0/0 (0) contexts 0/0 (0) scancache 8280
memory scancache 8892(208Kb+347Kb) found 4359(136Kb) fcontext 1646(38Kb) = 730Kb
average 686705 chars/s 2866 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 241 (41 ms): 0, 0, 0, 41; from 66402-91537, loops=30492,chars=25135,blocks 1203/1208 (0) contexts 378/379 (0) scancache 8281
memory scancache 8893(208Kb+347Kb) found 4360(136Kb) fcontext 1646(38Kb) = 730Kb
average 683810 chars/s 2959 chars/run
scancache integrity check done in 1,165999 ms.
scanning run 242 (41 ms): 0, 0, 0, 41; from 66402-91538, loops=30494,chars=25136,blocks 1202/1209 (0) contexts 378/379 (0) scancache 8282
memory scancache 8894(208Kb+347Kb) found 4360(136Kb) fcontext 1646(38Kb) = 730Kb
average 681134 chars/s 3051 chars/run
scancache integrity check done in 1,168001 ms.
scanning run 243 (40 ms): 0, 0, 0, 40; from 66402-91539, loops=30413,chars=25137,blocks 1186/1189 (0) contexts 412/413 (0) scancache 8242
memory scancache 8854(207Kb+345Kb) found 4344(135Kb) fcontext 1680(39Kb) = 728Kb
average 679258 chars/s 3141 chars/run
scancache integrity check done in 1,113000 ms.
scanning run 244 (41 ms): 0, 0, 0, 41; from 66412-91540, loops=30485,chars=25128,blocks 1202/1210 (0) contexts 378/380 (0) scancache 8284
memory scancache 8896(208Kb+347Kb) found 4361(136Kb) fcontext 1647(38Kb) = 730Kb
average 676922 chars/s 3232 chars/run
scancache integrity check done in 1,094999 ms.
scanning run 245 (0 ms): 0, 0, 0, 0; from 66412-66523, loops=131,chars=111,blocks 0/0 (0) contexts 0/0 (0) scancache 8284
memory scancache 8896(208Kb+347Kb) found 4361(136Kb) fcontext 1647(38Kb) = 730Kb
average 677018 chars/s 3219 chars/run
Nothing to scan anymore, total run timer took 1510 ms
scanning run 246 (0 ms): 0, 0, 0, 0; from 66413-66524, loops=130,chars=111,blocks 0/0 (0) contexts 0/0 (0) scancache 8284
memory scancache 8896(208Kb+347Kb) found 4361(136Kb) fcontext 1647(38Kb) = 730Kb
average 677113 chars/s 3206 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 247 (0 ms): 0, 0, 0, 0; from 66413-66525, loops=131,chars=112,blocks 0/0 (0) contexts 0/0 (0) scancache 8284
memory scancache 8896(208Kb+347Kb) found 4361(136Kb) fcontext 1647(38Kb) = 730Kb
average 677209 chars/s 3194 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 248 (0 ms): 0, 0, 0, 0; from 66413-66526, loops=132,chars=113,blocks 0/0 (0) contexts 0/0 (0) scancache 8284
memory scancache 8896(208Kb+347Kb) found 4361(136Kb) fcontext 1647(38Kb) = 730Kb
average 677306 chars/s 3181 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 249 (0 ms): 0, 0, 0, 0; from 66413-66527, loops=133,chars=114,blocks 0/0 (0) contexts 0/0 (0) scancache 8284
memory scancache 8896(208Kb+347Kb) found 4361(136Kb) fcontext 1647(38Kb) = 730Kb
average 677404 chars/s 3169 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 250 (0 ms): 0, 0, 0, 0; from 66413-66528, loops=134,chars=115,blocks 0/0 (0) contexts 0/0 (0) scancache 8284
memory scancache 8896(208Kb+347Kb) found 4361(136Kb) fcontext 1647(38Kb) = 730Kb
average 677503 chars/s 3157 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 251 (0 ms): 0, 0, 0, 0; from 66413-66529, loops=135,chars=116,blocks 0/0 (0) contexts 0/0 (0) scancache 8284
memory scancache 8896(208Kb+347Kb) found 4361(136Kb) fcontext 1647(38Kb) = 730Kb
average 677602 chars/s 3145 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 252 (0 ms): 0, 0, 0, 0; from 66413-66530, loops=136,chars=117,blocks 0/0 (0) contexts 0/0 (0) scancache 8284
memory scancache 8896(208Kb+347Kb) found 4361(136Kb) fcontext 1647(38Kb) = 730Kb
average 677703 chars/s 3133 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 253 (0 ms): 0, 0, 0, 0; from 66826-66922, loops=112,chars=96,blocks 1/2 (0) contexts 1/2 (0) scancache 8286
memory scancache 8898(208Kb+347Kb) found 4362(136Kb) fcontext 1648(38Kb) = 731Kb
average 677785 chars/s 3121 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 254 (0 ms): 0, 0, 0, 0; from 66826-66923, loops=113,chars=97,blocks 0/0 (0) contexts 0/0 (0) scancache 8286
memory scancache 8898(208Kb+347Kb) found 4362(136Kb) fcontext 1648(38Kb) = 731Kb
average 677868 chars/s 3109 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 255 (0 ms): 0, 0, 0, 0; from 66850-66924, loops=86,chars=74,blocks 0/0 (0) contexts 0/0 (0) scancache 8286
memory scancache 8898(208Kb+347Kb) found 4362(136Kb) fcontext 1648(38Kb) = 731Kb
average 677932 chars/s 3097 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 256 (0 ms): 0, 0, 0, 0; from 66850-66925, loops=87,chars=75,blocks 0/0 (0) contexts 0/0 (0) scancache 8286
memory scancache 8898(208Kb+347Kb) found 4362(136Kb) fcontext 1648(38Kb) = 731Kb
average 677996 chars/s 3085 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 257 (0 ms): 0, 0, 0, 0; from 66850-66926, loops=88,chars=76,blocks 0/0 (0) contexts 0/0 (0) scancache 8286
memory scancache 8898(208Kb+347Kb) found 4362(136Kb) fcontext 1648(38Kb) = 731Kb
average 678061 chars/s 3073 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 258 (0 ms): 0, 0, 0, 0; from 66850-66927, loops=89,chars=77,blocks 0/0 (0) contexts 0/0 (0) scancache 8286
memory scancache 8898(208Kb+347Kb) found 4362(136Kb) fcontext 1648(38Kb) = 731Kb
average 678127 chars/s 3062 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 259 (0 ms): 0, 0, 0, 0; from 66850-66928, loops=90,chars=78,blocks 0/0 (0) contexts 0/0 (0) scancache 8286
memory scancache 8898(208Kb+347Kb) found 4362(136Kb) fcontext 1648(38Kb) = 731Kb
average 678194 chars/s 3050 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 260 (0 ms): 0, 0, 0, 0; from 66850-66929, loops=91,chars=79,blocks 0/0 (0) contexts 0/0 (0) scancache 8286
memory scancache 8898(208Kb+347Kb) found 4362(136Kb) fcontext 1648(38Kb) = 731Kb
average 678262 chars/s 3039 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 261 (0 ms): 0, 0, 0, 0; from 66850-66930, loops=92,chars=80,blocks 0/0 (0) contexts 0/0 (0) scancache 8286
memory scancache 8898(208Kb+347Kb) found 4362(136Kb) fcontext 1648(38Kb) = 731Kb
average 678331 chars/s 3027 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 262 (0 ms): 0, 0, 0, 0; from 66850-66931, loops=93,chars=81,blocks 0/0 (0) contexts 0/0 (0) scancache 8286
memory scancache 8898(208Kb+347Kb) found 4362(136Kb) fcontext 1648(38Kb) = 731Kb
average 678400 chars/s 3016 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 263 (41 ms): 0, 0, 0, 41; from 66850-91560, loops=29988,chars=24710,blocks 1193/1197 (0) contexts 374/375 (0) scancache 8287
memory scancache 8899(208Kb+347Kb) found 4363(136Kb) fcontext 1648(38Kb) = 731Kb
average 675826 chars/s 3099 chars/run
scancache integrity check done in 1,140999 ms.
scanning run 264 (27 ms): 0, 0, 0, 27; from 66850-91561, loops=27854,chars=24711,blocks 696/698 (0) contexts 270/271 (0) scancache 7254
memory scancache 7866(184Kb+307Kb) found 3867(120Kb) fcontext 1544(36Kb) = 648Kb
average 681068 chars/s 3180 chars/run
scancache integrity check done in 1,018000 ms.
scanning run 265 (39 ms): 0, 0, 0, 39; from 66861-91562, loops=29976,chars=24701,blocks 1192/1198 (0) contexts 374/376 (0) scancache 8289
memory scancache 8901(208Kb+347Kb) found 4364(136Kb) fcontext 1649(38Kb) = 731Kb
average 679606 chars/s 3262 chars/run
scancache integrity check done in 1,159002 ms.
scanning run 266 (40 ms): 0, 0, 0, 40; from 66861-91563, loops=29978,chars=24702,blocks 1192/1198 (0) contexts 374/375 (0) scancache 8290
memory scancache 8902(208Kb+347Kb) found 4364(136Kb) fcontext 1649(38Kb) = 731Kb
average 677714 chars/s 3342 chars/run
scancache integrity check done in 1,103002 ms.
scanning run 267 (0 ms): 0, 0, 0, 0; from 66918-66936, loops=29,chars=18,blocks 0/0 (0) contexts 0/0 (0) scancache 8290
memory scancache 8902(208Kb+347Kb) found 4364(136Kb) fcontext 1649(38Kb) = 731Kb
average 677727 chars/s 3330 chars/run
Nothing to scan anymore, total run timer took 5414 ms
scanning run 268 (0 ms): 0, 0, 0, 0; from 66826-66893, loops=89,chars=67,blocks 0/0 (0) contexts 0/0 (0) scancache 8290
memory scancache 8902(208Kb+347Kb) found 4364(136Kb) fcontext 1649(38Kb) = 731Kb
average 677778 chars/s 3318 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 269 (0 ms): 0, 0, 0, 0; from 67647-67714, loops=89,chars=67,blocks 3/4 (0) contexts 2/3 (0) scancache 8296
memory scancache 8908(208Kb+347Kb) found 4367(136Kb) fcontext 1651(38Kb) = 731Kb
average 677830 chars/s 3305 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 270 (40 ms): 0, 0, 0, 40; from 68822-91469, loops=27549,chars=22647,blocks 1124/1128 (0) contexts 350/352 (0) scancache 8260
memory scancache 8872(207Kb+346Kb) found 4351(135Kb) fcontext 1650(38Kb) = 729Kb
average 674526 chars/s 3377 chars/run
scancache integrity check done in 1,186998 ms.
scanning run 271 (39 ms): 0, 0, 0, 39; from 68822-91470, loops=27556,chars=22648,blocks 1141/1146 (0) contexts 352/353 (0) scancache 8298
memory scancache 8910(208Kb+348Kb) found 4368(136Kb) fcontext 1652(38Kb) = 732Kb
average 671896 chars/s 3448 chars/run
scancache integrity check done in 1,157999 ms.
scanning run 272 (0 ms): 0, 0, 0, 0; from 68822-68964, loops=169,chars=142,blocks 0/0 (0) contexts 0/0 (0) scancache 8298
memory scancache 8910(208Kb+348Kb) found 4368(136Kb) fcontext 1652(38Kb) = 732Kb
average 671998 chars/s 3436 chars/run
Nothing to scan anymore, total run timer took 614 ms
scanning run 273 (0 ms): 0, 0, 0, 0; from 68947-68965, loops=24,chars=18,blocks 0/0 (0) contexts 0/0 (0) scancache 8298
memory scancache 8910(208Kb+348Kb) found 4368(136Kb) fcontext 1652(38Kb) = 732Kb
average 672011 chars/s 3424 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 274 (0 ms): 0, 0, 0, 0; from 68947-68966, loops=27,chars=19,blocks 0/0 (0) contexts 0/0 (0) scancache 8298
memory scancache 8910(208Kb+348Kb) found 4368(136Kb) fcontext 1652(38Kb) = 732Kb
average 672025 chars/s 3411 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 275 (0 ms): 0, 0, 0, 0; from 68947-68967, loops=28,chars=20,blocks 0/0 (0) contexts 0/0 (0) scancache 8298
memory scancache 8910(208Kb+348Kb) found 4368(136Kb) fcontext 1652(38Kb) = 732Kb
average 672039 chars/s 3399 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 276 (0 ms): 0, 0, 0, 0; from 68947-68968, loops=29,chars=21,blocks 0/0 (0) contexts 0/0 (0) scancache 8298
memory scancache 8910(208Kb+348Kb) found 4368(136Kb) fcontext 1652(38Kb) = 732Kb
average 672054 chars/s 3387 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 277 (0 ms): 0, 0, 0, 0; from 68947-68969, loops=30,chars=22,blocks 0/0 (0) contexts 0/0 (0) scancache 8298
memory scancache 8910(208Kb+348Kb) found 4368(136Kb) fcontext 1652(38Kb) = 732Kb
average 672070 chars/s 3374 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 278 (0 ms): 0, 0, 0, 0; from 68947-68970, loops=31,chars=23,blocks 0/0 (0) contexts 0/0 (0) scancache 8298
memory scancache 8910(208Kb+348Kb) found 4368(136Kb) fcontext 1652(38Kb) = 732Kb
average 672086 chars/s 3362 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 279 (0 ms): 0, 0, 0, 0; from 68947-68971, loops=32,chars=24,blocks 0/0 (0) contexts 0/0 (0) scancache 8298
memory scancache 8910(208Kb+348Kb) found 4368(136Kb) fcontext 1652(38Kb) = 732Kb
average 672104 chars/s 3350 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 280 (0 ms): 0, 0, 0, 0; from 68947-68972, loops=33,chars=25,blocks 0/0 (0) contexts 0/0 (0) scancache 8298
memory scancache 8910(208Kb+348Kb) found 4368(136Kb) fcontext 1652(38Kb) = 732Kb
average 672122 chars/s 3339 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 281 (0 ms): 0, 0, 0, 0; from 68822-68971, loops=178,chars=149,blocks 0/0 (0) contexts 0/0 (0) scancache 8298
memory scancache 8910(208Kb+348Kb) found 4368(136Kb) fcontext 1652(38Kb) = 732Kb
average 672229 chars/s 3327 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 282 (0 ms): 0, 0, 0, 0; from 68822-68970, loops=177,chars=148,blocks 0/0 (0) contexts 0/0 (0) scancache 8298
memory scancache 8910(208Kb+348Kb) found 4368(136Kb) fcontext 1652(38Kb) = 732Kb
average 672335 chars/s 3316 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 283 (0 ms): 0, 0, 0, 0; from 68822-68969, loops=176,chars=147,blocks 0/0 (0) contexts 0/0 (0) scancache 8298
memory scancache 8910(208Kb+348Kb) found 4368(136Kb) fcontext 1652(38Kb) = 732Kb
average 672441 chars/s 3305 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 284 (0 ms): 0, 0, 0, 0; from 68822-68968, loops=175,chars=146,blocks 0/0 (0) contexts 0/0 (0) scancache 8298
memory scancache 8910(208Kb+348Kb) found 4368(136Kb) fcontext 1652(38Kb) = 732Kb
average 672546 chars/s 3294 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 285 (0 ms): 0, 0, 0, 0; from 68947-68969, loops=30,chars=22,blocks 0/0 (0) contexts 0/0 (0) scancache 8298
memory scancache 8910(208Kb+348Kb) found 4368(136Kb) fcontext 1652(38Kb) = 732Kb
average 672562 chars/s 3282 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 286 (0 ms): 0, 0, 0, 0; from 68947-68970, loops=31,chars=23,blocks 0/0 (0) contexts 0/0 (0) scancache 8298
memory scancache 8910(208Kb+348Kb) found 4368(136Kb) fcontext 1652(38Kb) = 732Kb
average 672578 chars/s 3271 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 287 (0 ms): 0, 0, 0, 0; from 68947-68971, loops=32,chars=24,blocks 0/0 (0) contexts 0/0 (0) scancache 8298
memory scancache 8910(208Kb+348Kb) found 4368(136Kb) fcontext 1652(38Kb) = 732Kb
average 672595 chars/s 3259 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 288 (0 ms): 0, 0, 0, 0; from 68947-68972, loops=33,chars=25,blocks 0/0 (0) contexts 0/0 (0) scancache 8298
memory scancache 8910(208Kb+348Kb) found 4368(136Kb) fcontext 1652(38Kb) = 732Kb
average 672613 chars/s 3248 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 289 (0 ms): 0, 0, 0, 0; from 68947-68973, loops=34,chars=26,blocks 0/0 (0) contexts 0/0 (0) scancache 8298
memory scancache 8910(208Kb+348Kb) found 4368(136Kb) fcontext 1652(38Kb) = 732Kb
average 672632 chars/s 3237 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 290 (39 ms): 0, 0, 0, 39; from 68947-91481, loops=27425,chars=22534,blocks 1142/1146 (0) contexts 352/353 (0) scancache 8299
memory scancache 8911(208Kb+348Kb) found 4369(136Kb) fcontext 1652(38Kb) = 732Kb
average 670046 chars/s 3304 chars/run
scancache integrity check done in 1,128000 ms.
scanning run 291 (40 ms): 0, 0, 0, 40; from 68947-91482, loops=27427,chars=22535,blocks 1141/1147 (0) contexts 352/353 (0) scancache 8300
memory scancache 8912(208Kb+348Kb) found 4369(136Kb) fcontext 1652(38Kb) = 732Kb
average 667143 chars/s 3370 chars/run
scancache integrity check done in 1,099000 ms.
scanning run 292 (38 ms): 0, 0, 0, 38; from 68947-91483, loops=27423,chars=22536,blocks 1125/1128 (0) contexts 351/352 (0) scancache 8263
memory scancache 8875(208Kb+346Kb) found 4353(136Kb) fcontext 1651(38Kb) = 729Kb
average 665276 chars/s 3435 chars/run
scancache integrity check done in 1,144999 ms.
scanning run 293 (39 ms): 0, 0, 0, 39; from 68957-91484, loops=27418,chars=22527,blocks 1141/1148 (0) contexts 352/354 (0) scancache 8302
memory scancache 8914(208Kb+348Kb) found 4370(136Kb) fcontext 1653(38Kb) = 732Kb
average 663066 chars/s 3500 chars/run
scancache integrity check done in 1,145001 ms.
scanning run 294 (0 ms): 0, 0, 0, 0; from 68957-68978, loops=31,chars=21,blocks 0/0 (0) contexts 0/0 (0) scancache 8302
memory scancache 8914(208Kb+348Kb) found 4370(136Kb) fcontext 1653(38Kb) = 732Kb
average 663080 chars/s 3489 chars/run
Nothing to scan anymore, total run timer took 1133 ms
scanning run 295 (0 ms): 0, 0, 0, 0; from 68958-68979, loops=30,chars=21,blocks 0/0 (0) contexts 0/0 (0) scancache 8302
memory scancache 8914(208Kb+348Kb) found 4370(136Kb) fcontext 1653(38Kb) = 732Kb
average 663093 chars/s 3477 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 296 (0 ms): 0, 0, 0, 0; from 68958-68980, loops=31,chars=22,blocks 0/0 (0) contexts 0/0 (0) scancache 8302
memory scancache 8914(208Kb+348Kb) found 4370(136Kb) fcontext 1653(38Kb) = 732Kb
average 663107 chars/s 3465 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 297 (0 ms): 0, 0, 0, 0; from 68958-68981, loops=32,chars=23,blocks 0/0 (0) contexts 0/0 (0) scancache 8302
memory scancache 8914(208Kb+348Kb) found 4370(136Kb) fcontext 1653(38Kb) = 732Kb
average 663122 chars/s 3454 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 298 (0 ms): 0, 0, 0, 0; from 68958-68982, loops=33,chars=24,blocks 0/0 (0) contexts 0/0 (0) scancache 8302
memory scancache 8914(208Kb+348Kb) found 4370(136Kb) fcontext 1653(38Kb) = 732Kb
average 663138 chars/s 3442 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 299 (0 ms): 0, 0, 0, 0; from 68958-68983, loops=34,chars=25,blocks 0/0 (0) contexts 0/0 (0) scancache 8302
memory scancache 8914(208Kb+348Kb) found 4370(136Kb) fcontext 1653(38Kb) = 732Kb
average 663154 chars/s 3431 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 300 (0 ms): 0, 0, 0, 0; from 68958-68984, loops=35,chars=26,blocks 0/0 (0) contexts 0/0 (0) scancache 8302
memory scancache 8914(208Kb+348Kb) found 4370(136Kb) fcontext 1653(38Kb) = 732Kb
average 663171 chars/s 3419 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 301 (0 ms): 0, 0, 0, 0; from 68958-68985, loops=36,chars=27,blocks 0/0 (0) contexts 0/0 (0) scancache 8302
memory scancache 8914(208Kb+348Kb) found 4370(136Kb) fcontext 1653(38Kb) = 732Kb
average 663188 chars/s 3408 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 302 (0 ms): 0, 0, 0, 0; from 68958-68986, loops=37,chars=28,blocks 0/0 (0) contexts 0/0 (0) scancache 8302
memory scancache 8914(208Kb+348Kb) found 4370(136Kb) fcontext 1653(38Kb) = 732Kb
average 663206 chars/s 3397 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 303 (0 ms): 0, 0, 0, 0; from 68958-68987, loops=38,chars=29,blocks 0/0 (0) contexts 0/0 (0) scancache 8302
memory scancache 8914(208Kb+348Kb) found 4370(136Kb) fcontext 1653(38Kb) = 732Kb
average 663225 chars/s 3386 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 304 (0 ms): 0, 0, 0, 0; from 68958-68988, loops=39,chars=30,blocks 0/0 (0) contexts 0/0 (0) scancache 8302
memory scancache 8914(208Kb+348Kb) found 4370(136Kb) fcontext 1653(38Kb) = 732Kb
average 663244 chars/s 3375 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 305 (0 ms): 0, 0, 0, 0; from 4328-4331, loops=4,chars=3,blocks 0/0 (0) contexts 0/0 (0) scancache 244
memory scancache 8914(208Kb+348Kb) found 4370(136Kb) fcontext 1653(38Kb) = 732Kb
average 663246 chars/s 3364 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 306 (0 ms): 0, 0, 0, 0; from 4330-4333, loops=5,chars=3,blocks 0/0 (0) contexts 0/0 (0) scancache 244
memory scancache 8914(208Kb+348Kb) found 4370(136Kb) fcontext 1653(38Kb) = 732Kb
average 663248 chars/s 3353 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 307 (0 ms): 0, 0, 0, 0; from 4330-4334, loops=6,chars=4,blocks 0/0 (0) contexts 0/0 (0) scancache 244
memory scancache 8914(208Kb+348Kb) found 4370(136Kb) fcontext 1653(38Kb) = 732Kb
average 663251 chars/s 3342 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 308 (0 ms): 0, 0, 0, 0; from 4330-4335, loops=7,chars=5,blocks 0/0 (0) contexts 0/0 (0) scancache 244
memory scancache 8914(208Kb+348Kb) found 4370(136Kb) fcontext 1653(38Kb) = 732Kb
average 663254 chars/s 3331 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 309 (0 ms): 0, 0, 0, 0; from 4330-4336, loops=8,chars=6,blocks 0/0 (0) contexts 0/0 (0) scancache 244
memory scancache 8914(208Kb+348Kb) found 4370(136Kb) fcontext 1653(38Kb) = 732Kb
average 663258 chars/s 3320 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 310 (0 ms): 0, 0, 0, 0; from 4330-4337, loops=9,chars=7,blocks 0/0 (0) contexts 0/0 (0) scancache 244
memory scancache 8914(208Kb+348Kb) found 4370(136Kb) fcontext 1653(38Kb) = 732Kb
average 663263 chars/s 3309 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 311 (0 ms): 0, 0, 0, 0; from 4330-4338, loops=10,chars=8,blocks 0/0 (0) contexts 0/0 (0) scancache 244
memory scancache 8914(208Kb+348Kb) found 4370(136Kb) fcontext 1653(38Kb) = 732Kb
average 663268 chars/s 3299 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 312 (0 ms): 0, 0, 0, 0; from 4330-4339, loops=11,chars=9,blocks 0/0 (0) contexts 0/0 (0) scancache 244
memory scancache 8914(208Kb+348Kb) found 4370(136Kb) fcontext 1653(38Kb) = 732Kb
average 663274 chars/s 3288 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 313 (0 ms): 0, 0, 0, 0; from 4330-4340, loops=12,chars=10,blocks 0/0 (0) contexts 0/0 (0) scancache 244
memory scancache 8914(208Kb+348Kb) found 4370(136Kb) fcontext 1653(38Kb) = 732Kb
average 663280 chars/s 3278 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 314 (0 ms): 0, 0, 0, 0; from 4330-4341, loops=13,chars=11,blocks 0/0 (0) contexts 0/0 (0) scancache 244
memory scancache 8914(208Kb+348Kb) found 4370(136Kb) fcontext 1653(38Kb) = 732Kb
average 663287 chars/s 3267 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 315 (0 ms): 0, 0, 0, 0; from 4330-4342, loops=14,chars=12,blocks 0/0 (0) contexts 0/0 (0) scancache 244
memory scancache 8914(208Kb+348Kb) found 4370(136Kb) fcontext 1653(38Kb) = 732Kb
average 663295 chars/s 3257 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 316 (0 ms): 0, 0, 0, 0; from 4330-4343, loops=15,chars=13,blocks 0/0 (0) contexts 0/0 (0) scancache 244
memory scancache 8914(208Kb+348Kb) found 4370(136Kb) fcontext 1653(38Kb) = 732Kb
average 663303 chars/s 3247 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 317 (0 ms): 0, 0, 0, 0; from 4330-4344, loops=16,chars=14,blocks 0/0 (0) contexts 0/0 (0) scancache 244
memory scancache 8914(208Kb+348Kb) found 4370(136Kb) fcontext 1653(38Kb) = 732Kb
average 663312 chars/s 3237 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 318 (0 ms): 0, 0, 0, 0; from 4330-4345, loops=17,chars=15,blocks 0/0 (0) contexts 0/0 (0) scancache 244
memory scancache 8914(208Kb+348Kb) found 4370(136Kb) fcontext 1653(38Kb) = 732Kb
average 663322 chars/s 3226 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 319 (0 ms): 0, 0, 0, 0; from 4330-4346, loops=18,chars=16,blocks 0/0 (0) contexts 0/0 (0) scancache 244
memory scancache 8914(208Kb+348Kb) found 4370(136Kb) fcontext 1653(38Kb) = 732Kb
average 663332 chars/s 3216 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 320 (0 ms): 0, 0, 0, 0; from 4330-4347, loops=19,chars=17,blocks 0/0 (0) contexts 0/0 (0) scancache 244
memory scancache 8914(208Kb+348Kb) found 4370(136Kb) fcontext 1653(38Kb) = 732Kb
average 663343 chars/s 3206 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 321 (0 ms): 0, 0, 0, 0; from 4330-4348, loops=20,chars=18,blocks 0/0 (0) contexts 0/0 (0) scancache 244
memory scancache 8914(208Kb+348Kb) found 4370(136Kb) fcontext 1653(38Kb) = 732Kb
average 663355 chars/s 3196 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 322 (0 ms): 0, 0, 0, 0; from 4330-4351, loops=25,chars=21,blocks 1/0 (0) contexts 1/0 (0) scancache 244
memory scancache 8914(208Kb+348Kb) found 4371(136Kb) fcontext 1654(38Kb) = 732Kb
average 663369 chars/s 3187 chars/run
scancache integrity check done in 0,091000 ms.
scanning run 323 (0 ms): 0, 0, 0, 0; from 4330-4352, loops=26,chars=22,blocks 0/2 (0) contexts 0/2 (0) scancache 246
memory scancache 8916(208Kb+348Kb) found 4371(136Kb) fcontext 1654(38Kb) = 732Kb
average 663383 chars/s 3177 chars/run
scancache integrity check done in 0,096000 ms.
scanning run 324 (0 ms): 0, 0, 0, 0; from 4348-4351, loops=5,chars=3,blocks 0/0 (0) contexts 0/0 (0) scancache 246
memory scancache 8916(208Kb+348Kb) found 4371(136Kb) fcontext 1654(38Kb) = 732Kb
average 663385 chars/s 3167 chars/run
Nothing to scan anymore, total run timer took 793 ms
scanning run 325 (6 ms): 0, 0, 0, 6; from 88437-91173, loops=3449,chars=2736,blocks 151/154 (0) contexts 92/93 (0) scancache 8227
memory scancache 8841(207Kb+345Kb) found 4333(135Kb) fcontext 1653(38Kb) = 726Kb
average 662584 chars/s 3166 chars/run
scancache integrity check done in 1,222000 ms.
scanning run 326 (7 ms): 0, 0, 0, 7; from 88817-91174, loops=3078,chars=2357,blocks 189/191 (0) contexts 93/94 (0) scancache 8302
memory scancache 8916(208Kb+348Kb) found 4371(136Kb) fcontext 1654(38Kb) = 732Kb
average 661121 chars/s 3163 chars/run
scancache integrity check done in 1,236000 ms.
scanning run 327 (0 ms): 0, 0, 0, 0; from 88817-88917, loops=123,chars=100,blocks 0/0 (0) contexts 0/0 (0) scancache 8302
memory scancache 8916(208Kb+348Kb) found 4371(136Kb) fcontext 1654(38Kb) = 732Kb
average 661185 chars/s 3154 chars/run
Nothing to scan anymore, total run timer took 2403 ms
scanning run 328 (0 ms): 0, 0, 0, 0; from 88817-88918, loops=124,chars=101,blocks 0/0 (0) contexts 0/0 (0) scancache 8302
memory scancache 8916(208Kb+348Kb) found 4371(136Kb) fcontext 1654(38Kb) = 732Kb
average 661250 chars/s 3144 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 329 (0 ms): 0, 0, 0, 0; from 88817-88919, loops=125,chars=102,blocks 0/0 (0) contexts 0/0 (0) scancache 8302
memory scancache 8916(208Kb+348Kb) found 4371(136Kb) fcontext 1654(38Kb) = 732Kb
average 661316 chars/s 3135 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 330 (0 ms): 0, 0, 0, 0; from 88817-88920, loops=126,chars=103,blocks 0/0 (0) contexts 0/0 (0) scancache 8302
memory scancache 8916(208Kb+348Kb) found 4371(136Kb) fcontext 1654(38Kb) = 732Kb
average 661382 chars/s 3126 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 331 (0 ms): 0, 0, 0, 0; from 88817-88921, loops=127,chars=104,blocks 0/0 (0) contexts 0/0 (0) scancache 8302
memory scancache 8916(208Kb+348Kb) found 4371(136Kb) fcontext 1654(38Kb) = 732Kb
average 661448 chars/s 3117 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 332 (0 ms): 0, 0, 0, 0; from 88817-88922, loops=128,chars=105,blocks 0/0 (0) contexts 0/0 (0) scancache 8302
memory scancache 8916(208Kb+348Kb) found 4371(136Kb) fcontext 1654(38Kb) = 732Kb
average 661516 chars/s 3108 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 333 (0 ms): 0, 0, 0, 0; from 88817-88923, loops=129,chars=106,blocks 0/0 (0) contexts 0/0 (0) scancache 8302
memory scancache 8916(208Kb+348Kb) found 4371(136Kb) fcontext 1654(38Kb) = 732Kb
average 661583 chars/s 3099 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 334 (0 ms): 0, 0, 0, 0; from 88817-88924, loops=130,chars=107,blocks 0/0 (0) contexts 0/0 (0) scancache 8302
memory scancache 8916(208Kb+348Kb) found 4371(136Kb) fcontext 1654(38Kb) = 732Kb
average 661652 chars/s 3090 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 335 (6 ms): 0, 0, 0, 6; from 88817-91183, loops=3089,chars=2366,blocks 190/191 (0) contexts 93/94 (0) scancache 8303
memory scancache 8917(208Kb+348Kb) found 4372(136Kb) fcontext 1654(38Kb) = 732Kb
average 660628 chars/s 3088 chars/run
scancache integrity check done in 1,242000 ms.
scanning run 336 (6 ms): 0, 0, 0, 6; from 88817-91184, loops=3091,chars=2367,blocks 189/192 (0) contexts 93/94 (0) scancache 8304
memory scancache 8918(209Kb+348Kb) found 4372(136Kb) fcontext 1654(38Kb) = 732Kb
average 659612 chars/s 3086 chars/run
scancache integrity check done in 1,246000 ms.
scanning run 337 (5 ms): 0, 0, 0, 5; from 88817-91185, loops=3027,chars=2368,blocks 152/155 (0) contexts 93/94 (0) scancache 8230
memory scancache 8844(207Kb+345Kb) found 4335(135Kb) fcontext 1654(38Kb) = 726Kb
average 659022 chars/s 3083 chars/run
scancache integrity check done in 1,253000 ms.
scanning run 338 (6 ms): 0, 0, 0, 6; from 88841-91186, loops=3067,chars=2345,blocks 189/193 (0) contexts 93/95 (0) scancache 8306
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 658006 chars/s 3081 chars/run
scancache integrity check done in 1,263000 ms.
scanning run 339 (0 ms): 0, 0, 0, 0; from 88841-88929, loops=112,chars=88,blocks 0/0 (0) contexts 0/0 (0) scancache 8306
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 658061 chars/s 3072 chars/run
Nothing to scan anymore, total run timer took 1357 ms
scanning run 340 (0 ms): 0, 0, 0, 0; from 88842-88930, loops=111,chars=88,blocks 0/0 (0) contexts 0/0 (0) scancache 8306
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 658117 chars/s 3064 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 341 (0 ms): 0, 0, 0, 0; from 88842-88931, loops=112,chars=89,blocks 0/0 (0) contexts 0/0 (0) scancache 8306
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 658173 chars/s 3055 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 342 (0 ms): 0, 0, 0, 0; from 88842-88932, loops=113,chars=90,blocks 0/0 (0) contexts 0/0 (0) scancache 8306
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 658230 chars/s 3046 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 343 (0 ms): 0, 0, 0, 0; from 88842-88933, loops=114,chars=91,blocks 0/0 (0) contexts 0/0 (0) scancache 8306
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 658288 chars/s 3038 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 344 (0 ms): 0, 0, 0, 0; from 88842-88934, loops=115,chars=92,blocks 0/0 (0) contexts 0/0 (0) scancache 8306
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 658346 chars/s 3029 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 345 (0 ms): 0, 0, 0, 0; from 88842-88935, loops=116,chars=93,blocks 0/0 (0) contexts 0/0 (0) scancache 8306
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 658404 chars/s 3021 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 346 (0 ms): 0, 0, 0, 0; from 88842-88936, loops=117,chars=94,blocks 0/0 (0) contexts 0/0 (0) scancache 8306
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 658464 chars/s 3012 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 347 (0 ms): 0, 0, 0, 0; from 88842-88937, loops=118,chars=95,blocks 0/0 (0) contexts 0/0 (0) scancache 8306
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 658524 chars/s 3004 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 348 (0 ms): 0, 0, 0, 0; from 88842-88938, loops=119,chars=96,blocks 0/0 (0) contexts 0/0 (0) scancache 8306
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 658584 chars/s 2995 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 349 (0 ms): 0, 0, 0, 0; from 88842-88939, loops=120,chars=97,blocks 0/0 (0) contexts 0/0 (0) scancache 8306
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 658646 chars/s 2987 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 350 (0 ms): 0, 0, 0, 0; from 88854-88940, loops=108,chars=86,blocks 0/0 (0) contexts 0/0 (0) scancache 8306
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 658700 chars/s 2979 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 351 (0 ms): 0, 0, 0, 0; from 88842-88941, loops=123,chars=99,blocks 0/0 (0) contexts 0/0 (0) scancache 8306
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 658763 chars/s 2971 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 352 (0 ms): 0, 0, 0, 0; from 88842-88942, loops=124,chars=100,blocks 0/0 (0) contexts 0/0 (0) scancache 8306
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 658826 chars/s 2962 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 353 (0 ms): 0, 0, 0, 0; from 4330-4675, loops=411,chars=345,blocks 1/1 (0) contexts 1/1 (0) scancache 246
memory scancache 8920(209Kb+348Kb) found 4374(136Kb) fcontext 1656(38Kb) = 733Kb
average 659044 chars/s 2955 chars/run
scancache integrity check done in 0,108000 ms.
scanning run 354 (0 ms): 0, 0, 0, 0; from 4330-4674, loops=410,chars=344,blocks 0/2 (0) contexts 0/2 (0) scancache 246
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 659261 chars/s 2948 chars/run
scancache integrity check done in 0,088000 ms.
scanning run 355 (0 ms): 0, 0, 0, 0; from 4670-4672, loops=3,chars=2,blocks 0/0 (0) contexts 0/0 (0) scancache 246
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 659262 chars/s 2939 chars/run
Nothing to scan anymore, total run timer took 10167 ms
scanning run 356 (0 ms): 0, 0, 0, 0; from 4670-4673, loops=4,chars=3,blocks 0/0 (0) contexts 0/0 (0) scancache 246
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 659264 chars/s 2931 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 357 (0 ms): 0, 0, 0, 0; from 4670-4675, loops=6,chars=5,blocks 0/0 (0) contexts 0/0 (0) scancache 246
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 659267 chars/s 2923 chars/run
scancache integrity check done in 0,083000 ms.
scanning run 358 (0 ms): 0, 0, 0, 0; from 4670-4673, loops=4,chars=3,blocks 0/0 (0) contexts 0/0 (0) scancache 246
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 659269 chars/s 2915 chars/run
Nothing to scan anymore, total run timer took 633 ms
scanning run 359 (0 ms): 0, 0, 0, 0; from 4672-4675, loops=5,chars=3,blocks 0/0 (0) contexts 0/0 (0) scancache 246
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 659271 chars/s 2907 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 360 (0 ms): 0, 0, 0, 0; from 4672-4676, loops=6,chars=4,blocks 0/0 (0) contexts 0/0 (0) scancache 246
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 659274 chars/s 2898 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 361 (0 ms): 0, 0, 0, 0; from 4672-4677, loops=7,chars=5,blocks 0/0 (0) contexts 0/0 (0) scancache 246
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 659277 chars/s 2890 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 362 (0 ms): 0, 0, 0, 0; from 4672-4678, loops=8,chars=6,blocks 0/0 (0) contexts 0/0 (0) scancache 246
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 659281 chars/s 2882 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 363 (0 ms): 0, 0, 0, 0; from 4672-4679, loops=9,chars=7,blocks 0/0 (0) contexts 0/0 (0) scancache 246
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 659285 chars/s 2875 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 364 (0 ms): 0, 0, 0, 0; from 4672-4680, loops=10,chars=8,blocks 0/0 (0) contexts 0/0 (0) scancache 246
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 659290 chars/s 2867 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 365 (0 ms): 0, 0, 0, 0; from 4672-4681, loops=11,chars=9,blocks 0/0 (0) contexts 0/0 (0) scancache 246
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 659296 chars/s 2859 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 366 (0 ms): 0, 0, 0, 0; from 4672-4682, loops=12,chars=10,blocks 0/0 (0) contexts 0/0 (0) scancache 246
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 659302 chars/s 2851 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 367 (0 ms): 0, 0, 0, 0; from 4672-4683, loops=13,chars=11,blocks 0/0 (0) contexts 0/0 (0) scancache 246
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 659309 chars/s 2843 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 368 (0 ms): 0, 0, 0, 0; from 4672-4684, loops=14,chars=12,blocks 0/0 (0) contexts 0/0 (0) scancache 246
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 659317 chars/s 2836 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 369 (0 ms): 0, 0, 0, 0; from 4672-4685, loops=15,chars=13,blocks 0/0 (0) contexts 0/0 (0) scancache 246
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 659325 chars/s 2828 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 370 (0 ms): 0, 0, 0, 0; from 4672-4686, loops=16,chars=14,blocks 0/0 (0) contexts 0/0 (0) scancache 246
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 659334 chars/s 2820 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 371 (0 ms): 0, 0, 0, 0; from 4672-4687, loops=17,chars=15,blocks 0/0 (0) contexts 0/0 (0) scancache 246
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 659343 chars/s 2813 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 372 (0 ms): 0, 0, 0, 0; from 4574-4686, loops=133,chars=112,blocks 0/0 (0) contexts 0/0 (0) scancache 246
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 659414 chars/s 2806 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 373 (0 ms): 0, 0, 0, 0; from 4670-4672, loops=3,chars=2,blocks 0/0 (0) contexts 0/0 (0) scancache 246
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 659415 chars/s 2798 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 374 (0 ms): 0, 0, 0, 0; from 4670-4685, loops=16,chars=15,blocks 0/0 (0) contexts 0/0 (0) scancache 246
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 659425 chars/s 2791 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 375 (0 ms): 0, 0, 0, 0; from 4670-4684, loops=15,chars=14,blocks 0/0 (0) contexts 0/0 (0) scancache 246
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 659433 chars/s 2783 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 376 (0 ms): 0, 0, 0, 0; from 4672-4686, loops=16,chars=14,blocks 0/0 (0) contexts 0/0 (0) scancache 246
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 659442 chars/s 2776 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 377 (0 ms): 0, 0, 0, 0; from 4672-4687, loops=17,chars=15,blocks 0/0 (0) contexts 0/0 (0) scancache 246
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 659452 chars/s 2769 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 378 (0 ms): 0, 0, 0, 0; from 4672-4688, loops=18,chars=16,blocks 0/0 (0) contexts 0/0 (0) scancache 246
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 659462 chars/s 2761 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 379 (0 ms): 0, 0, 0, 0; from 4672-4689, loops=19,chars=17,blocks 0/0 (0) contexts 0/0 (0) scancache 246
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 659473 chars/s 2754 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 380 (0 ms): 0, 0, 0, 0; from 4672-4690, loops=20,chars=18,blocks 0/0 (0) contexts 0/0 (0) scancache 246
memory scancache 8920(209Kb+348Kb) found 4373(136Kb) fcontext 1655(38Kb) = 732Kb
average 659484 chars/s 2747 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 381 (0 ms): 0, 0, 0, 0; from 4672-4693, loops=24,chars=21,blocks 1/0 (0) contexts 1/0 (0) scancache 246
memory scancache 8920(209Kb+348Kb) found 4374(136Kb) fcontext 1656(38Kb) = 733Kb
average 659497 chars/s 2740 chars/run
scancache integrity check done in 0,094000 ms.
scanning run 382 (0 ms): 0, 0, 0, 0; from 4672-4692, loops=23,chars=20,blocks 0/0 (0) contexts 0/0 (0) scancache 246
memory scancache 8920(209Kb+348Kb) found 4374(136Kb) fcontext 1656(38Kb) = 733Kb
average 659510 chars/s 2732 chars/run
Nothing to scan anymore, total run timer took 228 ms
scanning run 383 (0 ms): 0, 0, 0, 0; from 4690-4693, loops=4,chars=3,blocks 0/0 (0) contexts 0/0 (0) scancache 246
memory scancache 8920(209Kb+348Kb) found 4374(136Kb) fcontext 1656(38Kb) = 733Kb
average 659512 chars/s 2725 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 384 (0 ms): 0, 0, 0, 0; from 4690-4694, loops=5,chars=4,blocks 0/0 (0) contexts 0/0 (0) scancache 246
memory scancache 8920(209Kb+348Kb) found 4374(136Kb) fcontext 1656(38Kb) = 733Kb
average 659514 chars/s 2718 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 385 (0 ms): 0, 0, 0, 0; from 4672-4695, loops=27,chars=23,blocks 1/2 (0) contexts 1/2 (0) scancache 248
memory scancache 8922(209Kb+348Kb) found 4374(136Kb) fcontext 1656(38Kb) = 733Kb
average 659529 chars/s 2711 chars/run
scancache integrity check done in 0,082000 ms.
scanning run 386 (0 ms): 0, 0, 0, 0; from 4672-4694, loops=26,chars=22,blocks 0/0 (0) contexts 0/0 (0) scancache 248
memory scancache 8922(209Kb+348Kb) found 4374(136Kb) fcontext 1656(38Kb) = 733Kb
average 659543 chars/s 2704 chars/run
Nothing to scan anymore, total run timer took 161 ms
scanning run 387 (0 ms): 0, 0, 0, 0; from 88939-88945, loops=9,chars=6,blocks 0/0 (0) contexts 0/0 (0) scancache 8306
memory scancache 8922(209Kb+348Kb) found 4374(136Kb) fcontext 1656(38Kb) = 733Kb
average 659547 chars/s 2697 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 388 (0 ms): 0, 0, 0, 0; from 88939-88944, loops=8,chars=5,blocks 0/0 (0) contexts 0/0 (0) scancache 8306
memory scancache 8922(209Kb+348Kb) found 4374(136Kb) fcontext 1656(38Kb) = 733Kb
average 659550 chars/s 2690 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 389 (0 ms): 0, 0, 0, 0; from 88906-88944, loops=51,chars=38,blocks 0/0 (0) contexts 0/0 (0) scancache 8306
memory scancache 8922(209Kb+348Kb) found 4374(136Kb) fcontext 1656(38Kb) = 733Kb
average 659574 chars/s 2684 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 390 (5 ms): 0, 0, 0, 5; from 88906-91112, loops=2830,chars=2206,blocks 145/149 (0) contexts 88/90 (0) scancache 8227
memory scancache 8843(207Kb+345Kb) found 4334(135Kb) fcontext 1655(38Kb) = 726Kb
average 658886 chars/s 2682 chars/run
scancache integrity check done in 1,236000 ms.
scanning run 391 (0 ms): 0, 0, 0, 0; from 88939-88944, loops=7,chars=5,blocks 0/0 (0) contexts 0/0 (0) scancache 8227
memory scancache 8843(207Kb+345Kb) found 4334(135Kb) fcontext 1655(38Kb) = 726Kb
average 658889 chars/s 2676 chars/run
Nothing to scan anymore, total run timer took 246 ms
scanning run 392 (7 ms): 0, 0, 0, 7; from 88939-91114, loops=2861,chars=2175,blocks 185/188 (0) contexts 89/91 (0) scancache 8306
memory scancache 8922(209Kb+348Kb) found 4374(136Kb) fcontext 1656(38Kb) = 733Kb
average 657361 chars/s 2674 chars/run
scancache integrity check done in 1,313000 ms.
scanning run 393 (0 ms): 0, 0, 0, 0; from 88942-88946, loops=7,chars=4,blocks 0/0 (0) contexts 0/0 (0) scancache 8306
memory scancache 8922(209Kb+348Kb) found 4374(136Kb) fcontext 1656(38Kb) = 733Kb
average 657364 chars/s 2667 chars/run
Nothing to scan anymore, total run timer took 1423 ms
scanning run 394 (0 ms): 0, 0, 0, 0; from 88942-88947, loops=8,chars=5,blocks 0/0 (0) contexts 0/0 (0) scancache 8306
memory scancache 8922(209Kb+348Kb) found 4374(136Kb) fcontext 1656(38Kb) = 733Kb
average 657367 chars/s 2661 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 395 (0 ms): 0, 0, 0, 0; from 88942-88948, loops=9,chars=6,blocks 0/0 (0) contexts 0/0 (0) scancache 8306
memory scancache 8922(209Kb+348Kb) found 4374(136Kb) fcontext 1656(38Kb) = 733Kb
average 657371 chars/s 2654 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 396 (0 ms): 0, 0, 0, 0; from 88942-88949, loops=10,chars=7,blocks 0/0 (0) contexts 0/0 (0) scancache 8306
memory scancache 8922(209Kb+348Kb) found 4374(136Kb) fcontext 1656(38Kb) = 733Kb
average 657375 chars/s 2647 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 397 (0 ms): 0, 0, 0, 0; from 88942-88950, loops=11,chars=8,blocks 0/0 (0) contexts 0/0 (0) scancache 8306
memory scancache 8922(209Kb+348Kb) found 4374(136Kb) fcontext 1656(38Kb) = 733Kb
average 657380 chars/s 2641 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 398 (0 ms): 0, 0, 0, 0; from 88942-88951, loops=12,chars=9,blocks 0/0 (0) contexts 0/0 (0) scancache 8306
memory scancache 8922(209Kb+348Kb) found 4374(136Kb) fcontext 1656(38Kb) = 733Kb
average 657386 chars/s 2634 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 399 (0 ms): 0, 0, 0, 0; from 88942-88952, loops=13,chars=10,blocks 0/0 (0) contexts 0/0 (0) scancache 8306
memory scancache 8922(209Kb+348Kb) found 4374(136Kb) fcontext 1656(38Kb) = 733Kb
average 657392 chars/s 2627 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 400 (0 ms): 0, 0, 0, 0; from 88942-88953, loops=14,chars=11,blocks 0/0 (0) contexts 0/0 (0) scancache 8306
memory scancache 8922(209Kb+348Kb) found 4374(136Kb) fcontext 1656(38Kb) = 733Kb
average 657399 chars/s 2621 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 401 (1 ms): 0, 0, 0, 1; from 88942-89009, loops=79,chars=67,blocks 2/2 (0) contexts 0/0 (0) scancache 8307
memory scancache 8923(209Kb+348Kb) found 4375(136Kb) fcontext 1656(38Kb) = 733Kb
average 657029 chars/s 2615 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 402 (1 ms): 0, 0, 0, 1; from 88942-89010, loops=81,chars=68,blocks 1/3 (0) contexts 0/0 (0) scancache 8308
memory scancache 8924(209Kb+348Kb) found 4375(136Kb) fcontext 1656(38Kb) = 733Kb
average 656660 chars/s 2608 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 403 (5 ms): 0, 0, 0, 5; from 88942-91125, loops=2800,chars=2183,blocks 146/149 (0) contexts 89/90 (0) scancache 8230
memory scancache 8846(207Kb+345Kb) found 4336(135Kb) fcontext 1656(38Kb) = 727Kb
average 655973 chars/s 2607 chars/run
scancache integrity check done in 1,230000 ms.
scanning run 404 (7 ms): 0, 0, 0, 7; from 88952-91126, loops=2860,chars=2174,blocks 185/189 (0) contexts 89/91 (0) scancache 8310
memory scancache 8926(209Kb+348Kb) found 4376(136Kb) fcontext 1657(38Kb) = 733Kb
average 654471 chars/s 2606 chars/run
scancache integrity check done in 1,238000 ms.
scanning run 405 (0 ms): 0, 0, 0, 0; from 88952-88958, loops=11,chars=6,blocks 0/0 (0) contexts 0/0 (0) scancache 8310
memory scancache 8926(209Kb+348Kb) found 4376(136Kb) fcontext 1657(38Kb) = 733Kb
average 654474 chars/s 2600 chars/run
Nothing to scan anymore, total run timer took 534 ms
scanning run 406 (0 ms): 0, 0, 0, 0; from 88953-88959, loops=10,chars=6,blocks 0/0 (0) contexts 0/0 (0) scancache 8310
memory scancache 8926(209Kb+348Kb) found 4376(136Kb) fcontext 1657(38Kb) = 733Kb
average 654478 chars/s 2593 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 407 (0 ms): 0, 0, 0, 0; from 88953-88960, loops=11,chars=7,blocks 0/0 (0) contexts 0/0 (0) scancache 8310
memory scancache 8926(209Kb+348Kb) found 4376(136Kb) fcontext 1657(38Kb) = 733Kb
average 654482 chars/s 2587 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 408 (0 ms): 0, 0, 0, 0; from 88953-88961, loops=12,chars=8,blocks 0/0 (0) contexts 0/0 (0) scancache 8310
memory scancache 8926(209Kb+348Kb) found 4376(136Kb) fcontext 1657(38Kb) = 733Kb
average 654487 chars/s 2581 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 409 (0 ms): 0, 0, 0, 0; from 88953-88962, loops=13,chars=9,blocks 0/0 (0) contexts 0/0 (0) scancache 8310
memory scancache 8926(209Kb+348Kb) found 4376(136Kb) fcontext 1657(38Kb) = 733Kb
average 654493 chars/s 2574 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 410 (0 ms): 0, 0, 0, 0; from 88953-88963, loops=14,chars=10,blocks 0/0 (0) contexts 0/0 (0) scancache 8310
memory scancache 8926(209Kb+348Kb) found 4376(136Kb) fcontext 1657(38Kb) = 733Kb
average 654499 chars/s 2568 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 411 (0 ms): 0, 0, 0, 0; from 88953-88964, loops=15,chars=11,blocks 0/0 (0) contexts 0/0 (0) scancache 8310
memory scancache 8926(209Kb+348Kb) found 4376(136Kb) fcontext 1657(38Kb) = 733Kb
average 654506 chars/s 2562 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 412 (0 ms): 0, 0, 0, 0; from 88953-88965, loops=16,chars=12,blocks 0/0 (0) contexts 0/0 (0) scancache 8310
memory scancache 8926(209Kb+348Kb) found 4376(136Kb) fcontext 1657(38Kb) = 733Kb
average 654513 chars/s 2556 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 413 (0 ms): 0, 0, 0, 0; from 88953-88966, loops=17,chars=13,blocks 0/0 (0) contexts 0/0 (0) scancache 8310
memory scancache 8926(209Kb+348Kb) found 4376(136Kb) fcontext 1657(38Kb) = 733Kb
average 654522 chars/s 2549 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 414 (0 ms): 0, 0, 0, 0; from 88953-88967, loops=18,chars=14,blocks 0/0 (0) contexts 0/0 (0) scancache 8310
memory scancache 8926(209Kb+348Kb) found 4376(136Kb) fcontext 1657(38Kb) = 733Kb
average 654530 chars/s 2543 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 415 (0 ms): 0, 0, 0, 0; from 88953-88968, loops=19,chars=15,blocks 0/0 (0) contexts 0/0 (0) scancache 8310
memory scancache 8926(209Kb+348Kb) found 4376(136Kb) fcontext 1657(38Kb) = 733Kb
average 654540 chars/s 2537 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 416 (0 ms): 0, 0, 0, 0; from 88953-88969, loops=20,chars=16,blocks 0/0 (0) contexts 0/0 (0) scancache 8310
memory scancache 8926(209Kb+348Kb) found 4376(136Kb) fcontext 1657(38Kb) = 733Kb
average 654550 chars/s 2531 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 417 (0 ms): 0, 0, 0, 0; from 88953-88970, loops=21,chars=17,blocks 0/0 (0) contexts 0/0 (0) scancache 8310
memory scancache 8926(209Kb+348Kb) found 4376(136Kb) fcontext 1657(38Kb) = 733Kb
average 654560 chars/s 2525 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 418 (0 ms): 0, 0, 0, 0; from 88953-88971, loops=22,chars=18,blocks 0/0 (0) contexts 0/0 (0) scancache 8310
memory scancache 8926(209Kb+348Kb) found 4376(136Kb) fcontext 1657(38Kb) = 733Kb
average 654571 chars/s 2519 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 419 (0 ms): 0, 0, 0, 0; from 4672-4779, loops=127,chars=107,blocks 0/0 (0) contexts 0/0 (0) scancache 248
memory scancache 8926(209Kb+348Kb) found 4376(136Kb) fcontext 1657(38Kb) = 733Kb
average 654638 chars/s 2513 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 420 (0 ms): 0, 0, 0, 0; from 4777-4779, loops=3,chars=2,blocks 0/0 (0) contexts 0/0 (0) scancache 248
memory scancache 8926(209Kb+348Kb) found 4376(136Kb) fcontext 1657(38Kb) = 733Kb
average 654639 chars/s 2507 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 421 (0 ms): 0, 0, 0, 0; from 4691-4781, loops=108,chars=90,blocks 0/0 (0) contexts 0/0 (0) scancache 248
memory scancache 8926(209Kb+348Kb) found 4376(136Kb) fcontext 1657(38Kb) = 733Kb
average 654695 chars/s 2502 chars/run
scancache integrity check done in 0,139000 ms.
scanning run 422 (72 ms): 0, 0, 0, 72; from 0-65030, loops=78504,chars=65030,blocks 1825/1824 (0) contexts 1087/1067 (0) scancache 5544
memory scancache 14470(339Kb+565Kb) found 6201(193Kb) fcontext 2744(64Kb) = 1162Kb
average 665339 chars/s 2650 chars/run
scancache integrity check done in 0,626001 ms.
scanning run 423 (0 ms): 0, 0, 0, 0; from 11345-11421, loops=102,chars=76,blocks 0/0 (0) contexts 0/0 (0) scancache 5544
memory scancache 14470(339Kb+565Kb) found 6201(193Kb) fcontext 2744(64Kb) = 1162Kb
average 665384 chars/s 2644 chars/run
Nothing to scan anymore, total run timer took 114623 ms
scanning run 424 (0 ms): 0, 0, 0, 0; from 11648-11740, loops=121,chars=92,blocks 0/0 (0) contexts 0/0 (0) scancache 5544
memory scancache 14470(339Kb+565Kb) found 6201(193Kb) fcontext 2744(64Kb) = 1162Kb
average 665439 chars/s 2638 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 425 (0 ms): 0, 0, 0, 0; from 11345-11421, loops=102,chars=76,blocks 0/0 (0) contexts 0/0 (0) scancache 5544
memory scancache 14470(339Kb+565Kb) found 6201(193Kb) fcontext 2744(64Kb) = 1162Kb
average 665484 chars/s 2632 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 426 (0 ms): 0, 0, 0, 0; from 11345-11417, loops=98,chars=72,blocks 0/0 (0) contexts 0/0 (0) scancache 5544
memory scancache 14470(339Kb+565Kb) found 6201(193Kb) fcontext 2744(64Kb) = 1162Kb
average 665527 chars/s 2626 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 427 (66 ms): 0, 0, 0, 66; from 11345-65027, loops=64959,chars=53682,blocks 1535/1546 (0) contexts 911/895 (0) scancache 5546
memory scancache 14472(339Kb+565Kb) found 6202(193Kb) fcontext 2748(64Kb) = 1162Kb
average 671112 chars/s 2745 chars/run
scancache integrity check done in 0,670001 ms.
scanning run 428 (67 ms): 0, 0, 0, 67; from 11345-65028, loops=64957,chars=53683,blocks 1535/1544 (0) contexts 908/891 (0) scancache 5546
memory scancache 14472(339Kb+565Kb) found 6202(193Kb) fcontext 2745(64Kb) = 1162Kb
average 675918 chars/s 2864 chars/run
scancache integrity check done in 0,650996 ms.
scanning run 429 (66 ms): 0, 0, 0, 66; from 11345-65027, loops=64959,chars=53682,blocks 1535/1545 (0) contexts 911/894 (0) scancache 5546
memory scancache 14472(339Kb+565Kb) found 6202(193Kb) fcontext 2748(64Kb) = 1162Kb
average 680743 chars/s 2983 chars/run
scancache integrity check done in 0,711997 ms.
scanning run 430 (66 ms): 0, 0, 0, 66; from 11345-65026, loops=64953,chars=53681,blocks 1534/1544 (0) contexts 907/891 (0) scancache 5544
memory scancache 14470(339Kb+565Kb) found 6201(193Kb) fcontext 2744(64Kb) = 1162Kb
average 685241 chars/s 3101 chars/run
scancache integrity check done in 0,751997 ms.
scanning run 431 (0 ms): 0, 0, 0, 0; from 11345-11418, loops=99,chars=73,blocks 0/0 (0) contexts 0/0 (0) scancache 5544
memory scancache 14470(339Kb+565Kb) found 6201(193Kb) fcontext 2744(64Kb) = 1162Kb
average 685278 chars/s 3094 chars/run
Nothing to scan anymore, total run timer took 2364 ms
scanning run 432 (0 ms): 0, 0, 0, 0; from 11345-11419, loops=100,chars=74,blocks 0/0 (0) contexts 0/0 (0) scancache 5544
memory scancache 14470(339Kb+565Kb) found 6201(193Kb) fcontext 2744(64Kb) = 1162Kb
average 685316 chars/s 3087 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 433 (0 ms): 0, 0, 0, 0; from 11345-11420, loops=101,chars=75,blocks 0/0 (0) contexts 0/0 (0) scancache 5544
memory scancache 14470(339Kb+565Kb) found 6201(193Kb) fcontext 2744(64Kb) = 1162Kb
average 685355 chars/s 3080 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 434 (0 ms): 0, 0, 0, 0; from 11345-11421, loops=102,chars=76,blocks 0/0 (0) contexts 0/0 (0) scancache 5544
memory scancache 14470(339Kb+565Kb) found 6201(193Kb) fcontext 2744(64Kb) = 1162Kb
average 685394 chars/s 3073 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 435 (0 ms): 0, 0, 0, 0; from 11345-11422, loops=103,chars=77,blocks 0/0 (0) contexts 0/0 (0) scancache 5544
memory scancache 14470(339Kb+565Kb) found 6201(193Kb) fcontext 2744(64Kb) = 1162Kb
average 685433 chars/s 3066 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 436 (0 ms): 0, 0, 0, 0; from 11345-11423, loops=104,chars=78,blocks 0/0 (0) contexts 0/0 (0) scancache 5544
memory scancache 14470(339Kb+565Kb) found 6201(193Kb) fcontext 2744(64Kb) = 1162Kb
average 685473 chars/s 3059 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 437 (0 ms): 0, 0, 0, 0; from 11345-11424, loops=105,chars=79,blocks 0/0 (0) contexts 0/0 (0) scancache 5544
memory scancache 14470(339Kb+565Kb) found 6201(193Kb) fcontext 2744(64Kb) = 1162Kb
average 685514 chars/s 3052 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 438 (66 ms): 0, 0, 0, 66; from 11345-65034, loops=64966,chars=53689,blocks 1535/1546 (0) contexts 911/895 (0) scancache 5546
memory scancache 14472(339Kb+565Kb) found 6202(193Kb) fcontext 2748(64Kb) = 1162Kb
average 689711 chars/s 3168 chars/run
scancache integrity check done in 0,702003 ms.
scanning run 439 (0 ms): 0, 0, 0, 0; from 11345-11426, loops=102,chars=81,blocks 0/0 (0) contexts 0/0 (0) scancache 5546
memory scancache 14472(339Kb+565Kb) found 6202(193Kb) fcontext 2748(64Kb) = 1162Kb
average 689751 chars/s 3161 chars/run
Nothing to scan anymore, total run timer took 181 ms
scanning run 440 (0 ms): 0, 0, 0, 0; from 11356-11427, loops=90,chars=71,blocks 0/0 (0) contexts 0/0 (0) scancache 5546
memory scancache 14472(339Kb+565Kb) found 6202(193Kb) fcontext 2748(64Kb) = 1162Kb
average 689787 chars/s 3154 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 441 (66 ms): 0, 0, 0, 66; from 11356-65037, loops=64955,chars=53681,blocks 1535/1544 (0) contexts 908/891 (0) scancache 5546
memory scancache 14472(339Kb+565Kb) found 6202(193Kb) fcontext 2745(64Kb) = 1162Kb
average 693711 chars/s 3268 chars/run
scancache integrity check done in 0,720999 ms.
Nothing to scan anymore, total run timer took 3888 ms
scanning run 442 (0 ms): 0, 0, 0, 0; from 4777-4779, loops=3,chars=2,blocks 0/0 (0) contexts 0/0 (0) scancache 248
memory scancache 14472(339Kb+565Kb) found 6202(193Kb) fcontext 2745(64Kb) = 1162Kb
average 693712 chars/s 3261 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 443 (0 ms): 0, 0, 0, 0; from 4777-4780, loops=4,chars=3,blocks 0/0 (0) contexts 0/0 (0) scancache 248
memory scancache 14472(339Kb+565Kb) found 6202(193Kb) fcontext 2745(64Kb) = 1162Kb
average 693714 chars/s 3254 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 444 (0 ms): 0, 0, 0, 0; from 4779-4782, loops=5,chars=3,blocks 0/0 (0) contexts 0/0 (0) scancache 248
memory scancache 14472(339Kb+565Kb) found 6202(193Kb) fcontext 2745(64Kb) = 1162Kb
average 693715 chars/s 3246 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 445 (0 ms): 0, 0, 0, 0; from 4779-4783, loops=6,chars=4,blocks 0/0 (0) contexts 0/0 (0) scancache 248
memory scancache 14472(339Kb+565Kb) found 6202(193Kb) fcontext 2745(64Kb) = 1162Kb
average 693717 chars/s 3239 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 446 (0 ms): 0, 0, 0, 0; from 4779-4784, loops=7,chars=5,blocks 0/0 (0) contexts 0/0 (0) scancache 248
memory scancache 14472(339Kb+565Kb) found 6202(193Kb) fcontext 2745(64Kb) = 1162Kb
average 693719 chars/s 3232 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 447 (0 ms): 0, 0, 0, 0; from 4779-4785, loops=8,chars=6,blocks 0/0 (0) contexts 0/0 (0) scancache 248
memory scancache 14472(339Kb+565Kb) found 6202(193Kb) fcontext 2745(64Kb) = 1162Kb
average 693722 chars/s 3224 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 448 (0 ms): 0, 0, 0, 0; from 4779-4786, loops=9,chars=7,blocks 0/0 (0) contexts 0/0 (0) scancache 248
memory scancache 14472(339Kb+565Kb) found 6202(193Kb) fcontext 2745(64Kb) = 1162Kb
average 693726 chars/s 3217 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 449 (0 ms): 0, 0, 0, 0; from 4779-4787, loops=10,chars=8,blocks 0/0 (0) contexts 0/0 (0) scancache 248
memory scancache 14472(339Kb+565Kb) found 6202(193Kb) fcontext 2745(64Kb) = 1162Kb
average 693730 chars/s 3210 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 450 (0 ms): 0, 0, 0, 0; from 4779-4788, loops=11,chars=9,blocks 0/0 (0) contexts 0/0 (0) scancache 248
memory scancache 14472(339Kb+565Kb) found 6202(193Kb) fcontext 2745(64Kb) = 1162Kb
average 693734 chars/s 3203 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 451 (0 ms): 0, 0, 0, 0; from 4779-4789, loops=12,chars=10,blocks 0/0 (0) contexts 0/0 (0) scancache 248
memory scancache 14472(339Kb+565Kb) found 6202(193Kb) fcontext 2745(64Kb) = 1162Kb
average 693739 chars/s 3196 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 452 (0 ms): 0, 0, 0, 0; from 4779-4790, loops=13,chars=11,blocks 0/0 (0) contexts 0/0 (0) scancache 248
memory scancache 14472(339Kb+565Kb) found 6202(193Kb) fcontext 2745(64Kb) = 1162Kb
average 693744 chars/s 3189 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 453 (0 ms): 0, 0, 0, 0; from 4779-4793, loops=18,chars=14,blocks 1/0 (0) contexts 1/0 (0) scancache 248
memory scancache 14472(339Kb+565Kb) found 6203(193Kb) fcontext 2746(64Kb) = 1162Kb
average 693751 chars/s 3182 chars/run
scancache integrity check done in 0,091000 ms.
scanning run 454 (0 ms): 0, 0, 0, 0; from 4779-4794, loops=19,chars=15,blocks 0/2 (0) contexts 0/2 (0) scancache 250
memory scancache 14474(339Kb+565Kb) found 6203(193Kb) fcontext 2746(64Kb) = 1162Kb
average 693758 chars/s 3175 chars/run
scancache integrity check done in 0,094000 ms.
scanning run 455 (0 ms): 0, 0, 0, 0; from 4779-4796, loops=22,chars=17,blocks 0/0 (0) contexts 0/0 (0) scancache 250
memory scancache 14474(339Kb+565Kb) found 6203(193Kb) fcontext 2746(64Kb) = 1162Kb
average 693766 chars/s 3168 chars/run
Nothing to scan anymore, total run timer took 593 ms
scanning run 456 (0 ms): 0, 0, 0, 0; from 4790-4797, loops=10,chars=7,blocks 0/0 (0) contexts 0/0 (0) scancache 250
memory scancache 14474(339Kb+565Kb) found 6203(193Kb) fcontext 2746(64Kb) = 1162Kb
average 693769 chars/s 3161 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 457 (0 ms): 0, 0, 0, 0; from 4795-4797, loops=3,chars=2,blocks 0/0 (0) contexts 0/0 (0) scancache 250
memory scancache 14474(339Kb+565Kb) found 6203(193Kb) fcontext 2746(64Kb) = 1162Kb
average 693770 chars/s 3154 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 458 (0 ms): 0, 0, 0, 0; from 11379-11428, loops=69,chars=49,blocks 0/0 (0) contexts 0/0 (0) scancache 5546
memory scancache 14474(339Kb+565Kb) found 6203(193Kb) fcontext 2746(64Kb) = 1162Kb
average 693794 chars/s 3147 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 459 (66 ms): 0, 0, 0, 66; from 11418-65038, loops=64882,chars=53620,blocks 1533/1544 (0) contexts 909/893 (0) scancache 5556
memory scancache 14484(339Kb+565Kb) found 6208(194Kb) fcontext 2750(64Kb) = 1163Kb
average 697446 chars/s 3257 chars/run
scancache integrity check done in 0,766997 ms.
scanning run 460 (0 ms): 0, 0, 0, 0; from 11418-11430, loops=17,chars=12,blocks 0/0 (0) contexts 0/0 (0) scancache 5556
memory scancache 14484(339Kb+565Kb) found 6208(194Kb) fcontext 2750(64Kb) = 1163Kb
average 697451 chars/s 3250 chars/run
Nothing to scan anymore, total run timer took 186 ms
scanning run 461 (0 ms): 0, 0, 0, 0; from 11420-11431, loops=15,chars=11,blocks 0/0 (0) contexts 0/0 (0) scancache 5556
memory scancache 14484(339Kb+565Kb) found 6208(194Kb) fcontext 2750(64Kb) = 1163Kb
average 697457 chars/s 3243 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 462 (66 ms): 0, 0, 0, 66; from 11420-65041, loops=64871,chars=53621,blocks 1529/1538 (0) contexts 906/889 (0) scancache 5548
memory scancache 14476(339Kb+565Kb) found 6204(193Kb) fcontext 2747(64Kb) = 1163Kb
average 700890 chars/s 3352 chars/run
scancache integrity check done in 0,711997 ms.
scanning run 463 (0 ms): 0, 0, 0, 0; from 11387-11427, loops=63,chars=40,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14476(339Kb+565Kb) found 6204(193Kb) fcontext 2747(64Kb) = 1163Kb
average 700909 chars/s 3345 chars/run
Nothing to scan anymore, total run timer took 4586 ms
scanning run 464 (0 ms): 0, 0, 0, 0; from 11420-11428, loops=13,chars=8,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14476(339Kb+565Kb) found 6204(193Kb) fcontext 2747(64Kb) = 1163Kb
average 700912 chars/s 3338 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 465 (0 ms): 0, 0, 0, 0; from 11420-11429, loops=14,chars=9,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14476(339Kb+565Kb) found 6204(193Kb) fcontext 2747(64Kb) = 1163Kb
average 700916 chars/s 3331 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 466 (0 ms): 0, 0, 0, 0; from 11420-11430, loops=15,chars=10,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14476(339Kb+565Kb) found 6204(193Kb) fcontext 2747(64Kb) = 1163Kb
average 700921 chars/s 3324 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 467 (0 ms): 0, 0, 0, 0; from 11420-11431, loops=16,chars=11,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14476(339Kb+565Kb) found 6204(193Kb) fcontext 2747(64Kb) = 1163Kb
average 700926 chars/s 3317 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 468 (0 ms): 0, 0, 0, 0; from 11420-11432, loops=17,chars=12,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14476(339Kb+565Kb) found 6204(193Kb) fcontext 2747(64Kb) = 1163Kb
average 700931 chars/s 3309 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 469 (0 ms): 0, 0, 0, 0; from 11420-11433, loops=18,chars=13,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14476(339Kb+565Kb) found 6204(193Kb) fcontext 2747(64Kb) = 1163Kb
average 700937 chars/s 3302 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 470 (0 ms): 0, 0, 0, 0; from 11420-11434, loops=19,chars=14,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14476(339Kb+565Kb) found 6204(193Kb) fcontext 2747(64Kb) = 1163Kb
average 700943 chars/s 3295 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 471 (0 ms): 0, 0, 0, 0; from 11420-11435, loops=20,chars=15,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14476(339Kb+565Kb) found 6204(193Kb) fcontext 2747(64Kb) = 1163Kb
average 700950 chars/s 3288 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 472 (0 ms): 0, 0, 0, 0; from 4795-4798, loops=4,chars=3,blocks 0/0 (0) contexts 0/0 (0) scancache 250
memory scancache 14476(339Kb+565Kb) found 6204(193Kb) fcontext 2747(64Kb) = 1163Kb
average 700952 chars/s 3282 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 473 (0 ms): 0, 0, 0, 0; from 4797-4800, loops=5,chars=3,blocks 0/0 (0) contexts 0/0 (0) scancache 250
memory scancache 14476(339Kb+565Kb) found 6204(193Kb) fcontext 2747(64Kb) = 1163Kb
average 700953 chars/s 3275 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 474 (0 ms): 0, 0, 0, 0; from 4797-4801, loops=6,chars=4,blocks 0/0 (0) contexts 0/0 (0) scancache 250
memory scancache 14476(339Kb+565Kb) found 6204(193Kb) fcontext 2747(64Kb) = 1163Kb
average 700955 chars/s 3268 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 475 (0 ms): 0, 0, 0, 0; from 4797-4802, loops=7,chars=5,blocks 0/0 (0) contexts 0/0 (0) scancache 250
memory scancache 14476(339Kb+565Kb) found 6204(193Kb) fcontext 2747(64Kb) = 1163Kb
average 700957 chars/s 3261 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 476 (0 ms): 0, 0, 0, 0; from 4797-4803, loops=8,chars=6,blocks 0/0 (0) contexts 0/0 (0) scancache 250
memory scancache 14476(339Kb+565Kb) found 6204(193Kb) fcontext 2747(64Kb) = 1163Kb
average 700960 chars/s 3254 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 477 (0 ms): 0, 0, 0, 0; from 4797-4804, loops=9,chars=7,blocks 0/0 (0) contexts 0/0 (0) scancache 250
memory scancache 14476(339Kb+565Kb) found 6204(193Kb) fcontext 2747(64Kb) = 1163Kb
average 700963 chars/s 3247 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 478 (0 ms): 0, 0, 0, 0; from 4797-4805, loops=10,chars=8,blocks 0/0 (0) contexts 0/0 (0) scancache 250
memory scancache 14476(339Kb+565Kb) found 6204(193Kb) fcontext 2747(64Kb) = 1163Kb
average 700966 chars/s 3240 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 479 (0 ms): 0, 0, 0, 0; from 4797-4806, loops=11,chars=9,blocks 0/0 (0) contexts 0/0 (0) scancache 250
memory scancache 14476(339Kb+565Kb) found 6204(193Kb) fcontext 2747(64Kb) = 1163Kb
average 700971 chars/s 3234 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 480 (0 ms): 0, 0, 0, 0; from 4797-4807, loops=12,chars=10,blocks 0/0 (0) contexts 0/0 (0) scancache 250
memory scancache 14476(339Kb+565Kb) found 6204(193Kb) fcontext 2747(64Kb) = 1163Kb
average 700975 chars/s 3227 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 481 (0 ms): 0, 0, 0, 0; from 4797-4808, loops=13,chars=11,blocks 0/0 (0) contexts 0/0 (0) scancache 250
memory scancache 14476(339Kb+565Kb) found 6204(193Kb) fcontext 2747(64Kb) = 1163Kb
average 700980 chars/s 3220 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 482 (0 ms): 0, 0, 0, 0; from 4797-4809, loops=14,chars=12,blocks 0/0 (0) contexts 0/0 (0) scancache 250
memory scancache 14476(339Kb+565Kb) found 6204(193Kb) fcontext 2747(64Kb) = 1163Kb
average 700985 chars/s 3214 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 483 (0 ms): 0, 0, 0, 0; from 4797-4810, loops=15,chars=13,blocks 0/0 (0) contexts 0/0 (0) scancache 250
memory scancache 14476(339Kb+565Kb) found 6204(193Kb) fcontext 2747(64Kb) = 1163Kb
average 700991 chars/s 3207 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 484 (0 ms): 0, 0, 0, 0; from 4797-4813, loops=20,chars=16,blocks 1/0 (0) contexts 1/0 (0) scancache 250
memory scancache 14476(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 700999 chars/s 3200 chars/run
scancache integrity check done in 0,081000 ms.
scanning run 485 (0 ms): 0, 0, 0, 0; from 4797-4814, loops=21,chars=17,blocks 0/2 (0) contexts 0/2 (0) scancache 252
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701006 chars/s 3194 chars/run
scancache integrity check done in 0,090000 ms.
scanning run 486 (0 ms): 0, 0, 0, 0; from 4797-4813, loops=21,chars=16,blocks 0/0 (0) contexts 0/0 (0) scancache 252
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701014 chars/s 3187 chars/run
Nothing to scan anymore, total run timer took 453 ms
scanning run 487 (0 ms): 0, 0, 0, 0; from 4810-4814, loops=7,chars=4,blocks 0/0 (0) contexts 0/0 (0) scancache 252
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701015 chars/s 3181 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 488 (0 ms): 0, 0, 0, 0; from 4810-4815, loops=8,chars=5,blocks 0/0 (0) contexts 0/0 (0) scancache 252
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701018 chars/s 3174 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 489 (0 ms): 0, 0, 0, 0; from 4810-4816, loops=9,chars=6,blocks 0/0 (0) contexts 0/0 (0) scancache 252
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701020 chars/s 3168 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 490 (0 ms): 0, 0, 0, 0; from 4810-4817, loops=10,chars=7,blocks 0/0 (0) contexts 0/0 (0) scancache 252
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701023 chars/s 3161 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 491 (0 ms): 0, 0, 0, 0; from 4810-4818, loops=11,chars=8,blocks 0/0 (0) contexts 0/0 (0) scancache 252
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701027 chars/s 3155 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 492 (0 ms): 0, 0, 0, 0; from 4810-4819, loops=12,chars=9,blocks 0/0 (0) contexts 0/0 (0) scancache 252
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701031 chars/s 3148 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 493 (0 ms): 0, 0, 0, 0; from 11662-11738, loops=102,chars=76,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701066 chars/s 3142 chars/run
Nothing to scan anymore, total run timer took 4 ms
scanning run 494 (0 ms): 0, 0, 0, 0; from 11662-11739, loops=104,chars=77,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701100 chars/s 3136 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 495 (0 ms): 0, 0, 0, 0; from 11662-11740, loops=105,chars=78,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701136 chars/s 3130 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 496 (0 ms): 0, 0, 0, 0; from 11662-11741, loops=106,chars=79,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701171 chars/s 3124 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 497 (0 ms): 0, 0, 0, 0; from 11662-11742, loops=107,chars=80,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701208 chars/s 3118 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 498 (0 ms): 0, 0, 0, 0; from 11662-11743, loops=108,chars=81,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701244 chars/s 3111 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 499 (0 ms): 0, 0, 0, 0; from 11662-11744, loops=109,chars=82,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701281 chars/s 3105 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 500 (0 ms): 0, 0, 0, 0; from 11662-11745, loops=110,chars=83,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701319 chars/s 3099 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 501 (0 ms): 0, 0, 0, 0; from 11662-11746, loops=111,chars=84,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701357 chars/s 3093 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 502 (0 ms): 0, 0, 0, 0; from 11662-11747, loops=112,chars=85,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701395 chars/s 3087 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 503 (0 ms): 0, 0, 0, 0; from 11662-11748, loops=113,chars=86,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701434 chars/s 3081 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 504 (0 ms): 0, 0, 0, 0; from 11662-11749, loops=114,chars=87,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701474 chars/s 3075 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 505 (0 ms): 0, 0, 0, 0; from 11662-11750, loops=115,chars=88,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701514 chars/s 3069 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 506 (0 ms): 0, 0, 0, 0; from 4817-4819, loops=3,chars=2,blocks 0/0 (0) contexts 0/0 (0) scancache 252
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701514 chars/s 3063 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 507 (0 ms): 0, 0, 0, 0; from 4817-4820, loops=4,chars=3,blocks 0/0 (0) contexts 0/0 (0) scancache 252
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701516 chars/s 3057 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 508 (0 ms): 0, 0, 0, 0; from 4819-4822, loops=5,chars=3,blocks 0/0 (0) contexts 0/0 (0) scancache 252
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701517 chars/s 3051 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 509 (0 ms): 0, 0, 0, 0; from 4819-4823, loops=6,chars=4,blocks 0/0 (0) contexts 0/0 (0) scancache 252
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701519 chars/s 3045 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 510 (0 ms): 0, 0, 0, 0; from 4819-4824, loops=7,chars=5,blocks 0/0 (0) contexts 0/0 (0) scancache 252
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701521 chars/s 3039 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 511 (0 ms): 0, 0, 0, 0; from 4819-4825, loops=8,chars=6,blocks 0/0 (0) contexts 0/0 (0) scancache 252
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701524 chars/s 3033 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 512 (0 ms): 0, 0, 0, 0; from 4819-4826, loops=9,chars=7,blocks 0/0 (0) contexts 0/0 (0) scancache 252
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701527 chars/s 3028 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 513 (0 ms): 0, 0, 0, 0; from 4819-4827, loops=10,chars=8,blocks 0/0 (0) contexts 0/0 (0) scancache 252
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701531 chars/s 3022 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 514 (0 ms): 0, 0, 0, 0; from 4819-4828, loops=11,chars=9,blocks 0/0 (0) contexts 0/0 (0) scancache 252
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701535 chars/s 3016 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 515 (0 ms): 0, 0, 0, 0; from 4819-4829, loops=12,chars=10,blocks 0/0 (0) contexts 0/0 (0) scancache 252
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701539 chars/s 3010 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 516 (0 ms): 0, 0, 0, 0; from 4819-4830, loops=13,chars=11,blocks 0/0 (0) contexts 0/0 (0) scancache 252
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701544 chars/s 3004 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 517 (0 ms): 0, 0, 0, 0; from 4819-4831, loops=14,chars=12,blocks 0/0 (0) contexts 0/0 (0) scancache 252
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701550 chars/s 2998 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 518 (0 ms): 0, 0, 0, 0; from 4819-4832, loops=15,chars=13,blocks 0/0 (0) contexts 0/0 (0) scancache 252
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701556 chars/s 2993 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 519 (0 ms): 0, 0, 0, 0; from 4819-4833, loops=16,chars=14,blocks 0/0 (0) contexts 0/0 (0) scancache 252
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701562 chars/s 2987 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 520 (0 ms): 0, 0, 0, 0; from 4819-4834, loops=17,chars=15,blocks 0/0 (0) contexts 0/0 (0) scancache 252
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701569 chars/s 2981 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 521 (0 ms): 0, 0, 0, 0; from 4819-4835, loops=18,chars=16,blocks 0/0 (0) contexts 0/0 (0) scancache 252
memory scancache 14478(339Kb+565Kb) found 6205(193Kb) fcontext 2748(64Kb) = 1163Kb
average 701576 chars/s 2975 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 522 (0 ms): 0, 0, 0, 0; from 4819-4838, loops=23,chars=19,blocks 1/0 (0) contexts 1/0 (0) scancache 252
memory scancache 14478(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701585 chars/s 2970 chars/run
scancache integrity check done in 0,098000 ms.
scanning run 523 (0 ms): 0, 0, 0, 0; from 4819-4839, loops=24,chars=20,blocks 0/2 (0) contexts 0/2 (0) scancache 254
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701594 chars/s 2964 chars/run
scancache integrity check done in 0,098000 ms.
scanning run 524 (0 ms): 0, 0, 0, 0; from 4819-4853, loops=41,chars=34,blocks 0/0 (0) contexts 0/0 (0) scancache 254
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701609 chars/s 2959 chars/run
Nothing to scan anymore, total run timer took 520 ms
scanning run 525 (0 ms): 0, 0, 0, 0; from 4835-4854, loops=24,chars=19,blocks 0/0 (0) contexts 0/0 (0) scancache 254
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701618 chars/s 2953 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 526 (0 ms): 0, 0, 0, 0; from 4835-4854, loops=24,chars=19,blocks 0/0 (0) contexts 0/0 (0) scancache 254
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701626 chars/s 2947 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 527 (0 ms): 0, 0, 0, 0; from 4835-4854, loops=23,chars=19,blocks 0/0 (0) contexts 0/0 (0) scancache 254
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701635 chars/s 2942 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 528 (0 ms): 0, 0, 0, 0; from 4819-4854, loops=40,chars=35,blocks 0/0 (0) contexts 0/0 (0) scancache 254
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701651 chars/s 2936 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 529 (0 ms): 0, 0, 0, 0; from 11696-11738, loops=61,chars=42,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701670 chars/s 2931 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 530 (0 ms): 0, 0, 0, 0; from 11733-11739, loops=10,chars=6,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701672 chars/s 2925 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 531 (0 ms): 0, 0, 0, 0; from 11735-11740, loops=7,chars=5,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701675 chars/s 2920 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 532 (0 ms): 0, 0, 0, 0; from 11735-11741, loops=8,chars=6,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701677 chars/s 2914 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 533 (0 ms): 0, 0, 0, 0; from 11735-11742, loops=9,chars=7,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701680 chars/s 2909 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 534 (0 ms): 0, 0, 0, 0; from 11704-11741, loops=55,chars=37,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701697 chars/s 2904 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 535 (0 ms): 0, 0, 0, 0; from 11704-11740, loops=54,chars=36,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701714 chars/s 2898 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 536 (0 ms): 0, 0, 0, 0; from 11696-11739, loops=63,chars=43,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701733 chars/s 2893 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 537 (0 ms): 0, 0, 0, 0; from 11735-11740, loops=7,chars=5,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701735 chars/s 2887 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 538 (0 ms): 0, 0, 0, 0; from 11735-11741, loops=8,chars=6,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701738 chars/s 2882 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 539 (0 ms): 0, 0, 0, 0; from 11735-11742, loops=9,chars=7,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701741 chars/s 2877 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 540 (0 ms): 0, 0, 0, 0; from 11735-11743, loops=10,chars=8,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701745 chars/s 2871 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 541 (0 ms): 0, 0, 0, 0; from 11735-11744, loops=11,chars=9,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701749 chars/s 2866 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 542 (0 ms): 0, 0, 0, 0; from 11735-11745, loops=12,chars=10,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701753 chars/s 2861 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 543 (0 ms): 0, 0, 0, 0; from 11735-11746, loops=13,chars=11,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701758 chars/s 2856 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 544 (0 ms): 0, 0, 0, 0; from 11735-11747, loops=14,chars=12,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701764 chars/s 2850 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 545 (0 ms): 0, 0, 0, 0; from 11735-11748, loops=15,chars=13,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701770 chars/s 2845 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 546 (0 ms): 0, 0, 0, 0; from 11735-11749, loops=16,chars=14,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701776 chars/s 2840 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 547 (0 ms): 0, 0, 0, 0; from 11735-11750, loops=17,chars=15,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701783 chars/s 2835 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 548 (0 ms): 0, 0, 0, 0; from 11735-11751, loops=18,chars=16,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701790 chars/s 2830 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 549 (0 ms): 0, 0, 0, 0; from 4852-4854, loops=3,chars=2,blocks 0/0 (0) contexts 0/0 (0) scancache 254
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701791 chars/s 2825 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 550 (0 ms): 0, 0, 0, 0; from 4852-4855, loops=4,chars=3,blocks 0/0 (0) contexts 0/0 (0) scancache 254
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701792 chars/s 2819 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 551 (0 ms): 0, 0, 0, 0; from 4854-4857, loops=5,chars=3,blocks 0/0 (0) contexts 0/0 (0) scancache 254
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701794 chars/s 2814 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 552 (0 ms): 0, 0, 0, 0; from 4852-4858, loops=8,chars=6,blocks 0/0 (0) contexts 0/0 (0) scancache 254
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701796 chars/s 2809 chars/run
scancache integrity check done in 0,092000 ms.
scanning run 553 (0 ms): 0, 0, 0, 0; from 4854-4857, loops=5,chars=3,blocks 0/0 (0) contexts 0/0 (0) scancache 254
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701798 chars/s 2804 chars/run
Nothing to scan anymore, total run timer took 167 ms
scanning run 554 (0 ms): 0, 0, 0, 0; from 4854-4858, loops=6,chars=4,blocks 0/0 (0) contexts 0/0 (0) scancache 254
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701800 chars/s 2799 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 555 (0 ms): 0, 0, 0, 0; from 4854-4859, loops=7,chars=5,blocks 0/0 (0) contexts 0/0 (0) scancache 254
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701802 chars/s 2794 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 556 (0 ms): 0, 0, 0, 0; from 4854-4860, loops=8,chars=6,blocks 0/0 (0) contexts 0/0 (0) scancache 254
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701804 chars/s 2789 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 557 (0 ms): 0, 0, 0, 0; from 4854-4861, loops=9,chars=7,blocks 0/0 (0) contexts 0/0 (0) scancache 254
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701808 chars/s 2784 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 558 (0 ms): 0, 0, 0, 0; from 4854-4862, loops=10,chars=8,blocks 0/0 (0) contexts 0/0 (0) scancache 254
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701811 chars/s 2779 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 559 (0 ms): 0, 0, 0, 0; from 4854-4863, loops=11,chars=9,blocks 0/0 (0) contexts 0/0 (0) scancache 254
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701815 chars/s 2774 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 560 (0 ms): 0, 0, 0, 0; from 4854-4864, loops=12,chars=10,blocks 0/0 (0) contexts 0/0 (0) scancache 254
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701820 chars/s 2769 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 561 (0 ms): 0, 0, 0, 0; from 4854-4865, loops=13,chars=11,blocks 0/0 (0) contexts 0/0 (0) scancache 254
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701825 chars/s 2764 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 562 (0 ms): 0, 0, 0, 0; from 4852-4866, loops=16,chars=14,blocks 0/0 (0) contexts 0/0 (0) scancache 254
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701831 chars/s 2759 chars/run
scancache integrity check done in 0,093000 ms.
scanning run 563 (0 ms): 0, 0, 0, 0; from 4854-4865, loops=13,chars=11,blocks 0/0 (0) contexts 0/0 (0) scancache 254
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701836 chars/s 2754 chars/run
Nothing to scan anymore, total run timer took 49 ms
scanning run 564 (0 ms): 0, 0, 0, 0; from 4854-4866, loops=14,chars=12,blocks 0/0 (0) contexts 0/0 (0) scancache 254
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701842 chars/s 2750 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 565 (0 ms): 0, 0, 0, 0; from 4854-4867, loops=15,chars=13,blocks 0/0 (0) contexts 0/0 (0) scancache 254
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701847 chars/s 2745 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 566 (0 ms): 0, 0, 0, 0; from 4854-4868, loops=16,chars=14,blocks 0/0 (0) contexts 0/0 (0) scancache 254
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701854 chars/s 2740 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 567 (0 ms): 0, 0, 0, 0; from 4854-4869, loops=17,chars=15,blocks 0/0 (0) contexts 0/0 (0) scancache 254
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701861 chars/s 2735 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 568 (0 ms): 0, 0, 0, 0; from 4854-4870, loops=18,chars=16,blocks 0/0 (0) contexts 0/0 (0) scancache 254
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701868 chars/s 2730 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 569 (0 ms): 0, 0, 0, 0; from 4854-4871, loops=19,chars=17,blocks 0/0 (0) contexts 0/0 (0) scancache 254
memory scancache 14480(339Kb+565Kb) found 6206(193Kb) fcontext 2749(64Kb) = 1163Kb
average 701876 chars/s 2726 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 570 (0 ms): 0, 0, 0, 0; from 4854-4874, loops=24,chars=20,blocks 1/0 (0) contexts 1/0 (0) scancache 254
memory scancache 14480(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 701885 chars/s 2721 chars/run
scancache integrity check done in 0,085000 ms.
scanning run 571 (0 ms): 0, 0, 0, 0; from 4854-4875, loops=25,chars=21,blocks 0/2 (0) contexts 0/2 (0) scancache 256
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 701894 chars/s 2716 chars/run
scancache integrity check done in 0,086000 ms.
scanning run 572 (0 ms): 0, 0, 0, 0; from 4854-4885, loops=37,chars=31,blocks 0/0 (0) contexts 0/0 (0) scancache 256
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 701908 chars/s 2711 chars/run
Nothing to scan anymore, total run timer took 635 ms
scanning run 573 (0 ms): 0, 0, 0, 0; from 4871-4886, loops=19,chars=15,blocks 0/0 (0) contexts 0/0 (0) scancache 256
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 701915 chars/s 2707 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 574 (0 ms): 0, 0, 0, 0; from 4854-4886, loops=38,chars=32,blocks 0/0 (0) contexts 0/0 (0) scancache 256
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 701929 chars/s 2702 chars/run
Nothing to scan anymore, total run timer took 1 ms
scanning run 575 (0 ms): 0, 0, 0, 0; from 4854-4886, loops=37,chars=32,blocks 0/0 (0) contexts 0/0 (0) scancache 256
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 701944 chars/s 2697 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 576 (0 ms): 0, 0, 0, 0; from 11978-12042, loops=87,chars=64,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 701973 chars/s 2693 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 577 (0 ms): 0, 0, 0, 0; from 11978-12043, loops=89,chars=65,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702002 chars/s 2688 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 578 (0 ms): 0, 0, 0, 0; from 11978-12044, loops=90,chars=66,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702032 chars/s 2684 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 579 (0 ms): 0, 0, 0, 0; from 11978-12045, loops=91,chars=67,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702062 chars/s 2679 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 580 (0 ms): 0, 0, 0, 0; from 11978-12046, loops=92,chars=68,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702093 chars/s 2675 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 581 (0 ms): 0, 0, 0, 0; from 11978-12047, loops=93,chars=69,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702124 chars/s 2670 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 582 (0 ms): 0, 0, 0, 0; from 11978-12048, loops=94,chars=70,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702156 chars/s 2666 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 583 (0 ms): 0, 0, 0, 0; from 11978-12049, loops=95,chars=71,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702188 chars/s 2661 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 584 (0 ms): 0, 0, 0, 0; from 11978-12050, loops=96,chars=72,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702221 chars/s 2657 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 585 (0 ms): 0, 0, 0, 0; from 11978-12051, loops=97,chars=73,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702254 chars/s 2652 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 586 (0 ms): 0, 0, 0, 0; from 11978-12052, loops=98,chars=74,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702287 chars/s 2648 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 587 (0 ms): 0, 0, 0, 0; from 11978-12053, loops=99,chars=75,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702321 chars/s 2644 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 588 (0 ms): 0, 0, 0, 0; from 11978-12054, loops=100,chars=76,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702356 chars/s 2639 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 589 (0 ms): 0, 0, 0, 0; from 11978-12055, loops=101,chars=77,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702390 chars/s 2635 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 590 (0 ms): 0, 0, 0, 0; from 11978-12056, loops=102,chars=78,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702426 chars/s 2631 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 591 (0 ms): 0, 0, 0, 0; from 11978-12057, loops=103,chars=79,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702461 chars/s 2626 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 592 (0 ms): 0, 0, 0, 0; from 11978-12058, loops=104,chars=80,blocks 0/0 (0) contexts 0/0 (0) scancache 5548
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702498 chars/s 2622 chars/run
Nothing to scan anymore, total run timer took 2 ms
scanning run 593 (0 ms): 0, 0, 0, 0; from 4884-4886, loops=3,chars=2,blocks 0/0 (0) contexts 0/0 (0) scancache 256
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702499 chars/s 2618 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 594 (0 ms): 0, 0, 0, 0; from 4884-4887, loops=4,chars=3,blocks 0/0 (0) contexts 0/0 (0) scancache 256
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702500 chars/s 2613 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 595 (0 ms): 0, 0, 0, 0; from 4886-4889, loops=5,chars=3,blocks 0/0 (0) contexts 0/0 (0) scancache 256
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702501 chars/s 2609 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 596 (0 ms): 0, 0, 0, 0; from 4886-4890, loops=6,chars=4,blocks 0/0 (0) contexts 0/0 (0) scancache 256
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702503 chars/s 2604 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 597 (0 ms): 0, 0, 0, 0; from 4886-4891, loops=7,chars=5,blocks 0/0 (0) contexts 0/0 (0) scancache 256
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702505 chars/s 2600 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 598 (0 ms): 0, 0, 0, 0; from 4886-4892, loops=8,chars=6,blocks 0/0 (0) contexts 0/0 (0) scancache 256
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702508 chars/s 2596 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 599 (0 ms): 0, 0, 0, 0; from 4886-4893, loops=9,chars=7,blocks 0/0 (0) contexts 0/0 (0) scancache 256
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702511 chars/s 2591 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 600 (0 ms): 0, 0, 0, 0; from 4886-4894, loops=10,chars=8,blocks 0/0 (0) contexts 0/0 (0) scancache 256
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702515 chars/s 2587 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 601 (0 ms): 0, 0, 0, 0; from 4884-4895, loops=13,chars=11,blocks 0/0 (0) contexts 0/0 (0) scancache 256
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702520 chars/s 2583 chars/run
scancache integrity check done in 0,097000 ms.
scanning run 602 (0 ms): 0, 0, 0, 0; from 4886-4894, loops=10,chars=8,blocks 0/0 (0) contexts 0/0 (0) scancache 256
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702523 chars/s 2579 chars/run
Nothing to scan anymore, total run timer took 207 ms
scanning run 603 (0 ms): 0, 0, 0, 0; from 4886-4895, loops=11,chars=9,blocks 0/0 (0) contexts 0/0 (0) scancache 256
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702528 chars/s 2574 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 604 (0 ms): 0, 0, 0, 0; from 4886-4896, loops=12,chars=10,blocks 0/0 (0) contexts 0/0 (0) scancache 256
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702532 chars/s 2570 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 605 (0 ms): 0, 0, 0, 0; from 4886-4897, loops=13,chars=11,blocks 0/0 (0) contexts 0/0 (0) scancache 256
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702537 chars/s 2566 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 606 (0 ms): 0, 0, 0, 0; from 4886-4898, loops=14,chars=12,blocks 0/0 (0) contexts 0/0 (0) scancache 256
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702542 chars/s 2562 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 607 (0 ms): 0, 0, 0, 0; from 4886-4899, loops=15,chars=13,blocks 0/0 (0) contexts 0/0 (0) scancache 256
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702548 chars/s 2557 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 608 (0 ms): 0, 0, 0, 0; from 4886-4900, loops=16,chars=14,blocks 0/0 (0) contexts 0/0 (0) scancache 256
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702555 chars/s 2553 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 609 (0 ms): 0, 0, 0, 0; from 4886-4901, loops=17,chars=15,blocks 0/0 (0) contexts 0/0 (0) scancache 256
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702561 chars/s 2549 chars/run
Nothing to scan anymore, total run timer took 0 ms
scanning run 610 (0 ms): 0, 0, 0, 0; from 4886-4902, loops=18,chars=16,blocks 0/0 (0) contexts 0/0 (0) scancache 256
memory scancache 14482(339Kb+565Kb) found 6207(193Kb) fcontext 2750(64Kb) = 1163Kb
average 702569 chars/s 2545 chars/run




 --- MDM: .xsession-errors output limit reached. No more output will be written. ---
 --- Set 'LimitSessionOutput=false' in the [debug] section of /etc/mdm/mdm.conf to disable this limit. ---



```
I have uninstalled all nvidia drivers, purged all "nvidia*" from usr/lib, switched drivers to xserver.. used synaptic mainly to do it and reinstalled libgl1 today. Still in Fallback..
I fixed the "Cannot find nvidia.run" tho.. all I had to do is remove nvidia.run from my home folder.

For the drivers: everything I did, I did through either mintdrivers or synaptic.. so, nvidia-prime, settings, 352, some libcude and opengl libraries.. the standart reccommended stuff.

---

### Post by Bashing-om on 2016-06-04
Jan_Jindrek; Owweeee;

The deeper we dig the worse it looks to me .

Still booting with " plymouth:debug=1 " I do not know this as a valid boot parameter and surely do not know what damage it might cause.

And booting Intel as the graphic's set .

Are you running this as a Virtual machine ?
> 
(nemo:2926): Gtk-CRITICAL **: gtk_container_foreach: assertion 'GTK_IS_CONTAINER (container)' failed


It will take me a long bit to try and digest what I do not know . We got bad ram chips here ??
> 
cleanup_scanner, memory scancache 0(0Kb+0Kb) found 0(0Kb) fcontext 0(0Kb) = 0Kb



Presently I just do not know what to think
[INDENT][INDENT][INDENT]or what direction to go
[/INDENT][/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-06-04
Nope, no virtual machine.. I would just reinstall the system, but I have a pretty dope php server here. No bad RAM I think, computer is only 2 y/o

---

### Post by Bashing-om on 2016-06-04
Jan_Jindrek; Ok ..

Not hardware related then we say .
What is that "  plymouth:debug=1 "  boot option . Is it set in the /etc/default/grub file ?

[INDENT][INDENT]still trying to understand
[/INDENT][/INDENT]

---

### Post by mc4man on 2016-06-04
Just to note
you can't mix bumblebee & nvidia-prime
the upstream driver via the .run likely isn't a good idea with mobile/optimus chips on linux
nvidia drivers installed with the .run file should be removed (--uninstall) thru that same .run file

---

### Post by Bashing-om on 2016-06-04
@mc4man; :)

Pleased you dropped by .

[INDENT][INDENT]good things can happen
[/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-06-05
I don't have bumblebee and prime installed at once, when I tried to run --uninstall, it claimed I have no such driver in place.

Commenting this line out: ```
GRUB_CMDLINE_LINUX_DEFAULT="plymouth:debug=1"
```

Entire grub file
```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="plymouth:debug=1"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
GRUB_GFXPAYLOAD_LINUX=None

```

Edit: No changes after reboot

---

### Post by Bashing-om on 2016-06-05
Jan_Jindrek; Oh Kay ..

A small matter of concern, do we have a language barrier between us that I cause ? Is my  misuse of the English language causing a problem here in communications ?

Do I assume your skill level above actuality ? Believe me, I too have a long way to go on this learning curve, so no disrespect is meant in any form . Do I need to make adjustments ? We are working to get your system functional - whatever that might take. 
--------------------------

In small steps.
The grub edit .. after the change did you:
```

sudo update-grub

```
to propagate the change to the system ( /boot/grub/grub.cfg ) ?

Let's "find" that OEM driver:
```

sudo find / -name "NVIDIA-Linux-*"

```
Will take some time searching .. patience . With the goal to purge it from the system .

Next I think is to see what we can do to get the DE mdm in a consistent state .
Then see what we can do to get the open source driver functional in the GUI ; before we attempt any other action.

That is my plan
[INDENT][INDENT][INDENT]and I want to stick to it .
[/INDENT][/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-06-05
It's okay, really.. as long as I am just pushing commands onto the terminal it's cool. I did not know that I need to update grub, honestly, besides that it has to do something with boot, I have no idea what grub is.. I don't really do much with operating systems themselves - especially not on the boot level.
Aaanyways, code:
```

jan@localhost ~ $ sudo update-grub
[sudo] password for jan: 
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-87-generic
Found initrd image: /boot/initrd.img-3.13.0-87-generic
Found linux image: /boot/vmlinuz-3.13.0-86-generic
Found initrd image: /boot/initrd.img-3.13.0-86-generic
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found iPXE image: /boot/ipxe.lkrn
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
  No volume groups found
done
jan@localhost ~ $ sudo find / -name "NVIDIA-Linux-*"
/home/jan/Sta&#382;ené/ChromeFiles/NVIDIA-Linux-x86_64-340.32.run
/home/jan/Sta&#382;ené/ChromeFiles/NVIDIA-Linux-x86_64-355.00.09.run
/home/jan/Sta&#382;ené/ChromeFiles/NVIDIA-Linux-x86_64-343.13.run
/home/jan/Sta&#382;ené/ChromeFiles/NVIDIA-Linux-x86_64-355.00.09 (1).run
/home/jan/Sta&#382;ené/ChromeFiles/NVIDIA-Linux-x86_64-361.42.run
/home/jan/Sta&#382;ené/NVIDIA-Linux-x86_64-337.25.run

```
I'll reboot my system as soon as my legally downloading movie is finished!

---

### Post by Bashing-om on 2016-06-05
Jan_Jindrek; Right . Lots of conflicts now ..

Let's see what we can do to clean up .
We are going to move from your home directory.
We need to change directory (cd) to where the system commands sees the targets.
```

cd Sta&#382;ené/ChromeFiles/

```
now do you see the Nvidia files ?
```

ls -al 

```

If we are at the right place ( you see the Nvidia files) .. run terminal commands:
```

./NVIDIA-Linux-x86_64-340.32.run --uninstall
./NVIDIA-Linux-x86_64-355.00.09.run --uninstall
./NVIDIA-Linux-x86_64-343.13.run --uninstall
./NVIDIA-Linux-x86_64-355.00.09\ (1).run --uninstall
./NVIDIA-Linux-x86_64-361.42.run --uninstall
cd .
./NVIDIA-Linux-x86_64-337.25.run --uninstall
cd

```

Next IF those all run clean .. remove the residue:
```

sudo apt purge nvidia*

```

Now make sure we have the open source driver available:
```

sudo apt update
sudo apt upgrade
sudo rm /etc/X11/xorg.conf
sudo apt-get install xserver-xorg-video-nouveau

```

reboot:
```

sudo shutdown -r now

```

What now do you boot to ? The GUI ???

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-06-05
Ran all the commands, it kept saying that no nvidia drivers are present, did all the other commands, nothing changed, still booting in Fallback mode. But I did remember that I messed up with some libraries from /usr/lib/x86_64-gnu-linux.. libGLU I think.. I think I tried to manually replace them (yes, that stupid), so I'm going to reinstall them and show you the results after reboot!

EDIT: still in Fallback.. that was uneventful

---

### Post by Bashing-om on 2016-06-05
Jan_Jindrek;
Where did my suggested method to remove the Nvidia installers fail ?
when you cd'd to " Stažené/ChromeFiles/" and "ls -al " did you see the target files we want to remove ?

Sheeessshh .. this situation gets deeper and deeper .. and the more trying and difficult .
> 
ut I did remember that I messed up with some libraries from /usr/lib/x86_64-gnu-linux.. libGLU I think.


More than my little mind
[INDENT][INDENT][INDENT]can cope with ?
[/INDENT][/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-06-05
It didn't. I didn't install all of them. It's just not there I guess? In any case it is not detected by the nvidia file. Yeah, they are there, do you want me to uninstall or remove? I'm removing them.. the libGLU libraries.. I just had the genius idea to replace them with the libGLU libraries I found in nvidia-352 package.

---

### Post by Bashing-om on 2016-06-05
Jan_Jindrek; Yuk ...

I am having my problems keeping up with what you are doing and following your thought processes .

As there are several OEM Nvidia installers that were on the system .. did you ever at any time run the Nvidia OEM installer to install a proprietary driver ? Then we MUST uninstall with Nvidia's un-install routine .
Be aware there can be but ONE graphics driver installed for each graphics's card . Prior to installing another the former driver MUST be purged. As this system is with hybrid graphics, then there must be a means to control which graphics set is in use . As said before, I think in the case of Mint, that preferred controller is BumbleBee. However, in ubuntu, BumbleBee is depreciated in favor of nvidia-prime.

I do have in mind .. when the system is in a consistent state .. to have the system choose the driver and controller and have the system install that driver that the system chooses to install. The driver can not install until the Desktop Environment is consistent.

So where I am right now with your problem is to get all drivers removed ;
Make sure the system it's self is in a consistent state ( those libraries);
And get the DE repaired ;
Then have the system install the graphic's driver and controller .

Make sense ? It is a process and we can not go to point D unless point A B and C are accounted for.

So ... where are we in this process .. still on point A  ?

[INDENT][INDENT]which way do we go
[/INDENT][/INDENT]

---

### Post by Jan_Jindrek on 2016-06-06
Well first we must at least make the system boot into normal mode.. 
```

jan@localhost ~ $ cinnamon --replace
Xlib:  extension "GLX" missing on display ":0.0".


(cinnamon:5589): Clutter-CRITICAL **: Unable to initialize Clutter: Failed to connected to any renderer due to constraints
Window manager error: Unable to initialize Clutter.

```
As with the nvidia drivers.. the uninstall routine simply doesn't work for the one I know I installed, it doesn't work with the others I know I didn't, it just does not work.

---

### Post by mc4man on 2016-06-06
I tried a mint 17.3 cinnamon install with likely similar hardware & installing & using nvidia thru nvidia-prime works fine. 
(-I installed initially thru synaptic which  apparently mint has neutered so it needed a little help, installing from the cli was better choice.

So most likely your issues are from the .run install & subsequent mucking around. Did you try picking one of the .run files & running an install from it, then if successful running the uninstall?
Also bumblebee installs primus which must be removed for nvidia-prime.

What does this return?, with a proper nvidia install there wll be 3, when nvidia isn't installed only 1 (mesa)
```
sudo update-alternatives --list x86_64-linux-gnu_gl_conf
```

---

### Post by Jan_Jindrek on 2016-06-06
```
jan@localhost ~ $ sudo update-alternatives --list x86_64-linux-gnu_gl_conf
[sudo] password for jan: 
/usr/lib/x86_64-linux-gnu/mesa/ld.so.conf 
```

---

### Post by mc4man on 2016-06-06
Then maybe try a cli install, leave terminal open & read thru or post all
First make sure that primus isn't installed & also no ppa version of nvidia available, just normal trusty repos
```
sudo apt-get install nvidia-352
```
(- this should also install nvidia-prime, ect.

---

### Post by Jan_Jindrek on 2016-06-06
Nope, installed only nvidia-352, should I install prime and nvidia-settings?
```

DKMS: install completed.
Processing triggers for initramfs-tools (0.103ubuntu4.3) ...
update-initramfs: Generating /boot/initrd.img-3.19.0-32-generic
grep: /boot/config-3.19.0-32-generic: Adresá&#345; nebo soubor neexistuje
Warning: No support for locale: cs_CZ.utf8
depmod: WARNING: could not open /tmp/mkinitramfs_biS60B/lib/modules/3.19.0-32-generic/modules.builtin: No such file or directory

```
Okay, this seems like a problem to me?

---

### Post by mc4man on 2016-06-06
Odd, from command line it should install the recommends, did so here. 
(mint seems to set synaptic to not install recommends & also doesn't allow synaptic to install updates. Seems they want to control what is updated..
What would have been of interest would have been the complete terminal output, did the kernel  modules build & was update-alternatives updated?

The depmod warning is somewhat a concern, not normal..
I'll be back at the machine that has mint in a few hrs., at a min. you'd need this installed, the applet doesn't quite matter though useful - 
```
$ dpkg -l | grep -i nvidia
ii  bbswitch-dkms                  0.7-2ubuntu1                         amd64        Interface for toggling the power on nVidia Optimus video cards
ii  nvidia-352                     352.63-0ubuntu0.14.04.1              amd64        NVIDIA binary driver - version 352.63
ii  nvidia-prime                   0.6.2linuxmint1                      amd64        Tools to enable NVIDIA's Prime
ii  nvidia-prime-applet            1.0.3                                all          An applet for NVIDIA Prime
ii  nvidia-settings                331.20-0ubuntu8                      amd64        Tool for configuring the NVIDIA graphics driver
```

---

### Post by Jan_Jindrek on 2016-06-06
```

jan@localhost ~ $ sudo apt-get install nvidia-352
[sudo] password for jan: 
&#268;tu seznamy balík&#367;&#8230; Hotovo
Vytvá&#345;í se strom závislostí       
&#268;tu stavové informace&#8230; Hotovo
Následující balíky byly nainstalovány automaticky a ji&#382; nejsou pot&#345;eba:
  ktorrent-data libbs2b0 libfdk-aac1 libguess1 libktorrent-l10n libktorrent5
  libsoxr0 libsvga1 libuchardet0 primus-libs screen-resolution-extra
Pro jejich odstran&#283;ní pou&#382;ijte &#8222;apt-get autoremove&#8220;.
Doporu&#269;ované balíky:
  nvidia-settings nvidia-prime bumblebee libcuda1-352 nvidia-opencl-icd-352
Následující NOVÉ balíky budou nainstalovány:
  nvidia-352
0 aktualizováno, 1 nov&#283; instalováno, 0 k odstran&#283;ní a 11 neaktualizováno.
Pot&#345;ebuji stáhnout 0 B/60,4 MB archiv&#367;.
Po této operaci bude na disku pou&#382;ito dal&#353;ích 300 MB.
Vybírám dosud nevybraný balík nvidia-352.
(&#268;tu databázi &#8230; nyní je nainstalováno 458753 soubor&#367; a adresá&#345;&#367;.)
Preparing to unpack &#8230;/nvidia-352_352.63-0ubuntu0.14.04.1_amd64.deb ...
Unpacking nvidia-352 (352.63-0ubuntu0.14.04.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Nastavuji balík nvidia-352 (352.63-0ubuntu0.14.04.1) &#8230;
update-alternatives: pou&#382;ívám /usr/lib/nvidia-352/ld.so.conf pro poskytnutí /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf), automatický re&#382;im
update-alternatives: pou&#382;ívám /usr/lib/nvidia-352/alt_ld.so.conf pro poskytnutí /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf), automatický re&#382;im
update-alternatives: pou&#382;ívám /usr/share/nvidia-352/glamor.conf pro poskytnutí /usr/share/X11/xorg.conf.d/glamoregl.conf (glamor_conf), automatický re&#382;im
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-352                                                                     
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude                        
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad                      
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here                 
P&#345;idávám systémového u&#382;ivatele &#8222;nvidia-persistenced&#8220; (UID 116)&#8230;
P&#345;idávám novou skupinu &#8222;nvidia-persistenced&#8220; (GID 127)&#8230;
P&#345;idávám nového u&#382;ivatele &#8222;nvidia-persistenced&#8220; (UID 116) se skupinou &#8222;nvidia-persistenced&#8220;&#8230;
Nevytvá&#345;ím domovský adresá&#345; &#8222;/&#8220;.
Loading new nvidia-352-352.63 DKMS files...
First Installation: checking all kernels...
Building only for 3.13.0-87-generic
Building for architecture x86_64
Building initial module for 3.13.0-87-generic
Done.


nvidia_352:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-87-generic/kernel/drivers/char/drm/


nvidia_352_uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-87-generic/kernel/drivers/video/


depmod..........


DKMS: install completed.
Processing triggers for initramfs-tools (0.103ubuntu4.3) ...
update-initramfs: Generating /boot/initrd.img-3.19.0-32-generic
grep: /boot/config-3.19.0-32-generic: Adresá&#345; nebo soubor neexistuje
Warning: No support for locale: cs_CZ.utf8
depmod: WARNING: could not open /tmp/mkinitramfs_biS60B/lib/modules/3.19.0-32-generic/modules.builtin: No such file or directory
jan@localhost ~ $ 



```

---

### Post by mc4man on 2016-06-06
Seems i can't make a direct comparison as the current  mint is using 14.04.3 (lts-vivid) kernel, ex. of nvidia install below. 
I don't think that last depmod thing is that big of a concern, did you ever have 3.19.0-XX kernel installed?
So - when you reboot what happens?

Ex. here - 
```
 doug@doug-Lenovo-IdeaPad-Y510P ~ $ sudo apt-get install nvidia-352
[sudo] password for doug: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bbswitch-dkms lib32gcc1 libc6-i386 libcuda1-352 nvidia-opencl-icd-352
  nvidia-prime nvidia-settings screen-resolution-extra
Suggested packages:
  bumblebee
The following NEW packages will be installed:
  bbswitch-dkms lib32gcc1 libc6-i386 libcuda1-352 nvidia-352
  nvidia-opencl-icd-352 nvidia-prime nvidia-settings screen-resolution-extra
0 upgraded, 9 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B/79.4 MB of archives.
After this operation, 373 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Selecting previously unselected package libc6-i386.
(Reading database ... 162679 files and directories currently installed.)
Preparing to unpack .../libc6-i386_2.19-0ubuntu6.9_amd64.deb ...
Unpacking libc6-i386 (2.19-0ubuntu6.9) ...
Replaced by files in installed package libc6:i386 (2.19-0ubuntu6.9) ...
Selecting previously unselected package libcuda1-352.
Preparing to unpack .../libcuda1-352_352.63-0ubuntu0.14.04.1_amd64.deb ...
Unpacking libcuda1-352 (352.63-0ubuntu0.14.04.1) ...
Selecting previously unselected package lib32gcc1.
Preparing to unpack .../lib32gcc1_1%3a4.9.3-0ubuntu4_amd64.deb ...
Unpacking lib32gcc1 (1:4.9.3-0ubuntu4) ...
Selecting previously unselected package nvidia-352.
Preparing to unpack .../nvidia-352_352.63-0ubuntu0.14.04.1_amd64.deb ...
Unpacking nvidia-352 (352.63-0ubuntu0.14.04.1) ...
Selecting previously unselected package nvidia-opencl-icd-352.
Preparing to unpack .../nvidia-opencl-icd-352_352.63-0ubuntu0.14.04.1_amd64.deb ...
Unpacking nvidia-opencl-icd-352 (352.63-0ubuntu0.14.04.1) ...
Selecting previously unselected package bbswitch-dkms.
Preparing to unpack .../bbswitch-dkms_0.7-2ubuntu1_amd64.deb ...
Unpacking bbswitch-dkms (0.7-2ubuntu1) ...
Selecting previously unselected package nvidia-prime.
Preparing to unpack .../nvidia-prime_0.6.2linuxmint1_amd64.deb ...
Unpacking nvidia-prime (0.6.2linuxmint1) ...
Selecting previously unselected package screen-resolution-extra.
Preparing to unpack .../screen-resolution-extra_0.17.1_all.deb ...
Unpacking screen-resolution-extra (0.17.1) ...
Selecting previously unselected package nvidia-settings.
Preparing to unpack .../nvidia-settings_331.20-0ubuntu8_amd64.deb ...
Unpacking nvidia-settings (331.20-0ubuntu8) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Setting up libc6-i386 (2.19-0ubuntu6.9) ...
Setting up libcuda1-352 (352.63-0ubuntu0.14.04.1) ...
Setting up lib32gcc1 (1:4.9.3-0ubuntu4) ...
Setting up nvidia-352 (352.63-0ubuntu0.14.04.1) ...
update-alternatives: using /usr/lib/nvidia-352/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-352/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/share/nvidia-352/glamor.conf to provide /usr/share/X11/xorg.conf.d/glamoregl.conf (glamor_conf) in auto mode
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-352
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
Adding system user `nvidia-persistenced' (UID 115) ...
Adding new group `nvidia-persistenced' (GID 124) ...
Adding new user `nvidia-persistenced' (UID 115) with group `nvidia-persistenced' ...
Not creating home directory `/'.
Loading new nvidia-352-352.63 DKMS files...
First Installation: checking all kernels...
Building only for 3.19.0-32-generic
Building for architecture x86_64
Building initial module for 3.19.0-32-generic
Done.

nvidia_352:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-32-generic/kernel/drivers/char/drm/

nvidia_352_uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-32-generic/kernel/drivers/video/

depmod....

DKMS: install completed.
Setting up nvidia-opencl-icd-352 (352.63-0ubuntu0.14.04.1) ...
Setting up bbswitch-dkms (0.7-2ubuntu1) ...
Loading new bbswitch-0.7 DKMS files...
First Installation: checking all kernels...
Building only for 3.19.0-32-generic
Building initial module for 3.19.0-32-generic
Done.

bbswitch:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.19.0-32-generic/kernel/drivers/acpi/

depmod....

DKMS: install completed.
Setting up nvidia-prime (0.6.2linuxmint1) ...
nvidia-prime start/running, process 7870
Setting up screen-resolution-extra (0.17.1) ...
Setting up nvidia-settings (331.20-0ubuntu8) ...
Processing triggers for libc-bin (2.19-0ubuntu6.9) ...
Processing triggers for initramfs-tools (0.103ubuntu4.3) ...
update-initramfs: Generating /boot/initrd.img-3.19.0-32-generic
Warning: No support for locale: en_US.utf8
Processing triggers for ureadahead (0.100.0-16) ...

```

---

### Post by Jan_Jindrek on 2016-06-06
if I reboot with prime-select nvidia, all I get is a black screen, startx stop at NVCONTROL.. if I reboot with prime-select intel, I get fallback. Still the same situation.

---

