---
title: "Video Problems -- reinstall?"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by jmattos on 2007-03-18
Hi

I'm having a problem with ATI video drivers (I've tried binary and ubuntu versions) where the computer locks (screen goes black) after a few minutes. I thought that might be because when I installed, I had both monitors attached, could that have caused problems? should I look at reinstalling the OS?

---

### Post by wpshooter on 2007-03-18
What I do on my machines that use ATI video cards, is to install the **fglrx** drivers from **Synaptic** and then edit the xorg.conf file to substitute that parameter "fglrx" for the parameter "ATI" in the video driver section of the xorg.conf file.

Good luck.

---

### Post by jmattos on 2007-03-18
> **wpshooter said:**
> What I do on my machines that use ATI video cards, is to install the **fglrx** drivers from **Synaptic** and then edit the xorg.conf file to substitute that parameter "fglrx" for the parameter "ATI" in the video driver section of the xorg.conf file.

Good luck.

Cool, good info. A couple questions though..

1. Have you ever had the 5 minutes, then a blank screen thing happen?
2. if so, can you provide a little m ore detail about how to to what  you did?

Thanks!

---

### Post by wpshooter on 2007-03-18
As far a screen blanking, have you checked the power management setting to see what the slider is set on ?

Go into Software properties and make sure you have ALL of the repositories checked + you need to go to ADD and mark the Universe & Multi-universe reporitories and then let the reload of repositories take place so these will be written to your repositories listing.

Then go into Synaptic package manager and search for fglrx by **NAME**.

I think there are 3 packages that have to be installed for fglrx.

After those have been installed then to to the terminal and type:

sudo gedit /etc/X11/xorg.conf

Edit this portion of the file to look like this:

Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"

Yours will have a different Identifier but the driver need to read fglrx.

Good luck.

---

