---
title: "Installing on lenovo t430u with dual drives/mSata SSD?"
date: 2013-01-07
forum: Installation &amp; Upgrades
---

### Post by Lucky75 on 2013-01-07
Hi all,

I recently purchased a Lenovo t430u laptop, but it has one of those dual hard drive setups where there's a normal 500gb hdd and then a 24gb mSata SSD. Does anyone know what the setup is like with these sorts of things and how I would install ubuntu on there?

Does Lenovo just install windows to the ssd, or do they use it for some sort of caching? It wouldn't need a special driver to work properly, would it? How does the bootloader work?

If I was installing ubuntu, would I just wipe windows from the SSD and install ubuntu on there? I assume that I wouldn't want to put the swap on the ssd though.

I've looked around but there doesn't seem to be much information about how this works. Any pointers would be helpful.

Thanks


The only thing I've found is this ([http://superuser.com/questions/459578/ubuntu-on-an-xps-14-ultrabook-with-msata-cache-and-500gb-hd-how-to-partition-f](http://superuser.com/questions/459578/ubuntu-on-an-xps-14-ultrabook-with-msata-cache-and-500gb-hd-how-to-partition-f)), which seems to suggest that the ssd doesn't even show up?

---

### Post by oldfred on 2013-01-07
SSD is hidden in Windows. If you turn off the Intel SRT and remove the RAID then gparted will see both drives. Some have just installed Ubuntu to SSD, others to hard drive and then turned Intel back on. Not sure how that works with RAID though?

Vendor does not seem to matter as it is Intel and standard across vendors.

       Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Some info on re-instating  details in post #9
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it. 
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

    

---

### Post by Lucky75 on 2013-01-08
Thanks for the response.

So if I disable the Intel SRT, does that mean that the ssd isn't being used for the windows OS that's preinstalled and that it's installed fully to the hdd?

Would installing ubuntu on the ssd cause problems then? I would assume that less free space on the SSD would slow down windows a bit.

What about booting, how does that work? Would grub just install properly and allow me to boot both windows and ubuntu?

---

### Post by oldfred on 2013-01-08
The Intel SRT idea of the SSD is to cache some Windows files in faster memory than hard drive. But that is starting to not matter as much as with lots of RAM you should be using hard drive less. Of course Windows is so large that it does need more just for its own operating system. Linux caches all recent activity in RAM as you often reuse the same things Which helps speed things up with Linux.

If you are primarily a Windows user and want all the speed you can get,  you should leave the SSD with Windows. But if more a Linux user then installing Ubuntu in the SSD would still work as reported by those who did it in the links above.

You can install grub to the MBR of the hard drive or if installing Ubuntu to the SSD to the MBR of the SSD.

---

