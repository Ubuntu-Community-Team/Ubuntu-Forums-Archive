---
title: "Xorg.conf at default after upgrade to 12.04 LTS"
date: 2012-12-17
forum: Installation &amp; Upgrades
---

### Post by aplonis on 2012-12-17
After upgrading from 10.04 LTS to 12.04 LTS my Xorg.conf is reduced to only just this...

[COLOR="Red"]Section "Monitor"
   Identifier    "Monitor0"
   HorizSync 30-82
   VertRefresh 50-75
EndSection

Section "Device"
   Identifier    "Device0" 
EndSection  

Section "Screen"     
   Identifier    "Screen0" 
   Device        "Device0"     
   Monitor       "Monitor0"
EndSection[/COLOR]

...and is preventing this...

[COLOR="Red"]sudo apt-get install -f[/COLOR]

...from working to fix some other broken packages because the broken ones are dependent on Xorg. Or so reports the text in the CLI.

How do I address that please?

The monitor which I have is an **HP 2159m** since I'm sure that's important. Things were mostly fine before I went for the update from 10.04 LTS to 12.04 LTS, all except for Handbrake, which had stopped working right.

---

