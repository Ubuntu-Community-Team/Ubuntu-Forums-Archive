---
title: "Ubuntu SSD tweaks trashed my /etc/fstab"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by 02darkRS on 2011-10-15
I created this thread: [http://ubuntuforums.org/showthread.php?t=1861277](http://ubuntuforums.org/showthread.php?t=1861277) & fixed the problem BUT the initial situation still remains. My SSD is getting ripped apparently by Ubuntu. With nothing installed it's slowing down very quickly. I read a few threads & some other blogs then followed this: 
 
[http://www.zdnet.com/blog/perlow/geek-sheet-a-tweakers-guide-to-solid-state-drives-ssds-and-linux/9190](http://www.zdnet.com/blog/perlow/geek-sheet-a-tweakers-guide-to-solid-state-drives-ssds-and-linux/9190)
 
I only got as far as adding the following to my fstab:
```
**noatime**,discard,**data=ordered**
```it looked like this:
```
# /etc/fstab: static file system information.
 # # Use 'blkid -o value -s UUID' to print the universally unique identifier 
# for a device; this may be used with UUID= as a more robust way to name 
# devices that works even if disks are added and removed. See fstab(5). 
# # <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    nodev,noexec,nosuid 0       0 
# / was on /dev/sda2 during installation UUID=124f0412-3e68-46f4-a9df-162dc81b94e6 /               
ext4 [COLOR=red]**noatime**,discard,**data=ordered,**[/COLOR]errors=remount-ro 0       1 
# /home was on /dev/sdb5 during installation UUID=e3a1a937-a023-4757-a0bb-e3d4c737a7a4 /home           
ext4 defaults        0       2
# /tmp was on /dev/sdb7 during installation UUID=80cecb02-84e2-4e39-8aea-3ddeeca0b391 /tmp            
ext4 defaults        0       2 
# /var was on /dev/sdb8 during installation UUID=4e41415f-9378-4fe7-9d2a-95f9f8778802 /var          
ext4 defaults        0       2 
# swap was on /dev/sdb6 during installation UUID=2f7fd365-a71d-4401-86dd-29b8002b1e2a none           
swap sw              0       0
```I could not get into my system. 
 
SO, what did I do wrong? I can't fathom anything as I copied what was on the other site straight in. If I did nothing wrong, how can I tweak this install to stop constantly accessing my SSD as that blog states? 
Please provide insight or I am going to have to leave Ubuntu & lose the three weeks I've spent here learning....... please help

---

### Post by 02darkRS on 2011-10-16
^^successfully added the above to /etc/fstab & it's working. 

Been reading:
[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)
[http://www.zdnet.com/blog/perlow/geek-sheet-a-tweakers-guide-to-solid-state-drives-ssds-and-linux/9190](http://www.zdnet.com/blog/perlow/geek-sheet-a-tweakers-guide-to-solid-state-drives-ssds-and-linux/9190)
[http://www.linuxreaders.com/2009/04/14/free-linux-ram/](http://www.linuxreaders.com/2009/04/14/free-linux-ram/)

& some others. scared to try the rest after yesterday but it sounds as if this at least needs done for the ssd:
> If you have several disks or a mix of SSD and mechanical disks, install the **sysfsutils** package and add the following line at the end of **/etc/sysfs.conf**:
block/sda/queue/scheduler = noop

---

### Post by 02darkRS on 2011-10-17
good info on scheduler:
[http://ubuntuforums.org/showthread.php?t=1041524&highlight=sysfsutils](http://ubuntuforums.org/showthread.php?t=1041524&highlight=sysfsutils)

---

