---
title: "Ubuntu help"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by dcf-joe on 2008-04-28
I finally got it to work. I uninstalled Wubi, and then downloaded the ISO off of the internet. I burned the ISO onto a CD. To make a long story short, I successfully got Ubuntu to work. However, I made a fatal mistake. I forgot to shrink my Vista partition, so Ubuntu wrote right over it. So, no more Vista for me. Right now I am running the Vista recovery disk on the laptop to return everything to out-of-box condition, and this time I will shrink the Vista partition. However, I have two questions:

First, whenever I went into Ubuntu, I would see wavy lines on the screen. I think it is because the display driver is not loaded. So, I looked around, and I found the drivers. I have three of them, and ATI FireGL something is enabled, but not in use. How do I get this to work???

Second, I have a huge wireless problem, it simply doesn't work. Help on this too!!!!!

---

### Post by overdrank on 2008-04-28
> **dcf-joe said:**
> I finally got it to work. I uninstalled Wubi, and then downloaded the ISO off of the internet. I burned the ISO onto a CD. To make a long story short, I successfully got Ubuntu to work. However, I made a fatal mistake. I forgot to shrink my Vista partition, so Ubuntu wrote right over it. So, no more Vista for me. Right now I am running the Vista recovery disk on the laptop to return everything to out-of-box condition, and this time I will shrink the Vista partition. However, I have two questions:

First, whenever I went into Ubuntu, I would see wavy lines on the screen. I think it is because the display driver is not loaded. So, I looked around, and I found the drivers. I have three of them, and ATI FireGL something is enabled, but not in use. How do I get this to work???

Second, I have a huge wireless problem, it simply doesn't work. Help on this too!!!!!

Hi and when you get the live cd running use this command in the terminal ```
lspci
```the terminal is located under applications, accessories. This output will list your hardware, like VGA will be ATI and that is your graphics card. Then you wireless will look something like this ( sorry do not have wireless on my desktop)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
Then you can search the forums for advice. Good luck!

---

### Post by dcf-joe on 2008-04-29
So, I got the wavy line thing fixed by installing the 32-bit edition of Ubuntu. However, the ATI card still is in the restricted driver thing and I do not know how to fix it. I mean, yesterday was the first real day of using Linux in my lifetime. I also have a problem with the wireless system, I do not think that Atheros wireless is supported by Ubuntu stock. However, I found this driver here, [http://sourceforge.net/projects/madwifi/](http://sourceforge.net/projects/madwifi/)
but I need someone to tell me how to install the driver. I will need to download the driver with Vista, and then put in on a memory stick. When I get into Ubuntu, do I just double click on the driver thing, or do I need to do some crazy coding with the Terminal??? Also, to fix the ATI problem, do I just need to go to the ATI website, and get their linux driver for the card?

---

### Post by dcf-joe on 2008-05-01
So, I tried this, and the system is not even showing my wireless card. So I tried the ndiswrapper thingy, and it is not even on my system, or on the ISO Boot Disk. I also looked for something else that Ubuntu told me to look for, and it was not also not anywhere. The ATI card is enabled, but it has red letters by it saying that device is not in use.

I found Linux Atheros drivers from MadWifi, and they have file extensions GX2 or BZ2. Does anyone know how to install these, they might help.

---

