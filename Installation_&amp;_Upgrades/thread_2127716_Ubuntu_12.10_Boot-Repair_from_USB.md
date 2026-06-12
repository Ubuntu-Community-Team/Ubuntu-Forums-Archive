---
title: "Ubuntu 12.10 Boot-Repair from USB"
date: 2013-03-20
forum: Installation &amp; Upgrades
---

### Post by sjhlax89 on 2013-03-20
I've recently installed Ubuntu 12.10 on a new Dell XPS 13 that came preinstalled with Windows 8. I deleted all partitions except for what I think is the recovery partition of Windows 8. On top of that I've followed installation based on this link:

[http://www.calazan.com/how-to-install-the-ubuntu-12-04-sputnik-image-on-your-dell-xps-13-ultrabook/](http://www.calazan.com/how-to-install-the-ubuntu-12-04-sputnik-image-on-your-dell-xps-13-ultrabook/)

It has worked really well and I was able to get all the way through. After following the boot-repair step (find boot repair info here [http://paste.ubuntu.com/5632580/](http://paste.ubuntu.com/5632580/)) i restarted and was presented with Gnu Grub 2.0 after the Dell Spash.

After running updates and what-not I decided to restart the computer. Upon restart I was not presented with the Gnu Grub and instead the Dell spash screen was essentially looping.

I've booted from flash drive and run boot repair at least four more times with similar results. Always after first restart/shutdown I no longer boot to Grub. I've tried searching for similar problems but I haven't found any information. Does anyone have an idea as to what may be causing this?

---

### Post by oldfred on 2013-03-21
I do not know about the specific version you installed.

But you have installed in BIOS mode, so UEFI secure boot should not matter. Does it reset to UEFI somehow?

I have seen several users dual boot with UEFI.
       Dell XPS13 Details on how to install - UEFI and Intel SRT  in Post #10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)

I have also seen several users use the small SSD as the Ubuntu / (root) with all data on the rotating drive. That means they have to turn Intel SRT off in BIOS or Windows. Perhaps that is part of your issue. Intel SRT uses RAID and may be copying data back to sda?

      
  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

You also have to disable the RAID and remove the RAID meta data from the drives.
Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

---

### Post by sjhlax89 on 2013-03-22
Thanks for the quick reply oldfred. I saw the first thread you posted and read through that first before finding the last comment in the thread to the guide that I followed. I didn't choose to follow the first link you posted because I am not really interested in dual booting win8 and ubuntu. I plan on only using ubuntu but in the event I want to use Windows 8 I would like to keep the recovery drive around.

I am honestly not too familiar with UEFI. I wouldn't mind using it but I'm really looking for the simple answer so I can shutdown my laptop without having to boot from flash and re-do boot-repair every time. I do not think the BIOS is reverting to UEFI as I've gone back in to check that settings have stayed the same.

I've finally had more time to mess around with this more. I will update further after I play around some more. Thanks for the ideas.

---

### Post by sjhlax89 on 2013-03-22
So I was tried a couple things more tonight. I verified I was not booting in UEFI. I tried deleting and remaking the boot partition using gparted. I also tried using boot-repair again when I was able to get in. That had the same effect where for the following restart it would reboot. 

Finally I decided to just retry a fresh install. Essentially I did the standard install instead of specifying a directory. I chose the option to wipe the old install and start with a new one. I had some hesitations because I didn't want it to wipe the other partition that was not part of the last ubuntu install but based on the description I didn't think it would. It did. 

So it's working how I wanted it now but I feel like I didn't solve the problem.

---

