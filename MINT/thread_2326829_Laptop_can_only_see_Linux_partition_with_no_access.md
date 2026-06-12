---
title: "Laptop can only see Linux partition with no access to Windows"
date: 2016-06-05
forum: MINT
---

### Post by Hannahammer on 2016-06-05
Hey, 
So I couldn't find such a thread or a solution that'd work. 
Basically I installed linux mint on my Fujitsu. I've had Windows 10 on the laptop, and I made partitions during installation  of linux mint 64 bit.
All good, 30GB; however my laptop now thinks it has 30Gb and only linux. I have no way to access windows or windows files. Not even BIOS. 
I need to reach windows since I have certain tasks for my university that are windows only... Have anyone ever encountered such problems?
BIOS doesnt work. On linux only linux partition works.

---

### Post by jeremy31 on 2016-06-05
*Thread moved to **MINT**.*

Post results for ```
sudo blkid
```

---

### Post by yancek on 2016-06-05
Was your windows 10 UEFI/GPT?  Did you install Mint UEFI/GPT?

Go to the site below and get the boot repair software using your Mint install and run it.  Select the option to Create Bootinfo Summary and post a link to the output here which will show detailed info on your system.  Do not try to run any repairs.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Hannahammer on 2016-06-05
> **jeremy31 said:**
> *Thread moved to **MINT**.*

Post results for ```
sudo blkid
```


/dev/sda1: UUID="2caf2fe7-7302-440c-9ec8-bf421ec0fa5e" TYPE="ext4" 
/dev/sda5: UUID="bc4495dd-6c4b-4d0e-bdb3-27bdbee8fe6a" TYPE="ext4" 
/dev/sda6: UUID="a02bbde1-8d85-40eb-b744-2aae6c0bffd6" TYPE="swap"
> **yancek said:**
> Was your windows 10 UEFI/GPT?  Did you install Mint UEFI/GPT?

Go to the site below and get the boot repair software using your Mint  install and run it.  Select the option to Create Bootinfo Summary and  post a link to the output here which will show detailed info on your  system.  Do not try to run any repairs.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[http://paste2.org/zaE9jtWO](http://paste2.org/zaE9jtWO)

---

### Post by oldfred on 2016-06-05
Hope you have made good backups.

Sorry to report you erased Windows when you created new partitions. Do not know exactly how Mint handles Windows 10.

If you left Windows 10 always on hibernation which Windows calls fast start, the installer may not have shown the NTFS partitions.
That is why it is normally safer to use gparted to create new partitions. While it will show errors on the hibernated Windows it will show it.

---

### Post by Hannahammer on 2016-06-05
> **oldfred said:**
> Hope you have made good backups.

Sorry to report you erased Windows when you created new partitions. Do not know exactly how Mint handles Windows 10.

If you left Windows 10 always on hibernation which Windows calls fast start, the installer may not have shown the NTFS partitions.
That is why it is normally safer to use gparted to create new partitions. While it will show errors on the hibernated Windows it will show it.

Thanks for the reply. Backup no problem, it's just that i dont know how to reinstall windows since it was already on the laptop...

---

### Post by oldfred on 2016-06-05
Depends on what your backup is. If a full image of Windows you probably have to erase Ubuntu partitions, so it can restore to its NTFS partitions.

If you only have data, then you have to reinstall Windows your Windows product key is in UEFI, but that is only good for the OEM version.
 [http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c) 

If you did not make the vendor backup, then some vendors will ship you one for nominal charge. Others do not, you have to check.

      
 Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

---

