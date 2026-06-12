---
title: "Encrypted /boot + Ubiquity = Fail!"
date: 2017-04-05
forum: Installation &amp; Upgrades
---

### Post by dankstale on 2017-04-05
Yo, I wanted to install Ubuntu on an HDD with 'full' disk encryption including the /boot folder. I've manually formatted the disk by making a new disk label (non-GPT), and /dev/sda1 was the only partition on it. It was then LUKS formatted and the /dev/mapper/crypt-root device was formatted with ext4 as the / mount point. While I tried installing the system using the Ubiquity installed it failed to install GRUB2. I found out this was because grub refused to install because the GRUB_ENABLE_CRYPTODISK was not set in the config. That's OK because I have manually installed GRUB2 several times in the past so all I needed to do was ask Ubiquity to skip GRUB2 installation by running "ubiquity -b" as root from a terminal and then manually install it from a chrooted environment.

Anyway here's where I'm stuck. After running ubiquity installer with the "-b" flag (skip bootloader installation), it then refuses to continue the installation because the /boot folder is located on an encrypted partition. For some reason it wants to have an unencrypted /boot partition, but that's not what I'm aiming for. Is there a way to tell Ubiquity to ignore this and continue the installation? I wanted to give it a /dev/loop device that was mounted onto a blank 512MB file located in /tmp, and later copy the files back to /boot, but that device didn't even appear in the list of devices/partitions during installation.

Any ideas how to proceed? Is there a list of commands that are executed by ubiquity during installation so I can try to replicate the installation by hand?

EDIT: I was on ubuntu-mate 17.04 beta, but it should probably apply to all zesty flavors.

Thanks!

---

### Post by SeijiSensei on 2017-04-05
There's literally nothing in /boot that would benefit from encryption.  All it contains are kernel images, initrd images, a couple of other files, and the grub configuration. I don't get the need for encryption.

---

