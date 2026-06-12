---
title: "Monitor resolution detected incorrectly, how to fix?"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by the_blur on 2010-05-02
Hi guys, I have a Samsung 2443bw monitor connected to a Radeon 4870 1G card. My maximum resolution is showing up as 1680x1050, it should be 1920x1200. I have looked around and searched for a solution to this issue, but have not found anything that worked, I played around with xorg.conf, but gave up after deciding there has got to be a better way and that someone has already probably figured this out =)

Can anyone help? I am halfway competent. Everything works properly in windows of course (this is primarily a gaming system).

---

### Post by kansasnoob on 2010-05-02
I had a somewhat similar issue only with Intel 82945G/GZ Graphics, full story here:

[http://ubuntuforums.org/showthread.php?t=1462350](http://ubuntuforums.org/showthread.php?t=1462350)

And summed up in posts #3 and #4 here:

[http://ubuntuforums.org/showthread.php?t=1469567](http://ubuntuforums.org/showthread.php?t=1469567)

I should also add that I've only tried that with Karmic and Lucid!

---

### Post by quadproc on 2010-05-02
> **the_blur said:**
> Hi guys, I have a Samsung 2443bw monitor connected to a Radeon 4870 1G card. My maximum resolution is showing up as 1680x1050, it should be 1920x1200. I have looked around and searched for a solution to this issue, but have not found anything that worked, I played around with xorg.conf, but gave up after deciding there has got to be a better way and that someone has already probably figured this out =)

I am running HD4870x2 and I find that xrandr tells me that my maximum resolution is 1980x1080 for an auto-detected ASUS monitor.  I will paste my xorg.conf file below with most comments removed.  I run nearly as little as I can in that file; that seems to simplify things :D

```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
    Option        "DontZap" "False"
EndSection

Section "Monitor"

# I added the following line on 1/19/10
    Identifier   "Configured Monitor"
    Option        "DPMS"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```Hope this helps.

quadproc

---

### Post by the_blur on 2010-05-10
Hello everyone, I followed instructions from here:
[http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/](http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/)

And everything worked like a charm!

Linux community for the win!
Could not hope for a nicer, more helpful set of peeps!

---

