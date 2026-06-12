---
title: "Can't boot with grub (dual boot WIN 11)"
date: 2021-11-05
forum: Installation &amp; Upgrades
---

### Post by turtho on 2021-11-05
Hello,
I've just installed ubuntu alongside windows 11.
I  can boot in windows 11 if i modify the boot order in the bios but i  can't when using grub. It launches the windows repair tool when i do so,  and it restarts.
Also my boot options are messy and i don't know how to clean that. (some are doubled, others are in disks where i have no OS)
I would like to have a clean dual-boot install (Boths OSs on my SSD + /home and windows documents on my HDD).
I have tried boot-repair.
[https://paste.ubuntu.com/p/DJpRmJDQbz/](https://paste.ubuntu.com/p/DJpRmJDQbz/) 
This is the result.
Also there is the boot-info result :
[https://paste.ubuntu.com/p/zb4bgZzt2t/](https://paste.ubuntu.com/p/zb4bgZzt2t/)

---

### Post by oldfred on 2021-11-05
Grub only boots working Windows, or Windows cannot have hibernation flag set nor need chkdsk.
And Windows fast start up turns on hibernation flag. You must have fast start up off in Windows.

You also have two ESP - efi system partitions on your NVMe drive. While two may techincally be allowed, most systems only work or work well with one per drive. 
You will need to change UUID of ESP in fstab to use nvme0n1p1 not nvme0n1p5.
Then reinstall grub.
Details are in Boot-Repair report, but these commands will just show the issues.

UEFI uses GUID aka partUUID to find correct ESP to boot from. Compare these for  partUUID.
sudo efibootmgr -v
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid
and this for UUID of ESP.
cat /etc/fstab for UUID

---

### Post by turtho on 2021-11-06
Okay so i decided to wipe every partition on my hdd, delete the second efi partition from the ssd and reinstall ubuntu
It works now.
Thanks.

---

### Post by ActionParsnip on 2021-11-06
Please mark as solved if the issue is no longer an issue

---

