---
title: "&quot;The 'grub-efi-amd64-signed' package failed to install&quot;- while installing ubuntu16.04"
date: 2017-05-19
forum: Installation &amp; Upgrades
---

### Post by lelouch0296 on 2017-05-19
Recently my internal hard disk got dmaged and i cant use it now, so i was hoping to install ubuntu on my  external hdd ,so i created a 40 gb partition on it but when im trying to install ubuntu using live usb on my hdd its showing "The 'grub-efi-amd64-signed' package failed to install" error.
so i googled and installed boot repair but still the problem persists and i cant install ubuntu.

its a 1tb hdd , in which i created a 40 gb partion(for ubuntu)  and the other partition has data that i want to keep safe.
 
im new to ubuntu an dits my first time trying to install ubuntu ,so i need help.

---

### Post by oldfred on 2017-05-19
UEFI install of Ubuntu/grub requires an ESP - efi system partition on drive seen as sda. So internal drive must have ESP FAT32 with boot flag. 
If you disconnect internal drive and still want to install to external is it gpt partitioned and do you have an ESP on it?
Or you can install in the 35 year old BIOS/MBR configuration. With Ubuntu you can use newer gpt partitioning and older BIOS if you also include a bios_grub partition.

Only attempt any install using Something Else. Some options just erase entire hard drive. In Linux entire drive is entire physical drive including all partitions. Not Windows mixed definition where it calls partitions "drives". 

Post this:
sudo parted -l

---

### Post by lelouch0296 on 2017-05-19
actually im new to ubuntu and couldnt understand what you meant and about the internal drive its not accessible to me and i cant perform anything on it, its as good as dead.So if you can pls tell me step by step what i would have to do to install.

---

### Post by oldfred on 2017-05-19
Post this  first from Ubuntu live installer:
sudo parted -l 				

Just copy & paste terminal output. If long, include code tags which are the # icon in Forum's advanced editor.

---

### Post by Dennis N on 2017-05-19
If your disk was previously used only for data, it may not have the required EFI system partition.
If you would post the output of: 
```
sudo parted -l 
```
it would clarify the partitioning you have, and provide information to support any suggestions. Running this from the live media terminal should work.

---

### Post by lelouch0296 on 2017-05-19
Model: Seagate BUP Slim BK (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  958GB   958GB   primary  ntfs
 2      958GB   1000GB  41.7GB  primary  ext4
 3      1000GB  1000GB  228MB   primary  fat16        lba

is this what you asked for?

---

### Post by oldfred on 2017-05-19
Is that your external drive?
Do you have lots of data in the NTFS partition?

You probably can just install in BIOS/MBR configuration.
How you boot install media is then how it installs. So be sure to boot Ubuntu live installer in BIOS mode.
Your UEFI should show flash drive twice, once UEFI:flash and just flash where flash is name or label on the flash drive.

---

### Post by Dennis N on 2017-05-19
This disk has msdos parftitioning, and not usable for UEFI. So you need to boot the installer in BIOS mode, not UEFI mode. Identify the mode you are using by comparing first installer screens shown here:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

When running the installer, use the "something else' option on the "Installation Type" screen, and continue to the next screen which displays your partitions. You would select sda2 for your installation.

After selecting, click the "change" button under the partition display, and fill in the details. grub should be installed to sda. You should then be able to complete the installation.

---

### Post by lelouch0296 on 2017-05-19
yes thats my external drive and i want to keep the data in ntfs partition.
how to install in bios/mbr config?

---

### Post by Dennis N on 2017-05-19
> **lelouch0296 said:**
> how to install in bios/mbr config?

Since this is your first install, you probably need extra help beyond posts 7 and 8 above. Here is a good guide where a particular partition is selected for install, as you would be doing to install to sda2. 

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

Again, be sure you boot installer in BIOS mode.

---

