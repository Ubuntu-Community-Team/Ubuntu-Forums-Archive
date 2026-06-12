---
title: "Can't install Ati driver on jaunty"
date: 2009-03-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by leprotic on 2009-03-14
Hi. I just installed Jaunty because I had some underscan issue on intrepid (and I must confess I was excited about the new ext4 comments) as a friend suggested for better HW support (I know I am a newbie and shoud have waited for the stable release in april).

I can't install Ati driver (ati-driver-installer-9.2-x86.x86_64.run). I follow the installer notes and smash at the warning below.

Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.28-9-generic; make sure that the version is being
correctly set by --iscurrentdistro

I have 64-bit AMD with 2600XT.

Any help? Thanks already...

---

### Post by gjoellee on 2009-03-14
ATI does not yet have a driver for the new version of Xorg i think

---

### Post by Yashiro on 2009-03-14
There's no working fglrx driver for Jaunty yet.

---

### Post by sdowney717 on 2009-03-14
And no support for x series or lower cards

---

### Post by leprotic on 2009-03-25
How about open source drivers then? Are they supposed to work on Jaunty for 2600 HD?

---

### Post by logograf on 2009-03-25
> **leprotic said:**
> How about open source drivers then? Are they supposed to work on Jaunty for 2600 HD?

Yes. Aren't those used by default?

---

### Post by leprotic on 2009-03-25
I can't get the double screen feature working and there are only two resolution options withe the default state.

---

### Post by krazyd on 2009-03-25
There is now a Jaunty-compatible fglrx driver in the repos.

---

### Post by rbmorse on 2009-03-25
> **krazyd said:**
> There is now a Jaunty-compatible fglrx driver in the repos.

Not for the "X" cards.

---

### Post by psmar on 2009-03-25
I just installed jaunty four days ago (alpha 6 I think) and my ati x1650 worked right out of the box including with compiz, ?? I beleve till  they get the catalyst 9.2 over to Linux there wont be any restricted driver available

---

### Post by krazyd on 2009-03-26
> **rbmorse said:**
> Not for the "X" cards.
Yeah but those have support for 3D, Xv etc. under the open source driver.

---

### Post by screaminj3sus on 2009-03-26
> **leprotic said:**
> How about open source drivers then? Are they supposed to work on Jaunty for 2600 HD?

I am using the open source drivers with an hd2600 and it works fine, even metacity's compisitor works, but I don't believe compiz is. It was really laggy until I used this for my xorg.conf:

```
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
#       SubSection "Display"
#               Virtual 2960 1050
#       EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "ati"
        Option          "AccelDFS" "on"
        Option          "AccelMethod"  "EXA"
        Option          "MigrationHeuristic"  "smart"
        Option          "EnablePageFlip"  "on"
        Option          "EnableDepthMoves"  "on"
        Option          "ColorTiling"  "on"
#       Option          "DisplayPriority"  "HIGH"
#       Option          "DepthBits"  "24"
#       Option          "SubPixelOrder"  "RBG"
#       Option          "DRI" "on"
        Option          "FBTexPercent"  "0"
        Option          "RenderAccel"  "on"
EndSection

Section "ServerFlags"
        Option          "DontZap"       "off"
EndSection  
```

now it's smooth, and videos don't tear like with fglrx.

---

### Post by markharding557 on 2009-03-26
> **krazyd said:**
> Yeah but those have support for 3D, Xv etc. under the open source driver.

they don't work as well though frame rate is much reduced

---

### Post by Reiger on 2009-03-26
> **psmar said:**
> I just installed jaunty four days ago (alpha 6 I think) and my ati x1650 worked right out of the box including with compiz, ?? I beleve till  they get the catalyst 9.2 over to Linux there wont be any restricted driver available

Well then there never will, as the current ATI on Linux is a 9.4 beta. ;) (Installable from the repositories.)

---

### Post by ktp on 2009-03-26
> **screaminj3sus said:**
> I am using the open source drivers with an hd2600 and it works fine, even metacity's compisitor works, but I don't believe compiz is. It was really laggy until I used this for my xorg.conf:

```
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
#       SubSection "Display"
#               Virtual 2960 1050
#       EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "ati"
        Option          "AccelDFS" "on"
        Option          "AccelMethod"  "EXA"
        Option          "MigrationHeuristic"  "smart"
        Option          "EnablePageFlip"  "on"
        Option          "EnableDepthMoves"  "on"
        Option          "ColorTiling"  "on"
#       Option          "DisplayPriority"  "HIGH"
#       Option          "DepthBits"  "24"
#       Option          "SubPixelOrder"  "RBG"
#       Option          "DRI" "on"
        Option          "FBTexPercent"  "0"
        Option          "RenderAccel"  "on"
EndSection

Section "ServerFlags"
        Option          "DontZap"       "off"
EndSection  
```

now it's smooth, and videos don't tear like with fglrx.

That looks just like my xorg.

---

### Post by screaminj3sus on 2009-04-06
> **ktp said:**
> That looks just like my xorg.

thats because it is, i had forgotten the thread i found it in lol.

---

### Post by topcoder on 2009-04-16
Same problem here. Just upgraded to Jaunty an hour back, and have lots of problems with the graphics bit. It refused to boot up with the 2.6.28 kernel, whereas it did boot from the older 2.6.11 kernel. Then, when I uninstalled the ati drivers, the os did boot up. However I now cannot reinstall the ati drivers.

---

### Post by markbuntu on 2009-04-16
Drivers 9.3 and earlier are not compatible with xserver in Jaunty. Driver 9.4 has xserver support but no support for cards in the RV200-RV500 series, ie anything before HD3xxx series. 

If you have one of these cards and attempt to use the restricted driver anyway you will break your system. If you are upgrading from Intrepid remove any restricted driver from ati before upgrading.

Most RV200-500 cards are now fully supported by the open source ati and radeon drivers.

---

### Post by topcoder on 2009-04-17
So does this mean that the HD 3xxx series has support? And when can we expect 9.4 version drivers? By the way, I upgraded without removing the restricted drivers, and now the newer kernel does not boot, and I am forced to use the older kernel. Any way to fix this now?

---

