---
title: "Grub Software Raid Woes"
date: 2005-10-29
forum: Installation &amp; Upgrades
---

### Post by zli on 2005-10-29
Hi,

I've been trying to install Kubuntu 5.10 onto my NVidia NForce Raid 0 setup through [https://wiki.ubuntu.com/FakeRaidHowto?highlight=%28FAKERAID%29](https://wiki.ubuntu.com/FakeRaidHowto?highlight=%28FAKERAID%29).

My partition setup is:

```
                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_idbdhgaj1   *           1        9791    78646176    7  HPFS/NTFS
/dev/mapper/nvidia_idbdhgaj2            9792       42426   262140637+   7  HPFS/NTFS
/dev/mapper/nvidia_idbdhgaj3   *       42427       42430       32130   83  Linux
/dev/mapper/nvidia_idbdhgaj4           42431       61031   149412532+   5  Extended
/dev/mapper/nvidia_idbdhgaj5           42431       42626     1574338+  82  Linux swap / Solaris
/dev/mapper/nvidia_idbdhgaj6           42627       61031   147838131   83  Linux

```

where nvidia_idbdhgaj1 and nvidia_idbdhgaj2 are my NTFS partitions (with WIndows XP),
nvidia_idbdhgaj3 is my /boot (ext2),
nvidia_idbdhgaj5 is my swap, and
nvidia_idbdhgaj6 is my root (reiserfs).

I followed the guide and everything went very well until it was the time to install Grub as my bootloader :(. I opened a shell outside the chrooted environment and started Grub with ```
grub --device-map=/dev/null
``` as specified by the guide. When I entered the next 3 commands, I got this error message:

> grub> device (hd0,0) /dev/mapper/nvidia_idbdhgaj1

grub> device (hd0) /dev/mapper/nvidia_idbdhgaj

grub> root (hd0,0)
 Filesystem type unknown, partition type 0x7

and when I tried to set the root to nvidia_idbdhgaj3 I get:

> grub> device (hd0,2) /dev/mapper/nvidia_idbdhgaj3

grub> device (hd0) /dev/mapper/nvidia_idbdhgaj

grub> root (hd0,2)

Error 18: Selected cylinder exceeds maximum supported by BIOS

Does anyone now how to get Grub in work my Software Raid? Any help is really appreciated :razz:!

---

