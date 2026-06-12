---
title: "Accidentally removed all linux images"
date: 2013-08-02
forum: Installation &amp; Upgrades
---

### Post by hojjat on 2013-08-02
I accidentally removed all linux-images and now when the system restarts, I only have memcheck in the grub options.

It is a LVM encrypted installation of Ubuntu 12.04 with my root drive on /dev/sda5 and I only have one other logical partition for swap. In other words, /usr and /boot and others are all on sda5.

I used the Ubuntu 12.04 alternative CD to run the recovery tool. I can go as far as executing a shell under my root drive. Once there, I ran the following commands:

```

# update-initramfs -c -k all
update-initramfs: Generating /boot/initrd.img-3.2.0-51-generic
# update-grub
error: unknown LVM metadata header.
error: unknown LVM metadata header.
Generating grub.cfg
cat: /boot/grub/video.lst: No such file or directory
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
error: unknown LVM metadata header.
/usr/sbin/grub-probe: error: no such disk.
error: unknown LVM metadata header.
/usr/sbin/grub-probe: error: no such disk.
error: unknown LVM metadata header.
/usr/sbin/grub-probe: error: no such disk.
   Incorrect metadata area header checksum
error: unknown LVM metadata header.
done

```

Any recommendations on how to fix my grub?

---

### Post by grahammechanical on 2013-08-02
This says that there is still one image left

Found linux image: /boot/vmlinuz-3.2.0-51-generic

After running update-grub, which by the way, found that image did you run?

```
sudo grub-install /dev/sda
```


change to sda part to the correct hard disk that you are booting from. I do not know if this will work. I have no experience with LVM but I have found that for a change to grub.cfg to work we also need to run grub-install.

Regards.

---

### Post by hojjat on 2013-08-02
grub-install /dev/sda1 failed with an error, which seems to be a problem with LVM headers.

I have found [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/452350/comments/9](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/452350/comments/9) online but I'm not sure if I understand it enough to run it on my side. Basically, I need a way to fix my LVM headers.

---

### Post by hojjat on 2013-08-02
I made some progress. By creating a file named /boot/grub/device.map  with the following content, grub-update doesn't give me errors any more:

```

(MACHINENAME-root) /dev/mapper/MACHINENAME-root

```

I also updated my /etc/fstab so that the UUID for the /boot entry would be the same as what I found using vgdisplay.

Now I will try to install grub again (I need to figure out where to install it).

---

### Post by hojjat on 2013-08-02
Alright I made the situation worse. I did a "grub-install /dev/sda" which overwrote the whole LVM booting stuff (sorry for my uninformed language here), and now grub just gives me a disc not found error, and sends me to grub shell. There, if I do ls I only get (hd0) which means the whole LVM is not being read.

Seems like I have broke my LVM. Does anyone know how I can restore it, or recreate it while keeping the data?

---

### Post by hojjat on 2013-08-02
I understand it is hard to answer my question without knowing my partition structure. Here is some more info:

```

# vgscan
  Reading all physical volumes. This make take a while...
  Found volume group "MACHINENAME" using metadata type lvm2
# lvscan
  ACTIVE	'/dev/MACHINENAME/root' [461.60 GiB] inherit
  ACTIVE	'/dev/MACHINENAME/swap_1' [3.87 GiB] inherit

```

and the root volume is the one that contains /, /usr, /boot and all the others. (So no separate volume for boot, for example).

Also, the menuentry section of grub.cfg for 10_linux contains these lines:

```

...
  set root='(MACHINENAME-root)'
  search --no-floppy --fs-uuid --set=root eb8090d6-e4f6-46b9-9aaa-281cdbd4206f
...

```

That UUID is exactly the UUID that grub shows me when it fails to boot. It is NOT the same as the UUID for my logical volume though.

---

### Post by hojjat on 2013-08-02
I realized that my /boot used to be on /dev/sda1 so I did the following:

```

mount /dev/sda1 /boot
grub-install /dev/sda

```

That took me back to the state where I opened this thread. Now I have a working grub, which only lists memeory check as the boot option (so no linux image is recognized).

---

### Post by steeldriver on 2013-08-02
I think you will probably need to boot from a live CD/USB, then decrypt and mount your root lvm (installing the lvm2 package if not provided by the live environment), then chroot into it and purge and re-install grub from there

At least that's pretty much what I had to do recently when I messed up my [non-encrypted] lvm-based install

The boot-repair CD *may* work for you (although it didn't for me, even without the encryption) --> [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by hojjat on 2013-08-02
I fixed it!

I had to copy the existing vmlinuz and config files form the /boot directory in sda5 to sda1. Then I had to remove a few broken entries from /etc/fstab

It took so many hours to fix, but at least I still have my data!

---

