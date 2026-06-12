---
title: "can not set resolution after install"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by thanhthanh on 2007-07-09
i am a newbie in linux. i installed ubuntu, but i can not set 1024x768 resolution. it's hard to do anything in 640x480. i'm using mainboard intel 946gz.

anyone help me plz.

thanks!

---

### Post by Pumalite on 2007-07-09
What's your graphics card? What drivers are you using. Give your specs.

---

### Post by thanhthanh on 2007-07-09
my graphic card is intel 946gz express chipset. I dont know how to install graphic card driver in ubuntu. can you show me ?
thank u very much.

---

### Post by Pumalite on 2007-07-09
That's your motherboard. Do you have integrated video?

---

### Post by Gremlinzzz on 2007-07-09
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Graphics_Card](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Graphics_Card)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)
use the guide sometimes it helps.:guitar:

---

### Post by confused57 on 2007-07-09
> **thanhthanh said:**
> my graphic card is intel 946gz express chipset. I dont know how to install graphic card driver in ubuntu. can you show me ?
thank u very much.
Open a terminal(Applications---Accessories---Terminal), post the output of:
```
lspci
```
this will show which graphics card/chipset you're using, then someone can help you

---

### Post by thanhthanh on 2007-07-09
Yes, my MB have integrated video. And details of my chipset below :

00:00.0 Host bridge: Intel Corporation 82946GZ/PL/GL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82946GZ/GL Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
04:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)

so hard to do anything. everything so big ~^^~

---

### Post by thanhthanh on 2007-07-09
> **Gremlinzzz said:**
> [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Graphics_Card](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Graphics_Card)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)
use the guide sometimes it helps.:guitar:

it's show how to correct resolution of the graphic installed driver (945,915.....). i think my system didnt install graphic driver.

---

### Post by confused57 on 2007-07-09
The 2nd link that Greminlinzzz gave you has this guide that may help:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

You're probably using the i810 video driver...to check this, open a terminal(Applications---Accessories---Terminal), enter:
```
gedit /etc/X11/xorg.conf
```
scroll down to the video device section & check that the video driver is "i810"...if it is, then you can try installing the 915resolution.

Here's another guide that may help:
[http://ubuntuforums.org/showthread.php?t=269052](http://ubuntuforums.org/showthread.php?t=269052)

---

### Post by Wim Sturkenboom on 2007-07-09
Edit your xorg.conf.

Open a terminal
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo nano /etc/X11/xorg.conf

```
The first command creates a backup of the current configuration
nano is an editor and considered more user-friendly than vi; use <ctrl>w to search in the file.

1) videocard driver
Locate the *section "Device"* and change the *driver* to i810 (if it's not already).

2) monitor settings
Locate the *section "Monitor"* and make sure that *VertRefresh* and *HorizSync* reflect the capabilities of your monitor.

3) resolution settings
Locate the *section "Screen"* and check the *DefaultDepth*. It's usually 24.
Next Locate the *subsection "Display"* that has a *Depth* that is identical to the DefaultDepth. Check the resolutions (modes); remove the ones that are not supported.

4)
Save the file by pressing <ctrl>X

5)
Restart the x-server (using the key combination <ctrl><alt><backspace>).


This should do the trick. To revert (in case something does not work), press <ctrl><alt><F1> (or F2 or F3 ...) and login.
Copy the backup back
```

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

```
And restart the x-server.

Example from my config (for a matrox card and iiyama monitor); you more than likely can [COLOR="Red"]not[/COLOR] use the values shown below.

```
Section "Device"
        Identifier      "Matrox Graphics, Inc. MGA G400 AGP"
**        Driver          "mga"**
        BusID           "PCI:1:0:0"
        Option          "OldDmaInit"            "True"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
[B]        HorizSync       27.0 - 96.0
        VertRefresh     50 - 160
[/B]EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Matrox Graphics, Inc. MGA G400 AGP"
        Monitor         "Generic Monitor"
[B]        DefaultDepth    24
[/B]        ....
        ....
        SubSection "Display"
                Depth           24
[B]                Modes           "1280x960" "1152x864" "1024x768" "800x600" "640x480"
[/B]        EndSubSection

```

---

