---
title: "upgrade issue with switch from 16.04 to 18.04 64 bit"
date: 2018-11-06
forum: Installation &amp; Upgrades
---

### Post by mikealte2468 on 2018-11-06
I am somewhat new to Ubuntu.

earlier in the year I built this system using Gigabyte GA-z270p-d3 motherboard. With help from this forum I found a video driver from Nvidia that worked - driver file name NVIDIA-Linux-x86_64-390.25.run . Now that I upgraded to 18.04 that driver appears to  be 'broken'. All I see is part of the desktop with no way to change resolution.

I have explored the Nvidia website and the only drivers I can find are NVIDIA-Linux-x86_64-340.107.run  or similar of the 340 series.

I am going to post this message on the Nvidia forum.

Hopefully some one will have some ideas what to do / where to turn.

---

### Post by him610 on 2018-11-06
If you can boot your system, please show us its details between the code tags...
```
inxi -F
```

---

### Post by deadflowr on 2018-11-06
Ubuntu pacages nvidia drivers ready to use.
To enable go to open Software and Updates
go to Additional Drivers
Select the nvidia driver you would want to run and click Apply Changes to install.
When done reboot.
After rebooting you should have a new app for nvidia settings.
You can open that to configure whatever settings need to be set
(then click save configuration to save what changes you set.)

The Packaged drivers for nvidia Ubuntu packages are the nvidia drivers from nvidia, simply package to work correctly on Ubuntu.

---

### Post by mikealte2468 on 2018-11-08
deadflowr,

Thanks. Unfortunately, the system doesn't recognize the monitor I am using - asus wx24a LCD connected though a HDMI cable / connector. I still can't change the resolution.

There wasn't a problem with 16.04 Ubuntu. Since hardware is constantly changing, it might be a good idea to allow the o/s to be somewhat 'forgiving' of h/w changes. I have this monitor for more than 2 years.

---

### Post by dinkidonk on 2018-11-08
If you can enter the GRUB menu (by holding shift during boot) then highlight the used boot option (usually pre-selected) and press "e" on the keyboard. Add "nomodeset" to the first command (before "quiet splash") and boot your system by pressing CTRL+X. If this is possible, you should be able to update your nvidia driver - or at least get info from the system needed to fix your issue.

Look at the first reply here for a graphical instruction: [https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu](https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu)

---

### Post by deadflowr on 2018-11-08
Perhaps peruse the troubling shooting wiki:
[https://wiki.ubuntu.com/X/Troubleshooting/Resolution]("https://wiki.ubuntu.com/X/Troubleshooting/Resolution")

---

### Post by mikealte2468 on 2018-11-11
deadflowr and[FONT=arial] dinkidonk,

Thanks. For what ever reason the issue solved itself. I wound up booting a couple of times ( kept missing entry to grub) then booted 3rd time - missed again and system came up with a high resolution screen. Was able to set screen to more comfortable character size. I'm going to leave this thread open for a couple of days in case anyone wants to add additional comments.[/FONT][U][URL="https://ubuntuforums.org/member.php?u=2100547"][COLOR=#000000]


[/COLOR][/URL][/U]

---

