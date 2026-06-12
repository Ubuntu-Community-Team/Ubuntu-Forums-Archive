---
title: "Advce about partitions, OSs installation"
date: 2013-04-17
forum: Installation &amp; Upgrades
---

### Post by cpu2007 on 2013-04-17
Hello everyone,
I've installed ubuntu on my laptop, which has W8. I realized that after the installation I can't access W8 anymore as when I select it from the grub menu,it throws an error. However this is not a problem as I was never expecting to use it and eventually I'll delete that partition.

Now I have a few questions about what method should I apply and their possible adv and disadvatages
I need to install W7
- Will it be better to install W7 on the internal HDD so I have a dual boot, creating an os through visualization(virtualbox) or on an external usb drive and use it when I like it by plugging it into my computer. Which of these options is the best one?, I believe installing on the internal hdd would be the fast one.
 -I like the idea of a usb OS, so I'm wondering whether is possible to install OS (w7) on a usb and have a data partition on the laptop hdd? the reason why I'm asking this is because I'd like to know whether is possible to make an OS that can be easily accessed on other laptops as well(like ubuntu live cd), so that when I plug a usb on the computer of my friend, it will allow me to run w7 on it straight away; is this something possible?

Just in case,my laptop specs are:
samsung series 7 chronos 700z5c
8gb ram - 1tb hdd - i7

---

### Post by dabl on 2013-04-17
"Better" is very much in the eye of the beholder ....

Having said that, if your laptop is pretty beefy (dual core CPU @2+ GHz, 4GB RAM, fast GPU), I would install only my Linux OS, and then install Win 7 in a VM on that.  For example I have that setup on a Dell E6500 which only has 2 GB of memory, and it works very well.  The advantage of this approach is, you have _both_ Windows and Linux systems available simultaneously -- no need to reboot.

There is a disadvantage -- if you want to use Windows for gaming or heavy graphics work, then this won't be a good choice -- you need the real hardware for those activities.

My second choice, and the best if you need Windows for gaming or heavy graphics work, would be to install Linux on the bootable USB stick -- get a big 16 or 32MB stick and set it up like a normal hard drive, and boot that when you want Linux, and put your Win 7 on the hard drive.

I would only install both OS's on the hdd if (a) the laptop is a pre-UEFI model, or (b) I planned to spend a week studying UEFI and EFI partitioning and configuration -- you can search for those topics on this fourm and find out why.  I believe Win 7 would have to go on first, and after that you're on your own.

---

### Post by cpu2007 on 2013-04-17
Thanks
I have already installed ubuntu and configuring it it's a bit of a pain as you need to setup many things in order to make it work on a laptop that doesn't offcially suport linux. I had to setup the optimus nvidia graphic card and still have problems making some of the function keys work.

I decided to install ubuntu as I'll be using framework and development tools which do ultimately require some power, how much is the performance reduced if ubuntu is installed in the usb instead of internal hdd?

Having already installed ubuntu, I'm going to try to install w7 now, I know it gives a problem by messing with the grub menu but the fix seemed to be pretty straight forward; else I think w7 on the virtual machine seems to be the most appropriate solution. w7 might be used for some video editings, playing or other stuff but only if that can't be achieved in ubuntu - so far im trying to transit completaly to ubuntu and see whether I can replace all the things I was used to do in w7.

---

### Post by dabl on 2013-04-17
With Linux on the USB stick, the only performance lags will be those involved with writing to the flash media.  Normal browsing, terminal work, etc. will not be slowed down at all.

If you work with gimp for awhile, you will find very few needs for Windows graphics packages -- only the most proficient of graphics artists needs Photoshop over gimp, for example.  Linux video editing packages are pretty good nowadays -- check out avidemux, kdenlive, devede, etc.

There are a few proprietary Windows applications that simply have no satisfactory equivalent in Linux -- my genealogy and website authoring suite being one example, which is why I need a Windows VM.  Also Windows makes a dandy printer driver for Lexmarks, Canons, and miscellaneous other printers that have sucky or no CUPS drivers.

---

