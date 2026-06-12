---
title: "EFI partition dedicated to Ubuntu for a dual boot"
date: 2015-03-20
forum: Installation &amp; Upgrades
---

### Post by marco.cognetti on 2015-03-20
Hello everyone,

I recently installed Ubuntu following the guide posted [here]("https://help.ubuntu.com/community/UEFI"). As suggested, I created a EFI partition. What I would like to do is to have two different EFI partition, one for Windows (smaller) and one dedicated to Ubuntu (bigger). Is there a way to remap the EFI partition of Ubuntu (that is currently using the one for Windows) to the other one I created?

In addition, since I have an SSD, do you think a swap memory is not a great idea for my machine? (I have 16 GB of RAM).

Thank you,
Neostek

---

### Post by ajgreeny on 2015-03-20
As the EFI partition has to have the boot flag, and I think you can only have a single boot flag on a disk, I suspect you can't do what you want if you have only the one SSD hard disk.  Perhaps with two disks you could, but I may be totally wrong about that.

You are correct, I think, in your comments about swap on an SSD, and with 16GB ram you would probably never use swap anyway.  See what other people say before you take the final decision on that.

---

### Post by oldfred on 2015-03-20
The purpose of UEFI with an efi partition is so all systems can share one efi boot partition. Each has its own folder in the efi partition.

Supposedly the UEFI spec allows multiiple efi partitions, but I have yet to see any system that actually worked. Users that had two boot flags found systems would not boot at all. 

You can have one efi partition per drive, so if you have multiple drives or just want the efi partition on a flash drive or external drive that is possible, but not straight forward.

I prefer to has at least a little swap, some say it may boot slightly faster as it may look for it and have to time out. But you will probably never use swap unless editing large videos or something and some users have posted they do not have swap and system has worked.

---

### Post by Dennis N on 2015-03-20
> Supposedly the UEFI spec allows multiiple efi partitions, but I have yet to see any system that actually worked. 

J.A. Watson of ZDNet claims he is using multiple EFI system partitions. In this quote from his recent column, he is talking about installing Mint and Ubuntu, which we know will both create an Ubuntu folder in the EFI system partition, and overwrite an existing one.

> If you don't take any action to prevent it, whichever of those you install second will overwrite the UEFI boot setup of the first. Not nice, and not much fun.
The only solution I have found is after installing the first one, and before installing the second, you need to create a second EFI boot partition and move the EFI boot directory for the first to this new partition. Finally, don't forget to update the 'fstab' file accordingly.

Entire article: [http://www.zdnet.com/article/building-a-pre-release-linux-testbed-with-opensuse-fedora-ubuntu-and-more/](http://www.zdnet.com/article/building-a-pre-release-linux-testbed-with-opensuse-fedora-ubuntu-and-more/)

Since he is using an Acer Netbook, might we assume there is just one drive involved?

I haven't tried his method, as I am satisfied with the write-over of the Ubuntu folder and select my OS from Grub. Maybe someone would like to try Watson's method and report back.

---

### Post by oldfred on 2015-03-20
I think if you update fstab, then the second install will overwrite the first in the efi partition on major update. Still an issue.
I found even trying to install to a second drive, that it overwrote the efi partition on the first drive. But I had partitioned in advance and just copied ubuntu folder to sdb drive's efi partition. And had to reinstall grub on version in sda.
I would not have had to reinstall grub if I was sure I had same version of grub as the only difference or setting in the efi partition is a tiny grub.cfg that is a configfile entry to link to the grub.cfg in the install. I probably could have just edited that.

But best to have a separate backup of the efi partition before installing anything.

Not sure how you could change before install, but the folder name in the efi partition is the 
 GRUB_DISTRIBUTOR entry.

      Older bug now fixed I believe as have not seen issue lately.
 UEFI install broken when GRUB_DISTRIBUTOR!=Ubuntu (e.g. Kubuntu/UbuntuStudio) Mostly fixed in Saucy & Trusty
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1242417](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1242417)
grub2 installs bootloader in \EFI\${GRUB_DISTRIBUTOR} directory, where
GRUB_DISTRIBUTOR is defined in /etc/default/grub.

---

