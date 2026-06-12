---
title: "Isssues with 11.04 and Diamond ATI Radeon 9250 Graphics Card"
date: 2011-07-09
forum: Installation &amp; Upgrades
---

### Post by sscot600 on 2011-07-09
Hello everyone,
I just installed 11.04 on a brand new hard drive today on a Dell E520 and everything worked out great except my video card wont work.  When I take it out and use the on board graphics through my motherboard, i can boot up fine and see everything but when I put it in, nether the onboard graphics or the video from the card have a signal.  Is there a driver that I need to install or some settings that I need to change for it to recognize it? The card is a Diamond ATI Radeon 9250 Graphics Card.

---

### Post by Duncan Williams on 2011-07-10
check all your bios settings.
switch of your onboard graphics in bios.

---

### Post by sscot600 on 2011-07-10
I checked my BIOS and since it is a Dell, there isnt much to the BIOS.  I found the video section and there was one option to have onboard/PCI graphics or AUTO.  I tried enabling one or the other but bolth options didn't change anything, still no signal on onboard and on the card.

---

### Post by Duncan Williams on 2011-07-11
if its not getting recognised in the bios.
then you need to fix that issue.
if you could borrow another video card, and try that, for example.
(to determine if it's the card or not)

---

### Post by Mark Phelps on 2011-07-11
There are no restricted video drivers that will work with your Diamond card and any Ubuntu versions newer than 8.10.  ATI dropped Linux driver support for those cards years ago.

With switchable graphics, folks using 11.04 have reported that, in order to see the Diamond card, you have to be able to disable the onboard graphics -- which, in many cases, you can not do.

If yours has that problem, you're stuck using the onboard graphics.

---

### Post by sscot600 on 2011-07-11
This computer had windows XP on it the video card worked without having to mess with the BIOS.  So there isnt any driver that I can install or program that I can install into Ubuntu 11.04 for it to recognize it?  Oh and I forgot to mention, I installed ATI binary X.org driver from the ubuntu software center and after I rebooted, I was able to get a signal from the onboard graphics while my video card was installed, but still no luck from the card.

---

### Post by MAFoElffen on 2011-07-11
> **Mark Phelps said:**
> There are no restricted video drivers that will work with your Diamond card and any Ubuntu versions newer than 8.10.  ATI dropped Linux driver support for those cards years ago.

[COLOR=Red]With switchable graphics[/COLOR], folks using 11.04 have reported that, in order to see the Diamond card, you have to be able to disable the onboard graphics -- which, in many cases, you can not do.

If yours has that problem, you're stuck using the onboard graphics.
1. [COLOR=Red]This motherboard doesn't have switchable (hybred) graphics:[/COLOR]
> integrated Intel® Graphics Media Accelerator X3000 (Intel® GMA X3000)... so the question should be that if he set the BIOS to auto, if it saw the additional card, it should turn the onboard graphics chip off...  You can confirm what linux see's via
```

sudo hwinfo --framebuffer
lspci -nn | grep VGA

```If it reports that there is no command hwinfo, please install it... via
```
sudo apt-get install hwinfo

```2. "nomodeset" works for nvidia, not for Radeon... So he could use be using a "radeon.mode=1" switch in his kernel boot line...

3. Yes- The 9200 series is not supported anymore by ATI, but- It should be using the Ubuntu / Xorg opensourced Radeon dirver ( [xserver-xorg-video-radeon_6.14.0-0ubuntu4_i386]("https://launchpad.net/ubuntu/natty/+package/xserver-xorg-video-radeon")) and should be connected to that from xorg.conf file > Section Device > Driver Radeon... 

4. If it was an upgrade that changed this, it should have an xorg.conf file already that you can check or edit.  If it doesn't exst, go to a terminal and type in " sudo xorg --configure" and it will create a vanilla xorg.conf file.

5.  These instructions all assume that you can boot into a text console... since you have no graphics...  Follow the instructions from the first 3 post of this sticky to help you out:
**[B]Sticky:**[/B]                                      [COLOR=#008C00]**[all variants]**[/COLOR]                          [Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")
Concentrate on booting the kernel into a text console mode (in Post 1) or booting from a Livecd and mounting the installed system (Post 3).... so you can access, diagnose and make changes to your system.

---

### Post by sscot600 on 2011-07-11
Ok I have been trying a few of your tips and when I went into the bios and changed it to AUTO, the video signal started to go out of the card!  But how do I know it is running properly so that I can do the visuall effects and play some games?

---

### Post by Mark Phelps on 2011-07-12
> **sscot600 said:**
> Ok I have been trying a few of your tips and when I went into the bios and changed it to AUTO, the video signal started to go out of the card!  But how do I know it is running properly so that I can do the visuall effects and play some games?

Sorry to be repetitious -- but, as I said before -- you can't!

Linux driver support for the Radeon 9xxx series was dropped YEARS ago.  All you'll get now is the default open-source driver -- which, if you're seeing a desktop, you already have installed.

---

### Post by sscot600 on 2011-07-12
Ok I have another issue that i ran into.  when i log off to change to a different user or to shut down, all that is desplayed is a bunch of distorted lines.  any way to fix this?

---

