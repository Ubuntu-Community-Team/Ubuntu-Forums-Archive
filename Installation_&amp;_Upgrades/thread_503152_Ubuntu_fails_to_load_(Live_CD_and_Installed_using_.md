---
title: "Ubuntu fails to load (Live CD and Installed using Alternative CD)"
date: 2007-07-17
forum: Installation &amp; Upgrades
---

### Post by madlan on 2007-07-17
I have been told to post here (from the noob forum)
[http://ubuntuforums.org/showthread.php?p=3030116](http://ubuntuforums.org/showthread.php?p=3030116)

I attempted to load the live CD - menu loads fine, I select load/install, loading screen does its thing, then the screen switches off.

Caps/Num lock do not function (locked up?)

Is there anything I can do to get the deskop up?



Intel Quad core QX6700 2.66 GHz CPU
EVGA 8800GTX Graphics
4GB CM2X1024-8500C5D RAM
2X 150GB 10K RPM Raptors RAID 0 Hard Drives
24" Dell 2407WFP Monitor

---

### Post by loserboy on 2007-07-17
99% sure it's your 8800 card, theres numerous workarounds for it, try searching " 8800 and feisty" or "howto 8800"  something like that.... if you can't find anything let me know.

One thing you can try is safe graphics mode, the option just below start/install

---

### Post by dabl on 2007-07-17
Loserboy is correct.  At a high level, here is what you need to do:

- install Ubuntu in VGA/text mode, choose "VESA" as your display type (do NOT let it autodetect your card!)

- once running correctly as a VESA display, download and install Envy from here:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

- use Envy to install the latest Nvidia driver -- your card needs the 100.14.11 version

Then you should be up and running with the accelerated graphics.  :popcorn:

---

### Post by loserboy on 2007-07-17
> - install Ubuntu in VGA/text mode, choose "VESA" as your display type (do NOT let it autodetect your card!)

you're saying he needs to download the text only .iso (Alternate install) right?

[http://releases.ubuntu.com/7.04/](http://releases.ubuntu.com/7.04/)

---

### Post by Pumalite on 2007-07-17
Beware of the Raid 0 problem:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by loserboy on 2007-07-17
madlan, would you do me a favor and test this for me, it has the potential to save time from having to download another .iso and deal with a text based installer if it works, if it doesnt no harm will be done.

simply follow the steps here [https://wiki.ubuntu.com/EdgyKnownIssues/59618](https://wiki.ubuntu.com/EdgyKnownIssues/59618)

let me know how it goes

---

### Post by dabl on 2007-07-17
> **Pumalite said:**
> Beware of the Raid 0 problem:
]

Yikes -- I missed that!

NO, if you're thinking "Hardware RAID", this isn't going to work.  The drivers for the hardware RAID controllers are proprietary, for Windows only, and there are none for Linux.  There is a way to do a software RAID setup, so I read, using mdadm, but you're own with that.  ):P

---

