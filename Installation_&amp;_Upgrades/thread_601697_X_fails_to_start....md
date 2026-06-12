---
title: "X fails to start..."
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by chickensofdoom on 2007-11-03
I just freshly installed Feisty on my HP dv9500t laptop.  The installation went okay, but as soon as I tried to boot into ubuntu, I ran into problems.  After selecting ubuntu in GRUB, the load bar comes up, but after the load bar, xserver fails to start.  It gives me the option to view the logs, and this is the message it gives:

```

(EE) NV(0): No display devices found
(EE) Screen(s) found, but none have a usable configuration

Fatal server error: 
no screens found
```

My graphics card is an NVIDIA GeForce 8600M GS, but I don't think that's the problem.  I checked my xorg.conf file, and it had this for screen configs:

```

Section "Screen"
 Identifier "Default Screen"
 Device "nVidia Corporation NVIDIA Default Card"
 Monitor "Generic Monitor"
 DefaultDepth 16
 SubSection "Display"
  Depth 1
  Modes "1024x768" "800x600" "640x480"
 EndSubSection
(then those last 4 lines repeated for Depths 4, 8, 15, 16, and 24)
EndSection

```

My monitor is widescreen, so that may have something to do with it... how would I fix that?

---

### Post by kentl on 2007-11-03
I had the same error with my ATI Radeon X1300 card, but it started working when I installed the driver for my card. It's all I've got for you, but perhaps it'll lead you to an answer.

---

### Post by blueglue on 2007-11-03
Which graphics chipset doe's that model have?

---

### Post by Pumalite on 2007-11-03
Regarding wide screen:

[http://www.codeodor.com/index.cfm/2007/3/16/Ubuntu-and-Widescreen-Resolution-Fixed/1035](http://www.codeodor.com/index.cfm/2007/3/16/Ubuntu-and-Widescreen-Resolution-Fixed/1035)

[http://ubuntuforums.org/showthread.php?t=280683&page=3](http://ubuntuforums.org/showthread.php?t=280683&page=3)

[https://bugs.launchpad.net/ubuntu/+source/xresprobe/+bug/63551](https://bugs.launchpad.net/ubuntu/+source/xresprobe/+bug/63551)

---

### Post by pbcartwright on 2007-11-03
change your /etc/X11/xorg.conf device driver  from
Driver         "nvidia"
to this:
Driver         "nv"

then install envy and let it configure your Nvidia card. get envy here:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)


here is what my /etc/X11/xorg.conf file looks like:
Section "Device"

        #Driver         "nvidia"
    Identifier     "nVidia Corporation GeForce 7300 LE"
    Driver         "nvidia"

EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation GeForce 7300 LE"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050" "1600x1200" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050" "1600x1200" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050" "1600x1200" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050" "1600x1200" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "1600x1200" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1600x1200" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by chickensofdoom on 2007-11-03
> **kentl said:**
> I had the same error with my ATI Radeon X1300 card, but it started working when I installed the driver for my card. It's all I've got for you, but perhaps it'll lead you to an answer.

How exactly did you do that? I'm a bit new to getting all this stuff to work.

I'll try some of the stuff in those links.

@pbcartwright: I tried getting envy to work, but when I tried to install it (using only the command line) it apparently had some dependencies that needed the feisty cd, and it wouldn't work when I put the feisty cd in (although that may have been a problem with it not recognizing my cdrom drive or something)

---

### Post by kentl on 2007-11-03
I followed method 2 in this article: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

Hope it works out for you.

---

### Post by menonfire12 on 2007-12-15
Maybe you have the same problem than me, the dvdrom also doesn't work the solution that i used was :

-- The command "wget" (conected with ethernet of course) with the http direction of the file for envy and then it downloads it.   

sudo -s
(password of adm)
cd /home/user (you are the user)
mkdir envy
cd envy
wget [http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.9-0ubuntu2_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.9-0ubuntu2_all.deb) 

After that i did what says un the FAQ of the page [http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)  
following the instrunctions it will ask for the Fiesty CD but you type any character and then enter it search all on the us.archive.ubuntu page and download it  the last you type "envy -t" and choose option no. 1 starts a lot of downloads etc etc after that reboot you machine and it should work , well it worked for me i have the same notebook  dv9500t and i'm writting this on ubuntu ejejeje  :lolflag: 

Please if anyone knows how to solve the problem of the dvdrom please contact me, help!!  :confused:

---

