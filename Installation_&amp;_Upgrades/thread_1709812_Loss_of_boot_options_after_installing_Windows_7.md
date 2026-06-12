---
title: "Loss of boot options after installing Windows 7"
date: 2011-03-18
forum: Installation &amp; Upgrades
---

### Post by yvsong on 2011-03-18
I used to have Ubuntu 10.10 and Windows 7 RC on separate partitions and I could choose to boot into either. Today I installed Windows 7 Enterprise trial version over the Windows 7 RC partition, and lost the boot screen. Reboot goes to Windows automatically. How can I get the boot options back to launch Ubuntu?

Thanks for any advice.

---

### Post by XsheepX on 2011-03-18
Looks like the Windows boot manager overwrote your GRUB config.

---

### Post by Hedgehog1 on 2011-03-18
If your install of Windows 7 only overwrote/updated the current Windows 7 partition(s), then you are in luck; you only need to reinstall grub (**GR**and **U**nified **B**oot loader).

The instructions are here: [http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

You want section 13.

***The Hedge***

:KS

---

### Post by XsheepX on 2011-03-21
> **Hedgehog1 said:**
> If your install of Windows 7 only overwrote/updated the current Windows 7 partition(s), then you are in luck; you only need to reinstall grub (**GR**and **U**nified **B**oot loader).

The instructions are here: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

You want section 13.

***The Hedge***

:KS
But he can't access his Ubuntu partition to reinstall GRUB. His machine automatically boots to windoze now :\

---

### Post by Hedgehog1 on 2011-03-22
> **XsheepX said:**
> But he can't access his Ubuntu partition to reinstall GRUB. His machine automatically boots to windoze now :\

Assuming the OP is still reading the thread, you are right I did not explain it all.

**yvsong,**

To reinstall Grub on Hard Drive from LiveCD/LiveUSB:

Please boot off your LiveCD/LiveUSB, select TRY
In the Terminal (Menu to: Applications >> Accessories >> Terminal), copy and paste these one at a time:
  
 ```
sudo mount /dev/sda5 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
``` ```
grub-install /dev/sda
``````
update-grub
``````
exit
```                                  ```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
``````
sudo shutdown -r now
```

***The Hedge***

:KS

---

