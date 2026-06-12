---
title: "1 Drive LVM yes or no, dual boot"
date: 2015-03-19
forum: Installation &amp; Upgrades
---

### Post by Pat_Foc on 2015-03-19
Hi, I wanna try this ubuntu/xubuntu and would perhaps wanna try it as  dual boot with windows. I would be only using 1 drive for whole system. I  wonder if I should use this LVM during linux installation or not . I  know what it does I have been reading about it a little but I wonder if  its any good for me, I think mostlikely I wouldnt do much of partition  changes... but who knows. 

I wanna know if there are any disadvantages (perhaps slower system or such) or not at all and _if its only_ huge _plus_ and helpful tool so there are not any disadvantages why is it optional?

Also  if perhaps in the future I'd decide to let windows go off my hard drive  and use it all for linux only, could this LVM be any helpful to me with  this task? Or in other words, could I get back my disk space that was  windows previously using and use all of it for linux only the easy way? Thanks! :)

---

### Post by dino99 on 2015-03-20
the easy way is to select a simple installation ;) meaning no lvm

---

### Post by Impavidus on 2015-03-20
LVM is an additional layer of complexity and therefore an additional opportunity for failure. If you don't know for sure LVM will be good for you, then don't use it. You will be able to resize your partitions or simply reuse them at a later stage, in case you decide to remove Windows. Other people just wipe the entire drive and start afresh, for example when they want to move to the next Ubuntu release. (Re-)Installing isn't too painful in Linux.

LVM is mandatory for fully encrypted systems and may be useful on some servers.

---

### Post by oldfred on 2015-03-20
I do not use LVM as it just seems like another level of complication. It was another work around to the 4 primary partition limit with MBR(msdos), but now I only use gpt which does not have that limit.

 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)

Windows only boots from gpt with UEFI, but you can use Ubuntu with gpt whether BIOS or UEFI if you have a bios_grub partition for BIOS boot or an efi partition for UEFI boot.l

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by Pat_Foc on 2015-03-20
Thanks a lot guys! You have been very helpful, have a nice weekend! ;)

---

