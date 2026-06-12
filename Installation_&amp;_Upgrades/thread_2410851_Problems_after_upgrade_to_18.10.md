---
title: "Problems after upgrade to 18.10"
date: 2019-01-21
forum: Installation &amp; Upgrades
---

### Post by linux.girl on 2019-01-21
Hi friends,


After a lot of "pain" trying to update my ubuntu to 18.10, I had to finally re-install it from scratch. But I am seeing some weird things, perhaps you can explain it to me? Questions on attached text.


Thanks!!

---

### Post by oldfred on 2019-01-21
When you reinstalled you chose the advanced LVM type install. That is not really for beginners, but if you want or need full drive encryption you have to use LVM.
       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)

Unless you mount a partition, it will not be shown in the df command.
You can temporarily mount just by clicking on it with your file browser, but if an internal drive, you may want to always mount using fstab.
What entry you add to fstab depends on format, whether you have labeled partition, or what name you want to mount it as.
I label all partitions, so those that I do not always mount have an understandable name, not some very long UUID. I normally label with gparted which you can do, but gparted not installed by default and you can use Disks to add labels also. But do not use Disks to add entry to fstab. 

       
 I do not like Disks as it may not use correct parameters. Better to use template/example and adjust for your specifics
[https://askubuntu.com/questions/164926/how-to-make-partitions-mount-at-startup](https://askubuntu.com/questions/164926/how-to-make-partitions-mount-at-startup)
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well: 
   Typical fstab entry For ext4, copy & paste into fstab but use your UUID & mount point:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /mnt/data ext4 defaults,noatime 0 2
# Entry for /dev/sdb4 on Asus AR:
UUID=a0c1c99f-0f09-4787-a7cc-9e15bb3b4aa5 /mnt/data ext4 relatime,nofail,x-systemd.device-timeout=4 0 2

---

### Post by linux.girl on 2019-01-22
Thank you so much for the detailed response, really! Question: you mentioned advanced LVM install - does that mean that there is a LVM install type that is not advanced and more for beginners?

And since I already installed the system that way, and don't really want to re-install again, can you tell me from what you saw if it was installed correctly, i.e., the LVM is properly configured?

Thanks!!!!!

---

### Post by oldfred on 2019-01-22
I do not know LVM, nor encryption.
LVM is volumes, not partitions, so different tools are required. 

The standard Ubuntu install is just / (root) in one partition and an ESP - efi system partition if UEFI.
LVM puts volumes inside one partition fully using it. And you manage the volumes with LVM tools.
Often used with servers as some of the features let server management work better.

---

### Post by linux.girl on 2019-02-03
Thank you so much!!

Can anyone who understands LVM well take a quick look at the config I attached before just so I am sure I configured it correctly?

Thanks!!!

---

