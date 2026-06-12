---
title: "NTFS partition now mounting as read only"
date: 2017-03-08
forum: Installation &amp; Upgrades
---

### Post by Dáire Fagan on 2017-03-08
Hi

I have an NTFS partition on another disk which I have discovered I am unable to write to. I installed samba yesterday and set up a share for a folder on the disk, which may have caused this.

I have tried chmod 777 and chmod 777 on /media/dusf/DUMP but it has made no difference. I also right clicked the same mount point /media/dusf/DUMP and clicked the change permission button when everything was set to read and write but this has made no difference.

In the past when I would click on the partition to mount it in nautilus I could write files fine, but now that does not work, and if I try to mkdir using terminal:

```
mkdir: cannot create directory &#8216;123&#8217;: Read-only file system
```

The relevant output of mount:

```
/dev/sdd2 on /media/dusf/DUMP type fuseblk (ro,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)
```

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdc6 during installation
UUID=6dfb642e-cc3c-46a7-9e31-01ab286d642f /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdc2 during installation
UUID=440D-CC68  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/sdc5 during installation
UUID=bea25149-15bb-47ea-8b1a-8041c8d4ba63 /home           ext4    defaults        0       2
```

All partitions:

```
NAME   FSTYPE        SIZE MOUNTPOINT        LABEL
sdd                  1.8T                   
&#9500;&#9472;sdd2 ntfs          1.8T /media/dusf/DUMP DUMP
&#9492;&#9472;sdd1               128M                   
sdb                298.1G                   
&#9492;&#9472;sdb1 crypto_LUKS 298.1G                   
sdc                232.9G                   
&#9500;&#9472;sdc2 vfat          100M /boot/efi         
&#9500;&#9472;sdc5 ext4        117.2G /home             
&#9500;&#9472;sdc3                16M                   
&#9500;&#9472;sdc1 ntfs          450M                   Recovery
&#9500;&#9472;sdc6 ext4         14.7G /                 
&#9492;&#9472;sdc4 ntfs        100.5G                   
sda                931.5G                   
&#9500;&#9472;sda2 swap         30.5G                   
&#9492;&#9472;sda1 crypto_LUKS   901G                  

```

Ideally I would not just recover write access, but also the NTFS partition DUMP would mount automatically on boot - I will settle for write access though!

Please tell me what to do.

---

### Post by lisati on 2017-03-08
There are different things which can cause a disk or partition to be mounted as read-only. For example, have you been using the partition with Windows at any point?

---

### Post by Dáire Fagan on 2017-03-08
> **lisati said:**
> There are different things which can cause a disk or partition to be mounted as read-only. For example, have you been using the partition with Windows at any point?

Yes, for several years, on this install and others. I read it could be an issue with the filesystem, so I checked it via Windows 10, right clicked partition >> tools >> check file system. I also reinstalled ntfs-3g in case there was some issue with it.

Honestly, this is most likely a problem of my own making, somewhere along troubleshooting other issues!

What can we try please?

Okay, I have write access again after ntfsfix /dev/sdd2 and rebooting.

I had used ntfsfix before, but it was when the partition would not mount at all, if say Windows was in sleep/hibernate.

Can we add an entry to fstab to mount this partition automatically? I tried earlier but the partition disappeared completely!

Also, perhaps we could make Ubuntu always run ntfsfix automatically each boot?

---

### Post by lisati on 2017-03-08
I have no direct experience with Windows 10, but have heard that things like having fast-boot (?) active can sometimes cause issues. Other things to check include making sure that the partition or drive is safely unmounted before booting Ubuntu.

---

### Post by Dáire Fagan on 2017-03-08
> **lisati said:**
> I have no direct experience with Windows 10, but have heard that things like having fast-boot (?) active can sometimes cause issues. Other things to check include making sure that the partition or drive is safely unmounted before booting Ubuntu.

Think you must have been replying as the same time I was posting a second time, please see my last :)

---

### Post by ajgreeny on 2017-03-08
It is absolutely imperative that you unmount the ntfs file system properly from Windows before removing the disk from the system, and if it is a recent version of Windows you must also make sure that the OS is fully shutdown and not using faststart, or whatever it's called, as that is the equivalent of hibernation. Even though the OS appears to be shutdown it is not and if you remove a disk from Windows in that state it will be impossible to mount in Linux.

I have no idea how you unmount a partition from Windows any more as I don't use it, but there used to be an icon in the system tray for "Remove hardware safely" or somesuch; if that still exists, use it.

---

### Post by Dáire Fagan on 2017-03-08
This is an interal 3.5" HDD, so it is never removed. I will double check fast start / quick start, fast boot I think it is called, is turned off.

Any idea about making Ubuntu mount this drive automatically? By the was, is /media/dusf/DUMP the correct place for it, I saw references online to using /mnt?

---

### Post by QIII on 2017-03-08
Is this a dual boot?  If so, once mounted by Windows it doesn't matter if the drive has or has not been removed from the box.

As far as where to mount:  the conventional wisdom goes that removable media be mounted at /media, permanent media at /mnt.

But conventional wisdom is often just "we've always done it that way".  Functionally it makes no difference, but it may make a difference in keeping your head straight about where things are.

Use fstab to automatically mount the device.

---

### Post by Dáire Fagan on 2017-03-08
> **QIII said:**
> Is this a dual boot?  If so, once mounted by Windows it doesn't matter if the drive has or has not been removed from the box.

Yes, but there is no option in Windows to 'safely remove (eject?) drive' for permanent storage, just for USB connected storage.

> **QIII said:**
> As far as where to mount:  the conventional wisdom goes that removable media be mounted at /media, permanent media at /mnt.

But conventional wisdom is often just "we've always done it that way".  Functionally it makes no difference, but it may make a difference in keeping your head straight about where things are.

Let's stick with convention then :)

> **QIII said:**
> Use fstab to automatically mount the device.

As I mentioned, I did try this already but the drive was then inaccessible until I removed the line I input. With the information in my first post, can you please tell me the correct line to add to fstab?

---

### Post by oldfred on 2017-03-08
Morbius posted on mounting partitions with fstab.
And I have not seen anyway to unmount a Windows NTFS partition. It seems you just have to turn off fast start up, or else partition is always mounted.

 [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well: 
   fstab entry For ext4, copy & paste into fstab with correct UUID & mount point:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /mnt/data ext4 defaults,noatime 0 2 
   ** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data 
   ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
sudo nano /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a 

      
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by Dáire Fagan on 2017-03-09
Brilliant oldfred, I now have that NTFS partition mounting automatically, thank you.

During install, I wanted to set up a swap partition on sda2, but whether I created the swap before the encrypted partition on sda1, or vice versa, the installer would not let me continue, it warned about it not being encrypted. Due to this, I left 30.5G of space to configure swap post install. The one visible in my first post is my attempt to create it using the Disks program on Ubuntu. I ran tests and it seemed to work, but it was not automounting, and I am not sure if it is encrypted or not. I am happy to delete the swap and remake if necessary.

Can you please tell me, or link me to the correct way to configure the swap, on sda2, encrypted as I think that is the way to go, and automounting?

---

### Post by oldfred on 2017-03-09
I do not know encryption.
I thought with LVM and full disk encryption the swap was inside the LVM.

And with /home encrypted, it automatically created an encrypted swap.

I have seen a number of Boot-Repair summary reports with encrypted /home & swap, but never saved an example.
Many have gotten confused as  gparted shows it as an error as with encryption gparted does not know what it is. But it is then correct.

I found this:
[http://askubuntu.com/questions/463661/encrypted-swap-partition-for-14-04](http://askubuntu.com/questions/463661/encrypted-swap-partition-for-14-04)

---

