---
title: "Black screen after 7.04 clean install"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by joemilx on 2007-06-06
I installed Fiesty (how prophetic!) using the AMD 64 version and got a black screen on boot-up.  However, if I select the recovery option on start-up, then enter exit at the prompt, it boots to the sign-in screen without incident.

I've looked at helps and the forums and, as a rookie, have no idea how to proceed.  Any ideas will be appreciated.  Thanks in advance.



ASUS A8V-VM, AMD 64 4000+, 2GB DDR400, (4) Seagate 160GB SATA-2, Optiarc 16x burner

---

### Post by mlind on 2007-06-06
What graphics card do you have? What drivers are you using in /etc/X11/xorg.conf for your card ?

The most common way to solve similar problems is to reconfigure xserver and let it detect hardware again
```

sudo dpkg-reconfigure xserver-xorg

```

The other one could be to disable bootsplash, but you probably overcome this issue by changing the gfx card's driver.

---

### Post by joemilx on 2007-06-07
Using a Radeon X850.  Tried the  reconfigure with no luck:same black screen on reboot.  Is there an alternate driver that I should load?

---

### Post by mlind on 2007-06-07
> **joemilx said:**
> Using a Radeon X850.  Tried the  reconfigure with no luck:same black screen on reboot.  Is there an alternate driver that I should load?

You have two choices, opensource ati/radeon driver and proprietary fglrx driver. Your gfx card sounds very new which is probably issue for opensource driver.

Try out fglrx driver, it hopefully solves your issues
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I suggest not to run the aticonfig that wiki article describes, intead modify the /etc/X11/xorg.conf manually.

Here's the relevant part of the configuration
```

Section "Device"
        Identifier      "ATI RADEON 9550"
        Driver          "**fglrx**"
        BusID           "PCI:1:0:0"
        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "off"
        Option          "backingstore"  "true"
EndSection

```
BusID maybe different for you. You the entry you currently have in /etc/X11/xorg.conf.

---

### Post by Silenus on 2007-06-07
ATI radeon line has issues with the installation of any linux distro, I found that the only distro that works with the ati card I have is Knoppix-Std. Although, wait if you have an oboard card, switch to onboard on bios, then plug your monitor to onboard card, and boot, let us know the results. Also what video driver are you using? 
cat /etc/X11/xorg.conf

Paste results here.

---

### Post by crjackson on 2007-06-09
> **joemilx said:**
> I installed Fiesty (how prophetic!) using the AMD 64 version and got a black screen on boot-up.  However, if I select the recovery option on start-up, then enter exit at the prompt, it boots to the sign-in screen without incident.

I've looked at helps and the forums and, as a rookie, have no idea how to proceed.  Any ideas will be appreciated.  Thanks in advance.



ASUS A8V-VM, AMD 64 4000+, 2GB DDR400, (4) Seagate 160GB SATA-2, Optiarc 16x burner

I'm watching your thread with great interest.  I have the same problem with my ATI x800 XL.  I couldn't even load the live cd at first.  Then I found that if I hit the F4 and change the screen resolution to 640x480 the install was quick and uneventful.  MAN...  Then I rebooted and found as you did, the black screen of death.  Just like you, I also found that booting into recovery mode followed by a quick EXIT, the system ran just fine.

NOW HERE THIS...  I installed the x86 (32bit) version, install was flawless, operation IS flawless, no issues, restricted ATI driver from repository enabled.

The system (32bit) feels slightly slower than the A64 version.  I have backed up my system using disk images which I can load in under 2 minutes so I'm playing with both while working config. issues, and relying on the dreaded (but optimal performance) of XPpro.

Please let me know if you can get this worked out.  I'm planning to poking around some time in the next week or so, to see if I can solve the issue.  If I come up with a fix, I'll let you know what it was...

---

### Post by crjackson on 2007-06-09
> **Silenus said:**
> ATI radeon line has issues with the installation of any linux distro, I found that the only distro that works with the ati card I have is Knoppix-Std. Although, wait if you have an oboard card, switch to onboard on bios, then plug your monitor to onboard card, and boot, let us know the results. Also what video driver are you using? 
cat /etc/X11/xorg.conf

Paste results here.

Every Linux distro I've tired has worked fine as far as the install process and boot process - No black screen, EXCEPT ubuntu A64.  Maybe was just lucky. ;)

---

### Post by mlind on 2007-06-09
I guess crjackson is right, A64 arch is still bit 'exotic' in some cases.

---

### Post by joemilx on 2007-06-11
Been away for a few days.  Thanks for the replies.

I'm just about to revert to the 32 bit Feisty.  Far too much fiddling to get the 64 bit version functioning.  I've put in over 20 hours with few successes.

---

### Post by joemilx on 2007-06-14
Loaded 32-bit Feisty: NO BLACK SCREEN!  However, now I'm having a lot of fun with Wireless on an Atheros chipset (D-LINK DWL-510).  Got it to work with WPA after a lot of fiddling, but shows very low signal strength compared to same card on Windows XP.  Well, back to the Wireless threads for a solution, I hope.

Again, thanks for the help.  I'll wait a few months before trying 64-bit again.

---

