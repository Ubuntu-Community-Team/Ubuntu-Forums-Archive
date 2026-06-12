---
title: "Resolution issues after upgrade"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by JackHarper on 2011-05-05
Yesterday I upgraded from Maverick Meerkat to the new 11.4.  Everything went ok but I cannot select the resolution 1024x768 16:9.... It was fine on Meerkat but now I have limited options which are 1024x768 4:3, 800x600 4:3, 848x480 16:9 and 640x480 4:3, thats it. I should also add that my monitor is a 40" Bravia connected through VGA. I tried plugged in an Acer 17" TFT and got the same result. 
Any help is much appreciated, thanks in advance.

---

### Post by dino99 on 2011-05-05
if you have created an xorg.conf, delete it and let the kernel doing its job

sudo rm /etc/X11/xorg.conf

and check that the graphic driver is activated (system admin additional driver)

---

### Post by JackHarper on 2011-05-06
There is no xorg.conf available and there are no proprietary drivers installed. Any other idea's......

---

### Post by Quackers on 2011-05-06
Does a graphics driver appear when you run Additional Drivers?

---

### Post by JackHarper on 2011-05-09
no it doesn't.

---

### Post by Grenage on 2011-05-09
I believe that there is an xorg setting called *dislaysize* which does what you need; there may be an xrandr alternative, but I've not used xrandr much.  If you want to go down the xorg.conf route, then I can try and help you out; if not, I'm sure someone will post an alternative.

---

### Post by JackHarper on 2011-05-12
> **Grenage said:**
> I believe that there is an xorg setting called *dislaysize* which does what you need; there may be an xrandr alternative, but I've not used xrandr much.  If you want to go down the xorg.conf route, then I can try and help you out; if not, I'm sure someone will post an alternative.


Yes please.

---

### Post by Grenage on 2011-05-12
No problem; I'll have to have a quick read of the syntax, but I'll try and get something posted back today.  Do you know what graphics card you have?  If not, post the results of:

```
lspci | grep VGA
```

---

### Post by JackHarper on 2011-05-16
ian@ian-Dell-DE051:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

---

### Post by Grenage on 2011-05-16
Try the configuration below; since you don't have an existing xorg.conf, you won't need to back it up.  If you encounter any problems when using this configuration, you need only delete or rename the file, and normal operation should resume.  I've never had to use *DisplaySize*, so we'll have to see how it works out; the Bravia frequency ranges are a _complete_ guess.

```
Section "Monitor"
    Identifier  "Monitor0"
    VendorName  "Sony"
    ModelName   "Bravia"
    HorizSync   35 - 65
    VertRefresh 60
    DisplaySize  347 195
EndSection

Section "Device"
    Identifier "Device0"
    Driver "intel"
    VendorName "Intel 82865G"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device "Device0"
    Monitor "Monitor0"
    DefaultDepth 24
    SubSection "Display"
        Depth 24
        Modes "1024x768"
    EndSubSection
EndSection
```

---

### Post by MAFoElffen on 2011-05-16
> **JackHarper said:**
> Yesterday I upgraded from Maverick Meerkat to the new 11.4.  Everything went ok but I cannot select the resolution 1024x768 16:9.... It was fine on Meerkat but now I have limited options which are 1024x768 4:3, 800x600 4:3, 848x480 16:9 and 640x480 4:3, thats it. I should also add that my monitor is a 40" Bravia connected through VGA. I tried plugged in an Acer 17" TFT and got the same result. 
Any help is much appreciated, thanks in advance.
On boxes without proprietary drivers, you can still generate an xorg.conf via
```
 (My notes)
In order to generate xorg.conf you need to switch to one virtual console using the key combination CTRL + ALT + F1.
 Now execute the following commands:
[code]
sudo service gdm stop

```This command will stop the X.
 Now we need to generate the xorg.conf file:
```

  sudo Xorg -configure

``` This has generated the file in ~/xorg.conf.new.
 We need to make the X using it so we have to put this file inside /etc/X11/
```

  sudo mv ~/xorg.conf.new /etc/X11/xorg.conf

``` After moving this file to the proper location you can start the X again and see what happens:
```

  sudo service gdm start

```[/code]Which would generate an xorg.conf on his PC that he could edit without worrying about external things that were added or different.

Another way is to add an ~/.xprofille file as a text file with added xrandr commands such as
```

xrandr --output VGA1 --mode 1024x768
xrandr --output LVDS1 --mode 1024x768

```Where you can get the device names and modes by running 
```

xrandr -q

```Form a terminal, testing the output commands from a terminal to see if the y worked, before adding them to that file.... BUT... You really might not need that if...

If you go to /etc/default/grub and... go to the line
```

# GRUB_GFXMODE=640x480

```And change it to the modes you said it supported, separated with a semi-colon:
```

GRUB_GFXMODE=1024x768x24;800x600x24;848x480x24;640x480x24

``` Then those modes are there and you only need to press <cntrl><+> and <cntrl><-> to toggle between them.

Either way should work.

EDIT:  Just reread > Changing Aspect Ratio's...  He's right- Xorg.conf.

---

