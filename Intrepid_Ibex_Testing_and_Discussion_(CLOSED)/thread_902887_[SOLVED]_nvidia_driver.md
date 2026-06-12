---
title: "[SOLVED] nvidia driver"
date: 2008-08-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by gmxgeek on 2008-08-27
Since the latest update, I have been unable to load my nvidia drivers. They used to work, but since the update, it's been 'nv' drivers for me. 

If I use this in my Device Section
```

Driver "nv"

```
It works fine, but without many useful things like multiple monitors. On the other hand, if I use this:
```

Driver "nvidia"

```
Then it fails and defaults to the vesa drivers, and runs xorg.conf.failsafe

Attached Files
----------------------

log.txt = /var/log/Xorg.0.log when trying to use nvidia driver
log2.txt = /var/log/Xorg.0.log when trying to use nv driver

[ETC ETC ETC] means i cut out much of the same stuff to make the files small enough to upload



Does anyone know why it is going to failsafe when trying to load nvidia?

---

### Post by decard_pain on 2008-08-27
i have same problem ..it's to do with the new kernal.i'm going to try building my driver ..i'll post back if it works

---

### Post by cariboo on 2008-08-27
I a little extra research would have helped both of you, see this thread:

[http://ubuntuforums.org/showthread.php?t=896390](http://ubuntuforums.org/showthread.php?t=896390)

Check out post #74

Jim

---

### Post by gmxgeek on 2008-08-27
Thanks for the quick response, but no dice

```

fieldsm@GATZ:~$ ls -l /var/lib/dkms/nvidia/
total 8
drwxr-xr-x 5 root root 4096 2008-08-22 16:35 177.68
lrwxrwxrwx 1 root root   31 2008-08-22 16:27 kernel-2.6.24-21-generic-x86_64 -> 177.68/2.6.24-21-generic/x86_64
lrwxrwxrwx 1 root root   30 2008-08-22 16:35 kernel-2.6.26-5-generic-x86_64 -> 177.68/2.6.26-5-generic/x86_64
drwxr-xr-x 3 root root 4096 2008-08-22 16:27 original_module
fieldsm@GATZ:~$ 

```

also using kernel 2.6.26-5, not -2.6.27-1


EDIT:
Will try upgrading kernel version first

---

### Post by Nullack on 2008-08-27
Dont manually build the driver. Use the repo's tools.

Heres the fix:

First synch to the main repo to not get any proxy delay from a proxy

cd /var/lib/dkms/nvidia
sudo rm -fR 177.13 177.67
sudo apt-get install --reinstall linux-image-2.6.27-1-generic

---

### Post by bballa23523 on 2008-08-27
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by gmxgeek on 2008-08-27
Okay, so now i have the latest and greatest everything. Here is the contents of /var/lib/dkms/nvidia
```

total 8
drwxr-xr-x 6 root root 4096 2008-08-27 19:50 177.68
lrwxrwxrwx 1 root root   31 2008-08-22 16:27 kernel-2.6.24-21-generic-x86_64 -> 177.68/2.6.24-21-generic/x86_64
lrwxrwxrwx 1 root root   30 2008-08-22 16:35 kernel-2.6.26-5-generic-x86_64 -> 177.68/2.6.26-5-generic/x86_64
lrwxrwxrwx 1 root root   30 2008-08-27 19:50 kernel-2.6.27-1-generic-x86_64 -> 177.68/2.6.27-1-generic/x86_64
drwxr-xr-x 3 root root 4096 2008-08-22 16:27 original_module

```

nv driver still works, nvidia driver still doesn't.
Also, I now get a message about MP_BIOS bug: timer not connected to IO_APIC...

---

### Post by Gourgi on 2008-08-27
> **gmxgeek said:**
> Okay, so now i have the latest and greatest everything. Here is the contents of /var/lib/dkms/nvidia
```

total 8
drwxr-xr-x 6 root root 4096 2008-08-27 19:50 177.68
lrwxrwxrwx 1 root root   31 2008-08-22 16:27 kernel-2.6.24-21-generic-x86_64 -> 177.68/2.6.24-21-generic/x86_64
lrwxrwxrwx 1 root root   30 2008-08-22 16:35 kernel-2.6.26-5-generic-x86_64 -> 177.68/2.6.26-5-generic/x86_64
lrwxrwxrwx 1 root root   30 2008-08-27 19:50 kernel-2.6.27-1-generic-x86_64 -> 177.68/2.6.27-1-generic/x86_64
drwxr-xr-x 3 root root 4096 2008-08-22 16:27 original_module

```
nv driver still works, nvidia driver still doesn't.

confirming this with same driver and nvidia 6600gt

---

### Post by Nullack on 2008-08-27
If your still having problems its because youve messed around with compiling your own driver and your now in a messy state. Youll need to do further manual cleanup.

---

### Post by gmxgeek on 2008-08-27
No, all my stuff is from synaptic, no manual aything...

---

### Post by LemurApocalypse on 2008-08-27
Er, my understanding is that gmxgeek did NOT compile his own driver. I'm having a similar issue with repo drivers only.

---

### Post by decard_pain on 2008-08-27
again my problem seems worse.i didn't build the driver.
seems this kernal cant tell what my card is anymore and as a result gives me no drivers to pick from the list.
worse   is same result from an 8.4 install with upgrade.
same result from daily build aswell

---

### Post by gmxgeek on 2008-08-27
> **LemurApocalypse said:**
> Er, my understanding is that gmxgeek did NOT compile his own driver. I'm having a similar issue with repo drivers only.

Yes, all of my drivers are straight from syn. I am going to reinstall all of my nvidia stuff now, which should rebuild the modules from my understanding. We'll se if this fixes it. *Reboot*

---

### Post by gmxgeek on 2008-08-27
> **decard_pain said:**
> again my problem seems worse.i didn't build the driver.
seems this kernal cant tell what my card is anymore and as a result gives me no drivers to pick from the list.
worse   is same result from an 8.4 install with upgrade.
same result from daily build aswell

Do you have the modaliases installed? The drivers won't show in Jockey unless you do.

---

### Post by gmxgeek on 2008-08-27
Still no dice. This is getting annoying. Anyone have any idea?

---

### Post by decard_pain on 2008-08-27
yes seems i removed it at some point..i can see it now..
but back to original problem of them not working on reboot .i get the display and vidio card screen again

my card is an old geforce fx 5600 by the way

---

### Post by gmxgeek on 2008-08-27
> **decard_pain said:**
> yes seems i removed it at some point..i can see it now..
but back to original problem of them not working on reboot .i get the display and vidio card screen again

Explain? You have nvidia drivers working?
Or just the control panel for them?

---

### Post by Gourgi on 2008-08-27
> **gmxgeek said:**
> Explain? You have nvidia drivers working?
Or just the control panel for them?
after installing modaliases i just have jockey telling me that they are in use (!) but nvidia-settings telling me that they are not

i'm still in nv

---

### Post by decard_pain on 2008-08-27
well i can see them in the restricted driver list.i enable it.log out to reboot and .thats as far as i get..xserver config kicks in asking me my vidio card and display type

---

### Post by gmxgeek on 2008-08-27
> **Gourgi said:**
> after installing modaliases i just have jockey telling me that they are in use (!) but nvidia-settings telling me that they are not

i'm still in nv

If you are in nv, then nvidia-settings won't work, as you are not using the nvidia driver.

---

### Post by gmxgeek on 2008-08-27
> **decard_pain said:**
> well i can see them in the restricted driver list.i enable it.log out to reboot and .thats as far as i get..xserver config kicks in asking me my vidio card and display type

Yup same here. Welcome to the party. Drinks are on the table, kick your feet up and stay awhile. :)

---

### Post by decard_pain on 2008-08-27
no the driver fails and i have to go back to nv

---

### Post by gmxgeek on 2008-08-27
Yes, i think the concensus is that if the nvidia drivers are enabled and in use, then xserver kicks in failsafe, defaulting to vesa, and low res. If not nvidia drivers, (nv is in use), then display looks alright, but no advanced gfx. At least, that is the current situation for me.

* Using latest version of kernel
* All packages are up to date
* nVidia drivers installed through synaptic
* /var/lib/dkms/nvida only has 177.38 and the generic ones
* 'Driver "nv"' uses xorg.conf
* 'Driver "nvidia"' uses xorg.conf.failsafe

---

### Post by Nullack on 2008-08-27
Reasons why it still doesnt work after you have followed the fix instructions and you *did not compile your own driver* earlier:

1. You didnt run the fix instructions correctly
2. You have some non-default weirdness in your xorg.conf and/or you ran nvidia's xconfig tool rather than letting the repo package install and configure xorg

---

### Post by decard_pain on 2008-08-27
yes thats exactly the problem.

---

### Post by gmxgeek on 2008-08-27
Can I give you some terminal output to determine if I did not follow your instructions, as earlier I copied and pasted them into terminal...

I will post my current xorg.conf using nvidia drivers

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@crested)  Sun Aug 10 11:14:56 UTC 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

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
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic VX2245wm"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL E197FP"
    HorizSync       31.0 - 80.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GTS"
    BusID          "PCI:1:0:0"
    Screen          0
    Option         "CustomEDID" "DFP-0:/home/fieldsm/.nVidia-edid/edid.bin"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GTS"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "DFP-0: 1680x1050_60_0 +0+0; DFP-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

And that exact same config works fine if i replace nvidia with nv, i just don't get accellerated gfx, etc

---

### Post by Gourgi on 2008-08-27
> **Nullack]
Reasons why it still doesnt work after you have followed the fix instructions and you *did not compile your own driver* earlier:

1. You didnt run the fix instructions correctly
2. You have some non-default weirdness in your xorg.conf and/or you ran nvidia's xconfig tool rather than letting the repo package install and configure xorg
[/QUOTE]
1. i did 
2. i don't think so,
i attach 2 xorg. :
this is using the 'try to fix X server' option from intrepid's Grub recovery 
```
 
# xorg.conf (X.Org X Window System server configuration file)
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

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

this is after installing nvidia-177 from synaptic
```

# xorg.conf (X.Org X Window System server configuration file)
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

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection
Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	#Uncomment if you have a wacom tablet
	#InputDevice     "stylus"        "SendCoreEvents"
	#     InputDevice     "cursor"        "SendCoreEvents"
	#     InputDevice     "eraser"        "SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection

```
after doing a reboot i still take this :
[QUOTE=gmxgeek said:**
>  if the nvidia drivers are enabled and in use, then xserver kicks in failsafe, defaulting to vesa, and low res. If not nvidia drivers, (nv is in use), then display looks alright, but no advanced gfx. 

now i use nv again.


> **gmxgeek said:**
> 
* Using latest version of kernel
* All packages are up to date
* nVidia drivers installed through synaptic
* /var/lib/dkms/nvida only has 177.38 and the generic ones
* 'Driver "nv"' uses xorg.conf
* 'Driver "nvidia"' uses xorg.conf.failsafe
me too ... 
i 'll fill a bug tomorrow about this, it's late here .

---

### Post by gmxgeek on 2008-08-27
Yeah, this sounds like more than just one person messing up their config...

---

### Post by autocrosser on 2008-08-27
I started up in low-rez & when I was to desktop--I re-installed all the nvidia stuff + the 2.6.27 restricted modules common & generic. After that I rebooted & got accelerated desktop the next log-in. Running a custom xorg-conf--I'll post it if you need it....

just my 2 pence

---

### Post by gmxgeek on 2008-08-27
> **autocrosser said:**
> I started up in low-rez & when I was to desktop--I re-installed all the nvidia stuff + the 2.6.27 restricted modules common & generic. After that I rebooted & got accelerated desktop the next log-in. Running a custom xorg-conf--I'll post it if you need it....

just my 2 pence

I just reinstalled everything nvidia, and still nothing works.
I didn't see a reinstall option for 2.6.27 restricted modules common & generic.

---

### Post by vrdabomb5717 on 2008-08-27
If you needed any further confirmation of this bug, I have the same problem too. Not sure if it's the latest kernel that's causing the problem, but nvidia drivers refuse to load, even though they are enabled. The generic driver works though, which is a relief, because at least I'm not stuck in low-graphics mode 800x600 resolution the entire time.

Using Nvidia Geforce 7600GS and Dell 1800FP monitor.

---

### Post by gmxgeek on 2008-08-27
Okay, I think that four people is enough. Filing a bug at this time.

---

### Post by autocrosser on 2008-08-27
Went to Synaptic & rechecked all of the above--worked for me--sorry 'bout your issues--will look into it a bit further....What cards/version of driver are all of you using?

---

### Post by gmxgeek on 2008-08-27
nVidia 8600 GTS / 1.77.68-0ubuntu1 using ViewSonic VX2245wm

---

### Post by vrdabomb5717 on 2008-08-27
I've tried all the available versions of the nvidia-restricted driver: version 96, 173, and 177. None of them load properly.

Again, using Nvidia 7600GS and Dell 1800FP monitor.

EDIT: according to Synaptic, 177.68.0ubuntu-1, 173.14.12-0ubuntu5, and 96.43.05-0ubuntu10 .

---

### Post by decard_pain on 2008-08-27
geforce fx 5600

---

### Post by gmxgeek on 2008-08-27
Bug Report Filed

[https://bugs.launchpad.net/ubuntu/+bug/262074](https://bugs.launchpad.net/ubuntu/+bug/262074)

---

### Post by Nullack on 2008-08-27
Please restart X in extra verbose mode and scan the log for what its doing with the nvidia driver.

---

### Post by syko21 on 2008-08-28
In the mean time uninstalling the nvidia driver with envyng and compiling the 177.67 drivers from nvidia.com works well.

---

### Post by dawynn on 2008-08-28
> **Nullack said:**
> Reasons why it still doesnt work after you have followed the fix instructions and you *did not compile your own driver* earlier:

1. You didnt run the fix instructions correctly
2. You have some non-default weirdness in your xorg.conf and/or you ran nvidia's xconfig tool rather than letting the repo package install and configure xorg

So, nvidia-xconfig is a bad thing now?  After two (was it three?) releases of training us that we must use it in order to get our older nVidia cards working, now its a bad thing?

OK -- if it messes everything up so bad, why is it still in the repositories?

I'll have to try reinstalling the nVidia modules later when I'm back at my home PC.  Are we having success now with nVidia in the 2.6.25 kernels, or just the 2.6.27?  Because I can't get the 2.6.27 kernel to boot yet (probably an issue unrelated to this nVidia thread -- please feel free to stay on topic here).

---

### Post by ronacc on 2008-08-28
just for info , using the previously posted instructions ( remove extra nvidida dirs from /var/lib/dkms/nvidia  and reinstall linux-image-2.6.27-1-generic ) the 177.68 driver works fine for my 7600gs .

---

### Post by gmxgeek on 2008-08-28
> **Nullack said:**
> Please restart X in extra verbose mode and scan the log for what its doing with the nvidia driver.

How might I go about doing that?

---

### Post by cjm5229 on 2008-08-28
I've had this problem for a couple of days now. I just reinstalled Intrepid this morning and updated it, and got the new 2.6.27.1.Kernel, and now I have I have everything working again. I think that 2.6.26.5 kernel had a problem. I do have the Intrepid proposed updates checked, and the new kernel is in the updates.

---

### Post by gmxgeek on 2008-08-28
Yeah, if this doesn't resolve in a few days, I am going to reinstall myself. Would really like to get it working without having to do that though.

---

### Post by Gourgi on 2008-08-28
after today's updates 
```

x11-apps (7.3+2) to 7.3+3
x11-xserver-utils (7.3+3) to 7.3+5
x11proto-input-dev (1.4.3-2ubuntu1) to 1.4.3-2ubuntu2
xserver-xorg-core (2:1.4.99.906-1ubuntu4) to 2:1.4.99.906-2ubuntu2
xserver-xorg-input-synaptics (0.14.7~git20070706-2.1ubuntu4) to 0.15.0+git20080820-1ubuntu1

```
i tried what i did yesterday:removed nvidia* from synaptic, reinstall 2.6.27* kernel's stuff and after required reboot i reinstalled nvidia-glx-177 from command-line.
everything is working great here now!

compiz again !:lolflag:

---

### Post by gmxgeek on 2008-08-28
Good to hear you got it working again. I will be sure to try it when I get off work.

---

### Post by waratah on 2008-08-28
My system was working fine this morning and I upgraded.

I removed everything /var/lib/dkms/nvidia and did the reinstall:

sudo aptitude reinstall linux-image-2.6.27-1-generic
...

 * Running DKMS auto installation service for kernel 2.6.27-1-generic        
 *  nvidia ()...                                                             nvidia (): AUTOINSTALL not set in its dkms.conf.

I am now switching drivers, I was on 173:

sudo apt-get install nvidia-glx-177

Unpacking nvidia-glx-177 (from .../nvidia-glx-177_177.68-0ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up nvidia-177-kernel-source (177.68-0ubuntu1) ...
Removing all DKMS Modules
Done.
Adding Module to DKMS build system
driver version= 177.68
Doing initial module build
Installing initial module
Done.

Setting up nvidia-glx-177 (177.68-0ubuntu1) ...


I am now rebooting hopefully be back soon.

OK I rebooted,  nvidia is back but I have a constant scream from the PC speaker.   Sounds like a machine gun on startup.  I will now swithc back to 173 and see if problem subsides.

---

### Post by waratah on 2008-08-28
From build log for 173:

echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\


include/asm/compat.h: In function ‘compat_alloc_user_space’:
include/asm/compat.h:210: warning: pointer of type ‘void *’ used in arithmetic
In file included from /var/lib/dkms/nvidia/173.14.12/build/nv.c:14:
/var/lib/dkms/nvidia/173.14.12/build/nv-linux.h: In function ‘nv_execute_on_all_cpus’:
/var/lib/dkms/nvidia/173.14.12/build/nv-linux.h:674: error: too many arguments to function ‘on_each_cpu’
/var/lib/dkms/nvidia/173.14.12/build/nv.c: In function ‘__nv_setup_pat_entries’:
/var/lib/dkms/nvidia/173.14.12/build/nv.c:944: warning: comparison between signed and unsigned
/var/lib/dkms/nvidia/173.14.12/build/nv.c: In function ‘__nv_restore_pat_entries’:
/var/lib/dkms/nvidia/173.14.12/build/nv.c:970: warning: comparison between signed and unsigned
/var/lib/dkms/nvidia/173.14.12/build/nv.c: In function ‘nv_kern_cpu_callback’:
/var/lib/dkms/nvidia/173.14.12/build/nv.c:1296: warning: comparison between signed and unsigned
/var/lib/dkms/nvidia/173.14.12/build/nv.c:1299: error: too many arguments to function ‘smp_call_function’
/var/lib/dkms/nvidia/173.14.12/build/nv.c:1303: warning: comparison between signed and unsigned
/var/lib/dkms/nvidia/173.14.12/build/nv.c:1306: error: too many arguments to function ‘smp_call_function’


Switching back to 177 and hopign a reboot will work!

---

### Post by gmxgeek on 2008-08-28
Okay, so i reinstalled everything nvidia, updated the kernel, and basically redid all of my packages. I did all this before, and it didn't work for whatever reason, but I suppose with some new packages it works. So, bottom line, my system is back online :)

One interesting note however. I use dual monitors, and thus have two Device sections in my xorg.conf. I used Jockey to turn on the nvidia drivers, and it ended up changing the driver for one and not the other, so i had one monitor running on nvidia, and the other on nv. Needless to say X didn't like this, and just gave me a blank screen. I changed the nv one to nvidia, and it boots up fine now. Many thanks to all who helped.

---

### Post by cjm5229 on 2008-08-29
One thing about being on the bleeding edge is, sometimes, you have to wait for the bleeding to stop before you can get the band aid to stick! :)

---

### Post by gmxgeek on 2008-08-29
> **cjm5229 said:**
> One thing about being on the bleeding edge is, sometimes, you have to wait for the bleeding to stop before you can get the band aid to stick! :)

Yeah, live on the cutting edge and you just might bleed.

---

