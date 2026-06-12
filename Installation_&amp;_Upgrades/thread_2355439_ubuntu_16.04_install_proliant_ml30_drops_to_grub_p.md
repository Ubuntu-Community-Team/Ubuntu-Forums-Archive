---
title: "ubuntu 16.04 install proliant ml30 drops to grub prompt"
date: 2017-03-12
forum: Installation &amp; Upgrades
---

### Post by keirvt2 on 2017-03-12
Just bought Hp Proliant ML30 and would like to install Ubuntu Mint.

I'm running RAID 1 and EFI boot so /dev/sda and /dev/sdb are hardware RAIDed by HP provisioning and should be the same
Have tried Mint and Ubuntu 16.04. iso on a USB. Both install okay but when trying to boot to disk it fails and drops to a Grub prompt.

Booting to the USB "Try Ubuntu" .With fdisk I  can see the partitions although there are two EFI partitions. Also DOS EFI partition
i have tried mounting /dev/sda2 /mnt and /dev/sda1  /mnt/boot/EFI then chrooting /mnt then upgrade-grub/install-grub  This doesn't work.

The third partition is shown by fdisk as a boot partition. I haven't tried this yet.
 HP advised I should install Unix drivers but I can only see drivers for RedHat Enterprise, and few other non Ubuntu flavours.
[http://login.ubuntu.com/token/7Pdxk8zpDbZ6NpyZvwjL/+newemail/keirvt@optusnet.com.au](http://login.ubuntu.com/token/7Pdxk8zpDbZ6NpyZvwjL/+newemail/keirvt@optusnet.com.au)

Would Red Hat drivers work? Does anyone know if there are Ubuntu drivers?
I did an install on a Proliant ML50 and everything was fine

---

