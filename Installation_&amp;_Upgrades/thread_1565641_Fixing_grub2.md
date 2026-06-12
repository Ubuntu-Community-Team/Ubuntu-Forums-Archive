---
title: "Fixing grub2"
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by vortmax on 2010-09-01
I just upgraded my system to Lucid, which killed grub in the process.  After much searching, I found the Grub 2 wiki and followed the instructions to rescue grub.  However, now when I boot, I don't get any grub screen giving me the option to select  a kernel.  It just starts quickly dumping text to the screen (like the kernel is loading), then gives a warning about sdb not being able to be loaded (which is odd since, /boot and /root and all swap is on sda), then the signal to the monitor drops and it freezes like that.

Here are the steps that I took to repair grub:

first my fdisk -l output:
```

disk /dev/sda: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x689e689e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13       98248+  83  Linux
/dev/sda2              14        5169    38979360    5  Extended
/dev/sda5              14         142      975208+  82  Linux swap / Solaris
/dev/sda6             143        5169    38004088+  83  Linux

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30515   245111706   83  Linux

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004ed39

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30515   245111706   83  Linux

```


sda1 is the partition with /boot and sda6 is /root

now the steps I took:

```

mount /dev/sda6 /mnt
mount /dev/sda1 /mnt/boot
mount --bind /dev /mnt/dev
mount --bind /sys /mnt/sys
mount --bind /proc /mnt/proc

chroot /mnt

update-grub
grub-install /dev/sda

```

any ideas on what to try next?

---

### Post by andrewthomas on 2010-09-01
The chroot is unnecessary

From a Live CD 


```
sudo mount /dev/sda6 /mnt
sudo mount /dev/sda1 /mnt/boot
sudo grub-install --root-directory=/mnt/ /dev/sda
sudo update-grub
```reboot

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

post any errors you get

---

### Post by vortmax on 2010-09-01
This time, I get a message indicating grub is loading, then get this error:

```

error: file not found
  [Linux-bzImage, setup=0x3400, size=0x3d5ba0]

```

The system then proceeds just as before.

---

### Post by vortmax on 2010-09-01
so oddly enough, it turns out the issue was partly with X.

I edited my /etc/defaults/grub file to add nomodeset, then rebuilt the config file and reinstalled grub via the chroot method.  I was then able to boot the system off the HD and get to a console.

I had swapped a new monitor on the system right after upgrade (right before I rebooted and killed it), so I decided just to see what would happen if I put the old one back on.  So I went ahead and pulled the 'nomodeset' option from the grub config, reinstalled grub from the live system, switched monitors and rebooted.  It came up without an issue.

---

