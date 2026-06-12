---
title: "Help Installing Geforce3"
date: 2004-11-29
forum: Installation &amp; Upgrades
---

### Post by tspec on 2004-11-29
Help, im really stuck :)

Where to begin, im still fairly new to linux so bare with me. Basically the guts of the problem is that im trying to install the nvidia drivers... simple? hah ;)

I downloaded the drivers nvidia.glx via apt-get and then theoretically installed it by typing nvidia-glx-config enable (have done this once before on a different machine and it worked perfectly) .... anyway, this time it didn't do anything, rebooted, no change. 

I began looking up various different ways of trying to get the thing installed, serveral sites I came across mentioned manually adding nvidia to the modules file in the etc dir and then running modprobe nvidia. Did that, didn't work, got the error:

"FATAL: Error inserting nvidia (/lib/modules/2.6.8.1-3-386/kernel/drivers/video/nvidia.ko): No such device"

Also said to run dpkg-reconfigure xserver-xfree86
Wasn't sure what some of the answers to the questions were e.g. busID for the video card so I left everything as default, still couldn't figure out the busID even after running lspici

Searched for that FATAL error and found there is problems between the lastest kernal and the latest nvidia drivers so I downloaded the patch from here: [http://ngc891.blogdns.net/index.php?2004/09/21/3-patched-nvidia-drivers](http://ngc891.blogdns.net/index.php?2004/09/21/3-patched-nvidia-drivers)

patch didn't work because it said i was running xserver so I rebooted, now gnome won't load because of the fact that I reconfigured xserver wrongly. I think the main problem with that is that the busID isn't correct but i can't figure out what it would be, this is an APG Geforce3, the busID defaults to PCI:1:0:0 or something. As I mentioned I ran lspci but it seems to claim the busID as 0000:01:0.0 which xserver claims isn't a real busID....

oh and now that I'm stuck in command mode, since xserver wasn't running i decided to try installing that nvidia patch again but it still won't install because it says im missing kernel-sources, tried looking them up via apt-cache search but nothing.

Well, I'm stuck bigtime at the moment, any help would be much appreciated. Sorry my post is a little all over the place but everytime i tried to fix one problem i seemed to hit another one that made things worse.

/edit: i guess you could say the first thing i need to do is to get xserver fixed in order to load gnome again, then concentrate on trying to install the nvidia drivers which seems to be only possible by installing the above mentioned patch.

---

