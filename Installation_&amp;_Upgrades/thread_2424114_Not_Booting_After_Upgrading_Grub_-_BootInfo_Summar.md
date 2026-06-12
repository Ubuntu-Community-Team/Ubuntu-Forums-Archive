---
title: "Not Booting After Upgrading Grub - BootInfo Summary Included"
date: 2019-08-03
forum: Installation &amp; Upgrades
---

### Post by dpippin2 on 2019-08-03
Running Ubuntu 18.04 zfs on root. None of my drives are showing on boot getting error "No Symbol Table". I suspect grub got overridden by UEFI which my bios doesn't support and I'm running LSI Hardware SATA controller. I am not sure and have no idea how to fix if that is the case. See here for BootInfo Summary [http://paste.ubuntu.com/p/Z7GDgrRRFx/](http://paste.ubuntu.com/p/Z7GDgrRRFx/).

Thank you

---

### Post by oldfred on 2019-08-03
Do not know zfs.

Your BIOS must be UEFI as you booted live installer/Boot-Repair in UEFI mode. And it shows UEFI boot entries, essentially just for hard drive default.

You do have bios_grub on sda & sdg. Any gpt drive with grub in BIOS mode, will need a bios_grub partition. If booting from sda, and if everything else is ok, then it should boot. But grub in sda, seems to be looking for a UUID 84e7.... that does not exist on hd0 (sda), or hd7 (sdh). And sdh shows syslinux or a Windows type boot loader, which may just be your live installer. Did you have another hd7 connected before? 

Boot-Repair seems to not see your ZFS, it tried mounting as NTFS and then gave lots of errors. And then could not see / & fstab which it needs to see.
If you can mount zfs before running Boot-Repair booted in BIOS mode, you may get a better report.

---

### Post by dpippin2 on 2019-08-06
I ended up doing the following: 
[COLOR=#24292E][FONT=Calibri]Boot the live CD open a terminal.

$ sudo -i
# apt update
# apt install --yes zfsutils-linux[/FONT][/COLOR]
[COLOR=#24292E][FONT=Calibri]This will automatically import your pool.Export it and re-import it to get the mounts right:[/FONT][/COLOR]
[COLOR=#24292E][FONT=Calibri]# zpool export -a
# zpool import -N -R /mnt rpool
# zfs mount rpool/ROOT/ubuntu
# zfs mount -a

From here I ran an snapshot before I did the upgrade. I have still yet been able to get UEFI to work with running ZFS as root. [/FONT][/COLOR]

---

