---
title: "Nvidia 180.44 Driver Activation Issue"
date: 2009-04-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nightstrike2009 on 2009-04-03
Hello I was just wondering has anybody got any idea about whats going wrong here, I have the files listed below but they refuse to activate in Hardware Drivers GUI and upon restart they crash my X server. Have I got any files missing? I had the same issue with 180.37 driver (That was resolved by using Nvidia Driver files from outside the repository but the link now appears unavailable).

[COLOR="Sienna"]dkms_2.0.21.1-0ubuntu3_all.deb
nvidia-180-kernel-source_180.44-0ubuntu1_i386.deb
nvidia-180-libvdpau_180.44-0ubuntu1_i386.deb
nvidia-180-libvdpau-dev_180.44-0ubuntu1_i386.deb
nvidia-180-modaliases_180.44-0ubuntu1_i386.deb
nvidia-common_0.2.9_i386.deb
nvidia-glx-180_180.44-0ubuntu1_i386.deb
nvidia-glx-180-dev_180.44-0ubuntu1_i386.deb
nvidia-settings_180.25-0ubuntu1_i386.deb[/COLOR]

And Have also got Compizconfig-settings-manager installed;
[COLOR="Sienna"]compizconfig-settings-manager_0.8.2-0ubuntu1_all.deb
python-compizconfig_0.8.2-0ubuntu1_i386.deb[/COLOR]

SYSTEM: Nvidia 6600GT & Ubuntu 9.04 (Beta)

---

### Post by BGFG on 2009-04-03
with the round of updates that brought the 180.44, after a restart my system went into low-graphics mode. through 'hardware drivers' i uninstalled then reinstalled the 180 series, and the system went to .44 properly.

As for the download locations :

[http://www.nvnews.net/vbulletin/showthread.php?p=1957328](http://www.nvnews.net/vbulletin/showthread.php?p=1957328)
[ftp://download.nvidia.com/XFree86/Linux-x86/](ftp://download.nvidia.com/XFree86/Linux-x86/)

---

### Post by Nightstrike2009 on 2009-04-03
Thanks BGFG,

I tried the .run method before though and completely borked by system, I understand many use this method and it works for them, I aint that fortunate though. I rather avoid that way if at all possible thanks for trying to help me though.

I have found that Nvidia 173.14 Driver does work though the files I have for them are:

[COLOR="SeaGreen"]dkms_2.0.21.1-0ubuntu3_all
nvidia-173-kernel-source_173.14.16-0ubuntu1_i386
nvidia-glx-173_173.14.16-0ubuntu1_i386
nvidia-settings_180.25-0ubuntu1_i386[/COLOR]

And for compiz:

[COLOR="SeaGreen"]compizconfig-settings-manager_0.8.2-0ubuntu1_all
python-compizconfig_0.8.2-0ubuntu1_i386[/COLOR]

I realise this is a workaround and not a solution, but I think the problem lies in the Nvidia .deb files in the Ubuntu Repository for 180 and upwards. :(

The offending files with 180.37 (and I assume are with 180.44 version too) were:
[COLOR="Red"]nvidia-180-kernel-source_180.37-0ubuntu1_i386
nvidia-180-libvdpau_180.37-0ubuntu1_i386
nvidia-180-libvdpau-dev_180.37-0ubuntu1_all
nvidia-glx-180_180.37-0ubuntu1_i386[/COLOR]

When replaced with thes file it worked (but the link is now dead)
[COLOR="SeaGreen"]nvidia-180-kernel-source_180.37-0ubuntu0_i386
nvidia-180-libvdpau_180.37-0ubuntu0_i386
nvidia-180-libvdpau-dev_180.37-0ubuntu0_all
nvidia-glx-180_180.37-0ubuntu0_i386[/COLOR]
[B]
I suspect that 180.44 suffers from the same official Ubuntu repository problem as 180.37 ([http://packages.ubuntu.com/jaunty/misc/nvidia-180-kernel-source]("http://packages.ubuntu.com/jaunty/misc/nvidia-180-kernel-source"), hence I am seeking replacement .deb files as I did then, does anyone know where I can find them?[/B] :(

PS: Previous problems (& probably now current problems too as the ppa link is broken now) with the 180.37 are detailed here:[http://ubuntuforums.org/showthread.php?t=1099569&highlight=nightstrike2009]("http://ubuntuforums.org/showthread.php?t=1099569&highlight=nightstrike2009") Compiz now works it was due to Python 2.6 being missing in an earlier test version.

---

### Post by Nightstrike2009 on 2009-04-07
Bump! Anyone any ideas?

---

### Post by douham on 2009-04-07
have you you tried using Michael Marley's (aka: The firstM) ppa.[https://launchpad.net/ubuntu/+ppas?name_filter=michael+marley]("https://launchpad.net/ubuntu/+ppas?name_filter=michael+marley")

He usually keeps the the latest Nvidia driver there. I'm running the 185.13 from his ppa driver with no probs.

---

### Post by Nightstrike2009 on 2009-04-07
Thanks douham, that may work I've downloaded all the files you suggested I noticed nvidiasettings is missing but I'll just use my old one LOL. UPDATE: Nope 185.19 doesn't work either on mine, thanks for trying to help though. :)

---

