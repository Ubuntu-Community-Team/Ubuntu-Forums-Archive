---
title: "New PC - HDs"
date: 2015-05-26
forum: Installation &amp; Upgrades
---

### Post by Quarkrad on 2015-05-26
Please forgive me - this isn't strictly a Ubuntu issue/question.  I'm running 14.04 and have two HD's one I use for day-to-day use and the other for Back-Up (both are 1TB) - I have purchased a new pc that is coming with two 1TB HDs.  My first thought was to use Clonezilla to copy from my existing HDs to the new ones but why do that(?) - why not just put the one HDs in the new machine? (There will be some issues like the HDs have a different UUIDs).  What ever way I go I will land up with 2 x 1TB HDs and do not know what (if any) issues there are storing brand new 1TB HDs.  Hopefully my existing drives will go on for some time - is there any issues storing the new drives?  Would it be better to swap my existing drives and store the new or use the new and store the old - or does it not really matter?  Many thanks.

---

### Post by SeijiSensei on 2015-05-26
I'd install the old drives and [use mdadm to convert them into a RAID1 array]("http://www.tecmint.com/create-raid1-in-linux/") for long-term storage.  This will destroy all the data on those disks, so copy what you want to save to the new drives first.

---

### Post by oldfred on 2015-05-26
How old are the old drives? Or how much have they been used.

No matter what the guarantee is on a drive, I prefer to have my main working drive as no more than 3 years old and use older drives as part of backup as long as Disks - Smart Info says they are good.

Also new system is probably UEFI and old system BIOS. So you are not taking advantage of the newer UEFI system. But UEFI is more complex since it is designed to support many more features than BIOS which was designed in the 1980's and patched to work with add the newer hardware since.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by SeijiSensei on 2015-05-26
I'm a little unclear on why UEFI would matter if these drives are not being used to boot the system.  I presume he'll be using the new drives for that.

---

### Post by grahammechanical on 2015-05-26
UUIDs come from the OS and not the hard drive. Every partition is given a UUID. Create a new partition and it will be given a UUID. Delete a partition and then create it again and the UUID will be a different UUID.

Grub looks for the Linux kernel by looking for a UUID. The UUID is not going to change is it?

The only problem I see with connecting existing drives (including an OS) to a new motherboard as with the video adapter. Is it a different video adapter? Does Ubuntu have the right proprietary video driver for that adapter? Better to make the switch to an open source video driver before trying the existing drive with Ubuntu in the new machine.

Regards.

---

### Post by Quarkrad on 2015-05-26
Thank you all for your replies and the links - my current drives are about 3 years old - do you think it would be better/wiser to do a clean 14.04 install? I have a few important virtual systems installed - do you think I should consider Cloneziller'ing my main HD to old of the new ones?

---

### Post by SeijiSensei on 2015-05-26
I would always start with a fresh install on a new machine so that Ubuntu can determine the correct drivers for the hardware.  I have moved intact Linux installations from one machine to another, but usually the machines were servers with pretty similar hardware.  Desktop machines have a wider array of devices like video cards and the like to configure.

I'm not sure what you mean by "virtual systems?" Virtual machines like ones created in VirtualBox or VMWare?  VirtualBox stores all its virtual machines in $HOME/VirtualBox VMs/.  Just copy that directory somewhere safe and restore it after you've finished installing the new machine.  Then you can import the VMs into the new VirtualBox instance using Machine > Add from the menu in the VB Manager.

---

### Post by Quarkrad on 2015-05-27
Sorry - I should have said Virtualbox. Thank you for your advice - I will do a clean install.

---

