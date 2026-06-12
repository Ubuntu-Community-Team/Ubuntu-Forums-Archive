---
title: "Upgrade to 12.10 - Boot stuck at &quot;Checking Battery Status&quot;"
date: 2013-02-03
forum: Installation &amp; Upgrades
---

### Post by benmarshalll on 2013-02-03
Hi,

I have a media server set up (xbmc)  that was running Ubuntu 11.04 until a few days ago. With the latest release of xbmc i planned to upgrade to the latest ubuntu as well.

I moved to 11.10 with no problems and updated xbmc, everything ran smooth for a few days. I then moved through 12.04 and on to 12.10. I did these upgrade essentially one straight after the other. All upgrades were done over ssh as the server is hidden and plugged into only a hdtv. What this means is that i am not sure where in the upgrade, 12.04 or 12.10 things went wrong.

The system seems to be fully functioning with most services started however xbmc wont load (set to do so on boot), Manually starting it results in an error saying it can't connect to the the x server.

When i set the server up on 11.04 i stripped out gdm and all non-essential graphical stuff as xbmc is the only software i needed to provide any gui.

From my research i believe i have issues with graphics drivers and have tried to resolve the issue a few different ways. Purging any existing nvidia drivers and installing various ones form the repositories and the latest from the NVIDIA site, none of which work. I have made sure i have the correct version of linux-headers-generic, i have tried falling back to ubuntu default drivers. Other posts mention lightdm, however this is not on my system (i imagine because gdm was not installed before the upgrade).

If anyone could help me out that would be fantastic. I will put a few bits of info about my system below and know my well round ubuntu reasonably so should be able to supply any additional debug or log info needed.

Cheers,
Ben

Output from lspic: [http://pastebin.com/jiwSgwqF](http://pastebin.com/jiwSgwqF)

/var/log/boot.log: [http://pastebin.com/02zh25fN](http://pastebin.com/02zh25fN)

Xorg.conf: [http://pastebin.com/c5rmw9JV](http://pastebin.com/c5rmw9JV)

---

### Post by MAFoElffen on 2013-02-03
If you check /var/log/Xorg.0.log, I believe you will find that you are hanging during your nvidia video driver load. That step, timing wise, occurs concurrently in background between the term message "checking battery status" and the one about checking system 5 compatability...

What is going on is that the old video driver was most likely compiled (installed) on a previous kernel version.

You didn't post which nvidia card or monitor you are using but just modify the driver package name in the instructions below to apply to the appropriate hardware. If you aren't certain about your specific hardware, please visit Post #2 of the sticky link below to find out how to query what those are. 

An easy fix would be to start the rescue menu, try low-graphics mode, go gui and remove the driver... then reinstall it. Another would be to start the rescue menu, go to a root prompt, rename your xorg.conf to something else
```

mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```
Then restart, remove/reinstall your driver.

This way would be to do it manually from the root prompt from the rescue menu. 
```

apt-get remove nidia*
apt-get install nvidia-current
nvidia-xconfig

```
Reboot

All the detailed instructions for these are in my sticky:
[Sticky: [all variants] Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")
Feel free to visit it for reference.

---

### Post by benmarshalll on 2013-02-03
Thanks,

Problem solved.

Issue was with xbmc init method proving to be incompatible with upgraded ubuntu.

---

