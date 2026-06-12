---
title: "Partitions question"
date: 2011-12-19
forum: Installation &amp; Upgrades
---

### Post by Arrow2Knee on 2011-12-19
Hi everyone, I have a dualboot on my laptop: I can choose from an Ubuntu installation and an OpenSUSE installation when starting up. I don't need the OpenSUSE partition anymore. Is there a way how I can delete the OpenSUSE part and then configure the Ubuntu partition to use the whole HDD?

Thanks already!

---

### Post by 2F4U on 2011-12-19
Which distribution provides the boot loader? If it is Ubuntu, you can just remove the openSUSE partition, for example, with gparted. Then you should manually adjust the boot loader configuration and remove the openSUSE entry.
I don't know if it is possible to extend the Ubuntu partition to use the whole hdd, but you can always mount the new partition and use it in Ubuntu.

---

### Post by darkod on 2011-12-19
Yeah, the main question is are you using the bootloader from uubntu or suse. If it's ubuntu, you can literary delete the suse partition without any problems (copy the data first if you need it).

Then either create a new ext4 partition in that place and use it like that, or if you insist you can expand the other partitions to include the unallocated space. But this would depend on the location on the disk, you can only expand a neighbouring partition.

And when resizing there is always the risk of thing going wrong.

---

### Post by Arrow2Knee on 2011-12-19
> **2F4U said:**
> Which distribution provides the boot loader? If it is Ubuntu, you can just remove the openSUSE partition, for example, with gparted. Then you should manually adjust the boot loader configuration and remove the openSUSE entry.
I don't know if it is possible to extend the Ubuntu partition to use the whole hdd, but you can always mount the new partition and use it in Ubuntu.

How can I see which distribution provides the bootloader? :o

---

### Post by Arrow2Knee on 2011-12-19
> **darkod said:**
> Yeah, the main question is are you using the bootloader from uubntu or suse. If it's ubuntu, you can literary delete the suse partition without any problems (copy the data first if you need it).

Then either create a new ext4 partition in that place and use it like that, or if you insist you can expand the other partitions to include the unallocated space. But this would depend on the location on the disk, you can only expand a neighbouring partition.

And when resizing there is always the risk of thing going wrong.

Yea but what do I see what the boot loader is?

---

### Post by darkod on 2011-12-19
You can try running the boot info script from the link in my signature. It should show more details.

On the other hand, a quick way to know might be that usually the OS running grub is the first in the list in the boot menu (but this is not definite proof sometimes). And that is unless you played with the order of the OSs in the menu.

I assumed you know which bootloader is running the show, you need to know when installing OSs.

---

### Post by Arrow2Knee on 2011-12-19
> **darkod said:**
> You can try running the boot info script from the link in my signature. It should show more details.


this is what the RESULTS.txt looks like: [http://pastebin.com/i85dNWpd](http://pastebin.com/i85dNWpd)

I can't find what the boot OS is ...

---

### Post by darkod on 2011-12-19
According to that you have two separate disks. The grub from ubuntu seems to be on the same disk as ubuntu, and the grub from suse on the suse disk.

As long as you have the ubuntu disk as first option to boot from you should be OK deleting the suse partitions on the other disk.

But in this case you can't expand the root partition onto another disk, you would need LVM for that. So the only choice would be to format it as ext4 and use it like that.

---

### Post by dino99 on 2011-12-19
as you only have 1 hdd, the boot loader might be installed on his mbr.
 So if suse have been installed first, it have installed the bootloader, right ? (you might remember what you have done, well usually if not drunk).
If you format this partition, then you will need a livecd to boot on then to reinstall grub-pc again:

sudo grub install /dev/sda
sudo update-grub

---

### Post by Arrow2Knee on 2011-12-19
> **darkod said:**
> According to that you have two separate disks. The grub from ubuntu seems to be on the same disk as ubuntu, and the grub from suse on the suse disk.

As long as you have the ubuntu disk as first option to boot from you should be OK deleting the suse partitions on the other disk.

But in this case you can't expand the root partition onto another disk, you would need LVM for that. So the only choice would be to format it as ext4 and use it like that.

> **dino99 said:**
> as you only have 1 hdd, the boot loader might be installed on his mbr.
 So if suse have been installed first, it have installed the bootloader, right ? (you might remember what you have done, well usually if not drunk).
If you format this partition, then you will need a livecd to boot on then to reinstall grub-pc again:

sudo grub install /dev/sda
sudo update-grub

I think it was OpenSUSE which I installed first, don't know sure though, it's about a year ago ^^

So, I can safely remove OpenSUSE with Ubuntu, how should I do that?

---

### Post by dino99 on 2011-12-19
you have to boot on a livecd, then format the partition where suse is installed (with gparted or partedmagic, that last one is a good software)

---

### Post by Arrow2Knee on 2011-12-19
> **dino99 said:**
> you have to boot on a livecd, then format the partition where suse is installed (with gparted or partedmagic, that last one is a good software)

ok, I'll try that tomorrow, I'll post in this thread ;)

---

### Post by darkod on 2011-12-19
> **dino99 said:**
> as you only have 1 hdd, the boot loader might be installed on his mbr.
 So if suse have been installed first, it have installed the bootloader, right ? (you might remember what you have done, well usually if not drunk).
If you format this partition, then you will need a livecd to boot on then to reinstall grub-pc again:

sudo grub install /dev/sda
sudo update-grub

Please make sure you investigate things better before giving misleading info.
Number 1. The OP has two HDDs according to the script results, both of 250GB. Did you look at the results at all?
Number 2. grub-install and update-grub don't work from live mode, not unless you do a chroot.

---

### Post by darkod on 2011-12-19
> **Arrow2Knee said:**
> I think it was OpenSUSE which I installed first, don't know sure though, it's about a year ago ^^

So, I can safely remove OpenSUSE with Ubuntu, how should I do that?

There is even a better way, didn't think of it earlier.
Boot your ubuntu as you do normally. In terminal run:

sudo grub-install /dev/sda
sudo grub-install /dev/sdb

That will install grub2 from ubuntu (because you are running it from within ubuntu) to the MBR of BOTH disks, so it makes no difference which one you boot from.

After that you can do what ever you want with the suse disk. But after you delete suse it will not go away from your boot menu until you run in ubuntu:
sudo update-grub

---

### Post by Arrow2Knee on 2011-12-20
Ok, I managed to easily remove the partitions with GPARTED, thanks guys, now only Ubuntu is there! ;)

---

