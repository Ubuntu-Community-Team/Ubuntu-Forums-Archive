---
title: "accessing hard drive on PC with linux on USB"
date: 2010-12-02
forum: Installation &amp; Upgrades
---

### Post by ssharmab on 2010-12-02
Hi
 
I have Ubuntu 10.10 on my USB stick, and it boots fine. I want to be able to use the PC's hard drive, though, for storage of my files. My PC has WinXP on it and I dont want to lose it either.
 
Is there any way by which I can mount the hard drive whenever I boot using the USB stick so that I can use it for storage?
 
Thank you in advance
SsB

---

### Post by sikander3786 on 2010-12-02
That would only work if you have a persistent install on your USB i.e, it is able to save changes and not reset them on every reboot.

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

You need to define a mount for your Windows partition in /etc/fstab.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

Or install NTFS-Config, a gui tool to auto-mount NTFS drives.

Be cautious while using the Windows C: drive under Ubuntu ;-)

Important system files are not protected hence can be deleted by mistake.

If you want more help regarding the permanent mount, please post the output of these commands.

```
cat /etc/fstab
```

```
sudo fdisk -l
```

```
sudo blkid
```

---

### Post by cybergnome on 2010-12-02
I think you would do better to create a Linux partition on the hard drive, and not try to use the NTFS partition for storage when working with Linux.  While the Linux driver can read/write to the partition, the MFT won't be updated, and you will begin to create errors that Windows will discover when you run CHKDSK.

---

