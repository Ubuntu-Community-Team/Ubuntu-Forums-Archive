---
title: "How to get the list of apt keys from unbootable partition."
date: 2016-01-08
forum: Installation &amp; Upgrades
---

### Post by malapradej on 2016-01-08
Is there a way to get the list of apt keys corresponding to the ```
/etc/apt/sources.list
``` file. I am trying to back everything up before I try and rescue my partition and if this doesn't work I would like to install everything like it was before using [http://askubuntu.com/a/99151/156765](http://askubuntu.com/a/99151/156765) as example. If the partition was bootable and running, this would be a simple ```
sudo apt-key exportall > ~/Repo.keys
```.

---

### Post by matt_symes on 2016-01-08
Hi

Why is the partition unbootable ? Maybe that can be fixed.

If the file system is corrupted then an fsck may fix it.

Were you using full disk encryption on the disk ?

If the install can be fixed then you can just boot into it normally to get the keys.

As a last resort, you can chroot into it from a LiveCD/USB if the hard drive is not broken.

Please supply far more information to get any useful help.

Kind regards

---

### Post by malapradej on 2016-01-10
> **matt_symes said:**
> Hi

Why is the partition unbootable ? Maybe that can be fixed.

If the file system is corrupted then an fsck may fix it.

Were you using full disk encryption on the disk ?

If the install can be fixed then you can just boot into it normally to get the keys.

As a last resort, you can chroot into it from a LiveCD/USB if the hard drive is not broken.

Please supply far more information to get any useful help.

Kind regards

I have been trying to sort this out on another forum and have had no luck. I have tried to upgrade my windows partition to Win 10. Windows had corrupted my Linux partitions. The link to my discussion on the other forum is [http://askubuntu.com/questions/716367/how-to-repair-boot-record-using-testdisk-after-windows-10-upgrade-in-ubuntu-dual](http://askubuntu.com/questions/716367/how-to-repair-boot-record-using-testdisk-after-windows-10-upgrade-in-ubuntu-dual). It has been a lengthy discussion, and I am about to start the rescue process, but if anything goes wrong I would like to have sufficiently backed up my drive to be able to install and restore the system to a state which is as close to what I have now as possible. My discussion on this on another forum is [http://askubuntu.com/questions/718207/how-to-get-backup-and-restore-the-software-from-a-unbootable-hard-drive](http://askubuntu.com/questions/718207/how-to-get-backup-and-restore-the-software-from-a-unbootable-hard-drive).

Yes my home partition was encrypted. I am currently working from a live-usb session.

---

### Post by matt_symes on 2016-01-10
Hi

If only your home partition was encrypted then you should be able to chroot into your old root partition from the LiveUSB and export keys the or backup anything else you need from the root partition and copy it to another USB storage device connected to the computer. (ie. not the LiveUSB)

Do you know how to chroot from a Live USB ?

Kind regards

---

### Post by malapradej on 2016-01-12
> **matt_symes said:**
> Hi

If only your home partition was encrypted then you should be able to chroot into your old root partition from the LiveUSB and export keys the or backup anything else you need from the root partition and copy it to another USB storage device connected to the computer. (ie. not the LiveUSB)

Do you know how to chroot from a Live USB ?

Kind regards

Thanks for the reply Mat. I followed the instructions in the link I provided and although there was a few errors concerning Packages/repositories it could not find due to not having the keys and repository locations, the majority was reinstalled under the new system. I then had to individually install keys and packages for those it couldn't find. These are mostly keys such as Ubuntu-tweak and others that aren't part of the universe repository. My home directory was just restored from a backup using live usb and chroot to mount the drives.

---

### Post by matt_symes on 2016-01-13
Hi

> **malapradej said:**
> Thanks for the reply Mat. I followed the instructions in the link I provided and although there was a few errors concerning Packages/repositories it could not find due to not having the keys and repository locations, the majority was reinstalled under the new system. I then had to individually install keys and packages for those it couldn't find. These are mostly keys such as Ubuntu-tweak and others that aren't part of the universe repository. My home directory was just restored from a backup using live usb and chroot to mount the drives.

So your problem is fixed ? That's great news :)

BTW: Did you export the keys from the directory */etc/apt/trusted.gpg.d* as well ? This contains the keys to PPAs you may have added to your sources.

I expect this is where your missing keys may have been.

Ayway, if you think your problem has been fixed then please mark this thread as SOLVED using the thread tools under post #1.

Kind regards

---

### Post by malapradej on 2016-01-16
> **matt_symes said:**
> Hi



So your problem is fixed ? That's great news :)

BTW: Did you export the keys from the directory */etc/apt/trusted.gpg.d* as well ? This contains the keys to PPAs you may have added to your sources.

I expect this is where your missing keys may have been.

Ayway, if you think your problem has been fixed then please mark this thread as SOLVED using the thread tools under post #1.

Kind regards

No, didn't try that but hopefully someone will try this in future. Simply installed the apps as explained without additional PPA's.

---

