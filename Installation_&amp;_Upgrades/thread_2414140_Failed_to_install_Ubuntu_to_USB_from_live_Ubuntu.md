---
title: "Failed to install Ubuntu to USB from live Ubuntu"
date: 2019-03-06
forum: Installation &amp; Upgrades
---

### Post by wilson1218 on 2019-03-06
I am trying to install Ubuntu (latest LTS) from a live version (booted from USB on my Windows laptop) to a 128GiB USB. Whenever I try, it fails to format the ext4 partition. I set a 50GiB fat32 partition (mount at /UDISK), a 60GiB ext4 partition (mount at /), and a ~17GiB swap partition. I get an error message at this point, asking me to go back and add an EFI partition, and I have tried proceeding both with and without this partition (300MiB). Whichever way I try, a few seconds later I get the following message:

"The attempt to mount a file system with type ext4 in SCSI5 (0,0,0), partition #2 (sdc) at / failed."

When trying to partition via gparted or the terminal, the fat32 partition is created successfully, but the other partitions just say 'unformatted' (correct sizes though, and gparted seems to think that it was successful).

Is there anyone else who encountered this error or can help me?
Thanks!

P.S. I also tried formatting the partition via AOMEI Partition Assistant on Windows, and the same thing occurs: it says that it's successful, but is listed as unformatted.

P.S.S. I just tried formatting via AOMEI again, but putting the ext4 partition first, and that worked, but then the fat32 partition failed. Why would it only allow me to format the first partition?

---

### Post by C.S.Cameron on 2019-03-06
This works for me: [https://askubuntu.com/questions/873004/ubuntu-on-a-usb-stick-boot-in-both-bios-and-uefi-modes/1118412#1118412](https://askubuntu.com/questions/873004/ubuntu-on-a-usb-stick-boot-in-both-bios-and-uefi-modes/1118412#1118412)

---

### Post by oldfred on 2019-03-06
We recently saw one user use AOMEI and it had the same bug that Windows has had for years and did not update partition table with Linux partitions.
Best to use Windows tools for Windows & Linux tools for Linux.

So use gparted from Ubuntu live installer or a live ISO of gparted.

Is the purpose of the large FAT32 partition for data sharing with Windows?

For UEFI install you will need ESP - efi system partition FAT32 with boot flag and / (root) ext4. You now do not need swap as it uses a swap file.
But Ubuntu's installer wants to install grub's UEFI boot files to first drive, usually sda or first NVMe drive. You then have to copy files from internal drive's ESP to external drive's ESP.

I do not have Windows, and often configure partitions so flash drive could be converted to either UEFI or BIOS boot. For UEFI you need the ESP, and for BIOS you need a bios_grub. But I now normally only boot with UEFI.

My 128GB USB flash drive:
```
Disk /dev/sdc: 115.3 GiB, 123815854080 bytes, 241827840 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 1F55F36A-DD83-4E74-BD5E-5CBAB4F3FBB4

Device        Start       End   Sectors  Size Type
/dev/sdc1      2048    206847    204800  100M EFI System
/dev/sdc2    206848    208895      2048    1M BIOS boot
/dev/sdc3    208896  42192895  41984000   20G Linux filesystem
/dev/sdc4  42192896 241825791 199632896 95.2G Linux filesystem

```

---

### Post by oldfred on 2019-03-06
Use gparted to repartition USB your are installing into.
Then post this:
sudo gdisk -l /dev/sdc  #if flash drive still seen as sdc
and:
sudo parted -l

---

### Post by oldfred on 2019-03-06
Does gparted show your drive without error?
I just created partitions with gparted as shown above. I do not create a large / on flash drives as it is more for emergency boot with just a few additional apps installed. I primarily use rest of drive as a data partition for backup use.

Then I used Something Else install option when booted in UEFI boot mode and selected my sdc3 partition as / (root). I did ext4 & format but that was redundant. Install to flash drive was a lot slower than to my SSD. Install to SSD is about 10 min where flash drive was 45 min or so. Writing to flash drive is the issue.
Since UEFI, I had to copy all the files in the /EFI/ubuntu folder & /EFI/Boot folder in ESP on my sda to ESP on sdc. External devices only boot from /EFI/Boot/bootx64.efi.

---

