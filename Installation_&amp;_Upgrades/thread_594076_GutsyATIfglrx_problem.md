---
title: "Gutsy/ATI/fglrx problem"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by nisseman on 2007-10-27
I had the fglrx driver working without problems in fiesty. After an upgrade to gutsy i only had the mesa driver. The proprietary driverin the restricted-modules did not work on my ATI Mobility Radeon 9700.

I managed to get the the ATI driver installed using this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.41.7_Driver_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.41.7_Driver_Manually")
as suggested here:
[http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2007-10/msg02645.html]("http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2007-10/msg02645.html")

The driver seems to be installed correctly, I do get direct rendering: yes and the ATI instead of mesa, and do NOT get the 'Xlib: extension "XFree86-DRI" missing on display ":1.0"' line.

My problem is that as soon as i start anything that requires a bit of graphic the machine just crashes, sometimes the screen freezes and I can do nothing, other times it turns black. Only fix is a hard reboot.

I do not know which files or output from commands I should post, so please just post which you want to see if you think you can help me.

---

### Post by cow_racer on 2007-10-27
> **nisseman said:**
> I had the fglrx driver working without problems in fiesty. After an upgrade to gutsy i only had the mesa driver. The proprietary driverin the restricted-modules did not work on my ATI Mobility Radeon 9700.

I managed to get the the ATI driver installed using this guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.41.7_Driver_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.41.7_Driver_Manually")
as suggested here:
[http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2007-10/msg02645.html]("http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2007-10/msg02645.html")

The driver seems to be installed correctly, I do get direct rendering: yes and the ATI instead of mesa, and do NOT get the 'Xlib: extension "XFree86-DRI" missing on display ":1.0"' line.

My problem is that as soon as i start anything that requires a bit of graphic the machine just crashes, sometimes the screen freezes and I can do nothing, other times it turns black. Only fix is a hard reboot.

I do not know which files or output from commands I should post, so please just post which you want to see if you think you can help me.

I have this problem when I have xgl running. 

I turn turn xgl off when I need to play game.  you need xgl for compiz to work.

---

### Post by nisseman on 2007-10-28
> **cow_racer said:**
> I have this problem when I have xgl running. 

I turn turn xgl off when I need to play game.  you need xgl for compiz to work.

That is not the same situation as I do not have xgl running, and I have removed compiz in an attempt to get my 3D working.

---

