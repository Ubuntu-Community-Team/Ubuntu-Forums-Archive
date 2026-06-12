---
title: "Unity not working after upgrade"
date: 2014-04-24
forum: Installation &amp; Upgrades
---

### Post by benjamin-cartereau on 2014-04-24
I have been using Ubuntu 12.04 LTS for quite a few years without much problems.
My laptop has an ATI Mobility Radeon HD 5470.
I was using fglrx proprietary driver. Usually after kernel upgrades I had to reinstall the last version of the driver.
A few weeks ago I have decided to process a full upgrade.
Upgrading to the 12.10 version went just well. Then I did try to upgrade to 13.10. 
Upgrade went well but once logged in, only the desktop and icons on it are visible.
Unity (panels, launcher, windows decorations...) does not look to work.
A few days ago I gave a try to the 14.04 version but it has not fixed the issue.
Unity still looks KO.
I tried many fixes from different sites (for example : [http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html?m=1](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html?m=1) or [http://doc.ubuntu-fr.org/radeon](http://doc.ubuntu-fr.org/radeon)...) but none of them fixed it.
- /usr/lib/nux/unity_support_test -p
```

Not software rendered: yes
Not blacklisted: yes
GLX fbconfig: yes
GLX texture from pixmap: yes
GL npot or rect textures: yes
GL vertex program: no
GL fragment program: yes
GL vertex buffer object: yes
GL framebuffer object: yes
GL version is 1.4+: yes

Unity 3D supported: no

```
- lshw -c video
```
*-display
         description: VGA compatible controller
         produit: Park [Mobility Radeon HD 5430/5450/5470]
         fabricant: Advanced Micro Devices, Inc. [AMD/ATI]
         identifiant matériel: 0
         information bus: pci@0000:01:00.0
         version: 00
         bits: 64 bits
         horloge: 33MHz
         fonctionnalités: pm pciexpress msi vga_controller bus_master cap_list rom
         configuration: driver=radeon latency=0
         ressources: irq:46 mémoire:c0000000-cfffffff mémoire:d0020000-d003ffff portE/S:d0000(taille=256) mémoire:d0000000-d001ffff

```

Of course I have removed fglrx driver and I am using the provided open source (and recommanded) driver...

Here are some things I have checked...:



[LIST]
[*]"unity" package is installed (dpkg -l | grep unity)
[*]"ubuntu-desktop" is installed
[*]"compiz" is installed
[*]Under CCSM, I have checked that "Ubuntu Unity Plugin" is checked
[/LIST]



... and tried :
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
```
unity --reset-icons
```
```

gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
rm ~/.compiz-1/session/*
rm ~/.config/compiz-1/compizconfig/config

```
```
dconf reset -f /org/compiz/
```


Trying to connect as a new user did not make the trick neither...

Tell me if I should move this thread to the Desktop Environments sub-forum?

Thank you for any help/advice you could give me.

---

### Post by benjamin-cartereau on 2014-05-20
After trying many many workarounds found all over the internet, I did not find any fix.
Eventually, I did boot with the live version of Ubuntu 14.04 on a USB key.
I have tried the first option : "Reinstall Ubuntu 14.04" (which keeps personnal data). But it did not fix the issue. Launcher, windows decorations, ... were still missing.
After a full backup of my personal data, I then tried the second option : "Erase Ubuntu 14.04 and reinstall". Of course that did the trick and the fresh version of Ubuntu was working just fine. The good thing is that I used to have my personal data (/home) on a separate partition. The installation did not use that particular partition for the "/home". And I have been able to retrieve all my data easily...

Cheers

---

