---
title: "Grub: how is location of /boot configured?"
date: 2021-07-31
forum: Installation &amp; Upgrades
---

### Post by 7-mike-x on 2021-07-31
I have 2 Ubuntu 20.04 systems.
One, recently created from Live USB, allowed me to specify a boot partition separate from the root file system. The root file system is inside a (LVM) logical volume in an extended partition on the same device. The separate boot partition is mounted at /boot in the root file system.
The other looks like it has been tweaked by Grub Customizer, and the boot images are in a /boot directory - part of the root file system, and **not** inside a separate boot partition - which does exist, and is empty.
My question is:

[LIST]
[*]How does grub find the boot images on that 2nd system, where they are located inside a logical volume?
[*]And how was grub configured to support that placement?
[/LIST]

---

### Post by TheFu on 2021-07-31
LVM used a separate boot partition.
If LVM isn't used, a separate boot partition is not necessary.

Customization for everything can be accomplished by choosing "do something else" in the installer.

For clarity, perhaps if you ran boot-info on each system and compared the differences, it would jump out? It isn't just grub. It is the initramfs supported modules too.

---

### Post by MAFoElffen on 2021-07-31
In addition, the bootloader of grub should be installed to the base of the root drive (the simple explanation).

---

### Post by 7-mike-x on 2021-08-10
Answering my own question:
The location of /boot (more exactly, /boot/grub) is hard-coded into core.img, which is written to
sector 1 of the boot drive by grub-mkimage during grub-install.
The location of /boot/grub can be specified at grub-install via the --boot-directory option.
As of Ubuntu 20.04, at least, a separate boot partition is not required when installing on LVM
with Live CD/USB. During install, if "Something Else" is selected, and /boot is NOT separately
specified, then it will be created within the partition/logical volume specified via mount point "/".

---

### Post by MAFoElffen on 2021-08-10
LOL. Additional (again) to your explanation... (You are talking BIOS Booted Grub)

Then you add another Ubuntu installation (or other Linux Variants), like you have (and I)... Where there is still a /boot object added and mounted in each of the OS'es fstab files... They still exist somewhere. When you do an update-grub, the process does a OS-Probe, finds "other" OS'es and adds to the current Grub Menu. As both use Grub, whichever is the last system you updated Grub with becomes the first in the Grub Menu. So that order in the menu may change as you do system updates on each system... It's a juggling act. I keep it straight by having something different in the desktop, so I know  am. LOL

---

### Post by TheFu on 2021-08-11
Here's a 20.04 system with LVM:
```
$ df -Th
Filesystem                      Type  Size  Used Avail Use% Mounted on
/dev/vda1                       vfat  511M  7.1M  504M   2% /boot/efi
/dev/mapper/vgubuntu--mate-root ext4   19G   15G  3.4G  82% /
/dev/mapper/vgubuntu--mate-home ext4   12G  6.3G  4.9G  57% /home
```

```
$ sudo lvs
  LV     VG            Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  home   vgubuntu-mate -wi-ao---- 12.00g                                                    
  root   vgubuntu-mate -wi-ao---- 19.00g                                                    
  swap_1 vgubuntu-mate -wi-ao----  4.10g    

```

I can confirm that /boot is part of / and inside the root LV.

On a different system, with LVM + encryption, 
```
$ dft
Filesystem                            Type  Size  Used Avail Use% Mounted on
/dev/sda2                             ext2  721M  255M  430M  38% /boot
/dev/sda1                             vfat  511M  6.7M  505M   2% /boot/efi
/dev/mapper/ubuntu--mate--vg-root     ext4   25G   21G  3.2G  87% /
/dev/mapper/ubuntu--mate--vg-home--lv ext4   74G   24G   48G  34% /home
/dev/mapper/ubuntu--mate--vg-stuff    ext4   99G   57G   37G  62% /stuff

$ sudo lvs
  LV      VG             Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  home-lv ubuntu-mate-vg -wi-ao----  75.00g                                                    
  root    ubuntu-mate-vg -wi-ao----  25.00g                                                    
  stuff   ubuntu-mate-vg -wi-ao---- 100.00g                                                    
  swap_1  ubuntu-mate-vg -wi-ao----  <4.46g
```

FYI, 
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'

---

