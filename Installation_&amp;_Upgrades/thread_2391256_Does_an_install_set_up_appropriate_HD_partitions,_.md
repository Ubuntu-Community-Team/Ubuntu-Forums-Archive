---
title: "Does an install set up appropriate HD partitions, such as unencrypt..."
date: 2018-05-07
forum: Installation &amp; Upgrades
---

### Post by mawil10132 on 2018-05-07
Does an install set up HD partitions to only that which is required?

For some examples; 

01. Will an install of an older version of ubuntu with encrypted HD, delete that encrypted HD? Regardless of passwords?

02. Will an install review the number of HD partitions and delete any not relevant to new install? Or, 03. Will an install completely wipe and format a HD and then set it with just what is required for the new install? (My true wish!)

PS: I've reviewed BIOS settings and the password there is clear. When booting, there is a password for encryption currently as well as User password.

(Reason for my insecurity is I've already got one laptop unusable where I believe I had a set a password in BIOS when adjusting UEFI and a new install apparently did not account for it and I cannot get past some kind of password and the machine is unusable, when it functioned quite well on U before trying a different install of U.  ~Anyway, I'm not concerned with fixing that one but wish to update another laptop with U18.)

---

### Post by oldfred on 2018-05-07
It depends totally on what install choices you make.
And LVM or LVM with full drive encryption means it totally erases entire hard drive for new install.

You can have UEFI password, Ubuntu install (User) password & encryption passphrase. You have to keep them straight and know which is which. 

Post this:
sudo parted -l

---

### Post by mawil10132 on 2018-05-07
> **oldfred said:**
> It depends totally on what install choices you make.
And LVM or LVM with full drive encryption means it totally erases entire hard drive for new install.

You can have UEFI password, Ubuntu install (User) password & encryption passphrase. You have to keep them straight and know which is which. 

Post this:
sudo parted -l

When U does an install, does it kill old partitions and create new partitions? I won't be encrypting HD this time. I'm not concerned with erasing or cleaning old files, not selling machine nor giving away. I was thinking of doing what the tutorial details, Erase  disk and install U, but wasn't sure about LVM, although it does sound like an improvement, is there any negative going with LVM, wondering why the ask as it sounds like an improvdement.

---

### Post by Skaperen on 2018-05-07
you can force the install steps to deal with an "empty" (like-new) hard drive.  then it has to add a new partition table, add partitions (allocate drive space), and format ... if you choose the option to not do that yourself.  i forget the wording of that option.  in order to "zap" your current hard drive partition table, making it look like nothing is allocated on the drive, boot the CD or memory stick and select the "live" option.  once the live Ubuntu is up, open a terminal window and do this replacing "sdx" with your drive device name:

[COLOR=#ff0000]_**WARNING: the command below will destroy all your data, files, and everything installed on your hard drive.**_[/COLOR]

```
sudo dd if=/dev/zero bs=4096 count=64 oflag=direct of=_/dev/sdx_
```

[COLOR=#ff0000]_**WARNING: the command above will destroy all your data, files, and everything installed on your hard drive.**_[/COLOR]

that will "zap" the partition table and force the installer to initialize the disk.  now proceed with your install.

---

### Post by mawil10132 on 2018-05-07
> **oldfred said:**
> It depends totally on what install choices you make.
And LVM or LVM with full drive encryption means it totally erases entire hard drive for new install.

You can have UEFI password, Ubuntu install (User) password & encryption passphrase. You have to keep them straight and know which is which. 

Post this:
sudo parted -l

I went ahead and tried Install from U-MATE16 to U-18 and all went well. I checked the HD and it's now one partition. Thank you for helping!

---

### Post by mawil10132 on 2018-05-07
> **Skaperen said:**
> you can force the install steps to deal with an "empty" (like-new) hard drive.  then it has to add a new partition table, add partitions (allocate drive space), and format ... if you choose the option to not do that yourself.  i forget the wording of that option.  in order to "zap" your current hard drive partition table, making it look like nothing is allocated on the drive, boot the CD or memory stick and select the "live" option.  once the live Ubuntu is up, open a terminal window and do this replacing "sdx" with your drive device name:

[COLOR=#ff0000]_**WARNING: the command below will destroy all your data, files, and everything installed on your hard drive.**_[/COLOR]

```
sudo dd if=/dev/zero bs=4096 count=64 oflag=direct of=_/dev/sdx_
```

[COLOR=#ff0000]_**WARNING: the command above will destroy all your data, files, and everything installed on your hard drive.**_[/COLOR]

that will "zap" the partition table and force the installer to initialize the disk.  now proceed with your install.

I went ahead and installed U-18 over U=MATE 16 Encrypted, thank you for your suggestions! Great support here!

---

