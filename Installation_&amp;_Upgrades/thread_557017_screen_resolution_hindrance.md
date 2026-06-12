---
title: "screen resolution hindrance"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by whittler on 2007-09-22
Hi All,

I cannot install ubuntu. Running the CD installation, the installer set my screen resolution to 640X480. So I can't even access the next button at the bottom right of the screen.

The screen resolution tool in preferences is of no use as it does not offer an alternative resolution.

Unfortunately, I don't know what kind of graphics hardware this PC has. All I know is that it is on-board graphics.

If anyone knows of a way that I can adjust the resolution, that would be cool.

Thanks

---

### Post by PmDematagoda on 2007-09-22
Whats the VGA card that you have?

Anyway if it's something with your Live CD, why don't you try the Alternate CD?

[http://releases.ubuntu.com/feisty/](http://releases.ubuntu.com/feisty/)

---

### Post by w4ett on 2007-09-23
> **whittler said:**
> Hi All,

I cannot install ubuntu. Running the CD installation, the installer set my screen resolution to 640X480. So I can't even access the next button at the bottom right of the screen.

The screen resolution tool in preferences is of no use as it does not offer an alternative resolution.

Unfortunately, I don't know what kind of graphics hardware this PC has. All I know is that it is on-board graphics.

If anyone knows of a way that I can adjust the resolution, that would be cool.

Thanks

On the main menu of the live cd there is a tab labeled 'VGA',  you might be able to select additional resolutions there..

You can move any window by holding the 'ALT' key and click and drag the window.

To identify what video chipset you are using...in the terminal type:

```
lspci
```

This will list all chipsets and cards in your system.

---

### Post by whittler on 2007-09-23
Thanks for the suggestions. The VGA menu option only offered the same one small resolution.

The output from lspci is:
> 
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)

---

### Post by w4ett on 2007-09-23
This is your video chipset:

> 00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)


question...is this a Gygabyte or intel board?

Well...doesn't  look like this video chipset is going to be too much trouble to get running...you have two choices at this point..(1) continue on with your live cd install....or(2) download and use the Alternate install cd....I think you will be ok with the live cd, and we can modify your video settings after you install.

Just use the ALT key to move the input windows up, and all should go as planned.

---

### Post by whittler on 2007-09-23
I shall proceed with the install and get back.

---

### Post by w4ett on 2007-09-23
Good Luck.  We'll be here if you need some guidance. :)

---

### Post by whittler on 2007-09-23
OK.

I have now installed Feisty Fawn to my hard drive. I now need to address the screen resolution issue. As above, I have tried the preferences and only have the one screen resolution as an option (640X480).

I guess I need a bit of guidance from here.

---

### Post by w4ett on 2007-09-23
Ok...let us see your xorg.conf file...in the terminal type:

```
cat /etc/X11/xorg.conf
```

and post the results of the command.

---

### Post by dabl on 2007-09-23
I think you want the xserver-xorg-video-intel driver, available in the repos.

```
sudo apt-get install xserver-xorg-video-intel
```

Then restart your xserver with Ctrl-Alt-Backspace, and see how it looks. :popcorn:

---

### Post by whittler on 2007-09-23
Installing the xserver-xorg-video-intel driver worked.

Thanks very much for sorting this out for me. Much appreciated.

---

### Post by teamnoir on 2007-09-25
I now have this problem with gutsy.  I see no "vga" tab.  And alt-move won't let me move a window up above the menu bar so I still can't reach the bottom buttons.

VGA controller is an Intel 82865G.

Any suggestions?

---

