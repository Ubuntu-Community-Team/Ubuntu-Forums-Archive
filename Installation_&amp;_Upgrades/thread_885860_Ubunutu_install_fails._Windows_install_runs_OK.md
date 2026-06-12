---
title: "Ubunutu install fails. Windows install runs OK?"
date: 2008-08-10
forum: Installation &amp; Upgrades
---

### Post by Odyssey1942 on 2008-08-10
Am building a new computer which has a Gigabyte GA-P35-S3G mobo, Intel Core 2 Duo E6550 processor, Diamond Viper X1650 Pro 8X AGP video, 2GB RAM and a Thermaltake 500W PSU. 

So far, in addition to the above, have only connected a CDRom to run setup CD's and a series of HDD's, one of which came out of a Dell 4500 with XP Pro already installed on it. Interestingly the latter was able to boot and run XP at least to a screen that says that I need to register/validate. (I supose it realizes that it is in a different hardware setup, but at least it booted!)

Have tried to use an XP Home install CD and an Ubuntu 8.04 desktop CD. The XP install CD gets as far as the partitioning screen and can see the four (linux, although it calls them "Unknown format") partitions. I don't need to install XP since this HDD already has Ubuntu installed and if I go any further with the XP install it will want to format the entire disk (since it will not be able to read C:). I just am testing the hardware to see that everything is "seen".

For all of the hdd's, the Ubunutu (virtual desktop) install, however, gets through the screen with the moving bar (activity indicator), then the bar that starts filling from the left and when it fills all the way to the right, switches to the next step in the install but at that point the screen goes dark and in a bit the CD stops reading.

Ubuntu CD integrity check routine shows no errors and the memory test shows no errors after running for nearly an hour.

Why can windows see the partitions, but Ubunutu cannot?

Why is Ubunutu shutting down? The video card is only DVI output and this computer is connected to an old crt monitor via an adapter. Could this be causing the problem?

TIA.

---

### Post by TenPlus1 on 2008-08-10
The windows partitions might be in NTFS format which Ubuntu CAN read, but you need to install ntfstools and ntfsconfig for it to be recognised...  It's not a default linux filesystem so the extra packages are required for it to work properly...

---

### Post by hal8000 on 2008-08-10
What you have done is used a HD with Ubuntu already installed for different hardware, motherboard chipset, CPU and graphics card, its not surprising that your system fails to start.

As the display is not visible you need to start in console mode, or try ctrl-alt-f1 to watch the boot messages. You need to re-configure the xdispaly to take account of the new graphics card, but possibly also you would benefit from a differemt kernel now that you have a dual core cpu.

Not sure what graphics chipset your diamond uses, but I always stick with Nvidia, or any vendor that actively supports linux.

If you manage to boot into console mode, then
sudo dpkg-reconfigure xserver-xorg

may allow you to get your system working again.
Hope that helps

---

### Post by Odyssey1942 on 2008-08-10
Apologies. I guess my post was confusing.

At the beginning, some hours ago, I attempted to boot from several different hdd's with various versions of Windoze and Ubuntu. Only the one XP Pro actually booted.

I stopped my attempts to boot from hdd's and reset the bios so that the 1,2,3 boot options are to boot from CD.

All of the Windoze install CD's will take an install all of the way through, but I stop at the formatting stage as it is unproductive to take it any further.

Where I am now, is attempting to install Ubunutu 8.04. The situation is as described in the original post, and I don't imagine what is on the hdd has anything to do with it at this point since the hdd is for all intents and purposes inactive during the startup of the install, but could be wrong about this. 

The problem is that the Ubunutu install, whether to a live CD (virtual desktop) or full install, fails and the screen goes dark.

I suspect the problem has to do with the video card. I'm afraid I don't understand Hal's suggestion about booting into the display console. Please elaborate.

---

### Post by Odyssey1942 on 2008-08-10
OK, it appears that the culprit is a mismatch between the video card and CRT. I found a 7.10 Ubuntu CD with a boot into safe video option. It brings up the live cd desktop just fine. Thanks for all your help.

---

