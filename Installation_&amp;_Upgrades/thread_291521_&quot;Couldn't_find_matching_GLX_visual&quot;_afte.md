---
title: "&quot;Couldn't find matching GLX visual&quot; after 6.10 install."
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by adair on 2006-11-02
I've installed 6.10 + nvidia-glx-legacy, etc. X seems to be working fine, but when I try to start BZFlag I get the following message:

$ bzflag
Could not set Video Mode: Couldn't find matching GLX visual.
Error creating window - Exiting

I've tried some likely solutions off the message boards but they've either crashed X or had no effect.

Just for the record this is the contents of the 'Modules' section from xorg.conf:

Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"

Has anyone got any suggestions?

Thanks and regards, Adair.

---

