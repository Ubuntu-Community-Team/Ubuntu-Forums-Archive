---
title: "graphic problem after upgrading"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by aakaasha on 2008-04-15
Hello!

Yesterday I upgraded from Ubuntu 7.04 to version 7.10. Everything worked fine but after the system restart there was displayed nothing. The monitor switched from on to off periodically, which is an indication that the graphic card isn't working correct. I could log in without seeing the login screen.
I entered the console, which showed up in text mode. (Recovery mode did work too.)

In the Xorg.0.log there were some errors, among them one, where Ubuntu switched from BusID "PCI:1:0:1" to "PCI:1:0:0".

I changed this again to "PCI:1:0:1" in the xorg.conf.

After reboot Ubuntu entered the "low graphics mode" and let me choose the correct graphic card driver, but none of the ATI drivers (I'm using an ATI card) worked.

I clicked "cancel" and the login screen appeared!

Now the very strange thing: I could not login with my username/pwd! "Legitimation failed..." I switched to console, where I could login with my user/pwd!

I again took a look into the xorg.conf:

```

Section "Device"
  Identifier  "ATI Technologies Inc RV280 [Radeon 9200 PRO]"
  Driver   "ati"
  BusID  "PCI:1:0:1"
End Section

Section "Screen"
  Identifier  "Default Screen"
  Device  "ATI Technologies Inc RV280 [Radeon 9200 PRO]"
  Monitor  "DAEWOO"
  DefaultDepth 24
  SubSection "Display"
    Modes  "1280x1024"  "1024x768"  "832x624"  "800x600"  "720x400"  "640x480"
  EndSubSection
EndSection

```

Please help me! I don't have any idea what's going wrong.

Regards, Florian

P.S.: I forgot to mention that I have a multiboot system with WinXP.

---

### Post by aakaasha on 2008-04-15
Oh come one, pros! ;-)

I want to try getting it to run when I come home this evening...

Thanks in advance, Florian

---

### Post by aakaasha on 2008-04-15
Hi again!

I solved the problem!

I opened the terminal and after establishing an internet connection I did the following steps:

```

sudo apt-get install xorg-driver-fglrx
sudo dpkg-reconfigure xserver-xorg

```

Then followed the screen instructions.

Nevertheless I'd like to know, why I could not login using low graphics mode. :confused:

Kind regards, Florian

---

