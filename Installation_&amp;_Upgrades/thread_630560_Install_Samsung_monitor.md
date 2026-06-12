---
title: "Install Samsung monitor"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by GeertPoels on 2007-12-03
I purchased a Samsung 2232BW.
Somewhere I read about doing a "sudo dpkg-reconfigure xserver-xorg".
A lot of parameters were, some of which I found nothing on the internet.
The monitor seems to be running ok.
Isn't there an easier and more correct way of configuring a display ?

BTW : I wrote an e-mail to Samsung yesterday, suggesting them to supply minimal Linux support.
They bluntly answered that Linux wasn't supported :confused:

---

### Post by jbt on 2007-12-05
> **GeertPoels said:**
> I purchased a Samsung 2232BW.
Somewhere I read about doing a "sudo dpkg-reconfigure xserver-xorg".
A lot of parameters were, some of which I found nothing on the internet.
The monitor seems to be running ok.
Isn't there an easier and more correct way of configuring a display ?


Yes, go to System->Administration->Screens and Graphics

You can select you Monitor from there.
If it doesn't appear on the list, then choose Generic LCD Panel of the correct size.

[It may also be an idea to backup /etc/X11/xorg.conf - just in case you make a mistake]

JohnT

---

### Post by GeertPoels on 2007-12-19
These are my current settings.
Is that all there is to configuring a monitor ??

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
        HorizSync       30-81
        VertRefresh     56-75
EndSection

---

### Post by Pumalite on 2007-12-19
If 17" run of the mill LCD, you can just connect it. The image adjust itself. I just did it. A Samsung SynMaster 740N

---

### Post by jbt on 2007-12-20
> **GeertPoels said:**
> These are my current settings.
Is that all there is to configuring a monitor ??

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
        HorizSync       30-81
        VertRefresh     56-75
EndSection

You may not even need the HorizSync and VertRefresh.

Regards
JohnT

---

### Post by itaylor on 2008-01-07
After much struggling, I finally installed the xserver-xorg-video-intel driver to replace the i810 and then got my Samsung 2232BW to work (as external monitor to Thinkpad Z61t running Gutsy).

---

