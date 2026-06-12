---
title: "Cannot boot ubuntu 15.10 from Samsung 950 Pro PCIe NVME SSD"
date: 2016-04-17
forum: Installation &amp; Upgrades
---

### Post by lixu on 2016-04-17
[COLOR=#111111][FONT=Ubuntu]I just installed desktop 15.10 but met the same problem described here [http://ubuntuforums.org/showthread.php?t=2309056](http://ubuntuforums.org/showthread.php?t=2309056)
I am using a Dell XPS 8900 with i7 6500 CPU. [/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]I have windows 10 installed on another disk. 950 pro is an empty disk. I tried both automatic install (remove everything on the disk) and manual partition(something else) and neither worked.[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR]When doing manually partition, Ubuntu is installed on [COLOR=#111111][FONT=Consolas]/dev/nvme0n1, but [/FONT][/COLOR][COLOR=#111111][FONT=Consolas]/dev/nvme0n1 is not found in GParted[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I tried the boot-repair method but it told me there was an error when it finished running and it still couldn't boot. It sometimes ran into no such device error and booted into a grub cmd like this -[/FONT][/COLOR]
> error: no such device: ........  
grub rescue>

See detailed error info here: [http://paste.ubuntu.com/15907401/](http://paste.ubuntu.com/15907401/)

---

### Post by oldfred on 2016-04-18
I might partition in advance with gparted, but you need the newest version of gparted.
       gparted should be at least version 0.24.0-1 to recognize NVMe devices
[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)
Filesystem support
[http://ubuntuforums.org/showthread.php?t=2318570](http://ubuntuforums.org/showthread.php?t=2318570)

Make sure UEFI/BIOS is updated to latest version from vendor.

 Support for NVMe in grub-mkdevicemap fixed in 2014
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1275162](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1275162)
spec entry for nvme devices (UEFI v2.4A 9.3.5.22)

And I might just try 16.04 as it has many updates built in. It will be officially release later this week.


Different models, but issues often common by vendor.

 Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch)
[http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843)
Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch) post 272 says 16.04 good
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)
[http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241](http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241)

---

### Post by lixu on 2016-04-18
Thx for the info 
If I install 16.04 beta now, can I upgrade to the official version after it's released?

---

### Post by oldfred on 2016-04-18
I would use the daily as it is almost the final, if not. They need a day or two to finalize ISO.
       Daily builds
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Regular updates will automatically update you to final. I just always reinstall as the older dailies or even beta have many changes to final. So your system need major housecleaning of old .deb and logs are large because of so many changes.
I just installed 16.04 which will be my new LTS, but still on 14.04. I keep at least two versions of Ubuntu on SSD & a few more to experiment with on HDD.

---

