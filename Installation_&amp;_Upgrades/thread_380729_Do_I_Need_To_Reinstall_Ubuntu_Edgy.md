---
title: "Do I Need To Reinstall Ubuntu Edgy?"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by n8oay on 2007-03-10
I installed a ATI All-In-Wonder 2006 AGP video card using the ati-driver-installer-8.26.18-i386 from ATI's web page. I could not get it to work at any resolution higher than 1024x786, so I tried to go back to the integrated S3 Graphics UniChrome Pro IGP on the Biostar P4M80-M4 motherboard. Now, it will only boot to a text logon. Do I need to reinstall Ubuntu, or is there another way to fix this mess?

---

### Post by beefcurry on 2007-03-10
no you just need to change the xorg.conf.

type in your terminal 
```
gksudo gedit /etc/X11/xorg.conf
```

Then create your modline [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl) and insert it into your xorg.conf under the [Monitor] section.

Remember to backup your xorg.conf first with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

---

### Post by garybrlow on 2007-03-10
You do not need to reinstall Ubuntu!!! Hmm I don't really have much experience with ATI since I own an NVIDIA card but installation is pretty much the same. They all use the use the Xorg Video configuration file. You may have to reset your Xorg configuration and you have to manually adjust your resolutions. Consult the Video and Multimedia Section of forums They have a sticky for installing the official and open source drivers for NVIDIA and ATI. This should should be transferred to that section anyways.

Am not really sure what resolution you want to be on but if your wanted resolution is not in the xorg configuration file you have to put it in there but I think ATI has an autamatic configuration script similar to NVIDIA's nvidia-xcnfig. The X  video server will always assume the first resolution (read left to right, highest to lowest)

ex.
Open /etc/X11/xorg.conf using a text editor and look for the section below.

SubSection     "Display"
        Depth       24
        Modes      "add resolution here" "1024x768" "800x600" "640x480"
EndSubSection


But before doing anything else read the HOWTOs first.



Cheers!!! :)


GaryBrlow :biggrin:

---

### Post by n8oay on 2007-03-10
Thank you! That has got me back to 1280x1024 (Sorry! I forgot to mention in the first post that I am using a Optiquest Q9 LCD). After inserting the 'modline''I had to change some settings in the System Settings Monitor window to get it to work.

Now, the next task is to install a new Netgear gigabit NIC.........



> **n8oay said:**
> I installed a ATI All-In-Wonder 2006 AGP video card using the ati-driver-installer-8.26.18-i386 from ATI's web page. I could not get it to work at any resolution higher than 1024x786, so I tried to go back to the integrated S3 Graphics UniChrome Pro IGP on the Biostar P4M80-M4 motherboard. Now, it will only boot to a text logon. Do I need to reinstall Ubuntu, or is there another way to fix this mess?

> **beefcurry said:**
> no you just need to change the xorg.conf.

type in your terminal 
```
gksudo gedit /etc/X11/xorg.conf
```

Then create your modline [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl) and insert it into your xorg.conf under the [Monitor] section.

Remember to backup your xorg.conf first with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

---

### Post by beefcurry on 2007-03-10
glad i helped :D

---

