---
title: "Trying to install Jammy in a dual-boot Jammy with encrypted Bionic install"
date: 2022-12-09
forum: Installation &amp; Upgrades
---

### Post by shingalated on 2022-12-09
I'm trying install 22.04 side-by-side with an existing 18.04 install on several PCs. (We need access to both on the same PC for development purposes, and VMs aren't really an option.) 
22.04 is installed with encryption using the LVM/LUKS setup offered in the installer.

I think I'm most of the way there, but I'm having trouble getting the bootloader to decrypt the partition. 

Here's the steps I'm trying so far (tiny disk sizes since I'm just testing the process in a VM):

Boot 22.04 installer in live mode unlock the disk by clicking the encrypted volume that shows in Nautilus.
```
sudo lvs
```
Shows:
  LV     VG       Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root   vgubuntu -wi-a----  <30g                                                    
  swap_1 vgubuntu -wi-a---- 976.00m

Shrink the existing logical volume that 18.04 root FS is on:
```
sudo lvreduce --resizefs --size 10G /dev/ubuntu-vg/root
```

Create a new logical volume (LV) for the installer to use for 22.04:
```
sudo lvcreate -n jammy-root -L 15G ubuntu-vg
```

At this point
```
sudo lvs
```
Shows the new volume, old volume, and swap.

Then I launch the 22.04 installer from the desktop icon, and select manual partitioning.
I select the new LVM volume, "/dev/mapper/ubuntu--vg-jammy-root" select format, use as EXT4, mount point: /

I select the existing swap to reuse as swap for both OSes

I selected the existing /boot partition to use as /boot for both OSes (hopefully this doesn't cause too many issues and is workable, it seemed WAY easier than moving all the partitions around and resizing to allow for 2 /boot partitions. Which I'm trying to avoid since I need to do this procedure multiple times.)

The install completes with these settings. At this point if I reboot, I get a grub menu for both OS installs, neither install seem to be aware of the LVs being on an encrypted volume. I get the following message: 
```
Volume group "ubuntu-vg" not found
Cannot process volume group ubuntu-vg
```
And I'm put into a BusyBox shell.

I also tried running the same procedure as above, **instead of rebooting when the installer finishes** running the following commands:
```
echo 'ubuntu-vg UUID=(uuid without quotes) none luks,discard' > /target/etc/crypttab
mount -t proc proc /target/proc

mount --rbind /sys /target/sys

mount --rbind /dev /target/dev

chroot /target

grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader=ubuntu --boot-directory=/boot/efi/EFI/ubuntu --recheck /dev/sda

grub-mkconfig --output=/boot/efi/EFI/ubuntu/grub/grub.cfg

update-initramfs -ck all

exit

reboot

```

This gives the same result.
Anyone have any tips about how I can get this to work and be an easily repeatable procedure?

Thanks!

---

