---
title: "grub: menu.lst update not correct"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by stoneman on 2009-12-05
Hi
on a netbook I use an USB stick with the /boot directory while the rest of ubuntu is on a SD card (MMC). The reason is, that the netbook us unable to boot directly from the SD card.
This is possible with the following entry in menu.lst

```
title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		<uuid of USB stick>
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=<uuid of SD card> ro quiet splash quiet 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet
```

When the kernel is updated on a dist-upgrade, it regenerates menu.lst but replaces <uuid of USB stick> by the <uuid of SD card>.
Is this a but that I should report to launchpad?

---

### Post by darkod on 2009-12-05
It puts the UUID of the card because that's where root is, where Ubuntu is running (like C: in windows). Your /boot partition is on the stick but that's not root.

Why would you want to report it, it stops working correctly after it updates?

PS. Sorry, I just noticed the stick UUID above it. If it changes that value too, then yes, it would stop working. But did you create this boot stick yourself manually? Maybe ubuntu thinks /boot folder is on the card (/) and that's why it changes it.

---

### Post by pete78 on 2009-12-06
Yes, I created this USB stick myself as the netbook cannot boot directly from the SD card and the USB stick is to small for the whole root file system.
It ONLY changes UUID above what makes it stop working. Yes, I guest it's because Ubuntu thinks that /boot and / are on the same partition what is not true in this case.

Is is true, that the line starting with uuid refers to the partition where the directory /boot is located (or with other words where the kernel is located) and the uuid in the line starting with kernel means the partition where / is located?

---

### Post by Herman on 2009-12-06
In your menu.lst file, look around half-way down and you'll see a line like:
[FONT=Bitstream Vera Sans Mono]### BEGIN AUTOMAGIC KERNELS LIST [/FONT][FONT=Bitstream Vera Sans Mono]
[/FONT]
Look below that line and inside the Debian Automagic Kernels list you will see a number of settings which the script 'update-grub' will look at the next time it automatically generates you a new menu.lst file after a kernel update, or when you run update-grub.

One of those is kopt. kopt stands for 'kernel options'. 
'kopt=root=UUID='This line should contain the UUID to point to your linux /  (root) partition, meaning the partition which contains /sbin/init. Yours is okay for that part.

Below kopt somewhere, maybe it will be the next one, you'll find 'groot'.
'groot' is short for 'grub root device'. That should be the partition your Linux kernel is located in, your /boot partition.
The problem is yours probably has the wrong UUID number and it needs to be updated since you made your own separate /boot.
If you run the command 'sudo blkid', you will see the UUID number for your root file system and also one for your /boot.
Make sure you copy the UUID for the /boot partition and paste it over the UUID number that's now after your groot command, to overwrite it, and save the changes.
Then you may run 'sudo update-grub', if you like. From now on your UUID for the file system your kernel is in will be corrrect after each update.

---

### Post by Herman on 2009-12-06
> Is is true, that the line starting with uuid refers to the partition where the directory /boot is located (or with other words where the kernel is located) and the uuid in the line starting with kernel means the partition where / is located?Yes, that's correct, or more exactly, the uuid line refers to the file system in which your kernel can be found, and in the next line down, your root=UUID= should be the file system where /sbin/init is located.

---

