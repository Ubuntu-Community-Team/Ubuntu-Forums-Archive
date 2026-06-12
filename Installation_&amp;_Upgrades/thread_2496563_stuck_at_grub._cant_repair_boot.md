---
title: "stuck at grub. cant repair boot"
date: 2024-04-03
forum: Installation &amp; Upgrades
---

### Post by mclovin1999 on 2024-04-03
Hello,
this is my first time installing a linux system. I wanted to use Kubuntu and also use LUKS Encryption.

I used this guide to install KUbuntu including LUKS Encryption:
[https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019](https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019)

It seemed like everything worked fine, but after the whole installation and rebooting the PC I get stuck at the grub screen.

I cant boot, because I cant initialize the kernel. I checked out many posts, which basically told me to do as this post
[https://askubuntu.com/questions/883992/stuck-at-grub-command-line](https://askubuntu.com/questions/883992/stuck-at-grub-command-line)

I tried the boot-repair using the live session on my usb stick, but all I got is this information: [https://paste.ubuntu.com/p/6J3YKDTdpN/](https://paste.ubuntu.com/p/6J3YKDTdpN/)

I tried to boot into all other boot options on my pc but it didnt work out, always the same results => GRUB


Can somebody help me out with this?

Thank you in forward!

---

### Post by yancek on 2024-04-04
Your drive with Kubuntu has a BIOS boot partition (partition 2) which is not needed as you also have an EFI partition (partition 3) which has all the necessary EFI boot files.  Is partition 5 your Kubuntu install?  What is supposed to be on the first partition?  Do you have a separate boot partition?  A separate boot partition is sometimes needed with encrypted drives but I don't use it so don't know if that is related to your problem.

Starting at Line 91 in boot repair you have information on the partitions but nothing shows for partition 5 which should be your Kubuntu system partition.  Beginning at line 200 you see 'unknown bootloader' for all 3 partitions so Grub failed to install properly.

Which release version of Kubuntu are you using?  The link you posted is for 18.04 and there may have been changes in newer versions.

---

