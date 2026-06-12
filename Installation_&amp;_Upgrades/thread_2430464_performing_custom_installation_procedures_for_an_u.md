---
title: "performing custom installation procedures for an ubuntu iso"
date: 2019-11-02
forum: Installation &amp; Upgrades
---

### Post by eankeen2 on 2019-11-02
i was wondering how to go about installing ubuntu without using the automated installer. I checked the wiki for custom installation procedures, but they all seemed to be installing using some live iso, or using some automated program that uses the iso file.

you might ask why - i ask because i was trying to use the live installer, and it was not working for a particular configuration i had in mind. in this configuration, i store two partition entries in the gpt. the first partition entry is a 5 gibibyte allocation for my esp, efi system partition. the second partition is a 500 or so gibibyte lvm physical volume containing a single volume group, which contains several logical volumes. some logical volumes contain the root file system of other linux distributions i have installed.

apparently, when using the ubuntu live iso installer, i need a `[FONT=courier new]/boot[/FONT]` partition. but, i like installing my kernel images and initial ramdisks etc. in my esp (ex. `[FONT=courier new]\EFI\manjaro\vmlinuz-5.3-x86_64[/FONT]` instead of in `[FONT=courier new]/boot[/FONT]`). i could not continue the installation procedure without creating a third partition for `[FONT=courier new]/boot[/FONT]`, and selecting that for the live install disk.

i do not like creating `[FONT=courier new]/boot[/FONT]` partitions for each distribution because it feels super messy and makes the output of 'lsblk', etc. messy and unpleasant (creating one, and moving any binaries to the esp, then removing the partition feels messy as well). i boot using refind, which does not support lvm - so naturally i put my kernels and initramfs crap in their respective vendor files in `[FONT=courier new]\EFI[/FONT]`. 

so again, i was wondering if i could put the ubuntu kernel, root file system, and initial ram disks in places i want, and install ubuntu that way, without using the automated installer

i was thinking of an approach to solve this problem. so far i was thinking this:
ubuntu offers their downstream (is that the right terminology?) 'mainline' kernels for download [here]("https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D"), so i guess i can use that. (i do not know how to convert the .deb kernel headers, images, and modules into something i can put in my efi system partition, but i am sure i can switch kernels after i boot into the system with a stock kernel). but, i do not know where to find the real 'root' file system that comes with installed ubuntu. i tried mounting the iso and looked for stuff like /[FONT=courier new]opt, /run, /var, /lib[/FONT], etc, but could not find any of the such. i also do not know where to find the default initial ramdisk that ubuntu uses. since i am using lvm, i would need to have lvm kernel modules so i can actually mount the real root file system

any help would be appreciated. let me know if i get any technical facts wrong (or even slightly incorrect), or if something is unconventional

---

