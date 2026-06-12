---
title: "dualbooting 2 ubuntu servers (encrypted lvm)"
date: 2014-02-04
forum: Installation &amp; Upgrades
---

### Post by PrSdNt on 2014-02-04
Okay, so I want to dualboot 2 ubuntu servers 13.10 on a single hdd. I have created 4 primary partitions (2x boot, non-encrypted) and two encrypted LVM in which the home, root & swap logical volumes are contained. Basically this is the setup:

- sda1: boot partition server 1
- sda2: encrypted LVM server 1 (root, home & swap)
- sda3: boot partition server 2
- sda4: encrypted LVM server 2 (root, home & swap)

Installation of server 1 went just fine. I could boot into the server. After the installation of server 2 (I chose to install GRUB in sda3), the system still booted in in server 1 (sda1 & 2). So I did an update-grub, but still it just found the images of server1 and not the ones on sda3. So after a lot of searching I found this page [http://askubuntu.com/questions/288281/dual-boot-grub2-not-detecting-ubuntu-server-10-4-64-bit-after-installing-ub]("http://askubuntu.com/questions/288281/dual-boot-grub2-not-detecting-ubuntu-server-10-4-64-bit-after-installing-ub"), which is pretty much the same problem I have. So I tried the solution that was given there (boot-repair), but unfortunately it did not solve my problem. It did however made a very detailed summary of my current setup: [http://paste.ubuntu.com/6874491/]("http://paste.ubuntu.com/6874491/").

It looks like the grub on sda1 is missing or corrupt. But actually that is the one that works! 

Does anyone have an idea how I can make this work?

Thanks!

oh, btw: I have also tried to install the GRUB of server 2 on the MBR. That way I could boot into server 2, but not into 1.

---

### Post by oldfred on 2014-02-04
I do not know LVM and encryption.

But have you tried just copying the entire boot stanza of the first entry of second install into 40_custom of first install and see if that boots? Not sure when you get asked for passphrase.

       gksudo gedit /etc/grub.d/40_custom

 sudo update-grub

Then grub menu in first root should have entry for second root.


```
 menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-2de282af-752e-46f5-8bd8-40b9b7fc2988' {
recordfail

 load_video
gfxmode $linux_gfx_mode
insmod gzio
insmod part_msdos
insmod ext2
set root='hd0,msdos3'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos3 --hint-efi=hd0,msdos3 --hint-baremetal=ahci0,msdos3  a5275030-553d-434a-bf4f-1c42c05e35c8
else
  search --no-floppy --fs-uuid --set=root a5275030-553d-434a-bf4f-1c42c05e35c8
fi
linux	/vmlinuz-3.11.0-12-generic root=/dev/mapper/vg02-root ro   
initrd	/initrd.img-3.11.0-12-generic


```

---

### Post by PrSdNt on 2014-02-05
I should have thought of that myself. It works perfectly! Thanks very much for the help.

---

