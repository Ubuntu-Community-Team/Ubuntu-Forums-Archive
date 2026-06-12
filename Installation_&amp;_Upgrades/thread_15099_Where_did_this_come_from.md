---
title: "Where did this come from?"
date: 2005-02-11
forum: Installation &amp; Upgrades
---

### Post by gclarkso on 2005-02-11
Hi,

Just successfully installed Warty on a IBM T-21 and after the GUI boots, there is a a 1/2" "X" in the middle of the screen that I can't delete (the cursor goes behind it!) I have no other screen abnormalities. 

I have searched for a solution to no avail. Has anyone else experienced this?

---

### Post by Jad on 2005-02-12
hmm can you attach a screenshot ?

---

### Post by gclarkso on 2005-02-12
[QUOTE=Jad]hmm can you attach a screenshot ?[/QUOTE]

Weird...it doesn't show up on a screenshot. Meaning...I'm one step closer!

---

### Post by zabilcm on 2005-02-12
You need to edit your /etc/ X11/XF86Config-4 and add a line called 

Option          "HWCursor"              "false"


Under 

Section "Device"


Mine looks like

```
Section "Device"
        Identifier      "S3 Inc. VT8636A [ProSavage KN133] AGP4X VGA Controller (TwisterK)"
        Driver          "savage"
        BusID           "PCI:1:0:0"
        Option          "UseFBDev"              "true"
        Option          "HWCursor"              "false"
        Option          "SWCursor"              "true"
EndSection

```

---

### Post by WW on 2005-02-13
[http://www.ubuntulinux.org/support/documentation/faq/hwcursor](http://www.ubuntulinux.org/support/documentation/faq/hwcursor)

---

