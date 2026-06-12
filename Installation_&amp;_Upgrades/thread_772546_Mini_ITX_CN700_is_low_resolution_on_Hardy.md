---
title: "Mini ITX CN700 is low resolution on Hardy"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by frankos44 on 2008-04-28
Trying to get the resolution correct with Hardy on my silent PC.
 
EPIA CN10000EG
VIA C7 1.0GHz NanoBGA2
VIA CN700 North Bridge
VIA VT8237R-Series South Bridge
1G DDR2 400/533 DIMM

It only allows maximum 800x600.

---

### Post by _sluimers_ on 2008-06-01
Mine works fine at 1680x1050 and I have an LN.
What have you tried?

---

### Post by frankos44 on 2008-06-02
> **_sluimers_ said:**
> Mine works fine at 1680x1050 and I have an LN.
What have you tried?

CN i would assume. The model is CN10000EG

---

### Post by _sluimers_ on 2008-06-04
I mean, have you tried editing in xorg.conf and stuff?

---

### Post by frankos44 on 2008-06-04
> **_sluimers_ said:**
> I mean, have you tried editing in xorg.conf and stuff?

No I simply installed a fresh copy of Hardy desktop. I dont think you can adjust screen resolution in xorg.conf in Hardy anyway?

---

### Post by linux4me on 2008-06-04
My monitor is attached via a KVM and doesn't properly get detected when I do an install, so I have adopted the following to get past the resolution problem. I'm not an expert, but this procedure has worked for me, and it may work for you.

First, open a Terminal window (Applications->Accessories->Terminal).
Next, back up your existing xorg.conf file by running the command:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
Then run the command:
```
sudo displayconfig-gtk
```
Select your monitor and intended resolution from the list. Here's where there may be a problem; your monitor configuration may not be ON the list. If that's the case, you may have to go with manually configuring xorg.conf.

If so, take a look at [this post]("http://ubuntuforums.org/showpost.php?p=1905799&postcount=2"), which walks you through the process of obtaining the correct modelines for your monitor's resolution and refresh rates. It does what displayconfig-gtk would have done for you. (You can get the figures for the resolution and refresh rates for your monitor from the monitor's manual or manufacturer's website if you don't know them.)

---

### Post by frankos44 on 2008-06-05
> **linux4me said:**
> My monitor is attached via a KVM and doesn't properly get detected when I do an install, so I have adopted the following to get past the resolution problem. I'm not an expert, but this procedure has worked for me, and it may work for you.

First, open a Terminal window (Applications->Accessories->Terminal).
Next, back up your existing xorg.conf file by running the command:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
Then run the command:
```
sudo displayconfig-gtk
```
Select your monitor and intended resolution from the list. Here's where there may be a problem; your monitor configuration may not be ON the list. If that's the case, you may have to go with manually configuring xorg.conf.

If so, take a look at [this post]("http://ubuntuforums.org/showpost.php?p=1905799&postcount=2"), which walks you through the process of obtaining the correct modelines for your monitor's resolution and refresh rates. It does what displayconfig-gtk would have done for you. (You can get the figures for the resolution and refresh rates for your monitor from the monitor's manual or manufacturer's website if you don't know them.)

I now use this box as a server so not an issue, however I re-visited the problem purely out of interest and loaded Hardy Desktop on a spare drive this morning. It all worked OK this time with all the resolutions available. 

From memory on the previous attempt the "Screen and Graphics" gtk dialog did not allow me to change the monitor model.

The graphics performance is not great though, looks to me as if the hardware acceleration is not working. Its currently using "openchrome" driver. 

I remember looking at the EPIA website last time and there was no driver for available for Hardy. Have you installed a third party driver on yours?

---

### Post by linux4me on 2008-06-05
> **frankos44 said:**
> I remember looking at the EPIA website last time and there was no driver for available for Hardy. Have you installed a third party driver on yours?

Sorry, I don't have the same hardware as you. I was just trying to help by giving you some general steps to get an improperly/undetected monitor to work. I am using a 3rd party Nvidia driver for mine, though. It cleared up a number of problems I was having with my display...

---

### Post by frankos44 on 2008-06-05
> **linux4me said:**
> Sorry, I don't have the same hardware as you. I was just trying to help by giving you some general steps to get an improperly/undetected monitor to work. I am using a 3rd party Nvidia driver for mine, though. It cleared up a number of problems I was having with my display...

It was helpful all the same, thanks.

---

