---
title: "To upgrade or not to upgrade..."
date: 2007-02-01
forum: Installation &amp; Upgrades
---

### Post by Gasp100 on 2007-02-01
I'm a windows system engineer but I really enjoy working with new (preferably free) stuff. I had an old Toshiba Satellite 4090X that was running Windows XP SP2 and was horrendously slow. PII 400Mhz and memory maxed out with 192MB. 
I had installed ubuntu 6.10 on a desktop and it seemed cool (I'm a big vmware guy so I've installed different flavors of Linux in vm's with varying degree's of success). I wanted to streamline the laptop and give it new life by installing something decent, light and quick (and free). I tried to install Ubuntu 6.10 and it would freeze during the installation and just stop responding... weird. SO I downloaded Kubuntu's alternate iso which said it could be installed on machines with less RAM. That went fine, but it did not use my full laptop screen and I could not find ANY info on how to change this... I spent a day on google trying to get the write commands to edit xorg.conf but to no avail. 
Finally I had an old Ubuntu 5.04 install CD so i gave that a shot. It installed fine, screen still too small but I figured I'd hack until I fixed it. Low and behold, the ubuntulinux forum showed me the way with the correct commend to get to the xf86 editor... finally, a freaking MENU. The fix was to change the depth from 24bit to 16bit, rebooted and were good. 
So, onto the wireless card... that was fixed following a great article in Tux magazine (online) for using NDISwrapper. I found the linksys drivers (same ones I would use in Windows XP), followed the directions and all is well. 
So now I go to use the auto updates and the distro is no longer supported. 
My question is... should I tempt fate and try to upgrade to 6.10? If I do this will it overwrite my monitor config? Will it whack my ndiswrapper configuration? Will it complete? Do I need to upgrade from CD or can it do it from online. 
Any help for a super newbie who is a windows guru but wants to learn much appreciated.

---

### Post by aysiu on 2007-02-01
Upgrading from 5.04 to 6.10 is a recipe for disaster. That's three releases you're skipping (Breezy, Dapper, Edgy).

---

### Post by nalmeth on 2007-02-01
> My question is... should I tempt fate and try to upgrade to 6.10? If I do this will it overwrite my monitor config? Will it whack my ndiswrapper configuration? Will it complete? Do I need to upgrade from CD or can it do it from online.
Definately don't jump from 5.04 to 6.10. You have to go from one version up to the next, leap-frogging will cause breakage. 

It will likely whack your ndiswrapper config too. Be ready for that. It's easy to setup though hey?

You can upgrade from CD, or do it online.
To do it from CD, open Synaptic, go to repositories, and click 'add cdrom'.

I would honestly suggest that you just download the Ubuntu (maybe xubuntu for a lighter system!) 6.10 alternate CD and perform the fixes you discovered to the new installation..

---

