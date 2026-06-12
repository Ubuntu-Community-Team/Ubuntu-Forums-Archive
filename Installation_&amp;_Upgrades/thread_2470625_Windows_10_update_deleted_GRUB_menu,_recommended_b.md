---
title: "Windows 10 update deleted GRUB menu, recommended boot-repair not working"
date: 2022-01-05
forum: Installation &amp; Upgrades
---

### Post by ceridwenreed on 2022-01-05
I have Windows and Linux dual booted on my laptop and after a windows 10 update the grub menu was deleted.  I booted ubuntu from a live disk and attempted to repair grub using recommend boot-repair option:

[FONT=courier new]sudo apt-add-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair[/FONT] 

Boot-repair offered up commands to type into terminal in order to purge and reinstall grub, however after inputing these into terminal, grub was not removed. (supposedly a window is meant to pop up to confirm grub removal but that did not happen)

I tried the terminal method using:
[FONT=courier new]
sudo grub-install --boot-directory=/mnt/ubuntu/boot /dev/sdX[/FONT]

This generated the message:

[INDENT][FONT=courier new]grub-install: warning: File system `ext2' doesn't support embedding.
grub-install: warning: Embedding is not possible. GRUB can only be  installed in this setup by using blocklists. However, blocklists are  UNRELIABLE and their use is discouraged..
grub-install: error: will not proceed with blocklists.[/FONT]
[/INDENT]


This is a copy of the boot-info:

[https://paste.ubuntu.com/p/WJZYkDQNTp/](https://paste.ubuntu.com/p/WJZYkDQNTp/)


[FONT=arial]Using  [FONT=courier new]**sudo efibootmgr**[/FONT]  outputs:
[/FONT]
[INDENT][FONT=courier new]BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0001, 0001
Boot0001* UEFI: SanDisk, Partition 1
Boot0002* UEFI: THNSN5256GPUK NVMe TOSHIBA 256GB, Partition 1[/FONT]
[/INDENT]

---

### Post by oldfred on 2022-01-05
You seem to have mixed up UUIDs.

The grub in the ESP is a configfile to your install ( or boot partition if you have one, but you do not) line 276
search.fs_uuid 04b2cbb9-42a3-44ee-bdec-6fba361c72a5 root

But your fstab is mounting This line 298:
UUID=04b2cbb9-42a3-44ee-bdec-6fba361c72a5 /               ext4    errors=remount-ro 0       1
And you have a strange mount which you should comment out. line 301
UUID=3eb42d51-fe9a-41ba-a256-5f6178cdfd9e /mnt/3eb42d51-fe9a-41ba-a256-5f6178cdfd9e auto nosuid,nodev,nofail,x-gvfs-show 0 0


You also show now UEFI entry for Windows.
sudo efibootmgr -v
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi" -d /dev/nvme0n1 -p 1

---

