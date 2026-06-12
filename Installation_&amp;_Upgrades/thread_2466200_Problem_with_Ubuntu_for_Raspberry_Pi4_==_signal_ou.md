---
title: "Problem with Ubuntu for Raspberry Pi4 == signal out of range"
date: 2021-08-22
forum: Installation &amp; Upgrades
---

### Post by waffen on 2021-08-22
Hello,

Sorry if this is not the correct thread for this post.

My Hardware:
Raspberry Pi 4 - 4GB RAM
LG Monitor (Model #19M38A) with only VGA port with Max res 1366*768
VGA to HDMI Cable converter
HDMI to Micro HDMI official cable converter.

Raspbian OS-> With that setup I can use that monitor with no issues, just a few changes in the config.txt for the resolution.
Ubuntu 21.04 -> Monitor show me "signal out of range" just since the beginning. I try with Manjaro and the same issue.

If I use a new HDMI monitor no issues using HDMI or VGA ports, so the issue is only for that monitor, what can I do?

Thanks!

Mario

---

### Post by TheFu on 2021-08-22
Seems the VGA to HDMI converter is likely the issue.

Can ssh into the pi and set the output to be a standard VGA resolution with xrandr?
It has to be a text interface, not GUI because the GUI would get information from the local machine, not the Pi.

---

### Post by waffen on 2021-08-23
> **TheFu said:**
> Seems the VGA to HDMI converter is likely the issue.

Can ssh into the pi and set the output to be a standard VGA resolution with xrandr?
It has to be a text interface, not GUI because the GUI would get information from the local machine, not the Pi.

I don't think the cable is the issue, I'm using the same cable with other new monitor with no issues or am I wrong?

I'll try you xrandr advise and post here later the results, thanks

---

### Post by waffen on 2021-08-23
> **TheFu said:**
> Seems the VGA to HDMI converter is likely the issue.

Can ssh into the pi and set the output to be a standard VGA resolution with xrandr?
It has to be a text interface, not GUI because the GUI would get information from the local machine, not the Pi.

I just try the xrandr but no lucky, any idea?

```
mario@mario-pi4ubu:~$ sudo cvt 1280 720 60
# 1280x720 59.86 Hz (CVT 0.92M9) hsync: 44.77 kHz; pclk: 74.50 MHz
Modeline "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
mario@mario-pi4ubu:~$ sudo xrandr --newmode "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
Can't open display 

```

---

### Post by TheFu on 2021-08-23
```
DISPLAY=:0 xrandr --newmode "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
```

---

### Post by waffen on 2021-08-23
> **TheFu said:**
> ```
DISPLAY=:0 xrandr --newmode "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
```

I'm using remote SSH access to the Rpi machine:

```
mario@mario-pi4ubu:~$ DISPLAY=:0 xrandr --newmode "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
Can't open display :0
mario@mario-pi4ubu:~$ sudo DISPLAY=:0 xrandr --newmode "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
[sudo] password for mario: 
Can't open display :0

```

---

### Post by TheFu on 2021-08-23
Can't open display :0 means that X/Windows isn't running. Check that.  And probably want to start with 800x600 resolution.  Even a framebuffer driver should work.

After the mode is setup, then changing the output for an enumerated device is something lie this:
```
xrandr  --output [COLOR="#FF0000"]VGA-1[/COLOR] --mode  1920x1200
xrandr  --output [COLOR="#FF0000"]HDMI-1[/COLOR] --mode  1920x1080
```

My powered on r-pi isn't running X/Windows now. It is a Kodi machine using a specialized distro just for that hardware, so I can't check the commands. I'd guess that a v4 r-pi would have HDMI-1 and HDMI-2 as output devices, but I don't know.

---

### Post by waffen on 2021-08-23
> **TheFu said:**
> Can't open display :0 means that X/Windows isn't running. Check that.  And probably want to start with 800x600 resolution.  Even a framebuffer driver should work.

After the mode is setup, then changing the output for an enumerated device is something lie this:
```
xrandr  --output [COLOR="#FF0000"]VGA-1[/COLOR] --mode  1920x1200
xrandr  --output [COLOR="#FF0000"]HDMI-1[/COLOR] --mode  1920x1080
```

My powered on r-pi isn't running X/Windows now. It is a Kodi machine using a specialized distro just for that hardware, so I can't check the commands. I'd guess that a v4 r-pi would have HDMI-1 and HDMI-2 as output devices, but I don't know.

Ok I'll check it.

If I change MicroSD to Raspbian or Kodi works fine with the same cables and monitor, the problem is only with Ubuntu 21

---

### Post by TheFu on 2021-08-23
> **waffen said:**
> Ok I'll check it.

If I change MicroSD to Raspbian or Kodi works fine with the same cables and monitor, the problem is only with Ubuntu 21

Wayland or X/Windows?

---

### Post by waffen on 2021-08-23
> **TheFu said:**
> Wayland or X/Windows?

This is crazy, I have the micro hdmi connected to the Port 1 in the Rpi (the closest to the ac/dc port) all the time, so just for test I turn on the system and change cable to micro hdmi port #2 and voila! works perfect with Ubuntu use the correct 1366*768 resolution... all fine. After update OS I restart the system and again black screen and signal out of range message again.

X11 I can see in the Ubuntu Config screen.

So what's happening?

---

### Post by TheFu on 2021-08-23
My only wild guess would be some DRM stuff doesn't like the monitor.  21.04 added some DRM libraries.  But I really don't know.  Does the X.0.log file have anything inside it?  Any logs from the prior boots with issues?  Use journalctl to see the prior boots.

---

### Post by MAFoElffen on 2021-08-23
My first question to you, is what port are you using? HDMI1 with a HDMI to VGA converter? If, so then...

It might be overwhelming to look at my whole /boot/firmware/usercfg.txt file here... This is my own version of that file. This file is an include from config.txt
```

# Place "config.txt" changes (dtparam, dtoverlay, disable_overscan, etc.) in
# this file. Please refer to the README file for a description of the various
# configuration files on the boot partition.
## Custom Slot is hdmi_grpoup=1 & hdmi_mode=65
### For this define, it uses mode 87, which is 1 above the defined modes...
#### Custom mode define ####
# hdmi_cvt=<width> <height> <framerate> <aspect> <margins> <interlace> <rb>
# width        width in pixels
# height       height in pixels
# framerate    framerate in Hz
# aspect       aspect ratio 1=4:3, 2=14:9, 3=16:9, 4=5:4, 5=16:10, 6=15:9
# margins      0=margins disabled, 1=margins enabled
# interlace    0=progressive, 1=interlaced
# rb           0=normal, 1=reduced blanking
###
#hdmi_cvt=1920 1080 60 3 0 0 0    # Custom mode definition
#hdmi_group=2
#hdmi_mode=87    #1 mode above defines in AEC
### Normal Mode Sets
hdmi_group=2    # 0:Autodetect EDID, 1:AEC, 2:DMT
hdmi_mode=82    # 1920x1080 60Hz
### For sound through HDMI ###
#hdmi_drive=2    # hdmi with sound
###########################################################
## If all above is commented, this displays as 1824x984 9:5
###########################################################
### If hdmi_group=1 AEC, then these
###########################################################
## Set to 640x480 60hz 4:3 VGA
#hdmi_mode=1
## Set to 480p 60hz 4:3
#hdmi_mode=2
## Set to 480p 60hz 16:9
#hdmi_mode=3
## Set to 720p 60hz 16:9
#hdmi_mode=4
## Set to 1080i 60hz 16:9
#hdmi_mode=5
## Set to 480i 60hz 4:3
#hdmi_mode=6
## Set to 480i 60hz 16:9
#hdmi_mode=7
## Set to 240p 60hz 4:3
#hdmi_mode=8
## Set to 240p 60hz 16:9
#hdmi_mode=9
## Set to 480i 60hz 4:3
#hdmi_mode=10
## Set to 480i 60hz 16:9
#hdmi_mode=11
## Set to 240p 60hz 4:3
#hdmi_mode=12
## Set to 240p 60hz 16:9
#hdmi_mode=13
## Set to 480p 60hz 4:3
#hdmi_mode=14
## Set to 480p 60hz 16:9
#hdmi_mode=15
## Set to 480p 60Hz 16:9
#hdmi_mode=16
## Set to 576p 50Hz 4:3     
#hdmi_mode=17
## Set to 576p 50Hz 16:9
#hdmi_mode=18
## Set to 720p 50hz 16:9
#hdmi_mode=19
## Set to 1080i 50hz 16:9
#hdmi_mode=20
## Set to 576i 50hz 4:3
#hdmi_mode=21
## Set to 576i 50hz 16:9
#hdmi_mode=22
## Set to 288p 50 hz 4:3
#hdmi_mode=23
## Set to 288p 50hz 16:9
#hdmi_mode=24
## Set to 576i 50hz 4:3
#hdmi_mode=25
## Set to 576i 50hz 16:9
#hdmi_mode=26
## Set to  288p 50Hz 4:3
#hdmi_mode=27
## Set to 288p 50Hz 16:9
#hdmi_mode=28
## Set to 576p 50Hz 4:3
#hdmi_mode=29
## Set to 576p 50Hz 16:9
#hdmi_mode=30
## Set to 1080p 50Hz 16:9
#hdmi_mode=31
## Set to 1080p 24Hz 16:9
#hdmi_mode=32
## Set to 1080p 25Hz 16:9
#hdmi_mode=33
## Set to 1080p 30Hz 16:9
#hdmi_mode=34
## Set to 480p 60Hz 4:3
#hdmi_mode=35
## Set to 480p 60Hz 16:9
#hdmi_mode=36
## Set to 576p 50Hz 4:3
#hdmi_mode=37
## Set to 576p 50Hz 16:9
#hdmi_mode=38
## Set to 1080i 50Hz 16:9
#hdmi_mode=39
## Set to 1080i 100Hz 16:9
#hdmi_mode=40
## Set to 720p 100Hz 16:9
#hdmi_mode=41
## Set to 576p 100Hz 4:3
#hdmi_mode=42
## Set to 576p 100Hz 16:9
#hdmi_mode=43    
## Set to 576i 100Hz 4:3
#hdmi_mode=44
## Set to 576i 100hz 16:9
#hdmi_mode=45
## Set to 1080i 120Hz 16:9
#hdmi_mode=46
## Set to 720p 120Hz 16:9
#hdmi_mode=47
## Set to 480p 120Hz 4:3     
#hdmi_mode=48
## Set to 480p 120Hz 16:9     
#hdmi_mode=49
## Set to 480i 120Hz 4:3     
#hdmi_mode=50
## Set to      480i     120Hz     16:9     
#hdmi_mode=51
## Set to      576p     200Hz     4:3     
#hdmi_mode=52
## Set to      576p     200Hz     16:9     
#hdmi_mode=53
## Set to      576i     200Hz     4:3     
#hdmi_mode=54
## Set to      576i     200Hz     16:9     
#hdmi_mode=55
## Set to      480p     240Hz     4:3     
#hdmi_mode=56
## Set to      480p     240Hz     16:9     
#hdmi_mode=57
## Set to      480i     240Hz     4:3     
#hdmi_mode=58
## Set to      480i     240Hz     16:9     
#hdmi_mode=59
## Set to      720p     24Hz     16:9     
#hdmi_mode=60
## Set to      720p     25Hz     16:9     
#hdmi_mode=61
## Set to      720p     30Hz     16:9     
#hdmi_mode=62
## Set to      1080p     120Hz     16:9     
#hdmi_mode=63
## Set to      1080p     100Hz     16:9     
#hdmi_mode=64
## Set to      Custom 
#hdmi_mode=65            
## Set to      720p     25Hz     64:27     Pi 4
#hdmi_mode=66
## Set to      720p     30Hz     64:27     Pi 4
#hdmi_mode=67
## Set to      720p     50Hz     64:27     Pi 4
#hdmi_mode=68
## Set to      720p     60Hz     64:27     Pi 4
#hdmi_mode=69
## Set to      720p     100Hz     64:27     Pi 4
#hdmi_mode=70
## Set to      720p     120Hz     64:27     Pi 4
#hdmi_mode=71
## Set to      1080p     24Hz     64:27     Pi 4
#hdmi_mode=72
## Set to      1080p     25Hz     64:27     Pi 4
#hdmi_mode=73
## Set to      1080p     30Hz     64:27     Pi 4
#hdmi_mode=74
## Set to     1080p     50Hz     64:27     Pi 4
#hdmi_mode=75
## Set to      1080p     60Hz     64:27     Pi 4
#hdmi_mode=76
## Set to      1080p     100Hz     64:27     Pi 4
#hdmi_mode=77
## Set to      1080p     120Hz     64:27     Pi 4
#hdmi_mode=78
## Set to      1680x720     24Hz     64:27     Pi 4
#hdmi_mode=79
## Set to      1680x720     25z     64:27     Pi 4
#hdmi_mode=80
## Set to      1680x720     30Hz     64:27     Pi 4
#hdmi_mode=81
## Set to      1680x720     50Hz     64:27     Pi 4
#hdmi_mode=82
## Set to      1680x720     60Hz     64:27     Pi 4
#hdmi_mode=83
## Set to      1680x720     100Hz     64:27     Pi 4
#hdmi_mode=84
## Set to      1680x720     120Hz     64:27     Pi 4
#hdmi_mode=85
## Set to      2560x720     24Hz     64:27     Pi 4
#hdmi_mode=86
## Set to      2560x720     25Hz     64:27     Pi 4
#hdmi_mode=87
## Set to      2560x720     30Hz     64:27     Pi 4
#hdmi_mode=88
## Set to      2560x720     50Hz     64:27     Pi 4
#hdmi_mode=89
## Set to      2560x720     60Hz     64:27     Pi 4
#hdmi_mode=90
## Set to      2560x720     100Hz     64:27     Pi 4
#hdmi_mode=91
## Set to      2560x720     120Hz     64:27     Pi 4
#hdmi_mode=92
## Set to      2160p     24Hz     16:9     Pi 4
#hdmi_mode=93
## Set to      2160p     25Hz     16:9     Pi 4
#hdmi_mode=94
## Set to      2160p     30Hz     16:9     Pi 4
#hdmi_mode=95
## Set to      2160p     50Hz     16:9     Pi 4
#hdmi_mode=96
## Set to      2160p     60Hz     16:9     Pi 4
#hdmi_mode=97
## Set to      4096x2160     24Hz     256:135     Pi 4
#hdmi_mode=98
## Set to      4096x2160     25Hz     256:135     Pi 4
#hdmi_mode=99
## Set to      4096x2160     30Hz     256:135     Pi 4
#hdmi_mode=100
## Set to     4096x2160     50Hz     256:135     Pi 4
#hdmi_mode=101 
## Set to      4096x2160     60Hz     256:135     Pi 4
#hdmi_mode=102
## Set to      2160p     24Hz     64:27     Pi 4
#hdmi_mode=103
## Set to      2160p     25Hz     64:27     Pi 4
#hdmi_mode=104
## Set to      2160p     30Hz     64:27     Pi 4
#hdmi_mode=105
## Set to      2160p     50Hz     64:27     Pi 4
#hdmi_mode=106
## Set to      2160p     60Hz     64:27     Pi 4
#hdmi_mode=107
############################################
### If hdmi_group=2, then thse are valid ###
############################################
## Set to      640x350     85Hz     
#hdmi_mode=1    
## Set to      640x400     85Hz     16:10 
#hdmi_mode=2    
## Set to     720x400     85Hz     
#hdmi_mode=3     
## Set to      640x480     60Hz     4:3     
#hdmi_mode=4
## Set to      640x480     72Hz     4:3     
#hdmi_mode=5
## Set to      640x480     75Hz     4:3     
#hdmi_mode=6
## Set to      640x480     85Hz     4:3     
#hdmi_mode=7
## Set to      800x600     56Hz     4:3     
#hdmi_mode=8
## Set to      800x600     60Hz     4:3     
#hdmi_mode=9
## Set to      800x600     72Hz     4:3     
#hdmi_mode=10
## Set to      800x600     75Hz     4:3     
#hdmi_mode=11
## Set to      800x600     85Hz     4:3     
#hdmi_mode=12
## Set to      800x600     120Hz     4:3     
#hdmi_mode=13
## Set to      848x480     60Hz     16:9     
#hdmi_mode=14
## Set to      1024x768     43Hz     4:3     incompatible with the Raspberry Pi
#hdmi_mode=15
## Set to      1024x768     60Hz     4:3     
#hdmi_mode=16
## Set to      1024x768     70Hz     4:3 
#hdmi_mode=17    
## Set to      1024x768     75Hz     4:3     
#hdmi_mode=18
## Set to      1024x768     85Hz     4:3     
#hdmi_mode=19
## Set to      1024x768     120Hz     4:3     
#hdmi_mode=20
## Set to      1152x864     75Hz     4:3     
#hdmi_mode=21
## Set to      1280x768     60Hz     15:9     reduced blanking
#hdmi_mode=22
## Set to      1280x768     60Hz     15:9     
#hdmi_mode=23
## Set to      1280x768     75Hz     15:9     
#hdmi_mode=24
## Set to      1280x768     85Hz     15:9     
#hdmi_mode=25
## Set to      1280x768     120Hz     15:9     reduced blanking
#hdmi_mode=26
## Set to      1280x800     60     16:10     reduced blanking
#hdmi_mode=27
## Set to      1280x800     60Hz     16:10     
#hdmi_mode=28
## Set to      1280x800     75Hz     16:10     
#hdmi_mode=29
## Set to      1280x800     85Hz     16:10     
#hdmi_mode=30
## Set to      1280x800     120Hz     16:10     reduced blanking
#hdmi_mode=31
## Set to      1280x960     60Hz     4:3     
#hdmi_mode=32
## Set to      1280x960     85Hz     4:3     
#hdmi_mode=33
## Set to      1280x960     120Hz     4:3     reduced blanking
#hdmi_mode=34
## Set to      1280x1024     60Hz     5:4     
#hdmi_mode=35
## Set to      1280x1024     75Hz     5:4     
#hdmi_mode=36
## Set to      1280x1024     85Hz     5:4     
#hdmi_mode=37
## Set to      1280x1024     120Hz     5:4     reduced blanking
#hdmi_mode=38
## Set to      1360x768     60Hz     16:9     
#hdmi_mode=39
## Set to     1360x768     120Hz     16:9     reduced blanking
#hdmi_mode=40 
## Set to      1400x1050     60Hz     4:3     reduced blanking
#hdmi_mode=41
## Set to      1400x1050     60Hz     4:3     
#hdmi_mode=42
## Set to      1400x1050     75Hz     4:3     
#hdmi_mode=43
## Set to      1400x1050     85Hz     4:3     
#hdmi_mode=44
## Set to      1400x1050     120Hz     4:3     reduced blanking
#hdmi_mode=45
## Set to      1440x900     60Hz     16:10     reduced blanking
#hdmi_mode=46
## Set to      1440x900     60Hz     16:10     
#hdmi_mode=47
## Set to      1440x900     75Hz     16:10     
#hdmi_mode=48
## Set to      1440x900     85Hz     16:10     
#hdmi_mode=49
## Set to      1440x900     120Hz     16:10     reduced blanking
#hdmi_mode=50
## Set to      1600x1200     60Hz     4:3     
#hdmi_mode=51
## Set to      1600x1200     65Hz     4:3     
#hdmi_mode=52
## Set to      1600x1200     70Hz     4:3     
#hdmi_mode=53
## Set to      1600x1200     75Hz     4:3     
#hdmi_mode=54
## Set to      1600x1200     85Hz     4:3     
#hdmi_mode=55
## Set to      1600x1200     120Hz     4:3     reduced blanking
#hdmi_mode=56
## Set to      1680x1050     60Hz     16:10     reduced blanking
#hdmi_mode=57
## Set to      1680x1050     60Hz     16:10     
#hdmi_mode=58
## Set to      1680x1050     75Hz     16:10     
#hdmi_mode=59
## Set to      1680x1050     85Hz     16:10     
#hdmi_mode=60
## Set to      1680x1050     120Hz     16:10     reduced blanking
#hdmi_mode=61
## Set to      1792x1344     60Hz     4:3     
#hdmi_mode=62
## Set to      1792x1344     75Hz     4:3     
#hdmi_mode=63
## Set to      1792x1344     120Hz     4:3     reduced blanking
#hdmi_mode=64
## Set to      1856x1392     60Hz     4:3     
#hdmi_mode=65
## Set to      1856x1392     75Hz     4:3     
#hdmi_mode=66
## Set to      1856x1392     120Hz     4:3     reduced blanking
#hdmi_mode=67
## Set to      1920x1200     60Hz     16:10     reduced blanking
#hdmi_mode=68
## Set to     1920x1200     60Hz     16:10     
#hdmi_mode=69 
## Set to      1920x1200     75Hz     16:10     
#hdmi_mode=70
## Set to      1920x1200     85Hz     16:10     
#hdmi_mode=71
## Set to      1920x1200     120Hz     16:10     reduced blanking
#hdmi_mode=72
## Set to      1920x1440     60Hz     4:3     
#hdmi_mode=73
## Set to      1920x1440     75Hz     4:3     
#hdmi_mode=74
## Set to      1920x1440     120Hz     4:3     reduced blanking
#hdmi_mode=75
## Set to      2560x1600     60Hz     16:10     reduced blanking
#hdmi_mode=76
## Set to      2560x1600     60Hz     16:10     
#hdmi_mode=77
## Set to      2560x1600     75Hz     16:10     
#hdmi_mode=78
## Set to      2560x1600     85Hz     16:10     
#hdmi_mode=79
## Set to      2560x1600     120Hz     16:10     reduced blanking
#hdmi_mode=80
## Set to      1366x768     60Hz     16:9     NOT on Pi4
#hdmi_mode=81
## Set to      1920x1080     60Hz     16:9     1080p
#hdmi_mode=82
## Set to      1600x900     60Hz     16:9     reduced blanking
#hdmi_mode=83
## Set to      2048x1152     60Hz     16:9     reduced blanking
#hdmi_mode=84
## Set to      1280x720     60Hz     16:9     720p
#hdmi_mode=85
## Set to      1366x768     60Hz     16:9     reduced blanking
#hdmi_mode=86
#############################################################
## HDMI Safe Mode
#hdmi_safe=1


```
Yes, I was bored one day... That is every mode that is standard to Raspberry Pi's, plus you can set custom modes... If they exist in xrandr -q just to see the modes possible from whatever connected display...

But look at the lines 20 through 23 of this file. Those are the lines you should be concerned with. Everything below those lines I have there just for reference... Look below, and find for a resolution your display can work at (mode), in what type of display (group.) Then set the values in line 20-23, of hdmi_group and hdmi_mode to match that resolution. 

Note that VGA does not pass sound, so set hdmi_drive=1...

Notice that I only have 2 lines unclommented at lines 20 and 21. you will uncomment line 23. and change the value to 1... It loads very fast. 

Note that if for some reason, your graphics boinks, power-off and take the MicroSD to another machine with a USB card reader to edit that file there (as text), to try another mode...

Have fun. This file should take care or you forever... For whatever you want to connect to.

---

### Post by waffen on 2021-08-23
In the image attached my setup: VGA cable -> VGA to HDMI converter -> HDMI to micro HDMI converter -> Rpi4 video port

Image from my Nextcloud-> [https://cloud.lacunza.biz/index.php/s/R4kPW9XmjDm6gi3](https://cloud.lacunza.biz/index.php/s/R4kPW9XmjDm6gi3)

I just buy a VGA to MicroHDMI converter to replace the black and white cables, I'll try with that setup tomorrow because the delivery arrives tomorrow morning

The problem with your setup is: Ubuntu don't have that config.txt file, I'll need to search how to do that. So looks like I'll not going to sleep tonight :lolflag:

Thanks a lot for all your help! I'll going to update this post tomorrow.

---

### Post by MAFoElffen on 2021-08-24
> **waffen said:**
> The problem with your setup is: [COLOR=#ff0000]Ubuntu don't have that config.txt file[/COLOR], I'll need to search how to do that. So looks like I'll not going to sleep tonight
LOL. The problem with my setup? My setup works great.. and contrary to what you just said, Ubuntu does have those configuration files... But they are not in the root of the boot directory, like some of the other Raspberry Pi images. They are in a subdirectory of the boot directory in this path: /boot/firmware/... Where I told you they were.

I gave you the full path and filename in my last post. Here is the Raspberry boot configuration files, if you are running Ubuntu:
```

mafoelffen@ubuntu:$ ls */boot/firmware/.txt
cmdline.txt  config.txt  syscfg.txt  usercfg.txt

```
And the top lines of the /boot/firmware/config.txt file says:
```
# Please DO NOT modify this file; [COLOR=#ff0000]if you need to modify the boot config, the
# "usercfg.txt" file is the place to include user changes.[/COLOR] Please refer to
# the README file for a description of the various configuration files on
# the boot partition.

```
The last two lines of the config.txt file are includes to syscfg.txt and usercfg.txt...

And this is what I am posting from:
```
mafoelffen@ubuntu:$ inxi -c
CPU: Quad Core Model N/A (-MCP-) speed/min/max: 1000/600/1500 MHz 
Kernel: 5.4.0-1042-raspi aarch64 Up: 1d 4h 04m 
Mem: 1961.3/7811.3 MiB (25.1%) Storage: 116.48 GiB (34.8% used) Procs: 232 
Shell: bash 5.0.17 inxi: 3.0.38 

mafoelffen@ubuntu:$ lsb_release -sd
Ubuntu 20.04.3 LTS

```
And yes, this is configured for 1920x1080 60hz.

---

### Post by waffen on 2021-08-24
> **MAFoElffen said:**
> LOL. The problem with my setup? My setup works great.. and contrary to what you just said, Ubuntu does have those configuration files... But they are not in the root of the boot directory, like some of the other Raspberry Pi images. They are in a subdirectory of the boot directory in this path: /boot/firmware/... Where I told you they were.

I gave you the full path and filename in my last post. Here is the Raspberry boot configuration files, if you are running Ubuntu:


That was sarcasm :o sorry.

And not, "normal" Ubuntu don't have that folder, I'm using Ubuntu 20.04 in my PC and don't have that path, I just checked with a card reader the 21.04 for Rpi and it have  /boot/firmware/, for that reason my confusion. So is that new in 21.04 or only for the Rpi version?

I'll work with the Rpi later today and I'll going to update this post, thanks!!

---

### Post by waffen on 2021-08-24
Just arrive the new VGA to MicroHDMI adapter.. that's not the problem, still the same not signal message.

Now in my /boot/firmware folder I can found only 2 files: cmdline.txt  config.txt

So I just added the usercfg.txt file with this code:

```
hdmi_group=2
hdmi_mode=86
hdmi_cvt=1366 768 60 3 0 0 1
hdmi_drive=1
dtoverlay=gpio-fan,gpiopin=18,temp=55000

```

The last line is for control a fan.

> The last two lines of the config.txt file are includes to syscfg.txt and usercfg.txt...
I can't see that lines, can you copy & paste that ones? 

Just restart the Rpi4 and still the same error... maybe am I missing the include lines?

---

### Post by waffen on 2021-08-24
I just found the way to add the:
```
include usercfg.txt
```

Now I start the Rpi, I can see the first screen with the colors(I never saw it before) , after that some starting text screens from Ubuntu and again signal our of range message....

This is my config.txt

```
[pi4]
max_framebuffers=2

[all]
kernel=vmlinuz
cmdline=cmdline.txt
initramfs initrd.img followkernel

# Enable the audio output, I2C and SPI interfaces on the GPIO header
dtparam=audio=on
dtparam=i2c_arm=on
dtparam=spi=on

# Enable the KMS ("full" KMS) graphics overlay, and allocate 128Mb to the GPU
# memory. The full KMS overlay is required for X11 application support under
# wayland
dtoverlay=vc4-kms-v3d
gpu_mem=128

# Uncomment the following to enable the Raspberry Pi camera module firmware.
# Be warned that there *may* be incompatibilities with the "full" KMS overlay
#start_x=1

# Comment out the following line if the edges of the desktop appear outside
# the edges of your display
disable_overscan=1

# If you have issues with audio, you may try uncommenting the following line
# which forces the HDMI output into HDMI mode instead of DVI (which doesn't
# support audio output)
#hdmi_drive=2

# If you have a CM4, uncomment the following line to enable the USB2 outputs
# on the IO board (assuming your CM4 is plugged into such a board)
#dtoverlay=dwc2,dr_mode=host

# Config settings specific to arm64
arm_64bit=1
dtoverlay=dwc2
include usercfg.txt
```

---

### Post by waffen on 2021-08-24
Full copy of  /var/log/Xorg.0.log

```
[   126.923]
X.Org X Server 1.20.11
X Protocol Version 11, Revision 0
[   126.923] Build Operating System: linux Ubuntu
[   126.923] Current Operating System: Linux mario-pi4ubu 5.11.0-1016-raspi #17-Ubuntu SMP PREEMPT Thu Jul 29 15:33:06 UTC 2021 aarch64
[   126.924] Kernel command line: coherent_pool=1M 8250.nr_uarts=0 snd_bcm2835.enable_compat_alsa=0 snd_bcm2835.enable_hdmi=1 video=HDMI-A-1:640x480M@60,margin_left=24,margin_>
[   126.924] Build Date: 06 July 2021  10:17:51AM
[   126.924] xorg-server 2:1.20.11-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support)
[   126.924] Current version of pixman: 0.40.0
[   126.924]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[   126.925] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   126.926] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 24 14:55:40 2021
[   126.928] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   126.931] (==) No Layout section.  Using the first Screen section.
[   126.931] (==) No screen section available. Using defaults.
[   126.931] (**) |-->Screen "Default Screen Section" (0)
[   126.931] (**) |   |-->Monitor "<default monitor>"
[   126.935] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[   126.935] (==) Automatically adding devices
[   126.935] (==) Automatically enabling devices
[   126.935] (==) Automatically adding GPU devices
[   126.935] (==) Automatically binding GPU devices
[   126.936] (==) Max clients allowed: 256, resource mask: 0x1fffff
[   126.936] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   126.936]    Entry deleted from font path.
[   126.936] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   126.936]    Entry deleted from font path.
[   126.936] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   126.936]    Entry deleted from font path.
[   126.936] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   126.936]    Entry deleted from font path.
[   126.936] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   126.936]    Entry deleted from font path.
[   126.936] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[   126.936] (==) ModulePath set to "/usr/lib/xorg/modules"
[   126.936] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[   126.936] (II) Loader magic: 0xaaaaea14e010
[   126.936] (II) Module ABI versions:
[   126.937]    X.Org ANSI C Emulation: 0.4
[   126.937]    X.Org Video Driver: 24.1
[   126.937]    X.Org XInput driver : 24.1
[   126.937]    X.Org Server Extension : 10.0
[   126.939] (--) using VT number 2

[   126.939] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[   126.946] (II) xfree86: Adding drm device (/dev/dri/card1)
[   126.946] (EE) /dev/dri/card1: failed to set DRM interface version 1.4: Permission denied
[   126.948] (II) xfree86: Adding drm device (/dev/dri/card0)
[   126.950] (II) no primary bus or device found
[   126.950]    falling back to /sys/devices/platform/v3dbus/fec00000.v3d/drm/card0
[   126.950] (II) LoadModule: "glx"
[   126.955] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   126.967] (II) Module glx: vendor="X.Org Foundation"
[   126.967]    compiled for 1.20.11, module version = 1.0.0
[   126.967]    ABI class: X.Org Server Extension, version 10.0
[   126.967] (==) Matched modesetting as autoconfigured driver 0
[   126.968] (==) Matched fbdev as autoconfigured driver 1
[   126.968] (==) Assigned the driver to the xf86ConfigLayout
[   126.968] (II) LoadModule: "modesetting"
[   126.974] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   126.979] (II) Module modesetting: vendor="X.Org Foundation"
[   126.979]    compiled for 1.20.11, module version = 1.20.11
[   126.979]    Module class: X.Org Video Driver
[   126.979]    ABI class: X.Org Video Driver, version 24.1
[   126.979] (II) LoadModule: "fbdev"
[   126.980] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   126.982] (II) Module fbdev: vendor="X.Org Foundation"
[   126.982]    compiled for 1.20.10, module version = 0.5.0
[   126.982]    Module class: X.Org Video Driver
[   126.982]    ABI class: X.Org Video Driver, version 24.1
[   126.983] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   126.983] (II) FBDEV: driver for framebuffer: fbdev
[   127.074] (WW) Falling back to old probe method for modesetting
[   127.074] (WW) Falling back to old probe method for fbdev
[   127.075] (II) Loading sub module "fbdevhw"
[   127.075] (II) LoadModule: "fbdevhw"
[   127.076] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   127.081] (II) Module fbdevhw: vendor="X.Org Foundation"
[   127.081]    compiled for 1.20.11, module version = 0.0.2
[   127.081]    ABI class: X.Org Video Driver, version 24.1
[   127.081] (II) FBDEV(0): using default device
[   127.081] (WW) VGA arbiter: cannot open kernel arbiter, no multi-card support
[   127.082] (II) FBDEV(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 16/16
[   127.082] (==) FBDEV(0): Depth 16, (==) framebuffer bpp 16
[   127.082] (==) FBDEV(0): RGB weight 565
[   127.082] (==) FBDEV(0): Default visual is TrueColor
[   127.082] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[   127.082] (II) FBDEV(0): hardware: vc4drmfb (video memory: 600kB)
[   127.082] (DB) xf86MergeOutputClassOptions unsupported bus type 0
[   127.082] (II) FBDEV(0): checking modes against framebuffer device...
[   127.082] (II) FBDEV(0): checking modes against monitor...
[   127.082] (II) FBDEV(0): Virtual size is 640x480 (pitch 640)
[   127.082] (**) FBDEV(0):  Built-in mode "current"
[   127.082] (==) FBDEV(0): DPI set to (96, 96)
[   127.082] (II) Loading sub module "fb"
[   127.082] (II) LoadModule: "fb"
[   127.088] (II) Loading /usr/lib/xorg/modules/libfb.so
[   127.092] (II) Module fb: vendor="X.Org Foundation"
[   127.092]    compiled for 1.20.11, module version = 1.0.0
[   127.092]    ABI class: X.Org ANSI C Emulation, version 0.4
[   127.092] (**) FBDEV(0): using shadow framebuffer
[   127.092] (II) Loading sub module "shadow"
[   127.092] (II) LoadModule: "shadow"
[   127.093] (II) Loading /usr/lib/xorg/modules/libshadow.so
[   127.095] (II) Module shadow: vendor="X.Org Foundation"
[   127.095]    compiled for 1.20.11, module version = 1.1.0
[   127.095]    ABI class: X.Org ANSI C Emulation, version 0.4
[   127.149] (==) FBDEV(0): Backing store enabled
[   127.152] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[   127.152] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[   127.152] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[   127.152] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[   127.155] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[   127.155] (==) FBDEV(0): DPMS enabled
[   127.156] (II) Initializing extension Generic Event Extension
[   127.156] (II) Initializing extension SHAPE
[   127.157] (II) Initializing extension MIT-SHM
[   127.157] (II) Initializing extension XInputExtension
[   127.159] (II) Initializing extension XTEST
[   127.160] (II) Initializing extension BIG-REQUESTS
[   127.160] (II) Initializing extension SYNC
[   127.161] (II) Initializing extension XKEYBOARD
[   127.161] (II) Initializing extension XC-MISC
[   127.161] (II) Initializing extension SECURITY
[   127.162] (II) Initializing extension XFIXES
[   127.162] (II) Initializing extension RENDER
[   127.162] (II) Initializing extension RANDR
[   127.163] (II) Initializing extension COMPOSITE
[   127.164] (II) Initializing extension DAMAGE
[   127.165] (II) Initializing extension MIT-SCREEN-SAVER
[   127.165] (II) Initializing extension DOUBLE-BUFFER
[   127.165] (II) Initializing extension RECORD
[   127.166] (II) Initializing extension DPMS
[   127.166] (II) Initializing extension Present
[   127.167] (II) Initializing extension DRI3
[   127.167] (II) Initializing extension X-Resource
[   127.167] (II) Initializing extension XVideo
[   127.167] (II) Initializing extension XVideo-MotionCompensation
[   127.168] (II) Initializing extension SELinux
[   127.168] (II) SELinux: Disabled on system
[   127.168] (II) Initializing extension GLX
[   127.168] (II) AIGLX: Screen 0 is not DRI2 capable
[   127.286] (II) IGLX: Loaded and initialized swrast
[   127.287] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[   127.287] (II) Initializing extension XFree86-VidModeExtension
[   127.287] (II) Initializing extension XFree86-DGA
[   127.287] (II) Initializing extension XFree86-DRI
[   127.291] (II) Initializing extension DRI2
[   127.681] (II) config/udev: Adding drm device (/dev/dri/card1)
[   127.681] (II) xfree86: Adding drm device (/dev/dri/card1)
[   127.681] (II) LoadModule: "modesetting"
[   127.682] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   127.682] (II) Module modesetting: vendor="X.Org Foundation"
[   127.682]    compiled for 1.20.11, module version = 1.20.11
[   127.682]    Module class: X.Org Video Driver
[   127.682]    ABI class: X.Org Video Driver, version 24.1
[   127.682] (II) UnloadModule: "modesetting"
[   127.682] (II) Unloading modesetting
[   127.682] (II) Failed to load module "modesetting" (already loaded, 0)
[   127.683] (II) modeset(G0): using drv /dev/dri/card1
[   127.683] (II) modeset(G0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[   127.683] (==) modeset(G0): Depth 24, (==) framebuffer bpp 32
[   127.683] (==) modeset(G0): RGB weight 888
[   127.683] (==) modeset(G0): Default visual is TrueColor
[   127.683] (II) Loading sub module "glamoregl"
[   127.683] (II) LoadModule: "glamoregl"
[   127.684] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[   127.706] (II) Module glamoregl: vendor="X.Org Foundation"
[   127.706]    compiled for 1.20.11, module version = 1.0.1
[   127.706]    ABI class: X.Org ANSI C Emulation, version 0.4
[   128.193] (II) modeset(G0): glamor X acceleration enabled on V3D 4.2
[   128.193] (II) modeset(G0): glamor initialized
[   128.220] (II) modeset(G0): Output HDMI-1-1 has no monitor section
[   128.221] (II) modeset(G0): Output HDMI-1-2 has no monitor section
[   128.248] (--) modeset(G0): HDMI max TMDS frequency 225000KHz
[   128.249] (==) modeset(G0): Using gamma correction (1.0, 1.0, 1.0)
[   128.249] (==) modeset(G0): DPI set to (96, 96)
[   128.249] (II) Loading sub module "fb"
[   128.249] (II) LoadModule: "fb"
[   128.250] (II) Loading /usr/lib/xorg/modules/libfb.so
[   128.250] (II) Module fb: vendor="X.Org Foundation"
[   128.250]    compiled for 1.20.11, module version = 1.0.0
[   128.250]    ABI class: X.Org ANSI C Emulation, version 0.4
[   128.254] (EE)
[   128.254] (EE) Backtrace:
[   128.261] (EE) 0: /usr/lib/xorg/Xorg (OsLookupColor+0x188) [0xaaaaea0ad4c8]
[   128.261] (EE) unw_get_proc_info failed: no unwind info found [-10]
[   128.262] (EE)
[   128.262] (EE)
Fatal server error:
[   128.262] (EE) Caught signal 6 (Aborted). Server aborting
[   128.262] (EE)
[   128.262] (EE)
Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.
[   128.263] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   128.263] (EE)
[   128.268] (EE) Server terminated with error (1). Closing log file.

```

---

### Post by MAFoElffen on 2021-08-24
> **waffen said:**
> 
My Hardware:
Raspberry Pi 4 - 4GB RAM
LG Monitor ([COLOR=#ff0000]Model #19M38A[/COLOR]) with only VGA port with Max res 1366*768
VGA to HDMI Cable converter
HDMI to Micro HDMI official cable converter.
Native is 1368x768...

Comment out what you did...

Use these lines, under this section:
```

### Normal Mode Sets
hdmi_group=2     # 0:Autodetect EDID, 1:AEC, 2:DMT
hdmi_mode=86     # 1366x768, 60Hz,16:9, reduced blanking
### For sound through HDMI ###
hdmi_drive=1     # hdmi without sound

```
That mode is native to both your Pi4 and to that LG Monitor (at least from the monitor's manual)...

And yes... I am also a Dev who has supported the Linux Graphics Layer for over 15 years now, so I sort of remember that I  added that file and those includes on my own, but did that based on what the Raspberry Pi standard is and tried to conform to what they say it should be... but adapted it how Ubuntu does it (for paths). It wasn't standard from the media I installed from, because I started out with the Ubuntu Server Edition Image for Pi... Which of course doesn't start out having a Graphics Layer, as default.

---

### Post by waffen on 2021-08-24
Yes I'm using that 3 lines and nothing...

---

### Post by MAFoElffen on 2021-08-24
I'm looking at your config.txt and comparing it to mine... near the bottom of your config.txt, you have 
```
dtoverlay=dwc2

```
Which is for the Compute Module 4 I/O option board... Do you have that option board and is it plugged in? If so, that command is incomplete... so is probably not working. If not plugged in, then it is probably throwing an error.

Please post the result of these: (or search for these strings in your /var/log/Xorg.0.log file)
```

egrep "FBDEV(0): Virtual size is" /var/log/Xorg.0.log
egrep "modeset(G0):" /var/log/Xorg.0.log

```

---

### Post by waffen on 2021-08-24
I don't touch that file before. And the only extra I have is an internal fan.

I posted the entire log file in a previous message, did you see it? 

Just in case here are the results:

```
[   127.081] (II) FBDEV(0): using default device
[   127.081] (WW) VGA arbiter: cannot open kernel arbiter, no multi-card support
[   127.082] (II) FBDEV(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 16/16
[   127.082] (==) FBDEV(0): Depth 16, (==) framebuffer bpp 16
[   127.082] (==) FBDEV(0): RGB weight 565
[   127.082] (==) FBDEV(0): Default visual is TrueColor
[   127.082] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[   127.082] (II) FBDEV(0): hardware: vc4drmfb (video memory: 600kB)
[   127.082] (DB) xf86MergeOutputClassOptions unsupported bus type 0
[   127.082] (II) FBDEV(0): checking modes against framebuffer device...
[   127.082] (II) FBDEV(0): checking modes against monitor...
[   127.082] (II) FBDEV(0): Virtual size is 640x480 (pitch 640)
[   127.082] (**) FBDEV(0):  Built-in mode "current"
[   127.082] (==) FBDEV(0): DPI set to (96, 96)
[   127.082] (II) Loading sub module "fb"
[   127.082] (II) LoadModule: "fb"
[   127.088] (II) Loading /usr/lib/xorg/modules/libfb.so
[   127.092] (II) Module fb: vendor="X.Org Foundation"
[   127.092]    compiled for 1.20.11, module version = 1.0.0
[   127.092]    ABI class: X.Org ANSI C Emulation, version 0.4
[   127.092] (**) FBDEV(0): using shadow framebuffer
[   127.092] (II) Loading sub module "shadow"
[   127.092] (II) LoadModule: "shadow"
[   127.093] (II) Loading /usr/lib/xorg/modules/libshadow.so
[   127.095] (II) Module shadow: vendor="X.Org Foundation"
[   127.095]    compiled for 1.20.11, module version = 1.1.0
[   127.095]    ABI class: X.Org ANSI C Emulation, version 0.4
[   127.149] (==) FBDEV(0): Backing store enabled
[   127.152] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[   127.152] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[   127.152] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[   127.152] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[   127.155] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[   127.155] (==) FBDEV(0): DPMS enabled
```


```
[   127.683] (II) modeset(G0): using drv /dev/dri/card1
[   127.683] (II) modeset(G0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[   127.683] (==) modeset(G0): Depth 24, (==) framebuffer bpp 32
[   127.683] (==) modeset(G0): RGB weight 888
[   127.683] (==) modeset(G0): Default visual is TrueColor
[   127.683] (II) Loading sub module "glamoregl"
[   127.683] (II) LoadModule: "glamoregl"
[   127.684] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[   127.706] (II) Module glamoregl: vendor="X.Org Foundation"
[   127.706]    compiled for 1.20.11, module version = 1.0.1
[   127.706]    ABI class: X.Org ANSI C Emulation, version 0.4
[   128.193] (II) modeset(G0): glamor X acceleration enabled on V3D 4.2
[   128.193] (II) modeset(G0): glamor initialized
[   128.220] (II) modeset(G0): Output HDMI-1-1 has no monitor section
[   128.221] (II) modeset(G0): Output HDMI-1-2 has no monitor section
[   128.248] (--) modeset(G0): HDMI max TMDS frequency 225000KHz
[   128.249] (==) modeset(G0): Using gamma correction (1.0, 1.0, 1.0)
[   128.249] (==) modeset(G0): DPI set to (96, 96)
```

---

### Post by waffen on 2021-08-24
> **MAFoElffen said:**
> I'm looking at your config.txt and comparing it to mine... near the bottom of your config.txt, you have 
```
dtoverlay=dwc2

``` 

I just comment it and still the same problem.

---

### Post by waffen on 2021-08-24
You mention before something about DRM issues, is this line relevant?

```
[   126.946] (EE) /dev/dri/card1: failed to set DRM interface version 1.4: Permission denied
```

---

### Post by MAFoElffen on 2021-08-24
Is this newly installed? And you say 21.04 right?

Just for giggles to see what happens... 
```

### Normal Mode Sets
hdmi_group=[COLOR=#FF0000]0[/COLOR]    # 0:Autodetect EDID, 1:AEC, 2:DMT
[COLOR=#FF0000]#[/COLOR]hdmi_mode=86     # 1366x768, 60Hz,16:9, reduced blanking
### For sound through HDMI ###
hdmi_drive=1     # hdmi without sound

```
Make sure everything else is commented out in that usercfg.txt file, except for the two lines shown.

That should query the monitor for it's EDID table and tell it to use it's modes... And since that is it's preferred mode...

---

### Post by waffen on 2021-08-24
Yes it's a new installation, the only thing I did was an update and upgrade command for the Ubuntu 21.04.

I just test: Now I can't see the first screen with the colors and the monitor goes directly to the signal out of range error.

---

### Post by MAFoElffen on 2021-08-24
it was something to try. Revert/change it back. 

Let me look at a few things. I have 21.04 and 21.10 on different SD cards. Be right back.

---

### Post by waffen on 2021-08-24
I install using the Raspberry Pi Imager App:: Ubuntu Desktop 21.04 (RPi 4/400) 64bits, 2021-04-22

---

### Post by waffen on 2021-08-24
Just in case, I have another card with Manjaro ARM 21.08 Gnome and the same issue....

---

### Post by MAFoElffen on 2021-08-24
> **waffen said:**
> Just in case, I have another card with Manjaro ARM 21.08 Gnome and the same issue....

LOL. Okay... 
So in the last Xorg.0.log file... did it have any entries on EDID?

Something like this?
```
[    21.432] (II) modeset(0): Monitor name: HDMI
[    21.432] (II) modeset(0): Number of EDID sections to follow: 1
[    21.432] (II) modeset(0): EDID (in hex):
[    21.432] (II) modeset(0):     00ffffffffffff005304000001010101
[    21.432] (II) modeset(0):     003a010380000078ea53a5a756529c26
[    21.432] (II) modeset(0):     1150540108008100814081809500b300
[    21.432] (II) modeset(0):     8bc0a9400101023a801871382d40582c
[    21.432] (II) modeset(0):     4500142b2100001e7f2156aa51001e30
[    21.432] (II) modeset(0):     468f3300142b2100001e000000fd0038
[    21.432] (II) modeset(0):     3e1e5319000a202020202020000000fc
[    21.432] (II) modeset(0):     0048444d490a2020202020202020011d
[    21.432] (II) modeset(0):     02031bf148900403021f1312112309ff
[    21.432] (II) modeset(0):     078301000065030c001000023a801871
[    21.432] (II) modeset(0):     382d40582c4500142b2100001e011d00
[    21.432] (II) modeset(0):     7251d01e206e285500142b2100001e8c
[    21.432] (II) modeset(0):     0ad08a20e02d10103e9600142b210000
[    21.432] (II) modeset(0):     18000000fc0048444d490a2020202020
[    21.432] (II) modeset(0):     20202000000000000000000000000000
[    21.432] (II) modeset(0):     00000000000000000000000000000045
[    21.433] (II) modeset(0): Printing probed modes for output HDMI-1

```

If so, right below that is going to be interpretations of the monitor's modes, like this...
```
[    21.433] (II) modeset(0): Printing probed modes for output HDMI-1
[    21.433] (II) modeset(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    21.433] (II) modeset(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    21.433] (II) modeset(0): Modeline "1920x1080"x59.9  148.35  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[    21.433] (II) modeset(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz e)
[    21.433] (II) modeset(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    21.433] (II) modeset(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    21.433] (II) modeset(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    21.433] (II) modeset(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    21.433] (II) modeset(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[    21.433] (II) modeset(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    21.434] (II) modeset(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    21.434] (II) modeset(0): Modeline "1280x720"x59.9   74.18  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    21.434] (II) modeset(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    21.434] (II) modeset(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    21.434] (II) modeset(0): Modeline "720x576"x50.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    21.434] (II) modeset(0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    21.434] (II) modeset(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    21.435] (II) modeset(0): EDID for output HDMI-2
[    21.435] (II) modeset(0): Output HDMI-1 connected
[    21.435] (II) modeset(0): Output HDMI-2 disconnected

```
If not, look where it might have failed to probe and return any EDID data...

---

### Post by waffen on 2021-08-24
No, nothing like that, here is the last one:

```
[   127.681] (II) LoadModule: "modesetting"
[   127.682] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   127.682] (II) Module modesetting: vendor="X.Org Foundation"
[   127.682]    compiled for 1.20.11, module version = 1.20.11
[   127.682]    Module class: X.Org Video Driver
[   127.682]    ABI class: X.Org Video Driver, version 24.1
[   127.682] (II) UnloadModule: "modesetting"
[   127.682] (II) Unloading modesetting
[   127.682] (II) Failed to load module "modesetting" (already loaded, 0)
[   127.683] (II) modeset(G0): using drv /dev/dri/card1
[   127.683] (II) modeset(G0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[   127.683] (==) modeset(G0): Depth 24, (==) framebuffer bpp 32
[   127.683] (==) modeset(G0): RGB weight 888
[   127.683] (==) modeset(G0): Default visual is TrueColor
[   127.683] (II) Loading sub module "glamoregl"
[   127.683] (II) LoadModule: "glamoregl"
[   127.684] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[   127.706] (II) Module glamoregl: vendor="X.Org Foundation"
[   127.706]    compiled for 1.20.11, module version = 1.0.1
[   127.706]    ABI class: X.Org ANSI C Emulation, version 0.4
[   128.193] (II) modeset(G0): glamor X acceleration enabled on V3D 4.2
[   128.193] (II) modeset(G0): glamor initialized
[   128.220] (II) modeset(G0): Output HDMI-1-1 has no monitor section
[   128.221] (II) modeset(G0): Output HDMI-1-2 has no monitor section
[   128.248] (--) modeset(G0): HDMI max TMDS frequency 225000KHz
[   128.249] (==) modeset(G0): Using gamma correction (1.0, 1.0, 1.0)
[   128.249] (==) modeset(G0): DPI set to (96, 96)

```

---

### Post by MAFoElffen on 2021-08-24
In the full Xorg.0.log file that you posted earlier, somewhere in the boot process, you have 640x480 hard set.

Search within your Xorg.0.log file. I see it here:
```
[   126.924] Kernel command line: coherent_pool=1M 8250.nr_uarts=0 snd_bcm2835.enable_compat_alsa=0 snd_bcm2835.enable_hdmi=1 [COLOR=#ff0000]video=HDMI-A-1:640x480M@60,margin_left=24,margin_>[/COLOR]f
```
As a linux kernel KMS boot option... and here:
```
[   127.082] (II) FBDEV(0): Virtual size is [COLOR=#ff0000]640x480 (pitch 640)[/COLOR]
```
Where it is respecting the boot option and resetting it to that in KMS and carrying that through to XServer... Which I don't think that monitor has that mode... 

What I think is going on. is that first the Pi reads the boot *.txt files and sets up the basic chips and system on the integrate board (where we trying to set the vieo mode from usrcfg.txt) Then it boots the kernel, seeing that boot parameter, which is reseting it back to 640x480... It takes which is last...

So here's what you do... Please post your cmdline.txt file... I think the problem is there...

---

### Post by waffen on 2021-08-24
Now I'm more confuse... I just mount the SD card with the RPi Ubuntu 21.04, in my PC running Ubuntu 20.04, I can see duplicate config files mounted in 2 differents points.

In the first path is located my usercfg.txt file, in the second path there are only 2 files.

Wich one is used?? 

**/system-boot**
config.txt
```
[pi4]
max_framebuffers=2

[all]
kernel=vmlinuz
cmdline=cmdline.txt
initramfs initrd.img followkernel

# Enable the audio output, I2C and SPI interfaces on the GPIO header
dtparam=audio=on
dtparam=i2c_arm=on
dtparam=spi=on

# Enable the KMS ("full" KMS) graphics overlay, and allocate 128Mb to the GPU
# memory. The full KMS overlay is required for X11 application support under
# wayland
dtoverlay=vc4-kms-v3d
gpu_mem=128

# Uncomment the following to enable the Raspberry Pi camera module firmware.
# Be warned that there *may* be incompatibilities with the "full" KMS overlay
#start_x=1

# Comment out the following line if the edges of the desktop appear outside
# the edges of your display
disable_overscan=1

# If you have issues with audio, you may try uncommenting the following line
# which forces the HDMI output into HDMI mode instead of DVI (which doesn't
# support audio output)
#hdmi_drive=2

# If you have a CM4, uncomment the following line to enable the USB2 outputs
# on the IO board (assuming your CM4 is plugged into such a board)
#dtoverlay=dwc2,dr_mode=host

# Config settings specific to arm64
arm_64bit=1
#dtoverlay=dwc2
include usercfg.txt
```

and cmdline.txt
```
dwc_otg.lpm_enable=0 console=tty1 root=LABEL=writable rootfstype=ext4 elevator=deadline rootwait fixrtc quiet splash
```

**/writable/boot/firmware**
Here I can found 2 files:
cmdline.txt
```
net.ifnames=0 dwc_otg.lpm_enable=0 console=ttyAMA0,115200 console=tty1 root=/dev/mmcblk0p2 rootfstype=ext4 elevator=deadline rootwait
```

and config.txt
```
# For more options and information see 
# http://www.raspberrypi.org/documentation/configuration/config-txt.md
# Some settings may impact device functionality. See link above for details

kernel=uboot.bin
device_tree_address=0x02000000

# enable i2c
dtparam=i2c_arm=on
dtparam=spi=on

# uncomment if you get no picture on HDMI for a default "safe" mode
#hdmi_safe=1

# uncomment this if your display has a black border of unused pixels visible
# and your display can output without overscan
#disable_overscan=1

# uncomment the following to adjust overscan. Use positive numbers if console
# goes off screen, and negative if there is too much border
#overscan_left=16
#overscan_right=16
#overscan_top=16
#overscan_bottom=16

# uncomment to force a console size. By default it will be display's size minus
# overscan.
#framebuffer_width=1280
#framebuffer_height=720

# uncomment if hdmi display is not detected and composite is being output
#hdmi_force_hotplug=1

# uncomment to force a specific HDMI mode (this will force VGA)
#hdmi_group=1
#hdmi_mode=1

# uncomment to force a HDMI mode rather than DVI. This can make audio work in
# DMT (computer monitor) modes
#hdmi_drive=2

# uncomment to increase signal to HDMI, if you have interference, blanking, or
# no display
#config_hdmi_boost=4

# uncomment for composite PAL
#sdtv_mode=2

#uncomment to overclock the arm. 700 MHz is the default.
#arm_freq=800

```

---

### Post by waffen on 2021-08-24
Reading the files, I think the ones located/mounted in /system-boot are the ones the RPi4 mount in running time in /boot/firmware, that path is used by my in SSH mode.

---

### Post by MAFoElffen on 2021-08-25
I don't see this string in any of those files:
```
video=HDMI-A-1:640x480M@60,margin_left=24,margin_>f
```
That is the string you need to find, to remove it...

How about /boot/grub/grubenv?

---

### Post by waffen on 2021-08-25
The file /boot/grub/grubenv only have ###### 

but this one grub.cfg have a lot of code, I don't know that language so I can't edit it, but I found /etc/default/grub config file, check the line #24 I guess there is the reference you search...

**grub**
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=640x480
#GRUB_GFXMODE=1280X720
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```


**grub.cfg**
```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${initrdfail}" = 2 ]; then
   set initrdfail=
elif [ "${initrdfail}" = 1 ]; then
   set next_entry="${prev_entry}"
   set prev_entry=
   save_env prev_entry
   if [ "${next_entry}" ]; then
      set initrdfail=2
   fi
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function initrdfail {
    if [ -n "${have_grubenv}" ]; then if [ -n "${partuuid}" ]; then
      if [ -z "${initrdfail}" ]; then
        set initrdfail=1
        if [ -n "${boot_once}" ]; then
          set prev_entry="${default}"
          save_env prev_entry
        fi
      fi
      save_env initrdfail
    fi; fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root  e666f127-b7f2-4c5a-bc1f-d7694d02ea41
else
  search --no-floppy --fs-uuid --set=root e666f127-b7f2-4c5a-bc1f-d7694d02ea41
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=es_PE
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-e666f127-b7f2-4c5a-bc1f-d7694d02ea41' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
	insmod part_msdos
	insmod ext2
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root  e666f127-b7f2-4c5a-bc1f-d7694d02ea41
	else
	  search --no-floppy --fs-uuid --set=root e666f127-b7f2-4c5a-bc1f-d7694d02ea41
	fi
	linux	/boot/vmlinuz-5.11.0-1016-raspi root=UUID=e666f127-b7f2-4c5a-bc1f-d7694d02ea41 ro  quiet splash $vt_handoff
	initrd	/boot/initrd.img-5.11.0-1016-raspi
	devicetree	/boot/dtb-5.11.0-1016-raspi
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-e666f127-b7f2-4c5a-bc1f-d7694d02ea41' {
	menuentry 'Ubuntu, with Linux 5.11.0-1016-raspi' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-5.11.0-1016-raspi-advanced-e666f127-b7f2-4c5a-bc1f-d7694d02ea41' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  e666f127-b7f2-4c5a-bc1f-d7694d02ea41
		else
		  search --no-floppy --fs-uuid --set=root e666f127-b7f2-4c5a-bc1f-d7694d02ea41
		fi
		echo	'Loading Linux 5.11.0-1016-raspi ...'
		linux	/boot/vmlinuz-5.11.0-1016-raspi root=UUID=e666f127-b7f2-4c5a-bc1f-d7694d02ea41 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-5.11.0-1016-raspi
		echo	'Loading device tree blob...'
		devicetree	/boot/dtb-5.11.0-1016-raspi
	}
	menuentry 'Ubuntu, with Linux 5.11.0-1016-raspi (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-5.11.0-1016-raspi-recovery-e666f127-b7f2-4c5a-bc1f-d7694d02ea41' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  e666f127-b7f2-4c5a-bc1f-d7694d02ea41
		else
		  search --no-floppy --fs-uuid --set=root e666f127-b7f2-4c5a-bc1f-d7694d02ea41
		fi
		echo	'Loading Linux 5.11.0-1016-raspi ...'
		linux	/boot/vmlinuz-5.11.0-1016-raspi root=UUID=e666f127-b7f2-4c5a-bc1f-d7694d02ea41 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-5.11.0-1016-raspi
		echo	'Loading device tree blob...'
		devicetree	/boot/dtb-5.11.0-1016-raspi
	}
	menuentry 'Ubuntu, with Linux 5.11.0-1007-raspi' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-5.11.0-1007-raspi-advanced-e666f127-b7f2-4c5a-bc1f-d7694d02ea41' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  e666f127-b7f2-4c5a-bc1f-d7694d02ea41
		else
		  search --no-floppy --fs-uuid --set=root e666f127-b7f2-4c5a-bc1f-d7694d02ea41
		fi
		echo	'Loading Linux 5.11.0-1007-raspi ...'
		linux	/boot/vmlinuz-5.11.0-1007-raspi root=UUID=e666f127-b7f2-4c5a-bc1f-d7694d02ea41 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-5.11.0-1007-raspi
		echo	'Loading device tree blob...'
		devicetree	/boot/dtb-5.11.0-1007-raspi
	}
	menuentry 'Ubuntu, with Linux 5.11.0-1007-raspi (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-5.11.0-1007-raspi-recovery-e666f127-b7f2-4c5a-bc1f-d7694d02ea41' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  e666f127-b7f2-4c5a-bc1f-d7694d02ea41
		else
		  search --no-floppy --fs-uuid --set=root e666f127-b7f2-4c5a-bc1f-d7694d02ea41
		fi
		echo	'Loading Linux 5.11.0-1007-raspi ...'
		linux	/boot/vmlinuz-5.11.0-1007-raspi root=UUID=e666f127-b7f2-4c5a-bc1f-d7694d02ea41 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-5.11.0-1007-raspi
		echo	'Loading device tree blob...'
		devicetree	/boot/dtb-5.11.0-1007-raspi
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_linux_zfs ###
### END /etc/grub.d/10_linux_zfs ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
```

---

### Post by waffen on 2021-08-25
I just edit /etc/default/grub  and update-grub but nothing...

---

### Post by waffen on 2021-08-25
This is the full line in the log file:

```
[   126.924] Kernel command line: coherent_pool=1M 8250.nr_uarts=0 snd_bcm2835.enable_compat_alsa=0 snd_bcm2835.enable_hdmi=1 video=HDMI-A-1:640x480M@60,margin_left=24,margin_right=24,margin_top=16,margin_bottom=16 video=HDMI-A-2:640x480M@60,margin_left=24,margin_right=24,margin_top=16,margin_bottom=16 smsc95xx.macaddr=DC:A6:32:3A:93:E5 vc_mem.mem_base=0x3ec00000 vc_mem.mem_size=0x40000000  dwc_otg.lpm_enable=0 console=tty1 root=LABEL=writable rootfstype=ext4 elevator=deadline rootwait fixrtc quiet splash
```

---

### Post by waffen on 2021-08-25
I just edit the grub file adding: GRUB_GFXMODE=1366X768

and this is the log file:

```
[   243.202] 
X.Org X Server 1.20.11
X Protocol Version 11, Revision 0
[   243.202] Build Operating System: linux Ubuntu
[   243.203] Current Operating System: Linux mario-pi4ubu 5.11.0-1016-raspi #17-Ubuntu SMP PREEMPT Thu Jul 29 15:33:06 UTC 2021 aarch64
[   243.203] Kernel command line: coherent_pool=1M 8250.nr_uarts=0 snd_bcm2835.enable_compat_alsa=0 snd_bcm2835.enable_hdmi=1 video=HDMI-A-1:1366x768M@60 smsc95xx.macaddr=DC:A6:32:3A:93:E5 vc_mem.mem_base=0x3ec00000 vc_mem.mem_size=0x40000000  dwc_otg.lpm_enable=0 console=tty1 root=LABEL=writable rootfstype=ext4 elevator=deadline rootwait fixrtc quiet splash
[   243.203] Build Date: 06 July 2021  10:17:51AM
[   243.204] xorg-server 2:1.20.11-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[   243.204] Current version of pixman: 0.40.0
[   243.204] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   243.204] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   243.205] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug 25 00:31:32 2021
[   243.209] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   243.212] (==) No Layout section.  Using the first Screen section.
[   243.212] (==) No screen section available. Using defaults.
[   243.212] (**) |-->Screen "Default Screen Section" (0)
[   243.212] (**) |   |-->Monitor "<default monitor>"
[   243.216] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[   243.216] (==) Automatically adding devices
[   243.216] (==) Automatically enabling devices
[   243.216] (==) Automatically adding GPU devices
[   243.216] (==) Automatically binding GPU devices
[   243.216] (==) Max clients allowed: 256, resource mask: 0x1fffff
[   243.216] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   243.216] 	Entry deleted from font path.
[   243.216] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   243.216] 	Entry deleted from font path.
[   243.216] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   243.216] 	Entry deleted from font path.
[   243.216] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   243.217] 	Entry deleted from font path.
[   243.217] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   243.217] 	Entry deleted from font path.
[   243.217] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[   243.217] (==) ModulePath set to "/usr/lib/xorg/modules"
[   243.217] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   243.217] (II) Loader magic: 0xaaaaad64e010
[   243.217] (II) Module ABI versions:
[   243.217] 	X.Org ANSI C Emulation: 0.4
[   243.217] 	X.Org Video Driver: 24.1
[   243.217] 	X.Org XInput driver : 24.1
[   243.217] 	X.Org Server Extension : 10.0
[   243.219] (++) using VT number 6

[   243.231] (II) systemd-logind: took control of session /org/freedesktop/login1/session/_32
[   243.239] (II) xfree86: Adding drm device (/dev/dri/card1)
[   243.245] (II) systemd-logind: got fd for /dev/dri/card1 226:1 fd 11 paused 0
[   243.248] (II) xfree86: Adding drm device (/dev/dri/card0)
[   243.253] (II) systemd-logind: got fd for /dev/dri/card0 226:0 fd 12 paused 0
[   243.255] (II) no primary bus or device found
[   243.255] 	falling back to /sys/devices/platform/gpu/drm/card1
[   243.255] (II) LoadModule: "glx"
[   243.262] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   243.274] (II) Module glx: vendor="X.Org Foundation"
[   243.274] 	compiled for 1.20.11, module version = 1.0.0
[   243.274] 	ABI class: X.Org Server Extension, version 10.0
[   243.275] (==) Matched modesetting as autoconfigured driver 0
[   243.275] (==) Matched fbdev as autoconfigured driver 1
[   243.275] (==) Assigned the driver to the xf86ConfigLayout
[   243.275] (II) LoadModule: "modesetting"
[   243.281] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   243.286] (II) Module modesetting: vendor="X.Org Foundation"
[   243.286] 	compiled for 1.20.11, module version = 1.20.11
[   243.286] 	Module class: X.Org Video Driver
[   243.286] 	ABI class: X.Org Video Driver, version 24.1
[   243.286] (II) LoadModule: "fbdev"
[   243.287] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   243.289] (II) Module fbdev: vendor="X.Org Foundation"
[   243.289] 	compiled for 1.20.10, module version = 0.5.0
[   243.289] 	Module class: X.Org Video Driver
[   243.290] 	ABI class: X.Org Video Driver, version 24.1
[   243.290] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   243.290] (II) FBDEV: driver for framebuffer: fbdev
[   243.290] (II) modeset(0): using drv /dev/dri/card1
[   243.290] (WW) Falling back to old probe method for fbdev
[   243.290] (II) Loading sub module "fbdevhw"
[   243.290] (II) LoadModule: "fbdevhw"
[   243.291] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   243.293] (II) Module fbdevhw: vendor="X.Org Foundation"
[   243.294] 	compiled for 1.20.11, module version = 0.0.2
[   243.294] 	ABI class: X.Org Video Driver, version 24.1
[   243.294] (WW) VGA arbiter: cannot open kernel arbiter, no multi-card support
[   243.294] (II) modeset(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[   243.294] (==) modeset(0): Depth 24, (==) framebuffer bpp 32
[   243.295] (==) modeset(0): RGB weight 888
[   243.295] (==) modeset(0): Default visual is TrueColor
[   243.295] (II) Loading sub module "glamoregl"
[   243.295] (II) LoadModule: "glamoregl"
[   243.295] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[   243.316] (II) Module glamoregl: vendor="X.Org Foundation"
[   243.316] 	compiled for 1.20.11, module version = 1.0.1
[   243.316] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   243.873] (II) modeset(0): glamor X acceleration enabled on V3D 4.2
[   243.873] (II) modeset(0): glamor initialized
[   243.900] (II) modeset(0): Output HDMI-1 has no monitor section
[   243.901] (II) modeset(0): Output HDMI-2 has no monitor section
[   243.928] (II) modeset(0): EDID for output HDMI-1
[   243.928] (II) modeset(0): Manufacturer: GSM  Model: 5acb  Serial#: 131253
[   243.928] (II) modeset(0): Year: 2016  Week: 3
[   243.928] (II) modeset(0): EDID Version: 1.3
[   243.928] (II) modeset(0): Digital Display Input
[   243.928] (II) modeset(0): Max Image Size [cm]: horiz.: 41  vert.: 23
[   243.928] (II) modeset(0): Gamma: 2.20
[   243.928] (II) modeset(0): DPMS capabilities: StandBy Suspend Off
[   243.928] (II) modeset(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   243.928] (II) modeset(0): First detailed timing is preferred mode
[   243.928] (II) modeset(0): redX: 0.636 redY: 0.345   greenX: 0.332 greenY: 0.609
[   243.928] (II) modeset(0): blueX: 0.156 blueY: 0.061   whiteX: 0.313 whiteY: 0.329
[   243.929] (II) modeset(0): Supported established timings:
[   243.929] (II) modeset(0): 720x400@70Hz
[   243.929] (II) modeset(0): 640x480@60Hz
[   243.929] (II) modeset(0): 640x480@75Hz
[   243.929] (II) modeset(0): 800x600@56Hz
[   243.929] (II) modeset(0): 800x600@60Hz
[   243.929] (II) modeset(0): 800x600@75Hz
[   243.929] (II) modeset(0): 832x624@75Hz
[   243.929] (II) modeset(0): 1024x768@60Hz
[   243.929] (II) modeset(0): 1024x768@75Hz
[   243.929] (II) modeset(0): Manufacturer's mask: 0
[   243.929] (II) modeset(0): Supported standard timings:
[   243.929] (II) modeset(0): #0: hsize: 640  vsize 480  refresh: 75  vid: 20273
[   243.929] (II) modeset(0): #1: hsize: 800  vsize 600  refresh: 75  vid: 20293
[   243.929] (II) modeset(0): #2: hsize: 1024  vsize 768  refresh: 75  vid: 20321
[   243.929] (II) modeset(0): #3: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[   243.929] (II) modeset(0): Supported detailed timing:
[   243.929] (II) modeset(0): clock: 85.5 MHz   Image Size:  410 x 230 mm
[   243.929] (II) modeset(0): h_active: 1366  h_sync: 1436  h_sync_end 1579 h_blank_end 1792 h_border: 0
[   243.929] (II) modeset(0): v_active: 768  v_sync: 771  v_sync_end 774 v_blanking: 798 v_border: 0
[   243.929] (II) modeset(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 61 kHz, PixClock max 95 MHz
[   243.929] (II) modeset(0): Monitor name: LG HD
[   243.929] (II) modeset(0): Serial No: 603NTBK3V253
[   243.930] (II) modeset(0): Supported detailed timing:
[   243.930] (II) modeset(0): clock: 27.0 MHz   Image Size:  160 x 90 mm
[   243.930] (II) modeset(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[   243.930] (II) modeset(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[   243.930] (II) modeset(0): Number of EDID sections to follow: 1
[   243.930] (II) modeset(0): EDID (in hex):
[   243.930] (II) modeset(0): 	00ffffffffffff001e6dcb5ab5000200
[   243.930] (II) modeset(0): 	031a010380291778ead025a258559c28
[   243.930] (II) modeset(0): 	0f5054a76a00314f454f614f81c00101
[   243.930] (II) modeset(0): 	010101010101662156aa51001e30468f
[   243.930] (II) modeset(0): 	33009ae61000001e000000fd00384b1e
[   243.930] (II) modeset(0): 	3d09000a202020202020000000fc004c
[   243.930] (II) modeset(0): 	472048440a20202020202020000000ff
[   243.930] (II) modeset(0): 	003630334e54424b33563235330a01df
[   243.930] (II) modeset(0): 	02031b61230907078301000067030c00
[   243.930] (II) modeset(0): 	2000802d43908402e2000f8c0ad08a20
[   243.930] (II) modeset(0): 	e02d10103e9600a05a00000000000000
[   243.930] (II) modeset(0): 	00000000000000000000000000000000
[   243.930] (II) modeset(0): 	00000000000000000000000000000000
[   243.930] (II) modeset(0): 	00000000000000000000000000000000
[   243.930] (II) modeset(0): 	00000000000000000000000000000000
[   243.930] (II) modeset(0): 	00000000000000000000000000000029
[   243.931] (--) modeset(0): HDMI max TMDS frequency 225000KHz
[   243.931] (II) modeset(0): Printing probed modes for output HDMI-1
[   243.931] (II) modeset(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[   243.931] (II) modeset(0): Modeline "1920x1080"x59.9  148.35  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[   243.931] (II) modeset(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[   243.931] (II) modeset(0): Modeline "1280x720"x59.9   74.18  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[   243.931] (II) modeset(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   243.931] (II) modeset(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   243.931] (II) modeset(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   243.931] (II) modeset(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   243.931] (II) modeset(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   243.931] (II) modeset(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   243.931] (II) modeset(0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[   243.931] (II) modeset(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[   243.932] (II) modeset(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   243.932] (II) modeset(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   243.932] (II) modeset(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   243.932] (II) modeset(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   243.933] (II) modeset(0): EDID for output HDMI-2
[   243.933] (II) modeset(0): Output HDMI-1 connected
[   243.933] (II) modeset(0): Output HDMI-2 disconnected
[   243.933] (II) modeset(0): Using exact sizes for initial modes
[   243.933] (II) modeset(0): Output HDMI-1 using initial mode 1920x1080 +0+0
[   243.933] (==) modeset(0): Using gamma correction (1.0, 1.0, 1.0)
[   243.933] (==) modeset(0): DPI set to (96, 96)
[   243.933] (II) Loading sub module "fb"
[   243.933] (II) LoadModule: "fb"
[   243.940] (II) Loading /usr/lib/xorg/modules/libfb.so
[   243.944] (II) Module fb: vendor="X.Org Foundation"
[   243.944] 	compiled for 1.20.11, module version = 1.0.0
[   243.944] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   243.944] (II) UnloadModule: "fbdev"
[   243.945] (II) Unloading fbdev
[   243.945] (II) UnloadSubModule: "fbdevhw"
[   243.945] (II) Unloading fbdevhw
[   244.033] (==) modeset(0): Backing store enabled
[   244.033] (==) modeset(0): Silken mouse enabled
[   244.148] (II) modeset(0): Initializing kms color map for depth 24, 8 bpc.
[   244.149] (==) modeset(0): DPMS enabled
[   244.149] (II) modeset(0): [DRI2] Setup complete
[   244.149] (II) modeset(0): [DRI2]   DRI driver: vc4
[   244.149] (II) modeset(0): [DRI2]   VDPAU driver: vc4
[   244.150] (II) Initializing extension Generic Event Extension
[   244.150] (II) Initializing extension SHAPE
[   244.151] (II) Initializing extension MIT-SHM
[   244.152] (II) Initializing extension XInputExtension
[   244.157] (II) Initializing extension XTEST
[   244.158] (II) Initializing extension BIG-REQUESTS
[   244.159] (II) Initializing extension SYNC
[   244.160] (II) Initializing extension XKEYBOARD
[   244.161] (II) Initializing extension XC-MISC
[   244.161] (II) Initializing extension SECURITY
[   244.162] (II) Initializing extension XFIXES
[   244.162] (II) Initializing extension RENDER
[   244.163] (II) Initializing extension RANDR
[   244.163] (II) Initializing extension COMPOSITE
[   244.164] (II) Initializing extension DAMAGE
[   244.164] (II) Initializing extension MIT-SCREEN-SAVER
[   244.165] (II) Initializing extension DOUBLE-BUFFER
[   244.165] (II) Initializing extension RECORD
[   244.165] (II) Initializing extension DPMS
[   244.166] (II) Initializing extension Present
[   244.166] (II) Initializing extension DRI3
[   244.166] (II) Initializing extension X-Resource
[   244.167] (II) Initializing extension XVideo
[   244.167] (II) Initializing extension XVideo-MotionCompensation
[   244.167] (II) Initializing extension SELinux
[   244.167] (II) SELinux: Disabled on system
[   244.167] (II) Initializing extension GLX
[   244.650] (II) AIGLX: Loaded and initialized vc4
[   244.650] (II) GLX: Initialized DRI2 GL provider for screen 0
[   244.650] (II) Initializing extension XFree86-VidModeExtension
[   244.651] (II) Initializing extension XFree86-DGA
[   244.651] (II) Initializing extension XFree86-DRI
[   244.657] (II) Initializing extension DRI2
[   244.661] (II) modeset(0): Damage tracking initialized
[   244.661] (II) modeset(0): Setting screen physical size to 508 x 285
[   245.030] (II) config/udev: Adding input device Logitech Wireless Keyboard PID:4023 (/dev/input/event0)
[   245.030] (**) Logitech Wireless Keyboard PID:4023: Applying InputClass "libinput keyboard catchall"
[   245.030] (II) LoadModule: "libinput"
[   245.031] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[   245.038] (II) Module libinput: vendor="X.Org Foundation"
[   245.038] 	compiled for 1.20.11, module version = 0.30.0
[   245.038] 	Module class: X.Org XInput Driver
[   245.039] 	ABI class: X.Org XInput driver, version 24.1
[   245.039] (II) Using input driver 'libinput' for 'Logitech Wireless Keyboard PID:4023'
[   245.042] (II) systemd-logind: got fd for /dev/input/event0 13:64 fd 25 paused 0
[   245.042] (**) Logitech Wireless Keyboard PID:4023: always reports core events
[   245.042] (**) Option "Device" "/dev/input/event0"
[   245.043] (**) Option "_source" "server/udev"
[   245.061] (II) event0  - Logitech Wireless Keyboard PID:4023: is tagged by udev as: Keyboard
[   245.062] (II) event0  - Logitech Wireless Keyboard PID:4023: device is a keyboard
[   245.063] (II) event0  - Logitech Wireless Keyboard PID:4023: device removed
[   245.063] (II) libinput: Logitech Wireless Keyboard PID:4023: needs a virtual subdevice
[   245.063] (**) Option "config_info" "udev:/sys/devices/platform/scb/fd500000.pcie/pci0000:00/0000:00:00.0/0000:01:00.0/usb1/1-1/1-1.4/1-1.4:1.1/0003:046D:C534.0002/0003:046D:4023.0003/input/input17/event0"
[   245.063] (II) XINPUT: Adding extended input device "Logitech Wireless Keyboard PID:4023" (type: MOUSE, id 6)
[   245.064] (**) Option "AccelerationScheme" "none"
[   245.064] (**) Logitech Wireless Keyboard PID:4023: (accel) selected scheme none/0
[   245.064] (**) Logitech Wireless Keyboard PID:4023: (accel) acceleration factor: 2.000
[   245.064] (**) Logitech Wireless Keyboard PID:4023: (accel) acceleration threshold: 4
[   245.077] (II) event0  - Logitech Wireless Keyboard PID:4023: is tagged by udev as: Keyboard
[   245.077] (II) event0  - Logitech Wireless Keyboard PID:4023: device is a keyboard
[   245.085] (II) config/udev: Adding input device Logitech Wireless Mouse (/dev/input/event1)
[   245.085] (**) Logitech Wireless Mouse: Applying InputClass "libinput pointer catchall"
[   245.085] (II) Using input driver 'libinput' for 'Logitech Wireless Mouse'
[   245.089] (II) systemd-logind: got fd for /dev/input/event1 13:65 fd 28 paused 0
[   245.089] (**) Logitech Wireless Mouse: always reports core events
[   245.089] (**) Option "Device" "/dev/input/event1"
[   245.089] (**) Option "_source" "server/udev"
[   245.101] (II) event1  - Logitech Wireless Mouse: is tagged by udev as: Mouse
[   245.102] (II) event1  - Logitech Wireless Mouse: device is a pointer
[   245.103] (II) event1  - Logitech Wireless Mouse: device removed
[   245.103] (**) Option "config_info" "udev:/sys/devices/platform/scb/fd500000.pcie/pci0000:00/0000:00:00.0/0000:01:00.0/usb1/1-1/1-1.4/1-1.4:1.1/0003:046D:C534.0002/0003:046D:4054.0004/input/input18/event1"
[   245.103] (II) XINPUT: Adding extended input device "Logitech Wireless Mouse" (type: MOUSE, id 7)
[   245.103] (**) Option "AccelerationScheme" "none"
[   245.103] (**) Logitech Wireless Mouse: (accel) selected scheme none/0
[   245.103] (**) Logitech Wireless Mouse: (accel) acceleration factor: 2.000
[   245.103] (**) Logitech Wireless Mouse: (accel) acceleration threshold: 4
[   245.115] (II) event1  - Logitech Wireless Mouse: is tagged by udev as: Mouse
[   245.116] (II) event1  - Logitech Wireless Mouse: device is a pointer
[   245.124] (II) config/udev: Adding input device Logitech Wireless Mouse (/dev/input/mouse0)
[   245.124] (II) No input driver specified, ignoring this device.
[   245.124] (II) This device may have been added with another device file.
[   245.127] (II) config/udev: Adding input device vc4 (/dev/input/event2)
[   245.127] (**) vc4: Applying InputClass "libinput keyboard catchall"
[   245.127] (II) Using input driver 'libinput' for 'vc4'
[   245.130] (II) systemd-logind: got fd for /dev/input/event2 13:66 fd 29 paused 0
[   245.130] (**) vc4: always reports core events
[   245.130] (**) Option "Device" "/dev/input/event2"
[   245.130] (**) Option "_source" "server/udev"
[   245.136] (II) event2  - vc4: is tagged by udev as: Keyboard Pointingstick
[   245.137] (II) event2  - vc4: device is a pointer
[   245.137] (II) event2  - vc4: device is a keyboard
[   245.138] (II) event2  - vc4: device removed
[   245.138] (II) libinput: vc4: needs a virtual subdevice
[   245.139] (**) Option "config_info" "udev:/sys/devices/platform/soc/fef00700.hdmi/rc/rc0/input19/event2"
[   245.139] (II) XINPUT: Adding extended input device "vc4" (type: MOUSE, id 8)
[   245.139] (**) Option "AccelerationScheme" "none"
[   245.139] (**) vc4: (accel) selected scheme none/0
[   245.139] (**) vc4: (accel) acceleration factor: 2.000
[   245.139] (**) vc4: (accel) acceleration threshold: 4
[   245.144] (II) event2  - vc4: is tagged by udev as: Keyboard Pointingstick
[   245.145] (II) event2  - vc4: device is a pointer
[   245.145] (II) event2  - vc4: device is a keyboard
[   245.149] (II) config/udev: Adding input device vc4 (/dev/input/event3)
[   245.149] (**) vc4: Applying InputClass "libinput keyboard catchall"
[   245.149] (II) Using input driver 'libinput' for 'vc4'
[   245.152] (II) systemd-logind: got fd for /dev/input/event3 13:67 fd 30 paused 0
[   245.152] (**) vc4: always reports core events
[   245.152] (**) Option "Device" "/dev/input/event3"
[   245.152] (**) Option "_source" "server/udev"
[   245.158] (II) event3  - vc4: is tagged by udev as: Keyboard Pointingstick
[   245.159] (II) event3  - vc4: device is a pointer
[   245.159] (II) event3  - vc4: device is a keyboard
[   245.160] (II) event3  - vc4: device removed
[   245.160] (II) libinput: vc4: needs a virtual subdevice
[   245.160] (**) Option "config_info" "udev:/sys/devices/platform/soc/fef05700.hdmi/rc/rc1/input20/event3"
[   245.160] (II) XINPUT: Adding extended input device "vc4" (type: MOUSE, id 9)
[   245.161] (**) Option "AccelerationScheme" "none"
[   245.161] (**) vc4: (accel) selected scheme none/0
[   245.161] (**) vc4: (accel) acceleration factor: 2.000
[   245.161] (**) vc4: (accel) acceleration threshold: 4
[   245.166] (II) event3  - vc4: is tagged by udev as: Keyboard Pointingstick
[   245.167] (II) event3  - vc4: device is a pointer
[   245.167] (II) event3  - vc4: device is a keyboard
[   245.401] (**) Logitech Wireless Keyboard PID:4023: Applying InputClass "libinput keyboard catchall"
[   245.401] (II) Using input driver 'libinput' for 'Logitech Wireless Keyboard PID:4023'
[   245.401] (II) systemd-logind: returning pre-existing fd for /dev/input/event0 13:64
[   245.401] (**) Logitech Wireless Keyboard PID:4023: always reports core events
[   245.401] (**) Option "Device" "/dev/input/event0"
[   245.401] (**) Option "_source" "_driver/libinput"
[   245.401] (II) libinput: Logitech Wireless Keyboard PID:4023: is a virtual subdevice
[   245.401] (**) Option "config_info" "udev:/sys/devices/platform/scb/fd500000.pcie/pci0000:00/0000:00:00.0/0000:01:00.0/usb1/1-1/1-1.4/1-1.4:1.1/0003:046D:C534.0002/0003:046D:4023.0003/input/input17/event0"
[   245.401] (II) XINPUT: Adding extended input device "Logitech Wireless Keyboard PID:4023" (type: KEYBOARD, id 10)
[   245.401] (**) Option "xkb_layout" "es"
[   245.452] (**) vc4: Applying InputClass "libinput keyboard catchall"
[   245.452] (II) Using input driver 'libinput' for 'vc4'
[   245.452] (II) systemd-logind: returning pre-existing fd for /dev/input/event2 13:66
[   245.453] (**) vc4: always reports core events
[   245.453] (**) Option "Device" "/dev/input/event2"
[   245.453] (**) Option "_source" "_driver/libinput"
[   245.453] (II) libinput: vc4: is a virtual subdevice
[   245.453] (**) Option "config_info" "udev:/sys/devices/platform/soc/fef00700.hdmi/rc/rc0/input19/event2"
[   245.453] (II) XINPUT: Adding extended input device "vc4" (type: KEYBOARD, id 11)
[   245.453] (**) Option "xkb_layout" "es"
[   245.454] (**) vc4: Applying InputClass "libinput keyboard catchall"
[   245.454] (II) Using input driver 'libinput' for 'vc4'
[   245.454] (II) systemd-logind: returning pre-existing fd for /dev/input/event3 13:67
[   245.454] (**) vc4: always reports core events
[   245.454] (**) Option "Device" "/dev/input/event3"
[   245.454] (**) Option "_source" "_driver/libinput"
[   245.454] (II) libinput: vc4: is a virtual subdevice
[   245.454] (**) Option "config_info" "udev:/sys/devices/platform/soc/fef05700.hdmi/rc/rc1/input20/event3"
[   245.454] (II) XINPUT: Adding extended input device "vc4" (type: KEYBOARD, id 12)
[   245.454] (**) Option "xkb_layout" "es"
[   251.499] (II) modeset(0): EDID vendor "GSM", prod id 23243
[   251.499] (II) modeset(0): DDCModeFromDetailedTiming: 720x480 Warning: We only handle separate sync.
[   251.500] (II) modeset(0): Using EDID range info for horizontal sync
[   251.500] (II) modeset(0): Using EDID range info for vertical refresh
[   251.500] (II) modeset(0): Printing DDC gathered Modelines:
[   251.500] (II) modeset(0): Modeline "1366x768"x0.0   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz eP)
[   251.500] (II) modeset(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[   251.500] (II) modeset(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[   251.500] (II) modeset(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[   251.500] (II) modeset(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   251.500] (II) modeset(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   251.500] (II) modeset(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   251.500] (II) modeset(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   251.500] (II) modeset(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   251.500] (II) modeset(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   251.500] (II) modeset(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   251.500] (II) modeset(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   251.500] (II) modeset(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   251.501] (--) modeset(0): HDMI max TMDS frequency 225000KHz
[   258.490] (II) modeset(0): EDID vendor "GSM", prod id 23243
[   258.490] (II) modeset(0): DDCModeFromDetailedTiming: 720x480 Warning: We only handle separate sync.
[   258.490] (II) modeset(0): Using hsync ranges from config file
[   258.490] (II) modeset(0): Using vrefresh ranges from config file
[   258.490] (II) modeset(0): Printing DDC gathered Modelines:
[   258.490] (II) modeset(0): Modeline "1366x768"x0.0   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz eP)
[   258.490] (II) modeset(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[   258.490] (II) modeset(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[   258.490] (II) modeset(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[   258.490] (II) modeset(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   258.491] (II) modeset(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   258.491] (II) modeset(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   258.491] (II) modeset(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   258.491] (II) modeset(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   258.491] (II) modeset(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   258.491] (II) modeset(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   258.491] (II) modeset(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   258.491] (II) modeset(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   258.492] (--) modeset(0): HDMI max TMDS frequency 225000KHz
[   261.359] (II) modeset(0): Disabling kernel dirty updates, not required.
[   469.646] (**) Option "fd" "25"
[   469.649] (**) Option "fd" "28"
[   469.650] (II) event1  - Logitech Wireless Mouse: device removed
[   469.653] (**) Option "fd" "29"
[   469.654] (**) Option "fd" "30"
[   469.657] (**) Option "fd" "25"
[   469.658] (II) event0  - Logitech Wireless Keyboard PID:4023: device removed
[   469.659] (**) Option "fd" "29"
[   469.659] (II) event2  - vc4: device removed
[   469.660] (**) Option "fd" "30"
[   469.660] (II) event3  - vc4: device removed
[   469.661] (II) AIGLX: Suspending AIGLX clients for VT switch
[   469.666] (II) systemd-logind: got pause for 13:65
[   469.666] (II) systemd-logind: got pause for 226:1
[   469.666] (II) systemd-logind: got pause for 226:0
[   469.666] (II) systemd-logind: got pause for 13:64
[   469.666] (II) systemd-logind: got pause for 13:66
[   469.666] (II) systemd-logind: got pause for 13:67
[   657.432] (II) systemd-logind: got resume for 13:65
[   657.433] (II) systemd-logind: got resume for 226:1
[   657.433] (II) systemd-logind: got resume for 226:0
[   657.433] (II) AIGLX: Resuming AIGLX clients after VT switch
[   657.486] (II) modeset(0): EDID vendor "GSM", prod id 23243
[   657.487] (II) modeset(0): DDCModeFromDetailedTiming: 720x480 Warning: We only handle separate sync.
[   657.487] (II) modeset(0): Using hsync ranges from config file
[   657.487] (II) modeset(0): Using vrefresh ranges from config file
[   657.487] (II) modeset(0): Printing DDC gathered Modelines:
[   657.487] (II) modeset(0): Modeline "1366x768"x0.0   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz eP)
[   657.487] (II) modeset(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[   657.487] (II) modeset(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[   657.487] (II) modeset(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[   657.487] (II) modeset(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   657.487] (II) modeset(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   657.487] (II) modeset(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   657.487] (II) modeset(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   657.487] (II) modeset(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   657.487] (II) modeset(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   657.487] (II) modeset(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   657.487] (II) modeset(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   657.487] (II) modeset(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   657.488] (--) modeset(0): HDMI max TMDS frequency 225000KHz
[   657.553] (II) modeset(0): EDID vendor "GSM", prod id 23243
[   657.553] (II) modeset(0): DDCModeFromDetailedTiming: 720x480 Warning: We only handle separate sync.
[   657.553] (II) modeset(0): Using hsync ranges from config file
[   657.553] (II) modeset(0): Using vrefresh ranges from config file
[   657.553] (II) modeset(0): Printing DDC gathered Modelines:
[   657.554] (II) modeset(0): Modeline "1366x768"x0.0   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz eP)
[   657.554] (II) modeset(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[   657.554] (II) modeset(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[   657.554] (II) modeset(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[   657.554] (II) modeset(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   657.554] (II) modeset(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   657.554] (II) modeset(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   657.554] (II) modeset(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   657.554] (II) modeset(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   657.554] (II) modeset(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   657.554] (II) modeset(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   657.554] (II) modeset(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   657.554] (II) modeset(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   657.555] (--) modeset(0): HDMI max TMDS frequency 225000KHz
[   657.591] (II) event1  - Logitech Wireless Mouse: is tagged by udev as: Mouse
[   657.591] (II) event1  - Logitech Wireless Mouse: device is a pointer
[   657.596] (II) systemd-logind: got resume for 13:64
[   657.608] (II) event0  - Logitech Wireless Keyboard PID:4023: is tagged by udev as: Keyboard
[   657.609] (II) event0  - Logitech Wireless Keyboard PID:4023: device is a keyboard
[   657.613] (II) systemd-logind: got resume for 13:66
[   657.618] (II) event2  - vc4: is tagged by udev as: Keyboard Pointingstick
[   657.619] (II) event2  - vc4: device is a pointer
[   657.621] (II) event2  - vc4: device is a keyboard
[   657.624] (II) systemd-logind: got resume for 13:67
[   657.631] (II) event3  - vc4: is tagged by udev as: Keyboard Pointingstick
[   657.631] (II) event3  - vc4: device is a pointer
[   657.632] (II) event3  - vc4: device is a keyboard
[   661.061] (**) Option "fd" "51"
[   661.067] (**) Option "fd" "28"
[   661.067] (II) event1  - Logitech Wireless Mouse: device removed
[   661.072] (**) Option "fd" "29"
[   661.075] (**) Option "fd" "49"
[   661.080] (**) Option "fd" "51"
[   661.080] (II) event0  - Logitech Wireless Keyboard PID:4023: device removed
[   661.082] (**) Option "fd" "29"
[   661.083] (II) event2  - vc4: device removed
[   661.085] (**) Option "fd" "49"
[   661.085] (II) event3  - vc4: device removed
[   661.087] (II) AIGLX: Suspending AIGLX clients for VT switch
[   661.146] (II) systemd-logind: got pause for 13:65
[   661.146] (II) systemd-logind: got pause for 226:1
[   661.146] (II) systemd-logind: got pause for 226:0
[   661.146] (II) systemd-logind: got pause for 13:64
[   661.147] (II) systemd-logind: got pause for 13:66
[   661.147] (II) systemd-logind: got pause for 13:67
```

---

### Post by waffen on 2021-08-27
Hello,

With the same monitor I can use a Raspbian OS with no issues, I don't know if this can help but here's a copy of the config files:

**config.txt**
```
# For more options and information see
# http://rpf.io/configtxt
# Some settings may impact device functionality. See link above for details

# uncomment if you get no picture on HDMI for a default "safe" mode
#hdmi_safe=1

# uncomment this if your display has a black border of unused pixels visible
# and your display can output without overscan
disable_overscan=1

# uncomment the following to adjust overscan. Use positive numbers if console
# goes off screen, and negative if there is too much border
#overscan_left=16
#overscan_right=16
#overscan_top=16
#overscan_bottom=16

# uncomment to force a console size. By default it will be display's size minus
# overscan.
#framebuffer_width=1280
#framebuffer_height=720

# uncomment if hdmi display is not detected and composite is being output
#hdmi_force_hotplug=1

# uncomment to force a specific HDMI mode (this will force VGA)
hdmi_group=2
hdmi_mode=86
hdmi_cvt=1366 768 60 3 0 0 1
# uncomment to force a HDMI mode rather than DVI. This can make audio work in
# DMT (computer monitor) modes
#hdmi_drive=2

# uncomment to increase signal to HDMI, if you have interference, blanking, or
# no display
#config_hdmi_boost=4

# uncomment for composite PAL
#sdtv_mode=2

#uncomment to overclock the arm. 700 MHz is the default.
#arm_freq=800

# Uncomment some or all of these to enable the optional hardware interfaces
#dtparam=i2c_arm=on
#dtparam=i2s=on
#dtparam=spi=on

# Uncomment this to enable infrared communication.
#dtoverlay=gpio-ir,gpio_pin=17
#dtoverlay=gpio-ir-tx,gpio_pin=18

# Additional overlays and parameters are documented /boot/overlays/README

# Enable audio (loads snd_bcm2835)
dtparam=audio=on

[pi4]
# Enable DRM VC4 V3D driver on top of the dispmanx display stack
dtoverlay=vc4-fkms-v3d
max_framebuffers=2

[all]
#dtoverlay=vc4-fkms-v3d
dtoverlay=gpio-fan,gpiopin=18,temp=55000
```

**cmdline.txt**
```
console=serial0,115200 console=tty1 root=PARTUUID=8cd88879-02 rootfstype=ext4 elevator=deadline fsck.repair=yes rootwait quiet splash plymouth.ignore-serial-consoles
```

---

### Post by waffen on 2021-09-07
Any help with this issue? I can't make it work with that monitor.

---

### Post by MAFoElffen on 2021-09-08
> **waffen said:**
> This is the full line in the log file:

```
[   126.924] Kernel command line: 
coherent_pool=1M 
8250.nr_uarts=0 
snd_bcm2835.enable_compat_alsa=0 
snd_bcm2835.enable_hdmi=1 
[COLOR=#ff0000]video=HDMI-A-1:640x480M@60,margin_left=24,margin_right=24,margin_top=16,margin_bottom=16 
video=HDMI-A-2:640x480M@60,margin_left=24,margin_right=24,margin_top=16,margin_bottom=16 [/COLOR]
smsc95xx.macaddr=DC:A6:32:3A:93:E5 
vc_mem.mem_base=0x3ec00000 
vc_mem.mem_size=0x40000000  
dwc_otg.lpm_enable=0 
console=tty1 
root=LABEL=writable 
rootfstype=ext4 elevator=deadline 
rootwait fixrtc quiet splash
```
This is still coming from "somewhere"...

This should display the filename of where that string is within the boot directory or any of it's subdirectories...
```

find /boot -type f | grep -v 'raspi' | xargs grep -r -l "640x480M@60"

```
If it doesn't display anything, then change to search from "/boot" to "etc".

It's getting that twice from "somewhere" and that is NOT a default setting...

---

