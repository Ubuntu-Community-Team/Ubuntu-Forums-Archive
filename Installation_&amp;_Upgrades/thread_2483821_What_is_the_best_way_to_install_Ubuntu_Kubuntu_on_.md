---
title: "What is the best way to install Ubuntu Kubuntu on a dell G5 5587"
date: 2023-02-09
forum: Installation &amp; Upgrades
---

### Post by Omnios on 2023-02-09
Greetings I am wondering what is the best way to install Ubuntu or Kubuntu on a Dell G5 5587 gamming laptop? It has a 8th gen i5 with onchip video and also have a GTX Nvidia 1050. I probably would prefer it to use the 1050 to free up ram from the onboard video. Also I am wondering if there is any known problems to worry about?. Basicly I am done with gamming so want to install Ubuntu or Kbuntu on my laptop.

---

### Post by #&amp;thj^% on 2023-02-09
Here is a testimony from a former Dell employee:[https://www.dell.com/community/Linux-General/Alienware-Aurora-support-for-Linux/m-p/8008307/highlight/true#M17792](https://www.dell.com/community/Linux-General/Alienware-Aurora-support-for-Linux/m-p/8008307/highlight/true#M17792)

---

### Post by oldfred on 2023-02-09
Make sure UEFI & SSD firmware is most current version.
Best to backup Windows if not dual booting. Many later find one application or game they just have to have that only runs in Windows.

Only use latest LTS, currently 22.04 in UEFI boot mode to gpt partitioned drive.
Older instructions have you turning off UEFI Secure boot and changing RAID (even if one drive) to AHCI.
Newest 22.04.1 (.2 later this month) installed even with those settings on  to my 11th Gen Intel Dell 5310.
I did have to turn bitlocker & Windows fast start up off in Windows.

You do need Safe Boot and install optional proprietary drivers to get correct nVidia driver installed as part of install. Otherwise a bit of a hassle but you can boot to recovery mode and add driver from command line. 

See link below in my signature for UEFI general install info.

---

### Post by SeijiSensei on 2023-02-10
If you are connected to the Internet during the installation, and you check the box to install "third-party" software, the installer should download and install the proper NVIDIA driver automatically. If that doesn't happen, open the "Driver Manager" when you boot the system up for the first time.

---

### Post by Omnios on 2023-02-14
WAs watching a youtube video about installing Kubuntu on a laptop and am wondering what is the purpose of a efi partison when setting up the partions?

---

### Post by oldfred on 2023-02-14
If you have the ESP - efi system partition, you do not create a second one on same drive.
Most systems only support one ESP per device.

Microsoft started requiring UEFI boot with gpt partitioning in 2012 with release of Windows 8.
UEFI uses an ESP for initial boot files. Windows boot loader & grub's .efi boot files are in separate folders in the ESP.

UEFI [https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
ESP/efi -  Efi System Partition  [http://en.wikipedia.org/wiki/EFI_System_partition](http://en.wikipedia.org/wiki/EFI_System_partition)
gpt(GUID) [https://en.wikipedia.org/wiki/GUID_Partition_Table]("http://en.wikipedia.org/wiki/GUID_Partition_Table")[URL="https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface"]
[/URL]

---

### Post by Omnios on 2023-02-14
> **oldfred said:**
> If you have the ESP - efi system partition, you do not create a second one on same drive.
Most systems only support one ESP per device.

Microsoft started requiring UEFI boot with gpt partitioning in 2012 with release of Windows 8.
UEFI uses an ESP for initial boot files. Windows boot loader & grub's .efi boot files are in separate folders in the ESP.

UEFI [https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
ESP/efi -  Efi System Partition  [http://en.wikipedia.org/wiki/EFI_System_partition](http://en.wikipedia.org/wiki/EFI_System_partition)
gpt(GUID) [https://en.wikipedia.org/wiki/GUID_Partition_Table]("http://en.wikipedia.org/wiki/GUID_Partition_Table")[URL="https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface"]
[/URL]


 Thank you for explaining that to me.

---

