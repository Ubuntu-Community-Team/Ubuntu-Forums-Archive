---
title: "Ubuntu install problems on an Nvidia GeForce FX5500"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by cisasteelersfan on 2007-10-22
hi i'm a really new user to ubuntu.  when i do the install, everything seems to work fine but after the ubuntu logo and the bar fills up, the screen goes blank. no console window, no blinking cursor, nothing.  

i have ubuntu 7.10

here are my specs:

2.0 ghz celeron processor
256 mb ram
Nvidia GeForce FX5500 w/ 256 mb ram
trying to install Ubuntu 7.10

any posts are greatly appreciated.

---

### Post by cisasteelersfan on 2007-10-22
ok so i did that thing with the quiet and unsound or w/e thing.  then i reconfigured the xserver and stuff but after i pick my monitor bits or something, i type "startx" and an error comes up. its error 104 (connection reset by peer) on X server ":0.0" after 0 requests (0 know processed) with 0 events remaining"

what can i do? any posts are GREATLY APPRECIATED. this is my first time with Linux and Ubuntu and i really want to be able to use it

---

### Post by bruban on 2007-10-22
Is your monitor an LCD and connected to your PC via a DVI cable?

If so there does appear to be an issue with this combination.

Assuming that this is the problem, try connecting to your monitor with the VGA DSUB cable to see if that makes a difference on reboot.

---

### Post by cisasteelersfan on 2007-10-22
My monitor is a 19" LCD.  it is connected by VGA (i think!)

Thanks for the suggestion.

---

### Post by gmoser on 2007-10-30
I got the same problem with a geforce FX5500.  If the card is installed I cannot run live cd, nor a regular install with onboard VGA and install and boot with the card in.

If that card is in the system will not boot.  Even tried to install the nvidia drivers then install... no go.

Any advice from the linux gods?

---

### Post by athailah on 2007-10-30
Me too, I confused with this distro. I has tried with openSUSE 10.3 I got no problem with this graphics card, but in Ubuntu...

I has install all version Ubuntu to make this card work... I tried from Ubuntu 6.06, 6.10, 7.04, and 7.10. and all got blank screen after Install driver. Tried driver from Ubuntu repo, and nvidia official site with same result, screen blank after run this driver...

What wrong with Ubuntu...?, Any body can tell us how to fix this problem in Ubuntu...?

My System:

Pentium 4 3 Ghz
RAM 2 GB DDR1
Nvidia GeForce FX5500
MAXTOR SATA 500 GB
LG DVD R/W
LG LCD Monitor 17 Inc

---

### Post by bruban on 2007-10-31
> **athailah said:**
> ... I tried from Ubuntu 6.06, 6.10, 7.04, and 7.10. and all got blank screen after Install driver. Tried driver from Ubuntu repo, and nvidia official site with same result, screen blank after run this driver...



I found the same problem after I enabled the proprietary NVIDIA drivers

_Steps I used to recover display_

- boot into Ubuntu. If you don't get anything displayed on screen, wait for a few minutes for disk activity to cease.

- press CTL-ALT-F1 to get a virtual terminal

- change user to root:

```
sudo -s -H
   <your password>
```

- backup your /etc/X11/xorg.conf file

- edit /etc/X11/xorg.conf:

- look for the section Device, It will be different to this, however this will give you an idea.

> 
Section "Device"
        Identifier      "nVidia Corporation NV18 [GeForce4 MX 4000]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection


- change the driver value to vesa as in

       ```
Driver          "vesa"
```

- if you also have 'Option' arguments defined in the Device section (as in the example above), remove them as well.

- reboot

- using System>Administration>Restricted Drivers Manager activate the NVIDIA drivers and then **_immediately_** deactivate the NVIDIA drivers with no reboot in between.

-  This should uninstall the proprietary NVIDIA drivers.

- after reboot, I found that my system display was again usable.

---

### Post by louieb on 2007-10-31
Quick question: is you FX5200 PCI or AGP? I have the FX5200 AGP interface in 2 computers both work flawlessly. But I have had trouble in the past with the PCI version of the card (didn't work) go figure.

---

### Post by athailah on 2007-11-01
> **bruban said:**
> I found the same problem after I enabled the proprietary NVIDIA drivers

_Steps I used to recover display_

- boot into Ubuntu. If you don't get anything displayed on screen, wait for a few minutes for disk activity to cease.

- press CTL-ALT-F1 to get a virtual terminal

- change user to root:

```
sudo -s -H
   <your password>
```

- backup your /etc/X11/xorg.conf file

- edit /etc/X11/xorg.conf:

- look for the section Device, It will be different to this, however this will give you an idea.



- change the driver value to vesa as in

       ```
Driver          "vesa"
```

- if you also have 'Option' arguments defined in the Device section (as in the example above), remove them as well.

- reboot

- using System>Administration>Restricted Drivers Manager activate the NVIDIA drivers and then **_immediately_** deactivate the NVIDIA drivers with no reboot in between.

-  This should uninstall the proprietary NVIDIA drivers.

- after reboot, I found that my system display was again usable.

Thanks bruban,

I tried already like your trics, now I can go to desktop. 

But one more question, how to make desktop effecs (compiz) active if I use vesa driver?

---

### Post by athailah on 2007-11-01
> **louieb said:**
> Quick question: is you FX5200 PCI or AGP? I have the FX5200 AGP interface in 2 computers both work flawlessly. But I have had trouble in the past with the PCI version of the card (didn't work) go figure.

Hi louieb,

My FX5500 type is AGP.

---

### Post by bruban on 2007-11-01
> **athailah said:**
> Thanks bruban,

I tried already like your trics, now I can go to desktop. 

But one more question, how to make desktop effecs (compiz) active if I use vesa driver?


I don't think that you'll be able to.

Keep an eye out for updated drivers for your card. When they become available, try them. The problems that you're facing may have been fixed. When you have new drivers active, you can try the desktop effects then.

Bruce

---

### Post by F-22 on 2007-11-01
Hi new here, does NVIDIA have dedicated drivers for ubuntu users? :confused:

---

### Post by bruban on 2007-11-02
> **F-22 said:**
> Hi new here, does NVIDIA have dedicated drivers for ubuntu users? :confused:

Yes...and no. See the following url for **_Linux_** drivers for NVIDIA cards. There are also install instructions if you feel confident enough to try the install (just make sure that your data is backed up first). They should work with Ubuntu, though I haven't had the need to try them myself yet.

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)


Alternatively, Synaptic can point you to a range of NVIDIA drivers that have been packaged for Ubuntu. I don't know how often these packages are updated. I suspect only with each 6 monthly release of Ubuntu. 

System>Administration>Synaptic Package Manager     and search on nvidia.


Another option would be to try the Ubuntu Development repositories for more up to date drivers, but if you are not that confident with Linux yet, I wouldn't recommend it.

Bruce

---

