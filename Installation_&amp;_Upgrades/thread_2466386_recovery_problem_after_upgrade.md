---
title: "recovery problem after upgrade"
date: 2021-08-26
forum: Installation &amp; Upgrades
---

### Post by 21Jerry on 2021-08-26
I was running 18.04 server as an owncloud and dlna server  for a while and wanted to upgrade packages.  So I did the update and upgrade didn't thinking it would update the system.  I wasn't running grub before, at least I don't think so, but it looks like it tried to do something with it and killed that partition table.  By the way, this was a default 18.04 system layout prior to this problem on a 250GB SAS SSD.

Near the end of the upgrade, I got this:
```

Sourcing file `/etc/default/grub'
Generating grub configuration file ...
grub-probe: error: cannot find a GRUB drive for /dev/sda1.  Check your device.map.
grub-probe: error: cannot find a GRUB drive for /dev/sda1.  Check your device.map.
Found linux image: /boot/vmlinuz-4.15.0-154-generic
Found initrd image: /boot/initrd.img-4.15.0-154-generic
/usr/sbin/grub-probe: error: cannot find a GRUB drive for /dev/sda1.  Check your device.map.
/usr/sbin/grub-probe: error: cannot find a GRUB drive for /dev/sda1.  Check your device.map.
/usr/sbin/grub-probe: error: cannot find a GRUB drive for /dev/sda1.  Check your device.map.
Found linux image: /boot/vmlinuz-4.15.0-153-generic
Found initrd image: /boot/initrd.img-4.15.0-153-generic
/usr/sbin/grub-probe: error: cannot find a GRUB drive for /dev/sda1.  Check your device.map.
/usr/sbin/grub-probe: error: cannot find a GRUB drive for /dev/sda1.  Check your device.map.
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
/usr/sbin/grub-probe: error: cannot find a GRUB drive for /dev/sda1.  Check your device.map.
/usr/sbin/grub-probe: error: cannot find a GRUB drive for /dev/sda1.  Check your device.map.
device-mapper: reload ioctl on osprober-linux-sdb1  failed: Device or resource busy

```

I tried rebooting and found the partition table was wacked on /sda, my boot drive.
I rescued two partitions, /sda1 /sda2 and now I also have an sda and sdaa listed in /dev

Prior to this I had a listing of /sda and it looked like this:

sda                                                    232.9GB
&#9500;&#9472;sda1                                               487M
&#9492;&#9472;sda5                                                 67.9G
   &#9500;&#9472;owncloud--server--vg-root               55.9G
   &#9492;&#9472;owncloud--server--vg-swap_1          12G

Granted I don't know much, hell, I'm a sales person, but I think the issue is sda2 should be labeled sda5, no?  It also looks like the entire drive isn't being used.  I think that is because originally I had a ~100Gb SAS in there and I think I just DD'ed it to the newer drive but notes were lost in the flood.  Also I see that the two owncloud logical volumes are split into the sda5, at least they add to 67.9 so that's where they are.

During reboot, the logical volume manager (I think that is what it is called) went looking for the two owncloud--server--vg--root and owncloud--server--vg-swap_1 logical volumes.  Is that what they are?  or are they logical partitions?  Anyway, it didn't find them.

I can mount /sda2 and on there, I see root files including all the roots for my zfs pools, /etc, /var, etc but none of them are found, of course, during operations.

I there an easy way to fix this?  I have a live CD but also have the machine booted right now with that initramfs (or whatever it is called) prompt.  

I'm not completely hopeless with ubuntu so before I do something stupid and change the label of /sda2  to /sda5, I thought I should post here.  I think most everything is backed up to tape except I don't have a system dump of /sda.  

Help!

Thanks (oh, and my wife is upset because we use it as a dlna server and my son's GF wants to look at baby pictures, so I have that to deal with).

Jerry

---

### Post by grahammechanical on 2021-08-27
> I wasn't running grub before, at least I don't think so, but it looks  like it tried to do something with it and killed that partition table.

I cannot add much to this conversation except to say that Grub is the bootloader for Linux. A normal install of Ubuntu server would install Grub as the boot loader. So, if this system was working acceptably in the past it was because Grub was installed and doing its job.

> /usr/sbin/grub-probe: error: cannot find a GRUB drive for /dev/sda1.  Check your device.map.

That is Grub giving you an error message. grub-probe is a component of Grub. When we install a new Linux kernel a command called update-grub is run and it probes for all the kernels. The list of places to look is in a grub configuration file. It is my guess that the list that Grub has no longer matches with the reality of your system.

Some Grub files are kept in /boot/grub/  Look for a file called grub.cfg. It is a text file so we can read it. And as administrator we can even edit this file. Look for something like this

> menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os

Then look for something like

> set root='hd1,msdos1'

What Grub calls hd1 we call sda. What Grub calles msdos1 we call sda1. See if "set root" matches reality. 

If you can access the Grub boot menu you can select Advanced Options for  Ubuntu. Select a Linux kernel with recovery mode. If that loads you  will get a recovery menu. One of the options will be "grub - Update grub  boot loader." That may fix things and edit grub.cfg for you.

Regards

---

### Post by 21Jerry on 2021-08-27
Thanks for the feedback.  I ultimately had to get the system back up so I reinstalled 20.04 server.  I read all I could, but the partition table was wacked somehow.  By the way, I never saw a grub display on the previous 18.04 system.  Given I had sda1 and sda5 as an extended partition, I tried to recreate sda2 as extended by deleting it and rebuilding it.  Well then I didn't have the logical volumes in it.  So I backed off my configuration files from /etc and /var/www and just reinstalled.  This will allow me to clean-up some things I never liked anyway.  Good news is my 20TB of zfs imported perfectly.  I have most of the system back up.

Thanks for the help anyway.

Jerry

---

### Post by ubfan1 on 2021-08-27
A minor note:  hd0 would be sda, (and hd1 would be sdb).  Disk enumeration starts at 0, partitions at 1.

---

