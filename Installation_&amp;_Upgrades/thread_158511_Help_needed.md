---
title: "Help needed"
date: 2006-04-11
forum: Installation &amp; Upgrades
---

### Post by nolongerlivecd on 2006-04-11
I'm using Ubuntu 5.10, freshly installed, but I can't configure my network, so I can't apt-get anything. Also, I'm using an ATi Mobility Radeon X700, which means I also can't use any GUI. Is there a way I can get the fglrx drivers in Windows for use in Ubuntu?

---

### Post by taurus on 2006-04-11
For your graphic card, try using vesa as your driver.  Get into a terminal (or console) and edit your /etc/X11/xorg.conf by
```

sudo nano /etc/X11/xorg.conf

```
Now, use the arrow to scroll down to the section about Device and replace whatever it is currently to vesa as
```

Driver                          "vesa"

```
And for your network problem, you need to tell us whether you have a wireless (I assume it's wireless for your laptop then) or a USB connection?  If it's a wireless, brand and model would be nice...

---

### Post by nolongerlivecd on 2006-04-11
[QUOTE=taurus]For your graphic card, try using vesa as your driver.  Get into a terminal (or console) and edit your /etc/X11/xorg.conf by
```

sudo nano /etc/X11/xorg.conf

```
Now, use the arrow to scroll down to the section about Device and replace whatever it is currently to vesa as
```

Driver                          "vesa"

```
And for your network problem, you need to tell us whether you have a wireless (I assume it's wireless for your laptop then) or a USB connection?  If it's a wireless, brand and model would be nice...[/QUOTE]


Firstly, I tried vesa already I think. It didn't work.

I use Intel PRO/Wireless 2200BG as eth1

I use a Broadcom Gigabit Ethernet as eth0. Cannot setup as both linked to Linksys WRT54G( I think ) which auto-assigns IP

---

### Post by nolongerlivecd on 2006-04-12
And I get a blank screen using "vesa", "vga" doesn't work.

---

### Post by nolongerlivecd on 2006-04-12
I reckon it might be my 14.1-inch LCD, which displays WXGA 1280x800. It's widescreen, and vga and vesa are just not working. Am I supposed to configure it as up to 14 inches or 15inches?

---

### Post by nolongerlivecd on 2006-04-12
As posted in Repository support:

Hi guys, I'm stuck with a laptop that has Ubuntu installed, but cannot work in GUI mode, only Command Line. Reason being something to do with the driver. Is there anyway that I can install the driver/download it in Windows? My network has not been configured, using wired/wireless with Linksys WRT54G (i think), and it auto-assigns IP addresses.

It always reports that "Failed to start X server"

Setup:
Acer Aspire 5504WXMi
Pentium M 760 2GHz
1GB DDR2 SDRAM
ATi Mobility Radeon X700 (cannot work with both vesa and vga) 64MB DDR SDRAM
Intel Centrino
Intel PRO/Wireless 2200BG
Some Broadcom Gigabit Ethernet (only using 100Mbps cable)
100GB Ultra/ATA 100 HDD (93GiB), out of which 87GiB Windows, 2GiB unallocated and last 6.1GiB Ubuntu
14.1" Widescreen with CrystalBrite/XBRITE/Ultrasharp/SuperFine WXGA 1280x800


So my questions are:

1) Is there a download for that I can use in Windows to set up my graphics card?
2) What could be causing the problem?
3) How do I set up the network connection?

---

### Post by nolongerlivecd on 2006-04-12
Can anyone help? I long to be free of Windows...

---

### Post by taurus on 2006-04-12
Get to a console (or a terminal) and do
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by nolongerlivecd on 2006-04-13
And... do what? I tried that already. Which driver should I use? Which screen size should I select?

---

### Post by taurus on 2006-04-13
[QUOTE=nolongerlivecd]And... do what? I tried that already. Which driver should I use? Which screen size should I select?[/QUOTE]
How about driver vesa as I described above.  You can pick 1280x800 or whatever screen size there is available from it!!!

---

### Post by nolongerlivecd on 2006-04-13
Using vesa gives me a blank screen...

---

