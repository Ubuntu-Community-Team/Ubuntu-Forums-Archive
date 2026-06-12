---
title: "Can't boot after LiveCD install"
date: 2011-01-31
forum: Installation &amp; Upgrades
---

### Post by escott28 on 2011-01-31
Hey, New Linux user here

Ok, I've dabbled in Linux before, but not too seriously. But I think I'm ready to give it a serious go

I have Fedora 14 installed on my laptop (Installed with few issues) and I'm trying to install ubuntu on my desktop. I had ubuntu 10.04 installed before on a second (250gb) hard drive (Windows 7 on the other 1TB drive) with a few issues and kinda screwed a few things up trying to upgrade to 10.10. So, I said screw it, and downloaded the live .iso for 10.10 (x64) and burned it to disk. I boot from the live CD and choose the install option to use entire 250Gb disk. I choose my options, including to download updates and install 3rd party software and let the install run its course. Everything seems to be going fine and it asks me to restart. So I say yes, the disk pops out and the screen goes dark... and then nothing happens. The computer's still on but hasn't restarted yet. I hit the del key (Which I use to enter BIOS) and the computer finally restarts. I enter BIOS and tell it to boot from the 250Gb HDD, save and exit. However, it gets stuck at the point where it (It, I assume to be the motherboard) says "Loading Operations System ..." and with a blinking cursor on the line underneath. Nothing happeneds. I let it sit for over half an hour. Nothing. So I boot into windows to confirm I hadn't messed anything up there (I didn't), give up and go to bed (The room-mates were already asleep) 

I tried again just this morning using the same procedure. I'm once again stuck at the "Loading Operating System .." screen. 

Is this a common issue? I saw a few threads on this, but couldn't find a solution. Any help would be awesome! 

Thanks

Erik

PS Sorry for the long winded explanation.

EDIT: After poking around a bit more, I remembered I was confronted by a GRUB menu when I booted into Windows 7 HDD. So, I selected Linux from the menu and all seems good. Does anyone know why this is? It's very odd, well at least to me. Why would GRUB be on the windows hard drive? Is this something I should be concerned about?

---

### Post by kansasnoob on 2011-01-31
> Why would GRUB be on the windows hard drive?

By default grub will normally install to /dev/sda (the first hard drive) unless you choose otherwise. The option to change the "grub-install" location in the 10.10 installer is only available if you choose manual partitioning:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

---

### Post by escott28 on 2011-01-31
Ok, thanks. I guess it's not a big deal then. 

On a totally different note, I can't seem to get my ATI driver working properly. Everything is really choppy and I can't enable desktop effects or install compiz without it. I installed it through the additional hardware menu and downloaded it from the ATI website, but didn't work. Any ideas?

EDIT: Not to make an annoyance of myself, but I managed to figure this out too (after a re-install #2of ubuntu) here: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)
This stuff really should be easier to find. So, for the record, if anyone else is having issues with ATI drivers, here you go.

---

