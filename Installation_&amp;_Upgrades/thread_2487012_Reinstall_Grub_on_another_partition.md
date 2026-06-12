---
title: "Reinstall Grub on another partition"
date: 2023-05-20
forum: Installation &amp; Upgrades
---

### Post by alexpeppino on 2023-05-20
I have no experience at all with partitions and boot loaders.
In my pc there is Ubuntu 20.04.6 LTS installed.
My pc has only one disk.
In /dev/sda2 there was Windows OS. Boot partition is sda2.
In /dev/sda5 there is the / directory of my Ubuntu installation.

I wiped all the contents of sda2 but did not format the partition.
Now I suppose that that partition is "damaged". GParted tells me that it is "Unable to detect file system" when I open the Information dialog on sda2.
Anyway, Grub still works so I can boot my Ubuntu OS. (I suppose Grub is still installed on sda2.)

**I want to format sda2**.
I suppose I should **reinstall Grub on sda5**, before, or I will not be able to boot after the formatting operation.

Maybe someone can tell me what should I do.
Thank you.

---

### Post by yancek on 2023-05-20
Which release of windows do/did you have?  Windows 7 had a separate boot partition but newer releases do not.  Since windows 8, I believe all windows installs from the factory have been EFI, certainly on a GPT disk.  If you have a newer windows, one of those partitions may have been the EFI partition.  If you have Ubuntu installed and running, open a terminal and run this command and post the output here which will list your partitions.  You should see one labelled as EFI and also telling you the size.  If not, you have a Legacy install.  You can also run:  sudo parted -l which will list the filesystem type for all your partitions to see what sda2 is.

You can see if you have an EFI partition with Ubuntu by running the following command to see if there is an ubuntu directory:

```
 sudo ls /boot/efi/EFI
```
 
>  I suppose I should **reinstall Grub on sda5**, 

No, you most certainly should NOT do that.  If you have an EFI install, the boot files are on the EFI partition and also the system partition.  If you have a Legacy install, some boot code is in the MBR but most boot files are on the system partition.  The ONLY time you would install Grub to a partition is if you have another Linux OS install and are/will continue to use that system boot loader.

---

### Post by alexpeppino on 2023-05-21
I think it was Windows 7. I bought the laptop in 2013.

```
$ sudo ls /boot/efi/EFI
ls: cannot access '/boot/efi/EFI': No such file or directory

```

```
$  sudo parted -l
Model: ATA Hitachi HTS54505 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  26.8GB  26.8GB  primary   fat32           hidden, lba
 2      26.8GB  36.8GB  10.0GB  primary                   boot
 3      227GB   427GB   200GB   primary   ntfs
 4      427GB   500GB   73.2GB  extended
 5      427GB   462GB   35.0GB  logical   ext4
 7      462GB   497GB   35.0GB  logical   ext4
 6      497GB   500GB   3218MB  logical   linux-swap(v1)

```

On sda7 there is an older version of Ubuntu (16.04).

---

### Post by yancek on 2023-05-21
sda2 does show the 'boot' flag in the parted output but it is considerably larger (10GB) that I would expect. sda3 is the largest windows partition by far so that is likely where the actual windows is installed.  If sda2 was actually your boot partition and you deleted the contents you no longer have the necessary windows boot files so it won't boot.

You do have a Legacy (non-UEFI) install based on the message you posted.

If your question is will there be a problem booting Ubuntu if you format sda2, I doubt it as your Ubuntu Grub boot code resides in the MR and mostly on sda5.
What is the reason you want to format sda2 rather than sda3 which is much larger and could be used on Ubuntu if formatted with a Linux filesystem?

Are you still planning/hoping to use windows?  If that's the case, you will need a windows installation or repair CD to re-install the proper boot files for windows 7.
Also, if sda2 was the windows boot partition, it has nothing to do with Grub or Ubuntu and is not used by Ubuntu.

---

### Post by alexpeppino on 2023-05-22
```
Number  Start   End     Size    Type      File system     Flags
 1      1049kB  26.8GB  26.8GB  primary   fat32           hidden, lba
 2      26.8GB  36.8GB  10.0GB  primary                   boot
 3      227GB   427GB   200GB   primary   ntfs
 4      427GB   500GB   73.2GB  extended
 5      427GB   462GB   35.0GB  logical   ext4
 7      462GB   497GB   35.0GB  logical   ext4
 6      497GB   500GB   3218MB  logical   linux-swap(v1)

```

Windows was on sda2 which size was 200 GB.
I use sda3 as the main partition for data (documents, movies, ...).
I reduced sda2 to 10 GB because I tried to add the other 190 GB to sda3 but it was not possible.
So sda2 is actually 200 GB (I will resize it to that size) which I cannot use because the partition is damaged.

> Also, if sda2 was the windows boot partition, it has nothing to do with Grub or Ubuntu and is not used by Ubuntu. 


I do not understand why sda2 has the boot flag if the boot loader is Grub and it is installed on sda5...
I would like to understand in which partition is the boot loader. 
What happens if I format sda2 (200 GB) ?

---

### Post by MAFoElffen on 2023-05-22
Nothing will happen if you format /dev/sda2...

Let me explain what I see, and anohter possibility of what you could do.

From what I see, you had a dual-boot of Windows 7 and a few versions of Ubuntu. The PC was setup to boot as MBR / Legacy boot on a disk with an old MBR / ms-dos disk partition. That is why there are primary partitions and an extended partition, that contains the logical partitions beyond that have Ubuntu installed to.

The Grub2 Legacy boot loader was installed to the MBR and points to one of the Ubuntu partitions.

/dev/sda1 and /dev/sda2 had Windows 7 installed to it. You deleted the contents of /dev/sda2... /dev/sda1 is now orphaned, containg the boot files from Windows 7, which now has nowhere to point to for the res of it's OS.

The plan from here, should be to use GParted and delete /dev/sda2, then format /dev/sda1 as ext4, and extend/grow it in the unallocated space. You could then mount it via the /etc/fstab file to use as more storage, or to move your home directory to.

You can do anything you want, but since you already have your home inside of your / partition, another posbility would be to create a directory inside your /home directory, to add more storage directly inside your already, existing /home directory... That way it is easily accessible.

Just some ideas.

---

### Post by alexpeppino on 2023-05-25
> The Grub2 Legacy boot loader was installed to the MBR and points to one of the Ubuntu partitions.

I ask again:
Why sda2 has the boot flag if the boot loader is Grub and it is installed on sda5 or sda7?

---

### Post by yancek on 2023-05-26
>  Why sda2 has the boot flag if the boot loader is Grub and it is installed on sda5 or sda7? 		

Grub does not use the boot flag, it is meaningless on a Legacy system such as yours.  Windows boot loaders use/need a boot flag.  Grub installs minimal code in the MBR on a Legacy install but almost all the Grub files are on the system partition which would be either sda5 or sda7.  I mentioned this in my earlier post!

---

