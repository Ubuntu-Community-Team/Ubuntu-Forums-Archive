---
title: "Cannot start X for user"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by mogliii on 2006-10-26
Hi,

I have a mobile computer and had WinXP and Ubuntu installed. 

root partition was hda2, and also grub was installed there

As the 30GB got too small, I installed a new harddrive (80GB). I used dd to move the partitions from the old harddrive, resize, create new ones and so on.

Win works fine.
Partition table looks like that: (with old numbers given in brackets, if not present, partition new)
hda1 - winxp (hda1)
hda2 - /boot (100mb)
hda3 - Extended (hda4)
hda5 - NTFS-partition
hda6 - /root Ubuntu (hda2)
hda7 - 1G for backupsystem
hda8 - swap
hda9 - /home (hda6)
hda10 - Data 

I copied /boot from the old root partition to hda2. As it stayed hda2 I didnt have to change the mbr.
I changed the entries in /boot/grub/menu.lst to match the new partition names
I changed in /etc/fstab of the Ubuntu system the parition numbers to mach the actual situation.

So I booted into Ubuntu, the loginmanager opened, but when I tried to login, the screen became black and I was back at the loginscreen.

I went to a prompt as root, and executed startx... worked fine, could boot into XFCE.

But with my normal user (/home directory present) it didnt work.
I have here the critical output given when crashing:

```
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux ****** 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Oct 26 10:57:39 2006
(==) Using config file: "/etc/X11/xorg.conf"
(**) RADEON(0): RADEONPreInit
    [..clip..]
(**) RADEON(0): RADEONScreenInit finished
[COLOR="Red"]error opening security policy file /etc/X11/xserver/SecurityPolicy
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
Synaptics DeviceOn called
(**) RADEON(0): RADEONSaveScreen(2)
xterm:  bad command line option "Synaptics DeviceOff called

waiting for X server to shut down (**) RADEON(0): RADEONCloseScreen
(**) RADEON(0): RADEONDRIStop[/COLOR]
    [..clip..]
(**) RADEON(0): RADEONDRICloseScreen
FreeFontPath: FPE "/usr/share/X11/fonts/misc" refcount is 2, should be 1; fixing.

```

Does anyone know which problem there is??

Dont want to work as root all time!

---

### Post by cosborn72 on 2006-10-26
I had almost this exact same problem.  However, it occurred after a simple daily update in one of the previous Edgy release candidate- I didn't partition anything.

I could only start X as root, not with my normal (administrative) account. 

Unfortunately, I have no guess as to the solution - I reconfigure X, removed and reinstalled it, checked my X config file- no luck. 

I ended up backing up my home folder and doing a complete re-install of Dapper.

(Since then I have dist-upgraded to the current edgy release candidate, which seems to be working fine.)

---

### Post by mogliii on 2006-10-26
Hi,

I found the problem. Its so simple that I am almost a little bit embarassed that it was not written as an error message. 

My /home partition was full. No more biyte could fit on it. As this may happen more often I guess it would be cool if there was a message telling me that this is the problem...

@cosborn72: Hope that was not the problem with you. Because otherwise you installed for vain :/ at least almost.

I dont want a baloon-tip as in WinXP, but maybe at least an pointing message should be possible when discs get full.

---

