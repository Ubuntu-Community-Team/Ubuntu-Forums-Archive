---
title: "Several problems after upgrading to 8.10"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by Dave_Dews on 2008-11-07
After upgrading from 8.04 Hardy (which worked fine) to 8.10 Intrepid I've encountered several problems:

Most commonly used programs, like rhythmbox, and pidgin crash whenever I try to use them (they fade and stop responding and can only be shut down using the broken window tool)

Notifications on the toolbar are blacked out, as well as several parts of Pidgin. Various features like the transparency of windows no longer work

Both system sound and audio are not working


This sounds like driver issues. I'm fairly new to linux so not too sure how to go about getting new drivers for these.

Any help would be great
Thanks 

GNOME DESKTOP 2.24.1

nVidia Geforce 8400M GT 128MB
Intel Core Duo 2 T8100/2.1 GH/z

---

### Post by petermck on 2008-11-07
Have you got 3D graphics effects turned on? If so try turning it off in System->Control Center->Appearance->Visual Effects.
If you don't see Control Center under System, go into Preferences->Main Menu, select System and tick Control Center.
I'm not a Nvidia expert, but what you describe sounds similar to a problem I had in Hardy (or was it Feisty) with 3D graphics and the ATI driver. Turning of 3D fixed it.
You can find out what graphics driver you are using by a couple of different methods. If it's proprietary it will be listed in System->Admin->Hardware Drivers. If not you can find it in Preferences->Harware Info.
If all else fails open a terminal and enter cat /etc/X11/xorg.conf|less and look for a section like this;
Section "Device"
        Identifier      "Configured Video Device"
        Boardname       "ATI Radeon (fglrx)"
        Busid           "PCI:1:5:0"
        Driver          "fglrx"
        Screen  0
        Vendorname      "ATI"
        Option          "MergedFB"      "off"
EndSection
Obviously yours will have info about Nvidia.
Post the info here.
If the less command gives you a problem install it with Synaptic or sudo apt-get install less. It's real handy piped with cat for viewing config files in a terminal because it works with page up/down and arrow keys unlike more.

---

### Post by Dave_Dews on 2008-11-07
Ok, thanks for the reply.

Turning off 3D effects did not work, so I went to the command line and this is what came up:


Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"

EndSection


Any ideas?
Thanks

---

### Post by Dave_Dews on 2008-11-07
I've now noticed that system sounds, like log on/off sounds are working, but trying to play songs using rhythmbox or amarok makes the program fade and become unresponsive. Sound on firefox doesn't work either.

Help would be much appreciated
Thanks

---

