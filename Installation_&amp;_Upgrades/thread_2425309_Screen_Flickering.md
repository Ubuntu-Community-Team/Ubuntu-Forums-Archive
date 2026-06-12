---
title: "Screen Flickering"
date: 2019-08-23
forum: Installation &amp; Upgrades
---

### Post by daudiihhdau on 2019-08-23
[COLOR=#000000]
[LIST]
[*]Hello,

I hope you can help me.
My second screen is flickering after my last ubuntu update.
And the screen resolution of my second screen is very low.

Here are some information about my system:

```

cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu 18.04.3 LTS"

uname -a  
Linux Sam 4.15.0-58-generic #64-Ubuntu SMP Tue Aug 6 11:12:41 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 09)
    Subsystem: CLEVO/KAPOK Computer Haswell-ULT Integrated Graphics Controller [1558:8400]
    Kernel driver in use: i915

env | grep DESK
DESKTOP_SESSION=gnome-flashback-compiz
XDG_SESSION_DESKTOP=gnome-flashback-compiz
XDG_CURRENT_DESKTOP=GNOME-Flashback:GNOME
GNOME_DESKTOP_SESSION_ID=this-is-deprecated

```

Thank you for your help :-)
[/LIST]
[/COLOR]

---

### Post by daudiihhdau on 2019-09-03
Bump

---

