---
title: "Screen resolution"
date: 2015-06-23
forum: Installation &amp; Upgrades
---

### Post by fsrgio2 on 2015-06-23
Hello, i just installed the Lubuntu 15.04 but after the installation and updating the screen size is too big only have 640x480 resolution size. How can i change this or add next resolution sizes? My graphics card is onboard and only says 661/741/760 PCI/AGP or 662/761Gx PCIE VGA display adapter.

---

### Post by v3.xx on 2015-06-23
SiS
[https://wiki.archlinux.org/index.php/SiS#lspci](https://wiki.archlinux.org/index.php/SiS#lspci)

xrandr give any options?
```
xrandr
```

And welcome to the forums :)

---

### Post by fsrgio2 on 2015-06-23
> **v3.xx said:**
> SiS
[https://wiki.archlinux.org/index.php/SiS#lspci](https://wiki.archlinux.org/index.php/SiS#lspci)

xrandr give any options?
```
xrandr
```

xrandr says that(640x480) is the maximum resolution

"xrandr: Failed to get sie of gamma for output default
Screen 0: minimum 640x480, current 640x480, maximum 640x480"

But i use different resolution when using win xp for example. The same when i installed Linux antiX. Do i need to edit that file that is explained in the link you just post here?
> **v3.xx said:**
> And welcome to the forums :)

Thank you and sorry for missing the presentation :p

---

### Post by v3.xx on 2015-06-23
I do not have first hand experience with your graphics and unsure of the best course of action.  I have found this.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=[SiS]+661%2F741%2F760+PCI%2FAGP+or+662%2F761Gx+PCIE&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=[SiS]+661%2F741%2F760+PCI%2FAGP+or+662%2F761Gx+PCIE&sa=Search&cof=FORID:9)

---

### Post by matt_symes on 2015-06-23
Hi

The sis vga chipset is a pain to get working with *buntu as sis were never very forth coming with the specs on how to write the driver.

I have the same problem with some Shuttle xpc boxes i have that also have.

I had to create an xorg.conf file to load the sis module and to add the correct screen resolution. I have only tried this on xubuntu 14.04.

I am not at home at the moment so i cannot check if you have the same chipset as me. You are also using 15.05 and not 14.04.

However, that being said and in the first instance, here is my xorg.conf file.

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "sis"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        # 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
        Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
        # 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
        Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
        SubSection "Display"
                Modes "1280x1024" "1024x768"
                Depth 24
        EndSubSection
EndSection

```

I think there is also a ppa with an updated driver for the new xorg stack but i hyave never used it.

Kind regards

---

### Post by fsrgio2 on 2015-06-24
Thank you guys for all your reply. I just download and installed the Lubuntu 14.04 and now the resolution is good and i have more resolution sizes to choose from. Thank you all but this was a much easier way to solve the problem :lolflag:

---

### Post by matt_symes on 2015-06-24
Hi

Excellent. 

It looks like you don't need the xorg config file for the later point releases of 14.04. 

You did when 14.04.0 was initially released so it's good to know that's been addressed.

Kind regards

---

