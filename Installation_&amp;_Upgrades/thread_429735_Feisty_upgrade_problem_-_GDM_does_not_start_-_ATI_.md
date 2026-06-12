---
title: "Feisty upgrade problem - GDM does not start - ATI Rage XL"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by lissakse on 2007-05-01
I upgraded to 7.04 using the prescribed method and encountered the following problem on reboot.
- gdm does not start, it consumes 99% CPU forever
- screen is black with the "hourglass" symbol

Thinking the problem is related to the ATI RAge XL graphics card (onboard card on a HP TC3100 server) I tried the various drivers (open source and proprietary) but to no result.

The system on the whole is up and running, but no GDM.

Any help would be greatly appreciated!

---

### Post by mole0815 on 2007-05-03
Hi,

i have the same problem. Yesterday i installed the latest updates and now gdm does not start (99% CPU).

I have a ATI Mobility 9000. It does not work either with ati driver nor radeon driver.

Any hints?

---

### Post by mole0815 on 2007-05-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/112174](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/112174) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I installed xdm and ubuntu starts. Nevertheless i cannot access my network interfaces when signing in with xdm.

I opened a bug for this problem. Hope they can fix it soon...

---

### Post by mole0815 on 2007-05-04
I solved it. The /usr -directory did not have the right permissions.  I changed it to 755.

---

### Post by lissakse on 2007-05-05
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/112174](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/112174) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The commet re. 755 permission on /usr did not help in my case.
Permissions were set correctly, but "changed" them in any case --> GDM keeps souring at 99%

---

### Post by garazy on 2007-05-20
I have this exact same problem as well now. Installed a few days ago. Was working fine. Switched it off and on again and I get 100% GDM and the hour glass and black screen.

 7292 ?        S      0:00 /usr/sbin/gdm
 7297 tty9     Ss+    0:00 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth vt9
 7305 ?        Rs     1:37 /usr/sbin/gdm





GDM Log has nothing of interest -

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux gary-laptop 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun May 20 16:35:02 2007
(==) Using config file: "/etc/X11/xorg.conf"
(EE) AIGLX: Screen 0 is not DRI capable
Synaptics Touchpad no synaptics event device found (checked 16 nodes)
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : No such file or directory
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!

---

### Post by maki_03 on 2007-05-20
I also had this problem for a few days.. I am running Ubuntu Feisty Fawn, with ATI Mobility Radeon X1600 graphics card.

My first workaround was to use a different display manager, i installed kdm and I was able to login to my box with a gnome session. But after testing the system, I found out that some of the apps depend on gdm. (my gaim would not start without gdm)...

I've been tweaking with the apt-get and I tried installing and reinstalling gdm to no avail. But yesterday, I tried the "purge" option of apt-get using this script:

**WARNING: I am a noob, and I am not sure of the full consequence of these scripts. please review these scripts before trying them on your system. :)**

*I removed the gdm currently installed in my system:*
|------------------------------------------------------
|     sudo apt-get --purge remove gdm
|------------------------------------------------------

*then, I reinstalled the desktop and gdm:*
|------------------------------------------------------
|     sudo apt-get install gdm ubuntu-desktop
|------------------------------------------------------

I made sure that gdm was the default desktop manager:
/etc/X11/default-display-manager 

Then I restarted the system, and the default ubuntu login screen greeted me. :D
I was also able to run gaim. This solved the problem for me. Hope this helps. :D

---

### Post by lissakse on 2007-05-29
Many thanks, the above re-installation did the trick (for me, at least)!

---

