---
title: "Problems with Upgrade to 8.10"
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by gbutler69 on 2008-10-18
Hello All,

I just purchased my third laptop through System76, a Pangolin Performance. It came with Ubunutu 8.04 64-Bit pre-installed.

After receiving it, the first thing I did was to upgrade to Ubuntu 8.10. After doing so, I am experiencing the following problems:

1. Upon first rebooting after the upgrade, the xorg.conf was messed up and it went into screen recover mode. After examining the errors and looking at the xorg.conf file, I found that the upgraded had commented out the device section for the synaptics touch pad, but, left the reference to the commented out section in the "ServerLayout" section. I fixed that and managed to boot up to the desktop with full graphics enabled.

2. Now, when I try to run firefox or epiphany, it fails. When I run firefox from the command line, I get the following:

```

gbutler@ubuntu:~$ firefox
Couldn't load XPCOM.
gbutler@ubuntu:~$

```

So, I looked at why I might be getting this error and tried:

```

gbutler@ubuntu:~$ xpcshell-1.9 
xpcshell-1.9: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory
gbutler@ubuntu:~$

```

OK, now this tells us something. So, I did a search for "libmozjs.so"

```

gbutler@ubuntu:/$ sudo find ./ -type f -name "libmozjs.so"
./usr/lib/xulrunner-1.9.0.3/libmozjs.so
./usr/lib/xulrunner-1.9.0.1/libmozjs.so
gbutler@ubuntu:/$

```

Ah-ha! So it's there, but, not in the library path. So, I next did the following:

```

gbutler@ubuntu:~$ export LD_LIBRARY_PATH=/usr/lib/xulrunner-1.9.0.3/
gbutler@ubuntu:~$ firefox

```

BAM! That works! OK, so the problem is with an incorrectly configured installation of "xulrunner". NOTE: Epiphany Webkit version works correctly obviously.

I've searched the forums and Google and see no evidence that this problem is being experienced in general. Is anyone else seeing this issue? I just upgraded to 8.10 last night (October 17, 2008 at around 9:30 PM EDT).

[B]
[INDENT]
UPDATE: Tentative Solution Found : I looked at the contents of /etc/gre.d and found several conf files there. I deleted all but the 1.9.0.3.system.conf and that seems to have fixed the problem.

NOTE: It was asac who suggested I look at the contents of /etc/gre.d. Thanks asac!
[/INDENT]
[/B]

3. The other problems I am seeing after the upgrade are as follows:

3.1. "Cheese" no longer works. Seems to be having trouble seeing the camera. Haven't been able to get to the bottom ofthis yet.

3.2. On "shutdown" the screen does a weird sort of thing with a splotchy dimming area on the screen and then stays white and the laptop doesn't power down. I have to turn the power off.

3.3. Sounds is awfully quiet, even with the volume control turned all the way up.

The main thing I want to understand are whether these issues are:

1. Pangolin specific problem/related

2. Ubuntu 8.10 Beta general problem that others are having

3. Something I've done wrong

Please Help!

Kind Regards,

Gerry B.

---

### Post by overdrank on 2008-10-18
Moved to Intrepid :)

---

### Post by inportb on 2008-10-18
How did you upgrade, and did you encounter the same issues in the live session?

---

### Post by asac on 2008-10-18
That library path is non-sense. firefox finds xulrunner by looking at /etc/gre.d/*.conf

please post what you get by:

dpkg -S usr/lib/xulrunner-1.9.0 | grep libmozjs

and

dpkg -l firefox*

and ls -l /usr/bin/firefox


also look what you have in /etc/gre.d/*.conf and if that makes sense.

---

### Post by jake3988 on 2008-10-18
1) A major problem is that xorg.conf isn't defined right.  Hal is now used for the devices and it comments them out but doesn't comment out the references to those devices and won't let X start.  Simply comment those devices out in the ServerLayout and you'll be ok.

2) Compiz is broke for many people with older graphics cards.  Uninstall or try a wm without compiz (installing lightweight fluxbox to test is good).

3) Xulrunner is a problem with firefox3.  Firefox3 uses xulrunner for the plugins but it's kinda broke for firefox3.1.

---

### Post by tseliot on 2008-10-18
> **jake3988 said:**
> 1) A major problem is that xorg.conf isn't defined right.  Hal is now used for the devices and it comments them out but doesn't comment out the references to those devices and won't let X start.  Simply comment those devices out in the ServerLayout and you'll be ok.

Can you attach your xorg.conf, please? I would like to see what happened to your xorg.conf (and possibly try to understand why).

---

### Post by gbutler69 on 2008-10-18
I don't understand what you mean by "Live Session".

---

### Post by gbutler69 on 2008-10-18
What do you mean by "kinda broke"? Someone else commented that my use of "LD_LIBRARY_PATH" was B.S., but, by doing that, it made firefox run.

---

### Post by MasterNetra on 2008-10-18
> **gbutler69 said:**
> I don't understand what you mean by "Live Session".

I believe inport means running Live-CD.

---

### Post by gbutler69 on 2008-10-18
> **asac said:**
> That library path is non-sense. firefox finds xulrunner by looking at /etc/gre.d/*.conf


Nonsense? It worked!

> 
please post what you get by:

dpkg -S usr/lib/xulrunner-1.9.0 | grep libmozjs



OK, here it is....

```

gbutler@ubuntu:~$ dpkg -S usr/lib/xulrunner-1.9.0 | grep libmozjs
xulrunner-1.9: /usr/lib/xulrunner-1.9.0.3/libmozjs.so
gbutler@ubuntu:~$ 

```

> 
and

dpkg -l firefox*


and here that is too...

```

gbutler@ubuntu:~$ dpkg -l firefox*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  firefox        3.0.3+nobinonl meta package for the popular mozilla web bro
un  firefox-2      <none>         (no description available)
ii  firefox-3.0    3.0.3+nobinonl safe and easy web browser from Mozilla
ii  firefox-3.0-br 3.0.3+nobinonl Package that ships the firefox branding
ii  firefox-3.0-gn 3.0.3+nobinonl Support for Gnome in Mozilla Firefox
ii  firefox-gnome- 3.0.3+nobinonl meta package pointing to the latest gnome-su
un  firefox-granpa <none>         (no description available)
un  firefox-granpa <none>         (no description available)
un  firefox-libtha <none>         (no description available)
un  firefox-trunk  <none>         (no description available)
un  firefox-trunk- <none>         (no description available)
gbutler@ubuntu:~$ 

```

> 
and ls -l /usr/bin/firefox


OK, here that is too...

```

gbutler@ubuntu:~$ ls -l /usr/bin/firefox
lrwxrwxrwx 1 root root 11 2008-10-18 00:02 /usr/bin/firefox -> firefox-3.0
gbutler@ubuntu:~$ 

```

> 
also look what you have in /etc/gre.d/*.conf and if that makes sense.


And, that is as follows:

```

gbutler@ubuntu:~$ ls -l /etc/gre.d/*.conf
-rwxr-xr-x 1 root root 76 2008-07-28 16:56 /etc/gre.d/1.9.0.1.system.conf
-rwxr-xr-x 1 root root 76 2008-10-13 11:59 /etc/gre.d/1.9.0.3.system.conf
-rwxr-xr-x 1 root root 68 2008-06-10 14:03 /etc/gre.d/1.9.system.conf
gbutler@ubuntu:~$ 

gbutler@ubuntu:/etc/gre.d$ cat 1.9.0.1.system.conf 
[1.9.0.1]
GRE_PATH=/usr/lib/xulrunner-1.9.0.1
xulrunner=true
abi=x86_64-gcc3gbutler@ubuntu:/etc/gre.d$ 

gbutler@ubuntu:/etc/gre.d$ cat 1.9.0.3.system.conf 
[1.9.0.3]
GRE_PATH=/usr/lib/xulrunner-1.9.0.3
xulrunner=true
abi=x86_64-gcc3gbutler@ubuntu:/etc/gre.d$ 

gbutler@ubuntu:/etc/gre.d$ cat 1.9.system.conf 
[1.9]
GRE_PATH=/usr/lib/xulrunner-1.9
xulrunner=true
gbutler@ubuntu:/etc/gre.d$

```

[B]
NOTE: I just removed 1.9.system.conf and 1.9.0.1.system.conf and found that this fixed the problem with firefox and epiphany start-up!
[/B]

---

### Post by gbutler69 on 2008-10-18
> **tseliot said:**
> Can you attach your xorg.conf, please? I would like to see what happened to your xorg.conf (and possibly try to understand why).

Sure, here it is:

```

gbutler@ubuntu:/etc/gre.d$ cat /etc/X11/xorg.conf
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

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Generic Keyboard"
#	Driver		"kbd"
#	Option		"XkbRules"	"xorg"
#	Option		"XkbModel"	"pc105"
#	Option		"XkbLayout"	"us"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Synaptics Touchpad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"	"/dev/psaux"
#	Option		"Protocol"	"auto-dev"
#	Option		"HorizEdgeScroll"	"0"
#EndSection

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
  screen "Default Screen"
###	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
gbutler@ubuntu:/etc/gre.d$ 

```

NOTE: I commented out the "Inputdevice 'Synaptics Touchpad' reference in order to get it to work as that section was commented out by the upgrade.

---

### Post by gbutler69 on 2008-10-19
> **overdrank said:**
> Moved to Intrepid :)

I couldn't figure out how to get to the "Intrepid" forums. I thought that disctinction existed, but, just couldn't seem to find how to get there.

Advise for future please.

Thanks.

---

### Post by tseliot on 2008-10-20
> **gbutler69 said:**
> Sure, here it is:
...
NOTE: I commented out the "Inputdevice 'Synaptics Touchpad' reference in order to get it to work as that section was commented out by the upgrade.
Ok, thanks. Can you attach the content of your /var/log/dist-upgrade/ directory and the backup of your xorg.conf which you will find in /etc/ (its name should begin with "xorg.conf.dist-upgrade-")?

---

### Post by gbutler69 on 2008-10-20
> **tseliot said:**
> Ok, thanks. Can you attach the content of your /var/log/dist-upgrade/ directory and the backup of your xorg.conf which you will find in /etc/ (its name should begin with "xorg.conf.dist-upgrade-")?

Sure thing. Glad of any help I can get and any help I can provide!

I attached "dist-upgrade.tar" that contains the contents of the /var/log/dist-upgrade directory as well as /etc/X11/xorg.*.

Let me know if anything else is needed.

---

