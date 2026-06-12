---
title: "Can't boot Live CD or install"
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by bhhandley on 2007-04-15
I want to use the i386 build because I don't like having to search for custom packages and a bunch of extra steps when running 64bit only to get a small performance boost.  I have tried 6.06, 6.10, 7.04 and all hang at the same point (see attachments) and after trying everything I have read I'm looking for some help.

With each version, I have tried none/some/all and in different combinations of the following boot options:

noapic, nolapic, acpi=noirq, iommu=off, pnpbios=off, pci=routeirq, pci=nomsi and couple others I can't remember...

I apologize for the quality of the images... The wife has my digital camera and all I had was my Treo to take the pictures with.

**Image 1:** The odd artifacts show up on 6.06 and 6.10 when I add in different boot options and they happen always with a standard boot of 7.04.

**Image 2:** I know it's hard to see but once Gnome starts to boot, it always hangs at this point with only a small strip of the Gnome loading window (or atleast I think it is) with strange graphics.  This happens in all versions, with or without extra boot options.

Please, if anyone can shine some light on my problem, even if the answer is that I will never be able to install on this setup, I would be much appreciative.


**_System Specs:_**
**CPU:** AMD Athlon X2 4200+
**Memory:** 2GB DDR PC-400
**Motherboard:** EVGA 133-K8-NF41
**Video:** EVGA 7800GT
**Sound:** Onboard Realtek

**_Storage:_**
Western Digital 74GB Raptor
Western Digital 160GB SATA
Seagate 120GB IDE


Thanks in advance.

---

### Post by mikewhatever on 2007-04-15
I'd suggest using the Alternate Install CD, which provides a text mode Ubuntu installer with no option for the Live cd. Use this guide if needed [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
Once Ubuntu is installed, you'll probably have errors saying 'xserver failed to load' and so on. In that case you'll need to reconfigure xserver, here is another guide [http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)
Another option would be to let envy program take care of the driver 
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
The Alternate CD installer can be downloaded from the same page as desktop, but lower down.

---

### Post by jay1227 on 2007-04-18
7800GT doesnt work with the default "nv" driver...

1) boot to CD
2) Press F6 and remove "quiet splash" and replace with "break=bottom"    --- no quotes!
3) hit enter

eventually the loading will seize, and you should type

"sudo chroot /root nano /etc/X11/xorg.conf"

hit enter

scroll down to where you will see DEVICE and your Nvidia card listed. the driver will be "nv"
change "nv" to "vesa"

press Ctrl+O --- enter  --- Ctrl+X

then type "exit" and hit enter

Voila!

---

