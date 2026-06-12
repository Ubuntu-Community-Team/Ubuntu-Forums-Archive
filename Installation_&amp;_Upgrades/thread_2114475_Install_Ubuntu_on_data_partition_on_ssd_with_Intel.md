---
title: "Install Ubuntu on data partition on ssd with Intel rapid storage technology howto?"
date: 2013-02-10
forum: Installation &amp; Upgrades
---

### Post by criusit on 2013-02-10
I have a Dell 15z with hhd of 500G and ssd of 32G. In the ssd is working  IRST that have create 2 volume: one of 20G used for the IRST operation,  the other of 12G for normal data storage.
I want to install my ubuntu in this 12G; Any suggestion?


The trick that I have done until now are:

[LIST=1]
[*]Install before ubuntu in a 12G partion and after active IRST, doesn't work because the IRST erase the whole ssd
[*]from  cd live I use the command: ```
sudo dmraid -ay
``` that allow me,  during the installation process, showing the ssd partition(/dev/sdb) in  this way:
[IMG]http://i.imgur.com/0pGjYez.png[/IMG]

If   I use Volume_0000p1 for mount the / point and at the voice "Device for  install boot loader" I select the Volume_0000 or  /dev/sda with inside a  bios boot partition; when I finish one of the two kind installation  grub start in rescue mode saying: "error: no suc device:  3d5ffec2-c32b-......"
[/LIST]


Any Idea?

Thanks

---

### Post by darkod on 2013-02-10
Usually the live cd doesn't install grub2 correctly on fakeraid (IRST is like a fakeraid installation hence you have the /dev/mapper/... device).

You can try from live mode to chroot into the root partition of the /dev/mapper/... and install grub2 to the MBR of the /dev/mapper/ device. That's where it needs to be usually.

The chroot would be like:
```
sudo dmraid -ay (if needed)
sudo mount /dev/mapper/blahblah_Volume_0000p1 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
grub-install /dev/mapper/blahblah_Volume_0000
update-grub
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```

Reboot and see if it helped.

I am not sure it can work like this with IRST and the ssd part split. I think you have to break up the IRST and use the hdd and ssd separately. That would definitely work.

---

