---
title: "cant access ubuntu after intallation"
date: 2013-08-15
forum: Installation &amp; Upgrades
---

### Post by fidel2 on 2013-08-15
Hello..

I have a HP pavilion 15 laptop with windows 8 and I "install" (or at least I think so) ubuntu with a liveUSB following the steps in this [guide]("https://help.ubuntu.com/community/UEFI"). the first thing that i noticed is that the option "Try Ubuntu" doesnt work, it prompts out the command line. 

I did the installation either way using the first option (keeping both Windows 8 and ubuntu) and when I restart it at the end it goes directly into windows no grub or anything.

I read that the best thing to do is to go into ubuntu with the liveUSB and use Boot restore but I cant as you know..

thanks for the help!

PS: ubuntu got installed because i see less space in the HD when i get into windows

---

### Post by fidel2 on 2013-08-20
Hi!..

Here goes my second change (my last post didnt get a reply and am still stuck at this)

this is my hardware:
HP Pavilion 15z laptop. AMD A4 5000, 4Gb RAM and AMD Radeon HD 8330

I installed (using a liveUSB) Ubuntu 12.04 (ubuntu-12.04.2-desktop-amd64). Since the start I could not use the "Try ubuntu" option because it will go into text mode so I decided to install it anyways. 

I did the installation with no problem (Graphical installation) but when I restarted the computer it went straight into text mode. 

I Try with "startx" but it shows the following error

```
[  3666.497] X.Org X Server 1.13.0
Release Date: 2012-09-05


[  3666.502] X Protocol Version 11, Revision 0


[  3666.503] Build Operating System: Linux 2.6.42-35-generic x86_64 Ubuntu


[  3666.504] Current Operating System: Linux axl456-laptop 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:13:26 UTC 2013 x86_64


[  3666.504] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-23-generic root=UUID=267c65b6-c9bd-4ea3-bda9-a8fbb084100a ro quiet splash vt.handoff=7


[  3666.507] Build Date: 19 January 2013  12:37:44PM


[  3666.509] xorg-server 2:1.13.0-0ubuntu6.1~precise2 (For technical support please see http://www.ubuntu.com/support) 


[  3666.511] Current version of pixman: 0.24.4


[  3666.514]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.


[  3666.514] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.


[  3666.521] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 20 18:38:43 2013


[  3666.523] (==) Using config file: "/etc/X11/xorg.conf"


[  3666.525] (==) Using system config directory "/usr/share/X11/xorg.conf.d"


[  3666.526] (==) No Layout section.  Using the first Screen section.


[  3666.526] (**) |-->Screen "Default Screen" (0)


[  3666.526] (**) |   |-->Monitor "Configured Monitor"


[  3666.526] (**) |   |-->Device "Configured Video Device"


[  3666.526] (==) Automatically adding devices


[  3666.526] (==) Automatically enabling devices


[  3666.526] (==) Automatically adding GPU devices


[  3666.526] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.


[  3666.526]     Entry deleted from font path.


[  3666.526] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.


[  3666.526]     Entry deleted from font path.


[  3666.526] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.


[  3666.526]     Entry deleted from font path.


[  3666.526] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.


[  3666.527]     Entry deleted from font path.


[  3666.527] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.


[  3666.527]     Entry deleted from font path.


[  3666.527] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.


[  3666.527]     Entry deleted from font path.


[  3666.527] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins


[  3666.527] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"


[  3666.527] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.


[  3666.527] (II) Loader magic: 0x7ff66f54dc20


[  3666.527] (II) Module ABI versions:


[  3666.527]     X.Org ANSI C Emulation: 0.4


[  3666.527]     X.Org Video Driver: 13.0


[  3666.527]     X.Org XInput driver : 18.0


[  3666.527]     X.Org Server Extension : 7.0


[  3666.529] (--) PCI:*(0:0:1:0) 1002:9832:103c:2139 rev 0, Mem @ 0xe0000000/268435456, 0xf0800000/8388608, 0xf0300000/262144, I/O @ 0x00005000/256, BIOS @ 0x????????/131072


[  3666.529] (II) Open ACPI successful (/var/run/acpid.socket)


[  3666.531] Initializing built-in extension Generic Event Extension


[  3666.533] Initializing built-in extension SHAPE


[  3666.535] Initializing built-in extension MIT-SHM


[  3666.537] Initializing built-in extension XInputExtension


[  3666.539] Initializing built-in extension XTEST


[  3666.541] Initializing built-in extension BIG-REQUESTS


[  3666.543] Initializing built-in extension SYNC


[  3666.545] Initializing built-in extension XKEYBOARD


[  3666.547] Initializing built-in extension XC-MISC


[  3666.548] Initializing built-in extension SECURITY


[  3666.550] Initializing built-in extension XINERAMA


[  3666.552] Initializing built-in extension XFIXES


[  3666.554] Initializing built-in extension RENDER


[  3666.556] Initializing built-in extension RANDR


[  3666.558] Initializing built-in extension COMPOSITE


[  3666.559] Initializing built-in extension DAMAGE


[  3666.561] Initializing built-in extension MIT-SCREEN-SAVER


[  3666.563] Initializing built-in extension DOUBLE-BUFFER


[  3666.565] Initializing built-in extension RECORD


[  3666.566] Initializing built-in extension DPMS


[  3666.568] Initializing built-in extension X-Resource


[  3666.569] Initializing built-in extension XVideo


[  3666.571] Initializing built-in extension XVideo-MotionCompensation


[  3666.573] Initializing built-in extension XFree86-VidModeExtension


[  3666.574] Initializing built-in extension XFree86-DGA


[  3666.576] Initializing built-in extension XFree86-DRI


[  3666.577] Initializing built-in extension DRI2


[  3666.577] (II) LoadModule: "glx"


[  3666.578] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so


[  3666.578] (II) Module glx: vendor="Advanced Micro Devices, Inc."


[  3666.578]     compiled for 6.9.0, module version = 1.0.0


[  3666.580] Loading extension GLX


[  3666.580] (II) LoadModule: "vesa"


[  3666.580] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so


[  3666.580] (II) Module vesa: vendor="X.Org Foundation"


[  3666.580]     compiled for 1.13.0, module version = 2.3.2


[  3666.580]     Module class: X.Org Video Driver


[  3666.580]     ABI class: X.Org Video Driver, version 13.0


[  3666.580] (II) VESA: driver for VESA chipsets: vesa


[  3666.580] (--) using VT number 7




[  3666.587] (II) Loading sub module "vbe"


[  3666.587] (II) LoadModule: "vbe"


[  3666.588] (II) Loading /usr/lib/xorg/modules/libvbe.so


[  3666.588] (II) Module vbe: vendor="X.Org Foundation"


[  3666.588]     compiled for 1.13.0, module version = 1.1.0


[  3666.588]     ABI class: X.Org Video Driver, version 13.0


[  3666.588] (II) Loading sub module "int10"


[  3666.588] (II) LoadModule: "int10"


[  3666.588] (II) Loading /usr/lib/xorg/modules/libint10.so


[  3666.589] (II) Module int10: vendor="X.Org Foundation"


[  3666.589]     compiled for 1.13.0, module version = 1.0.0


[  3666.589]     ABI class: X.Org Video Driver, version 13.0


[  3666.589] (II) VESA(0): initializing int10


[  3666.590] (EE) VESA(0): V_BIOS address 0x0 out of range


[  3666.590] (II) UnloadModule: "vesa"


[  3666.590] (II) UnloadSubModule: "int10"


[  3666.590] (II) Unloading int10


[  3666.590] (II) UnloadSubModule: "vbe"


[  3666.590] (II) Unloading vbe


[  3666.590] (EE) Screen(s) found, but none have a usable configuration.


[  3666.590] 
Fatal server error:


[  3666.590] no screens found


[  3666.590] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 


[  3666.590] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.


[  3666.590] (EE)
 
[  3666.611] Server terminated with error (1). Closing log file.



```

---

### Post by Quackers on 2013-08-20
Just so as you don't think you're just being ignored again I would say that you may have a graphics card problem. That is to say that your graphics card won't play nicely with Ubuntu.
It may be that a boot option such as "nomodeset" would get the live cd booting (but that's just a guess I'm afraid). I would try a couple of different boot options in the ubuntu mode.
When the live cd/usb boots does the screen go purple at all? If it does press F6 and select your language on the next screen then on the following screen you should see at the bottom right some boot options,  one of which will be nomodeset, which I would try first.
You could also try googling for boot options for your graphics card.
Good luck.

---

### Post by QIII on 2013-08-20
*Threads **merged.***

Sometimes questions go unanswered and fall through the cracks.  Rather than starting a new thread, just give it 24 hours and "bump" it back up to the top by adding a new post with just the word "bump" to get it up where it will be seen again.

The problem with duplicate threads is that people might start answering in two places, diluting everyone's effort to help.

Don't take a missed thread as a snub.  The community is world-wide and sometimes the person with just the right answer isn't around when you post.  We're all here to help, so don't be bashful about a 24 hour bump.  If you want, you can do a 36 hour bump to see if someone in a different time zone will see your question and pick it up.

Cheers and best wishes!

---

### Post by jonnyboysmithy on 2013-08-20
There have been a lot of changes in the 3.11 kernel. 
Your card is Radeon HD 8330 right? Support for the Radeon HD 8000 has been added. (see: [http://www.phoronix.com/scan.php?page=news_item&px=MTQ0MDY](http://www.phoronix.com/scan.php?page=news_item&px=MTQ0MDY) )
Maybe if you try booting with the 3.11 kernel you may just get lucky ;)
You can get the latest kernel here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11-rc6-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.11-rc6-saucy/)

---

### Post by fidel2 on 2013-08-21
thanks everyone for the replies.. I understand that sometimes questions go [COLOR=#000000]unanswered, Sorry for the trouble my double post caused..

am going to try everything you guys commented and Ill be back with the update.

Thanks...[/COLOR]

---

### Post by fidel2 on 2013-08-21
I tried nomodeset and sadly it doesnt do the trick, then I installed the 3.11 rc6 kernel and it doesnt do the trick either..

If the video card is not compatible with linux those that meant that I have to settle with Windows 8? :(

---

### Post by fidel2 on 2013-08-23
bump

---

### Post by fidel2 on 2013-08-27
last bump

---

### Post by Quackers on 2013-08-27
If Windows is still booting directly it means that grub has not been installed to the drive. Does your system use BIOS or (U)EFI? The installation of each may differ.

Also the 13-04 version has newer kernels and may be more suited to your system - but that's just a guess. It could be worth a try but the question above needs answering.

---

### Post by Quackers on 2013-08-27
Actually forget the above. I see you are using UEFI.
Which version of Ubuntu did you download? I know it was 12-04 but was it the desktop version?

---

### Post by fidel2 on 2013-08-28
Hi Quackers thanks for the reply.

Grub was suscessfully installed because if I hit f9 in the BIOS am able to directly boot into Ubuntu and I get the GRUB2 selection window (I installed the desktop version for amd64).

I think that the problem is solved because I can now get the graphical interface when I boot into linux!.

I did the following.


reinstalled xserver-xorg and xserver-xorg-amdcccle
Run X -configure (I got some errors here but was able to create the correct xorg.conf file)
then copy and paste the xorg.conf to the /etc/X11 directory
reboot system


with that I was able to get "basic" video with no hardware aceleration and yada yada (the mouse is sometimes flickering and stuffs)

The next problem was that the touchpad didnt work, so I installed xserver-xorg-input-synaptics (I think thats the one sorry I dont remember clearly)


So basically am OK, but I dont have any wifi and the video looks a little simple but with one battle down I can continue to fight the war.

Thanks everyone for your support and sugestions!..

---

### Post by mike105 on 2013-09-22
I have the same graphics card,this is how I got 13.04 to load up in gui mode,

Once you're in the terminal after the gui fails to load type this into the terminal

[B]sudo Xorg -configure (press enter)

sudo cp xorg.conf.new /etc/X11/xorg.conf (press enter)

startx (press enter)[/B]

This will load up the gui next you will have to download 13.8 beta catalyst driver from AMD, do a google search on installing .run files.

There's one caveat,last week after installing some updates the gui quit working and once again returned me to the terminal upon next restart.I didn't try to figure out what the problem was I just installed 12.04 LTS and I'm going to wait for the final release of 13.10.GOOD LUCK

---

