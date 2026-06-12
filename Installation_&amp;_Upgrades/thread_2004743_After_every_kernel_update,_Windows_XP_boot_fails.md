---
title: "After every kernel update, Windows XP boot fails"
date: 2012-06-16
forum: Installation &amp; Upgrades
---

### Post by rhauff on 2012-06-16
I have a triple boot setup on a Compaq Presario CQ60.  The problem is each time Ubuntu (12.04) updates the kernel, Windows XP will not boot.

I am able to fix it by running "Boot Repair", selecting advanced, then checking "Restore MBR", then apply & let it finish.  Next I run "Boot Repair" again, Advanced, and "Reinstall Grub" and apply.

How can I fix this so I don't have to go through all this each time I want to boot Windows? (Which I do only about as frequently as the kernel updates ;-) )

Here is the OS prober portion of my grug.cfg:

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 3AC0532DC052EF1F
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "LinuxMint GNU/Linux, with Linux 3.2.0-2-486 (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root dd0a1cfb-bcf7-4ab9-b462-933d34b3d04d
	linux /boot/vmlinuz-3.2.0-2-486 root=UUID=dd0a1cfb-bcf7-4ab9-b462-933d34b3d04d ro splash quiet
	initrd /boot/initrd.img-3.2.0-2-486
}
menuentry "LinuxMint GNU/Linux, with Linux 3.2.0-2-486 (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root dd0a1cfb-bcf7-4ab9-b462-933d34b3d04d
	linux /boot/vmlinuz-3.2.0-2-486 root=UUID=dd0a1cfb-bcf7-4ab9-b462-933d34b3d04d ro single splash
	initrd /boot/initrd.img-3.2.0-2-486
}
menuentry "LinuxMint GNU/Linux, with Linux 3.0.0-1-486 (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root dd0a1cfb-bcf7-4ab9-b462-933d34b3d04d
	linux /boot/vmlinuz-3.0.0-1-486 root=UUID=dd0a1cfb-bcf7-4ab9-b462-933d34b3d04d ro splash quiet
	initrd /boot/initrd.img-3.0.0-1-486
}
menuentry "LinuxMint GNU/Linux, with Linux 3.0.0-1-486 (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root dd0a1cfb-bcf7-4ab9-b462-933d34b3d04d
	linux /boot/vmlinuz-3.0.0-1-486 root=UUID=dd0a1cfb-bcf7-4ab9-b462-933d34b3d04d ro single splash
	initrd /boot/initrd.img-3.0.0-1-486
}
menuentry "LinuxMint GNU/Linux, with Linux 2.6.39-2-486 (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root dd0a1cfb-bcf7-4ab9-b462-933d34b3d04d
	linux /boot/vmlinuz-2.6.39-2-486 root=UUID=dd0a1cfb-bcf7-4ab9-b462-933d34b3d04d ro splash quiet
	initrd /boot/initrd.img-2.6.39-2-486
}
menuentry "LinuxMint GNU/Linux, with Linux 2.6.39-2-486 (recovery mode) (on /dev/sda3)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root dd0a1cfb-bcf7-4ab9-b462-933d34b3d04d
	linux /boot/vmlinuz-2.6.39-2-486 root=UUID=dd0a1cfb-bcf7-4ab9-b462-933d34b3d04d ro single splash
	initrd /boot/initrd.img-2.6.39-2-486
}
### END /etc/grub.d/30_os-prober ###

---

### Post by rhauff on 2012-08-19
After the last couple kernel updates, I have not  been able to repair the windows XP boot.  I was using the program "Boot Repair" and checking "Restore MBR" but that no longer works.  Any ideas??

---

### Post by oldfred on 2012-08-19
Post link from BootInfo report.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

Grub remembers where to reinstall, so I want to make sure it is not set for the wrong place.
And post this from both your systems or the one causing the issue:

#To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

---

### Post by rhauff on 2012-08-19
Here is the link to my Boot-info summary

[http://paste.ubuntu.com/1156424/](http://paste.ubuntu.com/1156424/)

---

### Post by oldfred on 2012-08-19
Boot script looks normal.

Post this from both installs:

#To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

---

### Post by rhauff on 2012-08-19
Ubuntu 12.04 is the main OS I run, and that is the one that gives me the problem when I update.  I believe I installed Mint first, Ubuntu 2nd, and Windows XP 3rd.

Here is the grub info you requested from Ubuntu:

roland@rolands_CQ60_Laptop:~$ sudo debconf-show grub-pc
  grub-pc/kopt_extracted: false
  grub2/kfreebsd_cmdline:
  grub2/device_map_regenerated:
* grub-pc/install_devices: /dev/disk/by-id/ata-ST9160827AS_5RF37BGD
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/disk_description:
  grub2/linux_cmdline:
  grub-pc/install_devices_empty: false
  grub2/kfreebsd_cmdline_default: quiet
  grub-pc/partition_description:
  grub-pc/install_devices_failed: false
  grub-pc/install_devices_disks_changed:
  grub2/linux_cmdline_default: quiet splash
  grub-pc/chainload_from_menu.lst: true
  grub-pc/hidden_timeout: false
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/timeout: 2
roland@rolands_CQ60_Laptop:~$  sudo grub-probe -t device /boot/grub
/dev/sda5

---

### Post by oldfred on 2012-08-20
I just wanted to check that some where you had not installed grub2 to the Windows partition and it was reinstalling. It looks like it reinstalls to the drive.

Generally LInux changes do not change XP booting, but my XP was on a separate drive.

---

