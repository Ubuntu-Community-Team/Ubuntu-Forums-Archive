---
title: "Problems after upgrade from 17.10 to 18.04"
date: 2018-06-12
forum: Installation &amp; Upgrades
---

### Post by rpiotr.sk on 2018-06-12
[COLOR=#111111][FONT=Ubuntu]I tried to upgrade Kubunutu 17.10 to 18.04, and now I'm in trouble :( Upgrade process ended with message[/FONT][/COLOR]
```
"Your system could be in an unusable state." 
```
[COLOR=#111111][FONT=Ubuntu]After reboot got blank screen. After some investigation I realized that problem is connected with graphics driver - when I add 'nomodeset' to grub options it boots, but is terribly slow. I am using Radeon R9 270x and amdgpu driver. When I try to start without nomodeset (and also without quiet to see the messages) boot process seems to stop with following message:[/FONT][/COLOR]
```
fb: switching to amdgpudrmfb from VESA VGA
```
[COLOR=#111111][FONT=Ubuntu]But in the background it continues, as I can see later in the syslog. I tried to reinstall Xorg and libdrm-amdgpu1, but it didn't help. Help please :)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Regards, Piotr[/FONT][/COLOR]

---

### Post by rpiotr.sk on 2018-06-12
[COLOR=#111111][FONT=Ubuntu]I have an update. I tried to boot in text mode (I mean pure text console, no framebuffer) and then start gui with startx. Xorg started and seems working properly. So probably graphics driver as such works. So now the question is why it doesn't work when booting directly ?[/FONT][/COLOR]

---

