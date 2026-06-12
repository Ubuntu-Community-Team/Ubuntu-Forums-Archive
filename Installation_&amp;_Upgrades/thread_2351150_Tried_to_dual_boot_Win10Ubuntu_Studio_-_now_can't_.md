---
title: "Tried to dual boot Win10/Ubuntu Studio - now can't even single boot!"
date: 2017-01-31
forum: Installation &amp; Upgrades
---

### Post by ollieacappella on 2017-01-31
Hello everybody,

after a long time of prevaricating, I finally decided to take the leap and install Ubuntu (Studio) on my laptop alongside Windows 10. I followed tutorials and common sense but am now forced to use Ubuntu on a live USB stick - I can load neither Ubuntu nor Windows anymore.

I've uploaded my boot log to Dropbox as I'm sure the key info will be in there somewhere: [https://www.dropbox.com/s/g2lk2yjg0wezap1/Boot%20Log.odt?dl=0](https://www.dropbox.com/s/g2lk2yjg0wezap1/Boot%20Log.odt?dl=0)

Basically, I bought an SSD, mirrored my original Windows setup onto it (all went smoothly), organised all my stuff between the two drives and then created a partition for Ubuntu on my old HDD. I created a live USB stick, "tried" Ubuntu out and installed it from the Ubuntu interface. Not once have I been able to successfully boot up in Ubuntu; Windows (being Windows) made sure that I always went straight to Windows. 

I used the Boot Repair Disk software from the live Ubuntu session - to no avail.

I reorganised my boot preferences from the Grub2Win control panel to open up Grub on bootup - to no avail.

I've now installed Ubuntu three times (go on, call me an idiot) and have installed the booter in /sda (SSD), /sdb (old HDD), /sdb1 (old Windows Boot Manager/WBM) and /sdb4 (Ubuntu installation). I *may* have installed it in /sda1 (current, active WBM), but I'm not sure about that. Something tells me that the problem lies somewhere here... Have I overwritten the normal WBM or corrupted it? 

What options do I now have to restore Windows (priority, unfortunately) and boot Ubuntu alongside it (ideal scenario), assuming that completely reinstalling Windows is the *last *thing I want to do?

Many thanks!
ollieacappella

[SOLVED] I opened up my UEFI and there was a boot option at the bottom of the list that I hadn't seen before - I think this may have been added by Boot Repair Disk, or perhaps on one of the later installation attempts. The option was Ubuntu Grub which, naturally, gave me a lot of hope. Now the Grub interface opens when I boot up and I can choose between about 15 options, one of which is Ubuntu Studio, the other Windows 10. No data (seems to have been) lost and all is up and running. Hooray!

---

