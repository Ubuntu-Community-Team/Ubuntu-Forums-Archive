---
title: "Problems with the installer/UEFI [solved]"
date: 2021-08-31
forum: Installation &amp; Upgrades
---

### Post by al53 on 2021-08-31
Hi,

This is my first time with Ubuntu, i'm trying to install the system but i don't think that i understand this installer. Would some body here please give me a brief instruction?.

*The capture is occluding the information ... it is ext4 to mount as /

---

### Post by coffeecat on 2021-08-31
I'm guessing here, but since you have three ext4 partitions and a swap partition, you probably created those partitions with gparted before starting the installer, rather than letting the installer set up a default partition layout. Am I correct? If so, your partition #1 (nvme0n1p1), which is 268MB and formatted fat32, should be fine as an EFI system partition. However, the installer is complaining that it can't find an EFI system partition. Perhaps that partition hasn't been flagged with the necessary flags.

If my assumptions so far are correct, close the installer, open gparted, highlight the first (fat32), partition, and from the Partition menu in gparted add the flags 'boot' and 'esp'.

Welcome to the forum!

---

### Post by al53 on 2021-08-31
Before to do anything, please tell me if you find anything wrong here, Gparted:

---

### Post by coffeecat on 2021-08-31
Yes, there is something wrong. Your nvme0n1p4 ext4 partition has the boot and esp flags. Was that the partition you were intending to install Ubuntu to? An ESP partition must be formatted FAT, and is separate from the root partition of the operating system, which is why I suggested adding the boot and esp flags to nvme0n1p1. The Ubuntu installer needs to use nvme0n1p1 as the EFI system partition (ESP). 

However, before you remove the boot and esp flags from nvme0n1p4 and add them to nvme0n1p1, check whether your Debian system on nvme0n1p5 is working and whether it boots in UEFI mode. I have no recent experience with Debian, but I would guess it needs a fat32 EFI system partition just like Ubuntu.

Also - you have an MXLinux system on nvme0n1p2, with that partition having the legacy_boot flag. (?!) I have no experience of MSLinux, nor of booting operating systems in legacy mode in a GPT partitioned disk, so that may be OK, but I have to admit to being puzzled. Hopefully, others will comment.

---

### Post by al53 on 2021-08-31
I do not know UEFI system, what I had before was Legacy on another old PC but now with this new one, well, that was the "best" thing I could do to install the systems.

 Debian does not interest me anymore, I removed it, very complicated for me, I just want to keep MXLinux and now install Ubuntu, it seems to be relatively friendlier.

Nobody told me how I had to configure the MXLinux partition (if you, or someone else here think it should be changed, please, tell me what I should do).

This is what I have now in Gparted:

---

### Post by coffeecat on 2021-08-31
Gparted is showing a red exclamation mark against nvme0n1p1. Although you have the correct flags set on it, the exclamation mark means there is a problem with it.

A few thoughts.

Since you no longer want Debian and have removed it, that's no longer a consideration.

MXLinux - from what you say and seeing the legacy_boot flag on your MXLinux partition, I would guess that MXLinuz was installed in legacy mode. That's a problem. I don't believe there's a way of mixing legacy mode booting and EFI booting on the same drive. If you proceed to install Ubuntu in EFI mode, then you may find your MXLinux system unbootable. Or at the very least you might have to use the "BIOS" boot menu rather than grub to boot each operating system. I don't know. I've never had a mixed system like that.

That all being said, you would benefit from learning about UEFI. This is a good start, although getting a bit old now: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

So - if this was my system, and since there's a likely problem with the nvme0n1p1 partition, I would start by reformatting it fat32, and not forgetting to add the boot and esp flags afterwards. Then I would install Ubuntu to my chosen partition. (And, from memory, if you are using the "something else" option in the installer, I believe you would have to configure the EFI partition to be mounted to /boot/efi). Once I had Ubuntu up and running I would see if MXLinux would boot and, if not, consider possibly re-installing it in EFI mode. I see you have plenty of partitions, no doubt in anticipation of trying other distros. Good luck!

By the way, I see that you have created a swap partition. As a point of information, recent releases of Ubuntu use a swap file by default and don't need a separate swap partition. I don't see that as a problem and the swap partition may come in useful if you decide to try a distro that still uses one.

---

### Post by Dennis N on 2021-08-31
> **al53 said:**
> Before to do anything, please tell me if you find anything wrong here, Gparted:
 
Here's are a couple of comments (which may echo what has been said) which might help:

The legacy_boot flag is used on a small 1-2 MB unformatted partition in order to use a GPT disk for BIOS installation. You don't have such a partition on your disk, so that suggests everything here is UEFI. You should remove that flag.

The boot,esp flags must be set on the fat 32 ESP partition, not on an ext4 partition. The MX Linux ext4 partition should not show any flags.

---

### Post by al53 on 2021-08-31
Okay, please, one last comment, I know you are all very busy.

Ubuntu is installed, as you said it was impossible to achieve it with that configuration that I had before, the red flag is no more.

The MXLinux boot very well. Do you think I can improve all of this if I remove from MXLinux that 'legacy-boot' that appears at the end?

Thank you very much for your time and attention.

---

### Post by Dennis N on 2021-08-31
> The MXLinux boot very well. Do you think I can improve all of this if I remove from MXLinux that 'legacy-boot' that appears at the end?
Since you say MX Linux works ok, it's apparently being ignored. But I would remove it anyway if I were you. See the screenshot I added to the previous post. I have no flags on the MX Linux partition.

---

### Post by al53 on 2021-08-31
Thanks!

---

