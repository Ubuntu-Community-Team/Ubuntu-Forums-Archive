---
title: "Just installed and now cant boot into windows"
date: 2015-10-25
forum: Installation &amp; Upgrades
---

### Post by alex461 on 2015-10-25
So i just installed ubuntus on my hdd which was formatted  and now when i try to boot with my SSD which was running windows 10,it prompts me to reboot and select proper boot device.
I can see with the linux file manager that the windows files inside my SSD are intact.
Tried using boot repair but it says "GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.
Alternatively, you can retry after activating the [Separate /boot/efi partition:] option."
I tried using Gparted but cant figure out how to add a flag so i need some help.
Finally,it's my first time installing Ubuntus so i dont really know how to procede..

---

### Post by yancek on 2015-10-25
The link below explains how to create the BIOS boot partition.  You would only do this if you are using GPT and NOT using EFI.  If you have an EFI partition with windows, you need Ubuntu also installed in EFI and then you would not need the BIOS boot partition.  Your forgot to post the output of the boot repair which would go a long way toward finding a solution.

[http://askubuntu.com/questions/473641/make-boot-partition-using-gparted-in-boot-repair](http://askubuntu.com/questions/473641/make-boot-partition-using-gparted-in-boot-repair)

---

