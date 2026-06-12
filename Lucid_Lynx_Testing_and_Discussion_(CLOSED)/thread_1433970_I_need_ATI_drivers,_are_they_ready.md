---
title: "I need ATI drivers, are they ready?"
date: 2010-03-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by greg606 on 2010-03-19
I need ATI drivers, are they ready? If not then when?
Regards,
Greg

---

### Post by GeoPrude on 2010-03-19
Catalyst doesn't work yet, the open drivers do.

---

### Post by greg606 on 2010-03-19
Where can I get them?
thanks ;)

---

### Post by gjoellee on 2010-03-19
> **greg606 said:**
> Where can I get them?
thanks ;)

I got my ATI drivers out of the box, but I think you can find some at [www.ati.com](www.ati.com) or in the "hardware drivers" program in the system menu

---

### Post by greg606 on 2010-03-19
I have read somewhere that those from ATI don't work yet as the previous post suggest

---

### Post by jppr on 2010-03-19
The fglrx binary driver for ATI video chipsets does not yet support the  X server in Lucid. As a workaround, users should use the open source  -ati driver instead. (494699)

---

### Post by descendent87 on 2010-03-19
[http://www.phoronix.com/scan.php?page=news_item&px=ODA4MA](http://www.phoronix.com/scan.php?page=news_item&px=ODA4MA) looks like they should work now, although the open source drivers work great for me so no need for catalyst

---

### Post by emarkay on 2010-03-20
See thisi thread - maybe "not ready yet"? 

[http://ubuntuforums.org/showthread.php?t=1434064&highlight=ati](http://ubuntuforums.org/showthread.php?t=1434064&highlight=ati)

---

### Post by jwssr on 2010-03-20
It works GREAT for me...with a small caveat...

First of all, only use the 0unbutu3  (launchpad.net/ubuntu/lucid/+source/fglrx-installer/2:8.721-0ubuntu3) link.  

The builds for i386 and amd64 are on this page...download and install.
Insure that you download and install in order...fglrx must be first..
Built files
   * fglrx_8.721-0ubuntu3_amd64.deb (27.8 MiB)
    * fglrx-amdcccle_8.721-0ubuntu3_amd64.deb (4.9 MiB)
    * fglrx-dev_8.721-0ubuntu3_amd64.deb (63.4 KiB)
    * fglrx-modaliases_8.721-0ubuntu3_amd64.deb (13.4 KiB)



I spent the better part of today getting unmet dependencies on 0unbuntu1/2..then I tried 0unbuntu3 and it works.

The caveat...is that when configuring Catalyst.

Display Manager /  MultiDisplay tab allows 4 options.
    Disabled Display
    Single Display Desktop(Multi-desktop)
    Cloned display from display(s)2
    Multi-display desktop with display(s)2     

My first (and I think the default) was Single Display Desktop......which allows for both monitors to have gnome panels with the cursor moving between monitors thru the bottom of each screen only.  You can open apps on each monitor but cannot drag them to the other monitor.

This is the CAVEAT....Nautilus goes ape(it fires up on its own)....running constantly...hogging cpu...blinking in lower gnome panel and the inability to run nautilus at all.

When I changed to Muti-display desktop with display(s)2....it works perfectly...

Gnome panel only only monitor 1....drag apps from monitor1 to monitor2 and back...change positions of monitor1 and Monitor2 to left or right...

Catalyst also allowed me to change the size of the display area on each monitor (ie  fillup screen or make smaller....black borders)
Its also nice to have sound again thru HDMI...although Alpha3 without a prop driver also allowed sound thru HDMI

This is beta1...2.6.32-16...xorg 1.7.5....gnome 2.29.92...ati Radeon HD 3200 Graphics tied to 47in Lcd via HDMI cable   and 24 in analog Lcd via 15pinVGA....AMD dual core x64.        

VERY NICE!!!!

---

