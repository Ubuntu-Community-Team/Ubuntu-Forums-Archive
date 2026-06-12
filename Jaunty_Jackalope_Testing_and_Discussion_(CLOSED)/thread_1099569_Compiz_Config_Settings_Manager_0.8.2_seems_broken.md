---
title: "Compiz Config Settings Manager 0.8.2 seems broken"
date: 2009-03-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nightstrike2009 on 2009-03-18
**Ubuntu 9.04 Alpha 6 (Using Ex4 Filesystem)**

After installing and activating the Nvidia 180 driver and [COLOR="SeaGreen"]compizconfig-settings-manager_0.8.2.0ubuntu1_all.deb[/COLOR] & [COLOR="SeaGreen"]python-compizconfig_0.8.2.0ubuntu1.i386.deb[/COLOR]

When you go to Compiz Config Settings Manager from the menu, General Options>Desktop Size> Horizontal Size>
The slider resets itself at 4 and goes back to 2, it doesn't seem to do this on any other value.

This may be a bug but don't know how to report it, could someone double-check this and report if possible, as "Desktop Cube" is impossible with out it.

---

### Post by rudenko_ruslan on 2009-03-18
> **Nightstrike2009 said:**
> This may be a bug but don't know how to report it, could someone double-check this and report if possible, as "Desktop Cube" is impossible with out it.
Tried to reproduce it, but everything is OK.

---

### Post by Nightstrike2009 on 2009-03-18
Thanks for the help thats weird though Iam using (nothing else installed yet);

For Nvidia 180 Driver:

[COLOR="SeaGreen"]dkms_2.0.21.1-0ubuntu3_all
nvidia-180-kernel-source_180.35-0ubuntu1_i386
nvidia-180-libvdpau_180.35-0ubuntu1_i386
nvidia-glx-180_180.35-0ubuntu1_i386
nvidia-settings_180.25-0ubuntu1_i386
[/COLOR]

For compizconfig-settings-manager_0.8.2

[COLOR="SeaGreen"]compizconfig-settings-manager_0.8.2-0ubuntu1_all
python-compizconfig_0.8.2-0ubuntu1_i386[/COLOR]

---

### Post by rudenko_ruslan on 2009-03-18
NVIDIA 180.37:
dkms_2.0.21.1-0ubuntu3
nvidia-180-kernel-source_180.37-0ubuntu1
nvidia-180-libvdpau_180.37-0ubuntu1
nvidia-glx-180_180.37-0ubuntu1
nvidia-settings_180.25-0ubuntu1

CCSM 0.8.2:
compizconfig-settings-manager_0.8.2-0ubuntu1
python-compizconfig_0.8.2-0ubuntu1

That's mine.

---

### Post by Nightstrike2009 on 2009-03-18
These must be the offending files then:

[COLOR="Red"]nvidia-180-kernel-source_180.35-0ubuntu1_i386
nvidia-180-libvdpau_180.35-0ubuntu1_i386
nvidia-glx-180_180.35-0ubuntu1_i386[/COLOR]

Has otherwise our files are the same must be a flaw in the Nvidia 180.35 driver that is rectified in the Nvidia 180.37 driver. 

Will try these files later and report back thanks for the help :)

---

### Post by Nightstrike2009 on 2009-03-18
UPDATE the above post didn't work for me the [COLOR="Red"]nvidia 180.37[/COLOR] broke my Ubuntu boot up so going back to [COLOR="SeaGreen"]180.35[/COLOR], this happened on both ex3 and ex4 filesystems. The failed [COLOR="Red"]180.37[/COLOR] driver would not enable in hardware drivers wizard after installation and rebooting crashed the Ubuntu boot up.My graphics card is Nvidia 6600GT, does anyone else know how to get around the compiz config settings problem?

> When you go to Compiz Config Settings Manager from the menu, General Options>Desktop Size> Horizontal Size>
The slider resets itself at 4 and goes back to 2, it doesn't seem to do this on any other value.

UPDATE: I Just had a thought the  Nvidia 180.37 driver may have failed due to the [COLOR="SeaGreen"]nvidia-180-modaliases_180.37-0ubuntu1_i386[/COLOR] being accidentally missing from  rudenko_ruslan's list, (as it was probably created after Ubuntu 9.04 Alpha 6 was built) this file should update the hardware Drivers wizard with the new driver information to allow activation, will try this & post back. :)

---

### Post by Nightstrike2009 on 2009-03-18
Tried installing these files:

NVIDIA 180.37:
[COLOR="SeaGreen"]dkms_2.0.21.1-0ubuntu3[/COLOR]
[COLOR="Red"]nvidia-180-kernel-source_180.37-0ubuntu1
[COLOR="Red"]nvidia-180-libvdpau_180.37-0ubuntu1[/COLOR]
nvidia-glx-180_180.37-0ubuntu1[/COLOR]
[COLOR="SeaGreen"]nvidia-settings_180.25-0ubuntu1[/COLOR]
[COLOR="Red"]nvidia-180-modaliases_180.37-0ubuntu1_i386[/COLOR]
[COLOR="SeaGreen"]compizconfig-settings-manager_0.8.2-0ubuntu1
python-compizconfig_0.8.2-0ubuntu1[/COLOR]

The files highlighted in red don't work on mine, I get application crash report [COLOR="Red"]"Jockey-backend closed unexpectantly"[/COLOR], Boot up failed, and ubuntu recovery reports [COLOR="Red"]"DKMS-[FAILED]"[/COLOR], The only way I could get around this was reinstalling my original [COLOR="SeaGreen"]180.35[/COLOR] by removing the [COLOR="Red"]180.37[/COLOR] files manually in synaptic.

My Files are:
[COLOR="SeaGreen"]dkms_2.0.21.1-0ubuntu3_all
nvidia-180-kernel-source_180.35-0ubuntu1_i386
nvidia-180-libvdpau_180.35-0ubuntu1_i386
nvidia-glx-180_180.35-0ubuntu1_i386
nvidia-settings_180.25-0ubuntu1_i386
compizconfig-settings-manager_0.8.2-0ubuntu1_all
python-compizconfig_0.8.2-0ubuntu1_i386[/COLOR]

Which brings me back to the start > When you go to Compiz Config Settings Manager from the menu, General Options>Desktop Size> Horizontal Size>
The slider resets itself at 4 and goes back to 2, it doesn't seem to do this on any other value.

I've since found out its possible to have 5 five sided-cube(?) or higher, but ideally I would want the normal 4 sided version working any ideas?

Think I may have the answer but need to test it Sourced from GARoss Thread:[http://ubuntuforums.org/showthread.php?t=1095916&highlight=nvidia+180.37]("http://ubuntuforums.org/showthread.php?t=1095916&highlight=nvidia+180.37")

I now have the following files thanks to his thread, and I will test them out and report my findings:
[COLOR="SeaGreen"]
dkms_2.0.21.1-0ubuntu3_all[/COLOR]
[COLOR="DarkOrange"]nvidia-180-kernel-source_180.37-0ubuntu1_i386
nvidia-180-libvdpau_180.37-0ubuntu1_i386[/COLOR]
nvidia-180-libvdpau-dev_180.37-0ubuntu1_all
[COLOR="DarkOrange"]nvidia-180-modaliases_180.37-0ubuntu1_i386[/COLOR]
nvidia-common_0.2.9_i386
[COLOR="DarkOrange"]nvidia-glx-180_180.37-0ubuntu1_i386[/COLOR]
nvidia-settings_180.25-0ubuntu1_i386
[COLOR="SeaGreen"]compizconfig-settings-manager_0.8.2-0ubuntu1_all
python-compizconfig_0.8.2-0ubuntu1_i386[/COLOR]

There also seems to be a "jagged edge" issue with 180.37 (If I ever get the damn thing to work LOL) that philinux has resolved on his thread [http://ubuntuforums.org/showthread.php?t=1099792&highlight=nvidia+180.37]("http://ubuntuforums.org/showthread.php?t=1099792&highlight=nvidia+180.37") Looks like if your cards not Nvidia your out of luck for the time being though :(

UPDATE These files dont work either on my machine for Nvidia 180.37 Driver:

[COLOR="Red"]nvidia-180-kernel-source_180.37-0ubuntu1_i386
nvidia-180-libvdpau_180.37-0ubuntu1_i386
nvidia-180-libvdpau-dev_180.37-0ubuntu1_all
nvidia-glx-180_180.37-0ubuntu1_i386[/COLOR]

The procedure I used for rescue is wait for "Ubuntu is running in low graphics mode" window to appear, click ok, select "reconfigure graphics", click ok, select "use default (generic) configuration", click ok, ok, & then reboot.

---

### Post by Nightstrike2009 on 2009-03-18
Gonna try these file originally posted by mgsfan [http://ppa.launchpad.net/nferenc/ppa/ubuntu]("http://ppa.launchpad.net/nferenc/ppa/ubuntu") their names are slightly different to those I used before (they seem to be located in pool>main>n>)

---

### Post by Nightstrike2009 on 2009-03-19
At last the files from mgsfan's link work:[http://ppa.launchpad.net/nferenc/ppa/ubuntu/pool/main/n/nvidia-graphics-drivers-180/]("http://ppa.launchpad.net/nferenc/ppa/ubuntu/pool/main/n/nvidia-graphics-drivers-180/")

Nvidia 180.37 is installed and working now these are my files:
[COLOR="SeaGreen"]
nvidia-180-kernel-source_180.37-0ubuntu0_i386
nvidia-180-libvdpau_180.37-0ubuntu0_i386
nvidia-180-libvdpau-dev_180.37-0ubuntu0_all
nvidia-180-modaliases_180.37-0ubuntu0_i386
nvidia-glx-180_180.37-0ubuntu0_i386
nvidia-glx-180-dev_180.37-0ubuntu0_i386
dkms_2.0.21.1-0ubuntu3_all
nvidia-settings_180.25-0ubuntu1_i386
nvidia-common_0.2.9_i386[/COLOR]

However the compiz problem persists:

> When you go to Compiz Config Settings Manager from the menu, General Options>Desktop Size> Horizontal Size>
The slider resets itself at 4 and goes back to 2, it doesn't seem to do this on any other value. 

This leads me to think that the problem is with the compiz files below, not the Nvidia driver:
[COLOR="SandyBrown"]compizconfig-settings-manager_0.8.2-0ubuntu1_all
python-compizconfig_0.8.2-0ubuntu1_i386[/COLOR]

Thanks to the Ubuntu community giving the information to get the Nvidia driver working, Has anyone got any ideas on the compiz problem?

eleifsp and others have the same problem on his thread[http://ubuntuforums.org/showthread.php?t=1095685]("http://ubuntuforums.org/showthread.php?t=1095685")

**UPDATE 03/04/09: This Solution no longer works as the website for the correct files is no longer hosting them :(**

---

### Post by Nightstrike2009 on 2009-03-19
I think this is down to a bug but a workaround is possible, (originally discovered by shane8002) :)

Right click virtual desktops on bottom gnome bar (where you actually select them) RIGHT CLICK>PREFERENCES>
Set Workspaces to 4
Set Rows to 1
Click X to close

There you have it desktop cube with 4 sides :) hope this helps, until bug is fixed ;)

---

