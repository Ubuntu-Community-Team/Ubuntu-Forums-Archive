---
title: "Cannot load 2.6.32-21"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by ubu newb on 2010-05-06
I upgraded from from 9.10 to 10.04 through update manager within 9.10.   All seemed to go well but upon rebooting I get a blinking screen.  

When I get to the boot screen I choose  2.6.32-21  

[[IMG]http://i580.photobucket.com/albums/ss246/hookemfins/th_LinuxBootScreen.jpg[/IMG]]("http://s580.photobucket.com/albums/ss246/hookemfins/?action=view&current=LinuxBootScreen.jpg")

Once I select 2.6.32-21, as it's loading up the screen blinks constantly  like below.  Only way out is a hard reboot.  What  went wrong? 

[[IMG]http://i580.photobucket.com/albums/ss246/hookemfins/th_19049259865_ORIG.jpg[/IMG]]("http://s580.photobucket.com/albums/ss246/hookemfins/?action=view&current=19049259865_ORIG.flv")
[URL="http://s580.photobucket.com/albums/ss246/hookemfins/?action=view&current=19049259865_ORIG.flv"]
[/URL]

---

### Post by tom4everitt on 2010-05-06
Try restoring grub:

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by ubu newb on 2010-05-06
I left out a detail, I am able to load 10.04 under the second option 2.6.31-20.   If my research is correct, is 2.6.31-20 an old beta version that I am loading?  

Thanks

---

### Post by tom4everitt on 2010-05-06
Okay, well, than grub is not the problem. Kernel number 22 is out, so try installing the latest upgrades and it should be included with those. It is no real problem booting the beta kernel, the difference is usually not that big. 

What you could also try is running:
```

sudo update-grub

```
once, which will regenerate the grub-configuration file. 

If you want to get rid of the malfunctioning kernel (number 21), you can run:
```

sudo apt-get remove --purge linux-image-2.6.32-21-generic

```
in a terminal

---

### Post by ubu newb on 2010-05-06
Thanks for the help Tom,

I tried sudo update-grub and same problem when I rebooted.  I went to purge and got this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-image-2.6.32-21-generic is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 34 not upgraded.
rick@rick-U:~$ 

I tried to update grub and I got Found linux image: /boot/vmlinuz-2.6.32-21-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-21-generic-pae

but I cannot remove or purge it.:confused:

---

### Post by ubu newb on 2010-05-06
OK, able to purge once I added the -pae at the end.  I ran update manager and it added 2.6.32-22 but I have the same problem with the screen blinking.   What is causing that?


When I purged 32-21 here is the readout:    What is the damaged link?


The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-2.6.32-21-generic-pae ...
Running postrm hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found Windows 7 (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
Found linux image: /boot/vmlinuz-2.6.32-22-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-22-generic-pae
Found linux image: /boot/vmlinuz-2.6.31-20-generic-pae
Found initrd image: /boot/initrd.img-2.6.31-20-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
done

---

### Post by Catharsis on 2010-05-07
It's probably a graphics issue. Try:

```
Xorg -configure
```

Or:
```
sudo dpkg-reconfigure xserver-xorg
```

Or:
In the GRUB menu:
1) Highlight the 32-22 kernel and hit 'e'.
2) Arrow down to the part with "quiet splash" and replace that text with "nomodeset".
3) Ctrl+x to boot.

If that doesn't work, instead of "nomodeset", try (individually): "i915.modeset=1", "i915.modeset=0", or "xforcevesa noapic noapci nosplash irqpoll".

You could also try booting into Recovery Mode (choose the kernel that says "recover" or something next to it).

---

### Post by ubu newb on 2010-05-07
> You could also try booting into Recovery Mode (choose the kernel that  says "recover" or something next to it).

When I get home tonight I'll try your suggestions.   I've tried recovery mode the problem is the same as regular boot.

---

### Post by ubu newb on 2010-05-07
[]("http://ubuntuforums.org/member.php?u=920304")Catharsis, none of those worked and each time quiet splash reappeared.  What would be my next move?

---

### Post by ubu newb on 2010-05-08
Any other suggestions to get this problem solved?  It seems that each  successive kernel I won't be able to upgrade to.  I have tried  everything above and recovery mode, each resulting in the same problem.

---

### Post by Catharsis on 2010-05-08
This is definitely very strange.

I suggest you post your dmesg and xorg logs in the 32-22 kernel in hopes that there's something exciting in them:
```
cat /var/log/dmesg
cat /var/log/Xorg.0.log
```

You can try updating your graphics drivers, although I doubt it'll help.
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update && sudo apt-get upgrade
```

It would also be nice to know your system specs:
```
lspci
```

---

### Post by ubu newb on 2010-05-08
> This is definitely very strange.

I suggest you post your dmesg and xorg logs in the 32-22 kernel in hopes  that there's something exciting in them:

I can get the dmesg from while in the 31-20 kernel?   I cannot do anything from the 32-22, the screen blinks way to fast.

I'll post the system specs later tonight.   Would I be better off just re-installing over the existing install from live cd instead?

---

### Post by Catharsis on 2010-05-08
You can also try:
[http://ubuntuforums.org/showpost.php?p=9242639&postcount=4](http://ubuntuforums.org/showpost.php?p=9242639&postcount=4)

A clean install might fix it. If you don't have anything to lose, it's worth a shot. At the very least, it'd be nice to know if the LiveCD can boot normally.

---

### Post by jnme on 2010-05-08
Upgraded to 10.04 via Update Manager.  GRUB menu gave two builds, 2.6.32-22 and 2.6.31.20.  32.22 was very slow, apparently due video performance (slow, lots of mouse pointer relics, and in terminal, no feedback on what was typed (like an old duplex issue).  31.20 worked great.   

Thanks to feedback above from CATHARSIS, I replaced QUIET SPLASH with NOMODESET and now 32-22 works as expected.  My kudos to all on the forums that help those of us less technologically proficient.

---

### Post by ubu newb on 2010-05-09
I am able to get in now by replacing quiet splash with nomodeset however it doesn't stick.  When I restart, even after updating the graphics card, quiet splash is back and I get the flashing.  Below are the logs requested:

(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.646 redY: 0.339   greenX: 0.290 greenY: 0.603
(II) RADEON(0): blueX: 0.145 blueY: 0.065   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x864@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1152  vsize 720  refresh: 60  vid: 113
(II) RADEON(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #4: hsize: 1600  vsize 1000  refresh: 60  vid: 169
(II) RADEON(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) RADEON(0): Ranges: V min: 48 V max: 76 Hz, H min: 24 H max: 83 kHz, PixClock max 160 MHz
(II) RADEON(0): Monitor name: HP w2207
(II) RADEON(0): Serial No: 3CQ8410CLR
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff0022f0a92601010101
(II) RADEON(0):     29120103802f1e78eeb535a5564a9a25
(II) RADEON(0):     105054a56b807100814081809500a900
(II) RADEON(0):     b3000101010121399030621a274068b0
(II) RADEON(0):     3600d9281100001c000000fd00304c18
(II) RADEON(0):     5310000a202020202020000000fc0048
(II) RADEON(0):     502077323230370a20202020000000ff
(II) RADEON(0):     0033435138343130434c520a202001df
(II) RADEON(0):     02031bf1230907074884020107161110
(II) RADEON(0):     1f8301000065030c0010008c0ad08a20
(II) RADEON(0):     e02d10103e9600d928110000188c0ad0
(II) RADEON(0):     90204031200c405500d9281100001801
(II) RADEON(0):     1d8018711c1620582c2500d928110000
(II) RADEON(0):     9e011d00bc52d01e20b8285540d92811
(II) RADEON(0):     00001e011d80d0721c1620102c2580d9
(II) RADEON(0):     281100009e0000000000000000000060
(II) RADEON(0): EDID vendor "HWP", prod id 9897
Dac detection success
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Unhandled monitor type 0
Dac detection success
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "HWP", prod id 9897
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1152x720"x60.0   67.32  1152 1208 1328 1504  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) RADEON(0): Modeline "1600x1000"x60.0  133.14  1600 1704 1872 2144  1000 1001 1004 1035 -hsync +vsync (62.1 kHz)
(II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Output: HDMI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: HDMI-0 ----------------------
(II) RADEON(0): Manufacturer: HWP  Model: 26a9  Serial#: 16843009
(II) RADEON(0): Year: 2008  Week: 41
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.646 redY: 0.339   greenX: 0.290 greenY: 0.603
(II) RADEON(0): blueX: 0.145 blueY: 0.065   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x864@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1152  vsize 720  refresh: 60  vid: 113
(II) RADEON(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #4: hsize: 1600  vsize 1000  refresh: 60  vid: 169
(II) RADEON(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) RADEON(0): Ranges: V min: 48 V max: 76 Hz, H min: 24 H max: 83 kHz, PixClock max 160 MHz
(II) RADEON(0): Monitor name: HP w2207
(II) RADEON(0): Serial No: 3CQ8410CLR
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff0022f0a92601010101
(II) RADEON(0):     29120103802f1e78eeb535a5564a9a25
(II) RADEON(0):     105054a56b807100814081809500a900
(II) RADEON(0):     b3000101010121399030621a274068b0
(II) RADEON(0):     3600d9281100001c000000fd00304c18
(II) RADEON(0):     5310000a202020202020000000fc0048
(II) RADEON(0):     502077323230370a20202020000000ff
(II) RADEON(0):     0033435138343130434c520a202001df
(II) RADEON(0):     02031bf1230907074884020107161110
(II) RADEON(0):     1f8301000065030c0010008c0ad08a20
(II) RADEON(0):     e02d10103e9600d928110000188c0ad0
(II) RADEON(0):     90204031200c405500d9281100001801
(II) RADEON(0):     1d8018711c1620582c2500d928110000
(II) RADEON(0):     9e011d00bc52d01e20b8285540d92811
(II) RADEON(0):     00001e011d80d0721c1620102c2580d9
(II) RADEON(0):     281100009e0000000000000000000060
(II) RADEON(0): EDID vendor "HWP", prod id 9897
Dac detection success
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Unhandled monitor type 0
Dac detection success
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "HWP", prod id 9897
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1152x720"x60.0   67.32  1152 1208 1328 1504  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) RADEON(0): Modeline "1600x1000"x60.0  133.14  1600 1704 1872 2144  1000 1001 1004 1035 -hsync +vsync (62.1 kHz)
(II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Output: HDMI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: HDMI-0 ----------------------
(II) RADEON(0): Manufacturer: HWP  Model: 26a9  Serial#: 16843009
(II) RADEON(0): Year: 2008  Week: 41
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.646 redY: 0.339   greenX: 0.290 greenY: 0.603
(II) RADEON(0): blueX: 0.145 blueY: 0.065   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x864@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1152  vsize 720  refresh: 60  vid: 113
(II) RADEON(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #4: hsize: 1600  vsize 1000  refresh: 60  vid: 169
(II) RADEON(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) RADEON(0): Ranges: V min: 48 V max: 76 Hz, H min: 24 H max: 83 kHz, PixClock max 160 MHz
(II) RADEON(0): Monitor name: HP w2207
(II) RADEON(0): Serial No: 3CQ8410CLR
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff0022f0a92601010101
(II) RADEON(0):     29120103802f1e78eeb535a5564a9a25
(II) RADEON(0):     105054a56b807100814081809500a900
(II) RADEON(0):     b3000101010121399030621a274068b0
(II) RADEON(0):     3600d9281100001c000000fd00304c18
(II) RADEON(0):     5310000a202020202020000000fc0048
(II) RADEON(0):     502077323230370a20202020000000ff
(II) RADEON(0):     0033435138343130434c520a202001df
(II) RADEON(0):     02031bf1230907074884020107161110
(II) RADEON(0):     1f8301000065030c0010008c0ad08a20
(II) RADEON(0):     e02d10103e9600d928110000188c0ad0
(II) RADEON(0):     90204031200c405500d9281100001801
(II) RADEON(0):     1d8018711c1620582c2500d928110000
(II) RADEON(0):     9e011d00bc52d01e20b8285540d92811
(II) RADEON(0):     00001e011d80d0721c1620102c2580d9
(II) RADEON(0):     281100009e0000000000000000000060
(II) RADEON(0): EDID vendor "HWP", prod id 9897
Dac detection success
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Unhandled monitor type 0
Dac detection success
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "HWP", prod id 9897
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1152x720"x60.0   67.32  1152 1208 1328 1504  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) RADEON(0): Modeline "1600x1000"x60.0  133.14  1600 1704 1872 2144  1000 1001 1004 1035 -hsync +vsync (62.1 kHz)
(II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Output: HDMI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: HDMI-0 ----------------------
(II) RADEON(0): Manufacturer: HWP  Model: 26a9  Serial#: 16843009
(II) RADEON(0): Year: 2008  Week: 41
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.646 redY: 0.339   greenX: 0.290 greenY: 0.603
(II) RADEON(0): blueX: 0.145 blueY: 0.065   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x864@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1152  vsize 720  refresh: 60  vid: 113
(II) RADEON(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #4: hsize: 1600  vsize 1000  refresh: 60  vid: 169
(II) RADEON(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) RADEON(0): Ranges: V min: 48 V max: 76 Hz, H min: 24 H max: 83 kHz, PixClock max 160 MHz
(II) RADEON(0): Monitor name: HP w2207
(II) RADEON(0): Serial No: 3CQ8410CLR
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff0022f0a92601010101
(II) RADEON(0):     29120103802f1e78eeb535a5564a9a25
(II) RADEON(0):     105054a56b807100814081809500a900
(II) RADEON(0):     b3000101010121399030621a274068b0
(II) RADEON(0):     3600d9281100001c000000fd00304c18
(II) RADEON(0):     5310000a202020202020000000fc0048
(II) RADEON(0):     502077323230370a20202020000000ff
(II) RADEON(0):     0033435138343130434c520a202001df
(II) RADEON(0):     02031bf1230907074884020107161110
(II) RADEON(0):     1f8301000065030c0010008c0ad08a20
(II) RADEON(0):     e02d10103e9600d928110000188c0ad0
(II) RADEON(0):     90204031200c405500d9281100001801
(II) RADEON(0):     1d8018711c1620582c2500d928110000
(II) RADEON(0):     9e011d00bc52d01e20b8285540d92811
(II) RADEON(0):     00001e011d80d0721c1620102c2580d9
(II) RADEON(0):     281100009e0000000000000000000060
(II) RADEON(0): EDID vendor "HWP", prod id 9897
Dac detection success
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Unhandled monitor type 0
Dac detection success
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "HWP", prod id 9897
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1152x720"x60.0   67.32  1152 1208 1328 1504  720 721 724 746 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) RADEON(0): Modeline "1600x1000"x60.0  133.14  1600 1704 1872 2144  1000 1001 1004 1035 -hsync +vsync (62.1 kHz)
(II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Output: HDMI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: HDMI-0 ----------------------
(II) RADEON(0): Manufacturer: HWP  Model: 26a9  Serial#: 16843009
(II) RADEON(0): Year: 2008  Week: 41
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.646 redY: 0.339   greenX: 0.290 greenY: 0.603
(II) RADEON(0): blueX: 0.145 blueY: 0.065   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x864@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1152  vsize 720  refresh: 60  vid: 113
(II) RADEON(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #4: hsize: 1600  vsize 1000  refresh: 60  vid: 169
(II) RADEON(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
(II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) RADEON(0): Ranges: V min: 48 V max: 76 Hz, H min: 24 H max: 83 kHz, PixClock max 160 MHz
(II) RADEON(0): Monitor name: HP w2207
(II) RADEON(0): Serial No: 3CQ8410CLR
(II) RADEON(0): Number of EDID sections to follow: 1
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff0022f0a92601010101
(II) RADEON(0):     29120103802f1e78eeb535a5564a9a25
(II) RADEON(0):     105054a56b807100814081809500a900
(II) RADEON(0):     b3000101010121399030621a274068b0
(II) RADEON(0):     3600d9281100001c000000fd00304c18
(II) RADEON(0):     5310000a202020202020000000fc0048
(II) RADEON(0):     502077323230370a20202020000000ff
(II) RADEON(0):     0033435138343130434c520a202001df
(II) RADEON(0):     02031bf1230907074884020107161110
(II) RADEON(0):     1f8301000065030c0010008c0ad08a20
(II) RADEON(0):     e02d10103e9600d928110000188c0ad0
(II) RADEON(0):     90204031200c405500d9281100001801
(II) RADEON(0):     1d8018711c1620582c2500d928110000
(II) RADEON(0):     9e011d00bc52d01e20b8285540d92811
(II) RADEON(0):     00001e011d80d0721c1620102c2580d9
(II) RADEON(0):     281100009e0000000000000000000060
(II) RADEON(0): EDID vendor "HWP", prod id 9897
Dac detection success
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
Unhandled monitor type 0
rick@rick-U:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
02:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3600 Series
02:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]
04:00.0 Network controller: RaLink RT2860
rick@rick-U:~$
rick@rick-U:~$ lspci | grep 'VGA'
02:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3600 Series

---

### Post by Catharsis on 2010-05-09
To make the changes permanent:
```
gksudo gedit /etc/default/grub
```
Change
```
GRUB_CMDLINE_LINUX=""
```
to
```
GRUB_CMDLINE_LINUX="nomodeset"
```
Save and exit, and then run
```
sudo update-grub
```

---

### Post by ubu newb on 2010-05-09
Thanks Catharsis, that worked.    One other little "annoyance".   When  ever I log onto Ubuntu the "can't log out of power management" pop up  shows up right after I enter my password.  I then choose either lock  screen or log out and it gets me in.

This happened no matter  which kernel I booted into to.

---

