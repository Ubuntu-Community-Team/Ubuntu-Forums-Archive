---
title: "VGA Resolution when connected to Projector"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by textguru on 2006-12-28
I have setup dapper using 1024 x 768 resolution. When connected to a multimedia projector, resolution was changed to VGA or 640 x 480. The projector actually can be used on XGA mode (tested on Windows) and I dont know why the resolution is changed to 640 x 480 when Ubuntu is being used. Any suggestions?

:confused:

---

### Post by textguru on 2007-01-01
Hoping for your response on my inquiry. I badly needed this.

---

### Post by Wim Sturkenboom on 2007-01-02
Check your xorg.conf. Not sure what to change but your system uses 'safe' settings as it does not recognize the projector.

If you have an nvidia card, the following might do the trick
```

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    **Option         "UseEdidFreqs" "false"**
EndSection

```

---

### Post by textguru on 2007-01-02
I have tried it and still the resolution is VGA. here are some lines of the xorg.conf:

```
Section "Device"
        Identifier      "ATI Technologies, Inc. 3D Rage Pro AGP 1X"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "UseEdidFreqs" "false"
EndSection

Section "Monitor"
        Identifier      "5En"
        Option          "DPMS"
EndSection

```

Any other suggestions?

---

### Post by textguru on 2007-01-02
I have tried some experiments. I initially connect my PC to monitor to preserve  the screen resolution. The screen resolution works on 1024x768 when connected to monitor, and transfer the video output while its powered on to projector and I made an XGA (or 1024x768) resolution to projector. But when I directly restart the PC where video was connected to the projector, the screen resolution returns to VGA (or 640x480). I have conclude that there is something to do with the screen refresh that made ubuntu not to change screen resolution to the right settings. Is it ubuntu cannot refresh the display or the projector?

---

### Post by Wim Sturkenboom on 2007-01-02
As I said, it uses safe settings as it does not recognize the (capabilities of the) projector. I'm not familiar enough with X to give a reliable advice in this case but I would try to add a modeline in the monitor section.

Search for modeline calculator using google (i.e. [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl) and fill in resolotion and vertical refresh rate)

---

