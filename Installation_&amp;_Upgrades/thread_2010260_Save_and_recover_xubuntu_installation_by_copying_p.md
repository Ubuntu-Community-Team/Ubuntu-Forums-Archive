---
title: "Save and recover xubuntu installation by copying partition"
date: 2012-06-25
forum: Installation &amp; Upgrades
---

### Post by ricoPan on 2012-06-25
I am trying to save a xubuntu precise installation on a dual boot with win7 that required reinstallation.  I have no idea if this will work.  At this point I have:

1) copied my / and /home partitions to a separate drive using Gparted

2) installed win7 to entire hard drive (couldn't force my Asus restore disk to install win7 to the existing partition)

3) created empty ext4 partitions for /boot, /, /home, /swap (not ext4) using Gparted

4) copied / and /home partitions back to the new partitions using Gparted

5) win7 boots fine.  Used EasyBCD to install Grub 2 but on selecting Xubuntu from menu sent to grub prompt (don't recall exact error)

6) from xubuntu disk, 'try ubuntu' selection

7) sudo mount /dev/sda6 /boot where sda6 is a new ext4 partition also labeled /boot

8) sudo apt-get install grub-pc

9) sudo grub-setup /dev/sda
 
grub-setup: error: cannot stat /boot/grub/boot.img

10) clearly I do not know what I am doing

---

### Post by sudodus on 2012-06-25
I think you can get important information to solve your problem in the following link

[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1195275_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1195275")

There might be addressing errors, for example that your root partition and swap partition for linux have now other UUIDs, and they need to be fixed, so that the system (first grub, then linux) will find them.

---

### Post by ricoPan on 2012-06-25
Thanks, looking at that thread now.

Did install boot-repair and in case anyone wants to delve in, disk info pasted at [http://paste.ubuntu.com/1059231/](http://paste.ubuntu.com/1059231/)

I may try the boot-repair auto repair...

---

### Post by sudodus on 2012-06-25
> **ricoPan said:**
> Thanks, looking at that thread now.

Did install boot-repair and in case anyone wants to delve in, disk info pasted at [http://paste.ubuntu.com/1059231/](http://paste.ubuntu.com/1059231/)

I may try the boot-repair auto repair...

Yes, the recommended repair at the end of the script output is

> This setting would reinstall the grub2 of sda4 into the MBR of sda.


By the way, the UUID of the linux root partition seems correct to me, and needs no correction.

If that does not work, you can do it some other way to get a correct grub installed into the MBR of the drive (according to tips in the link from my previous post).

---

### Post by ricoPan on 2012-06-25
Thanks. Will try that shortly.

Thanks also for the heads up about the root partition.  From fstab I see:

# / was on /dev/sda5 during installation UUID=4e17ddff-5fdd-45a6-9143-05c8e5ca5aa1 /               ext4    errors=remount-ro 0       1

but I'm don't know how to address that.  Can you point me in the right direction?


> **sudodus said:**
> 

By the way, the UUID of the linux root partition seems correct to me, and needs to correction.



---

### Post by sudodus on 2012-06-25
> **ricoPan said:**
> Thanks. Will try that shortly.

Thanks also for the heads up about the root partition.  From fstab I see:

# / was on /dev/sda5 during installation UUID=4e17ddff-5fdd-45a6-9143-05c8e5ca5aa1 /               ext4    errors=remount-ro 0       1

but I'm don't know how to address that.  Can you point me in the right direction?
Sorry a typing error switched the meaning of what I wrote: 

> ... and needs to correction should be > ... and needs no correction I think that line in /etc/fstab is OK.

---

