---
title: "ASrock h97m pro4 UEFI dual boot ubuntu 14.04 and windows 10 not show grub"
date: 2016-02-10
forum: Installation &amp; Upgrades
---

### Post by lnthai20022 on 2016-02-10
Hello,
I have an Asrock H97M Pro4 with an SSD and a SSHD. I disabled fast boot, secure boot in the efi. Then I installed windows 10 on the SSD (formatted as GPT using windows diskpart). Everything is fine. I noticed there is a boot/efi partition that windows 10 created in this disk.
Then i hooked in my SSHD, format it as GPT (using parted) and installed ubuntu 14.04 on it, I selected the custom installation and partition the disk as:
[LIST=1]
[*]Create a 200MB boot partition on the SSHD
[*]Create a 4gb swap area on the SSHD.
[*]Create an LVM pv, 1 vg and 2 lv
[*]Mapped the /boot to the boot partition create in 1.
[*]Mapped the 2 lv to / and /home
[/LIST]
Then finish the rest of the installation.
After the installation i went to the motherboard efi and set Ubuntu as the first boot loader then windows as the 2nd one and rebooted.
I was happy to see grub loaded and correctly recognize my windows 10 installation. The joy went on for a month or so and then suddenly (after a windows update i guess), i no longer see grub. When the machine boot **from cold state** (shutdown previously), **only windows boot loader is present in the motherboard efi** thus it boot directly to windows. If i restart the machine and go to motherboard efi i can see 2 boot loaders : windows as the 1st and ubuntu as 2nd. I can switch the order to make grub appear again but the boot order only stay when i reboot, if i shutdown the machine, i lost grub again.
I think i read something about some uefi implementation stop after it found the first boot partition, it it correct? Has anyone experience the same issue?

---

### Post by oldfred on 2016-02-10
I have an Asus Z97 but no Windows.

Back up entire ESP - efi system partition. Not large so easy to back up.

Windows 10 will on updates set itself back to first in boot order.
Can you use efibootmgr to change boot order and does it stay?
       Check entry is there.
sudo efibootmgr -v

 Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
Example to change order 0002 first, 0001 second;

 sudo efibootmgr -o 2,1

    
 [http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)


Also I like to make the fallback or default hard drive entry be shimx64.efi.
The fallback entry is /EFI/Boot/bootx64.efi. That is how all external drives boot, but can also be used for internal drives.
       From a working computer otherwise mount partition and include mount in every command (see note on permissions):
cd /boot/efi/EFI
sudo mkdir -p BOOT
sudo cp ubuntu/shimx64.efi BOOT/bootx64.efi
sudo cp ubuntu/grubx64.efi BOOT/grubx64.efi

If you already have a bootx64.efi best to back it up. Probably is just a copy of Windows boot efi file.

Permissions defaults in fstab for ESP.
My older UEFI has the ESP mounted with defaults, but newer installs changed from defaults to umask=0077 in fstab. You have to change to defaults in /etc/fstab and reboot. Just changing & running umount -a does not change it in a working install. 
Boot-Repair automatically does that so it can update things.

---

### Post by lnthai20022 on 2016-02-10
I tried to set the boot order with efibootmgr but it's the same as setting with the motherboard efi, the boot order is lost after the shutdown. In the fallback approach, are you trying to tell windows boot loader to load grub efi? I am not sure if my problem come from the fact that i have 2 boot partitions, one for windows and one for ubuntu. If that's the case I don't know how to move the linux boot partition to the windows one. Some article i saw recently suggest using the same boot partition for both windows and linux but may be it's because they install both OS on the same disk.

---

### Post by oldfred on 2016-02-10
Most UEFI do not support two ESP - efi system partitions. Spec says it can be done, and a few have had it work.
Most just install to one. Often the use of two flag flags is a huge problem, if on one device. You normally have one ESP per device/drive.

I have copied an entire /EFI/Ubuntu from one drive to another, so you should be able to copy from one ESP to another.
You will have to use efibootmager to create new entries as GUID for ESP, which UEFI uses will change.

---

