---
title: "Problem with installing NVIDIA 169.12 drivers on ubuntu 169.12: don't work after rest"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by rezaf_2000 on 2008-03-07
I'm trying to install the latest CUDA enabled NVIDIA drivers (either 169.09 or 169.12) on my freshly installed ubuntu 7.10. I have an Athlon 64 3700+ with 1GB ram, and 8600GT XFX card (256MB ram).

The ubuntu installation itself goes without a hitch. I then do the following: 

-1. Install ubuntu. Update ubuntu.
0. After ubuntu installation, "sudo apt-get install build-essential", which is required for steps 3 and 4.
1. download the driver package from Nnidia's website.
2. sudo telinit 1
3. Once X server dies, I install it using "sh NVIDIA-linux-......"
4. Installation completes.
5. sudo telinit 5
6. NVIDIA fullscreen logo shows for a second.
7. X restarts. Everything is fine. correct resolution. no problems here. 
8. But later, when I restart the system, the NVIDIA drivers apparently cannot be found. system always restarts in 640*480 mode (or maybe 800*600, I'm not sure, and is irrelevant). 
9. The only way to revive the system again is to redo the whole process, which again dies with the next system restart. 


Alternatively, I tried using Envy 0.9.10. the same results. Once I restart, the drivers are lost.

BTW, I did this installation process on another machine at my office, and it works perfectly there (Intel pentium 4, NVIDIA NVS 285)


What should I do? All I can think of at this stage is to move to another distro, but I love working in ubuntu!

(btw, this is my very first post in ubuntuforums!)

---

### Post by PmDematagoda on 2008-03-07
This problem maybe related to conflicting drivers, try doing this:-

1) Open a modules file for editing using:-
```
gksudo gedit /etc/default/linux-restricted-modules-common
```

2) Edit the DISABLED_MODULES line to make it look like this:-
```
DISABLED_MODULES="nv nvidia_new"
```
and save the file.

3) Reconfigure the X-Server(you need to kill the GUI) with:-
```
sudo dpkg-reconfigure xserver-xorg
```
then reboot the system and see if the problem is now solved.

---

### Post by rezaf_2000 on 2008-03-07
Thanks for the reply, but I don't think it will solve my problem. I'm trying it now, but if I'm not wrong, you're telling me to disable the NVIDIA-supplied driver and use the open source driver that comes with ubuntu. Well, I know that it would solve the problem, but I need NVIDIA drivers for their CUDA support, which is not provided by the open source driver.

Edit: As I thought, disabling the NVIDIA drivers and going back to the open source ones solves the issue, but isnt' the solution to my problem. I really need to get the NVIDIA drivers set on my machine, as I need the CUDA capabilities.

---

### Post by PmDematagoda on 2008-03-07
You have completely misunderstood me.

I am attempting to disable the open-source nv driver and the Ubuntu provided nvidia_new driver not the other way around. While I cannot 100% guarantee the success of this method it still has been rather successful for many people before.

---

### Post by PmDematagoda on 2008-03-07
> **rezaf_2000 said:**
> Edit: As I thought, disabling the NVIDIA drivers and going back to the open source ones solves the issue, but isnt' the solution to my problem. I really need to get the NVIDIA drivers set on my machine, as I need the CUDA capabilities.

Please check your drivers, can you use compositing effects such as Compiz-Fusion?

---

### Post by rezaf_2000 on 2008-03-07
No, when I try to activate compiz in "Appearance", it tells me it needs to enable the NVIDIA proprietary  drivers. If I let it activate it and restart for it to take effect, it will again restart in low graphics mode, warning that the driver was not found:

"Ubuntu is running in low-graphics mode

Your screen and graphics card could not be detected correctly. To use higher resolutions, visual effects aor multiple screens, you have to configure the display yourself"

---

### Post by PmDematagoda on 2008-03-07
By telling the Restricted Drivers Manger to enable the Nvidia driver I think you may have gone back to square one.

Please check the modules file again to see if the edits are still there, it they are then remove or disable the Nvidia driver, reinstall the Nvida driver using the downloaded installer and then see if you can enable Compiz-Fusion.

---

### Post by rezaf_2000 on 2008-03-07
Thanks again. I have to follow up on it tonight, as I'm at work now. Thanks for following up  with this issue.

---

### Post by art_erickson on 2008-03-08
I hope rezaf let's us know how this turns out for him.  Here's what I am experiencing:

I can install the 169.12 driver and verify the version in the Nvidia X Server Settings app.

If I go to the Restricted Drivers manager and enable the Nvidia driver there then the Nvidia X Server Settings app reports the old version of 100.14 (if memory servers).

From what I read here the Restricted Drivers manager overrides the installed Nvidia driver with an open source driver.  Is that correct?

The reason I'm dinking around with this at all is I am trying to get the Compiz 3D function to work.  I get all the other Compiz features but not 3D.  I was hoping the newer Nvidia driver would do the trick.  It may be because I'm running the AMD64 OS but I can't verify that.  I keep trolling around the forums hoping to stumble across a thread with the same/similar issue where the issue was resolved.

---

### Post by art_erickson on 2008-03-11
Oh well, another dead thread.  I doubt the info would have helped my particular case but you never know.

---

### Post by stchman on 2008-03-17
The latest Envy 0.9.10 will install the 169.12 drivers on your system.

Go to Install Nvidia driver Manually and the 169.12 will be an option.

For Gutsy and earlier use Envy Legacy
[http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu7_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu7_all.deb)

For Hardy use Envy NG
[http://albertomilone.com/ubuntu/nvidia/scripts/envyng/envyng_1.0.4ubuntu9_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envyng/envyng_1.0.4ubuntu9_all.deb)

Worked on my system and this is the only driver that supports the 8xxx series of Nvidia cards.

Hope this helps.

---

### Post by kugel. on 2008-03-17
Hey, I have used envy to get the latest nvidia (169.12) driver installed.

This worked fine, however, if I go to System->Settings->Appearance in order to activate the visual effects, it tells me that i have to install the restricted driverf (100.xx version).

Besides that I don't really want to install such an old driver, even if I do it it doesn't work. With the "official" ubuntu restricted driver version 100.14 it says that it cannot activate the effects.

Any help?

---

### Post by PmDematagoda on 2008-03-17
Please post the output of:-
```
cat /usr/bin/compiz
```

---

### Post by kugel. on 2008-03-17
> **PmDematagoda said:**
> Please post the output of:-
```
cat /usr/bin/compiz
```
```
#!/bin/sh
# Compiz Manager wrapper script
# 
# Copyright (c) 2007 Kristian Lyngstøl <kristian@bohemians.org>
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301  USA
#
#
# Contributions by: Treviño (3v1n0) <trevi55@gmail.com>, Ubuntu Packages
#
# Much of this code is based on Beryl code, also licensed under the GPL.
# This script will detect what options we need to pass to compiz to get it
# started, and start a default plugin and possibly window decorator.
# 


COMPIZ_BIN_PATH="/usr/local/bin/" # For window decorators and compiz
PLUGIN_PATH="/usr/local/lib/compiz/" 
GLXINFO="/usr/bin/glxinfo"
KWIN="/usr/bin/kwin"
METACITY="/usr/bin/metacity"
COMPIZ_NAME="compiz" # Final name for compiz (compiz.real) 

# For Xgl LD_PRELOAD
LIBGL_NVIDIA="/usr/lib/nvidia/libGL.so.1.2.xlibmesa"
LIBGL_FGLRX="/usr/lib/fglrx/libGL.so.1.2.xlibmesa"

# Minimum amount of memory (in kilo bytes) that nVidia cards need
# to be allowed to start
# Set to 262144 to require 256MB
NVIDIA_MEMORY="65536" # 64MB
NVIDIA_SETTINGS="nvidia-settings" # Assume it's in the path by default

# For detecting what driver is in use, the + is for one or more /'s
XORG_DRIVER_PATH="/usr/lib/xorg/modules/drivers/+"

FALLBACKWM="${METACITY}"
FALLBACKWM_OPTIONS="--replace $@"

# Driver whitelist
WHITELIST="nvidia intel ati radeon i810"

# blacklist based on the pci ids 
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
T="   1002:5954 1002:5854 1002:5955" # ati rs480
T="$T 1002:4153" # ATI Rv350
T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
T="$T 8086:2972" # i965 (x3000)
T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700 
BLACKLIST_PCIIDS="$T"
unset T

COMPIZ_OPTIONS="--ignore-desktop-hints --replace"
COMPIZ_PLUGINS=""
ENV=""

# Use emerald by default if it exist
USE_EMERALD="yes"

# No indirect by default
INDIRECT="no"

# Set to yes to enable verbose
VERBOSE="yes"

# Echos the arguments if verbose
verbose()
{
	if [ "x$VERBOSE" = "xyes" ]; then
		printf "$*"
	fi
}

# abort script and run fallback windowmanager
abort_with_fallback_wm()
{
	if [ "x$SKIP_CHECKS" = "xyes" ]; then
		verbose "SKIP_CHECKS is yes, so continuing despite problems.\n"
		return 0;
	fi

	verbose "aborting and using fallback: $FALLBACKWM \n"

	if [ -x $FALLBACKWM ]; then
		exec $FALLBACKWM $FALLBACKWM_OPTIONS
	else
		printf "no $FALLBACKWM found, exiting\n"
		exit 1
	fi
}

# Check for non power of two texture support
check_npot_texture()
{
	verbose "Checking for non power of two support: "
	if glxinfo 2> /dev/null | egrep -q '(GL_ARB_texture_non_power_of_two|GL_NV_texture_rectangle|GL_EXT_texture_rectangle|GL_ARB_texture_rectangle)' ; then
		verbose "present. \n";
		return 0;
	else
		verbose "Not present. \n"
		return 1;
	fi

}

# Check for presence of FBConfig
check_fbconfig()
{
	verbose "Checking for FBConfig: "
	if [ "$INDIRECT" = "yes" ]; then
		$GLXINFO -i | grep -q GLX.*fbconfig 
		FB=$?
	else
		$GLXINFO | grep -q GLX.*fbconfig 
		FB=$?
	fi

	if [ $FB = "0" ]; then
		unset FB
		verbose "present. \n"
		return 0;
	else
		unset FB
		verbose "not present. \n"
		return 1;
	fi
}


# Check for TFP
check_tfp()
{
	verbose "Checking for texture_from_pixmap: "
	if [ $($GLXINFO 2>/dev/null | grep GLX_EXT_texture_from_pixmap -c) -gt 2 ] ; then
		verbose "present. \n"
		return 0;
	else
		verbose "not present. \n"
		if [ "$INDIRECT" = "yes" ]; then
			unset LIBGL_ALWAYS_INDIRECT
			INDIRECT="no"
			return 1;
		else
			verbose "Trying again with indirect rendering:\n";
			INDIRECT="yes"
			export LIBGL_ALWAYS_INDIRECT=1
			check_tfp;
			return $?
		fi
	fi
}

# Check wether the composite extension is present
check_composite()
{
	verbose "Checking for Composite extension: "
	if xdpyinfo -queryExtensions | grep -q Composite ; then
		verbose "present. \n";
		return 0;
	else
		verbose "not present. \n";
		return 1;
	fi
}

# Detects if Xgl is running
check_xgl()
{
	verbose "Checking for Xgl: "
	if xvinfo | grep -q Xgl ; then
		verbose "present. \n"
		return 0;
	else
		verbose "not present. \n"
		return 1;
	fi
}

# Check if the nVidia card has enough video ram to make sense
check_nvidia_memory()
{
	MEM=$(${NVIDIA_SETTINGS} -q VideoRam | egrep Attribute\ \'VideoRam\'\ .*: | cut -d: -f3 | sed 's/[^0-9]//g')
	if [ $MEM -lt $NVIDIA_MEMORY ]; then
		verbose "Less than ${NVIDIA_MEMORY}kb of memory and nVidia";
		return 1;
	fi
	return 0;
}

# Check for existence if NV-GLX
check_nvidia()
{
	if [ ! -z $NVIDIA_INTERNAL_TEST ]; then
		return $NVIDIA_INTERNAL_TEST;
	fi
	verbose "Checking for nVidia: "
	if xdpyinfo | grep -q NV-GLX ; then
		verbose "present. \n"
		NVIDIA_INTERNAL_TEST=0
		return 0;
	else
		verbose "not present. \n"
		NVIDIA_INTERNAL_TEST=1
		return 1;
	fi
}

# Check if the max texture size is large enough compared to the resolution
check_texture_size()
{
	TEXTURE_LIMIT=$(glxinfo -l | grep GL_MAX_TEXTURE_SIZE | sed 's/.*=[^0-9]//g')
	RESOLUTION=$(xdpyinfo  | grep -i dimensions: | sed 's/[^0-9]*pixels.*(.*).*//' | sed 's/[^0-9x]*//')
	VRES=$(echo $RESOLUTION | sed 's/.*x//')
	HRES=$(echo $RESOLUTION | sed 's/x.*//')
	verbose "Comparing resolution ($RESOLUTION) to maximum 3D texture size ($TEXTURE_LIMIT): ";
	if [ $VRES -gt $TEXTURE_LIMIT ] || [ $HRES -gt $TEXTURE_LIMIT ]; then
		verbose "Failed.\n"
		return 1;
	fi
	verbose "Passed.\n"
	return 0
}

# check driver whitelist
running_under_whitelisted_driver()
{
	LOG=$(xset q|grep "Log file"|awk '{print $3}')
	if [ -z "$LOG" ];then
		verbose "AIEEEEH, no Log file found \n"
		verbose "$(xset q) \n"
	return 0
	fi
	for DRV in ${WHITELIST}; do
		if egrep -q "Loading ${XORG_DRIVER_PATH}${DRV}_drv\.so" $LOG &&
		   ! egrep -q "Unloading ${XORG_DRIVER_PATH}${DRV}_drv\.so" $LOG; 
		then
			return 0
		fi
	done
	verbose "No whitelisted driver found\n"
	return 1
}

# check pciid blacklist
have_blacklisted_pciid()
{
	OUTPUT=$(lspci -n)
	for ID in ${BLACKLIST_PCIIDS}; do
		if echo "$OUTPUT" | egrep -q "$ID"; then
			verbose "Blacklisted PCIID '$ID' found \n"
			return 0
		fi
	done
	OUTPUT=$(lspci -vn | grep -i VGA)
	verbose "Detected PCI ID for VGA: $OUTPUT\n"
	return 1
}

build_env()
{
	if check_nvidia; then
		ENV="__GL_YIELD=NOTHING "
	fi
	if [ "$INDIRECT" = "yes" ]; then
		ENV="$ENV LIBGL_ALWAYS_INDIRECT=1 "
	fi
	if check_xgl; then
		if [ -f ${LIBGL_NVIDIA} ]; then
			ENV="$ENV LD_PRELOAD=${LIBGL_NVIDIA}"
			verbose "Enabling Xgl with nVidia drivers...\n"
		fi
		if [ -f ${LIBGL_FGLRX} ]; then
			ENV="$ENV LD_PRELOAD=${LIBGL_FGLRX}"
			verbose "Enabling Xgl with fglrx ATi drivers...\n"
		fi
	fi

	ENV="$ENV FROM_WRAPPER=yes"

	if [ -n "$ENV" ]; then
		export $ENV
	fi
}

build_args()
{
	if [ $INDIRECT = "yes" ]; then
		COMPIZ_OPTIONS="$COMPIZ_OPTIONS --indirect-rendering "
	fi
	if check_nvidia; then
		COMPIZ_OPTIONS="$COMPIZ_OPTIONS --loose-binding"
	fi
}

####################
# Execution begins here.

# Read configuration from XDG paths
if [ -z "$XDG_CONFIG_DIRS" ]; then
	test -f /etc/xdg/compiz/compiz-manager && . /etc/xdg/compiz/compiz-manager
else
	test -f $XDG_CONFIG_DIRS/compiz/compiz-manager && . $XDG_CONFIG_DIRS/compiz/compiz-manager
fi

if [ -z "$XDG_CONFIG_HOME" ]; then
	test -f $HOME/.config/compiz/compiz-manager && . $HOME/.config/compiz/compiz-manager
else
	test -f $XDG_CONFIG_HOME/compiz/compiz-manager && .  $XDG_CONFIG_HOME/compiz/compiz-manager
fi

# Don't use compiz when running the failsafe session
if [ "x$GNOME_DESKTOP_SESSION_ID" = "xFailsafe" ]; then
	abort_with_fallback_wm
fi

if [ "x$LIBGL_ALWAYS_INDIRECT" = "x1" ]; then
	INDIRECT="yes";
fi

# if we run under Xgl, we can skip some tests here
if ! check_xgl; then
	# if vesa or vga are in use, do not even try glxinfo (LP#119341)
	if ! running_under_whitelisted_driver || have_blacklisted_pciid; then
		abort_with_fallback_wm
	fi
	# check if we have the required bits to run compiz and if not, 
	# fallback
	if ! check_tfp || ! check_npot_texture || ! check_composite || ! check_texture_size; then
		abort_with_fallback_wm
	fi

	if check_nvidia && ! check_nvidia_memory; then
		abort_with_fallback_wm
	fi

	if ! check_fbconfig; then
		abort_with_fallback_wm
	fi
fi

# load the ccp plugin if present and fallback to plain gconf if not
if [ -f ${PLUGIN_PATH}libccp.so ]; then
	COMPIZ_PLUGINS="$COMPIZ_PLUGINS ccp"
elif [ -f ${PLUGIN_PATH}libgconf.so ]; then
	COMPIZ_PLUGINS="$COMPIZ_PLUGINS glib gconf"
fi

# get environment
build_env
build_args

# start the gtk-window-decorator if present
if [ -x ${COMPIZ_BIN_PATH}emerald ] && [ "$USE_EMERALD" = "yes" ]; then
	verbose "Starting emerald\n"
	${COMPIZ_BIN_PATH}emerald --replace &
elif [ -x ${COMPIZ_BIN_PATH}gtk-window-decorator ] && [ -n "$GNOME_DESKTOP_SESSION_ID" ]; then
	verbose "Starting gtk-window-decorator\n"
	${COMPIZ_BIN_PATH}gtk-window-decorator --replace &
elif [ -x ${COMPIZ_BIN_PATH}kde-window-decorator ] && [ -n "$KDE_FULL_SESSION" ]; then
	verbose "Starting kde-window-decorator\n"
	${COMPIZ_BIN_PATH}kde-window-decorator --replace &
	FALLBACKWM="${KWIN}"
fi

${COMPIZ_BIN_PATH}${COMPIZ_NAME} $COMPIZ_OPTIONS "$@" $COMPIZ_PLUGINS || exec $FALLBACKWM $FALLBACKWM_OPTIONS

```

This is the file while driver version 169.12 if it matters.

---

### Post by James_mtl on 2008-03-18
I had the same problem and doing  DISABLED_MODULES="nv nvidia_new" did fix it.  

I did not need to reconfig X 

For some reason I was under the impression that this did not work for other people in this thread.  I did work for me.
Should this threat be marked as resolved ?

Anyways thanks for the tip !!

---

### Post by kugel. on 2008-03-19
> **James_mtl said:**
> I had the same problem and doing  DISABLED_MODULES="nv nvidia_new" did fix it.  No, that doesn't help me :( It still wants me to activate the restricted driver when I try to activate the visual desktop effects.

---

### Post by Daddyo-613 on 2008-03-19
I've had similar problems running the new nVidia drive after doing an upgrade to GUTSY. 

The install of the driver seemed to go fine but on restart the xorg.conf file was showing "nv" not the new driver. I changed the setting manually to "nvidia" but then GUTSY would only boot in low resolution mode. I had to go back to an older driver but I can't run compiz effects without the system freezing or running as slow as molasses.

I noticed in the output from the cat /usr/bin/compiz above that the following text was in the file:

# Minimum amount of memory (in kilo bytes) that nVidia cards need
# to be allowed to start
# Set to 262144 to require 256MB
NVIDIA_MEMORY="65536" # 64MB

I have a GF7300LE video card w/Turbo Cash 128MB TVOut DVI.

Does that mean I can't run compiz-fusion with only 128MB on my card?
Any thoughts?

---

### Post by art_erickson on 2008-03-20
169.12 is installed and runs fine.  Compiz provided no 3D effects so I uninstalled it.  Gnome reacts more quickly now.

If you don't need 3D (I know nothing of games) I recommend waiting until Compiz is more compatible with Nvidia - or vise versa.

Rejection of Linux by vendors is still a big hurdle.  It seems odd to me, but I am not a corporate chieftain.

---

### Post by GordonFreeman on 2008-03-21
I had the same problem as the thread creator and for me the blacklisting of the nv and nvidia-new did work.

I'm running XUbuntu 7.10 with 2.6.22-14-generic kernel.

---

### Post by art_erickson on 2008-03-21
Gordon, what Nvidia version are you running?  I have a 6200 card.  It may be that the older versions are more 'stable' - meaning mine will never have 3D in ubuntu.

Even then, I believe the manufacturer of the cards makes a difference.  Without taking the card out I don't know (anymore) who the manufacturer was.

As I said before, this has become a non issue for me.  I don't live or die by 3d.

---

### Post by GordonFreeman on 2008-03-21
I have a Geforce 8600M GT (in a notebook) and I'm running the 169.12 driver.

---

### Post by art_erickson on 2008-03-21
Ah, I could be way off base but I think new hardware helps.

I am still confused about whether the Restricted Driver Manager overrides the installed driver.

I have 169.12 installed and running fine (per the Nvidia Server X Settings screen).  When I enable the 'restricted' driver it reverts to the older version.

I tried the exclusionary statements previously mentioned but:
1. I did not implement the change correctly
2. It doesn't affect my machine

I have not a clue which of the two it is.

I will bow out of this discussion as I believe I am not relevant.

---

### Post by Quatrix on 2008-04-25
Did anyone ever get this sorted out?  I'm also getting the low-resolution "Your screen and graphics card could not be detected" error after installing the 100.14.23, 169.12, or latest 173.08 (4/10) drivers for an 8800GTS.  I've tried all of the tips in this thread with no luck.  One strange thing is that after installing the drivers and restarting Gnome, the NVIDIA settings app, high-quality desktop effects, etc. all work fine.  It's only after rebooting the PC that I get stuck in low-resolution mode.  This is a fresh Ubuntu 8.04 install.

---

### Post by gbgs53 on 2008-04-25
> **PmDematagoda said:**
> This problem maybe related to conflicting drivers, try doing this:-

1) Open a modules file for editing using:-
```
gksudo gedit /etc/default/linux-restricted-modules-common
```

2) Edit the DISABLED_MODULES line to make it look like this:-
```
DISABLED_MODULES="nv nvidia_new"
```
and save the file.

3) Reconfigure the X-Server(you need to kill the GUI) with:-
```
sudo dpkg-reconfigure xserver-xorg
```
then reboot the system and see if the problem is now solved.

This did it for me, except for #3.  I used the nvidia-settings application supplied with the driver to do the xorg.conf.  (This needs to be run as root to save the xorg.conf, the supplied link in System Tools doesn't run it as root)

---

### Post by Quatrix on 2008-04-26
**Thanks a bunch.**  Everything seems to be working now.  I don't know exactly what the problem was, but the only thing I did differently this time was use "Save to X Configuration File" in the NVIDIA X Server Settings.  The NVIDIA installer had already made changes to xorg.conf, but I think nvidia-settings added the additional lines below.  I also noticed that the Hardware Drivers dialog shows "No proprietary drivers are in use on this system."  Is that normal?  For what it's worth, I used the 173.08 drivers.

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS 512"
EndSection

---

