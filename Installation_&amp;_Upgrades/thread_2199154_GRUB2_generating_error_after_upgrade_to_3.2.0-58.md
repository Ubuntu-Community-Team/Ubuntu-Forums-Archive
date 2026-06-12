---
title: "GRUB2 generating error after upgrade to 3.2.0-58"
date: 2014-01-12
forum: Installation &amp; Upgrades
---

### Post by hoggsoft on 2014-01-12
Something went horribly wrong when I upgraded to 3.2.0-58. GRUB2 generated a duplicate entry for Previous Linus versions and also I think I saw 3.2.0-58 and 3.2.0-57 repeated twice. I tried deleting v57 off the system but grub is still generating an error.

/etc/grub.d$ sudo update-grub
[sudo] password for robert: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found linux image: /boot/vmlinuz-3.2.0-56-generic
Found initrd image: /boot/initrd.img-3.2.0-56-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 12.10 (12.10) on /dev/sda3
Found Windows Vista (loader) on /dev/sdc1
error: syntax error.
error: Incorrect command.
error: syntax error.
error: Incorrect command.
error: syntax error.
error: line no: 121
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
done

I have tried to attach the grub.cfg.new file but the uploaded always says the file is invalid. Don't know. Not tried this before.

I would appreciate any advice or help given.
Thanks
Rob.

---

### Post by hoggsoft on 2014-01-12
Further information here [http://paste.ubuntu.com/6739595/](http://paste.ubuntu.com/6739595/)

---

### Post by oldfred on 2014-01-13
Not sure if related to your posted issue.
But sda is a gpt drive and grub will not install to a gpt drive unless you have a 1 or 2MB unformatted partition with the bios_grub flag. It can be anywhere on drive. Use gparted to create that.
Shown as error on line 1420 in Boot-Repair.

You also have Windows main install in sdb1, but have the Windows boot partition in sdc1. Usually those are both on the same drive, but you must have installed to sdb when BIOS was set to boot from sdc. I would copy bootmgr & BCD as backups into your main install. But grub may then show both as bootable.

With multiple drives best not to run Boot-Repairs auto repair. Use advanced and install Windows boot loader to the Windows boot drive (sdc) and grub to Ubuntu drive.

With multiple drives I prefer to configure systems with Windows on one drive and Ubuntu on another. And every drive should have an operating system.
       Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

### Post by hoggsoft on 2014-01-13
Thanks oldfred but I am not sure I understand any thing of what you said.

I have had Ubuntu installed as it is for quite a long time now without problems. It was only after upgrading to v58 that a problem arose.

Is there not some way of editing the nn_* files in /etc/grub to remove the error?

---

### Post by oldfred on 2014-01-13
You still need to fix what I posted above.

But what is line 121? That is not the same line number in Boot-Repair. Often when grub has error it keeps old grub.cfg and creates a new grub.cfg.new. Do you have one of those. It may show error and you can check line 121 in it.

You also have in your grub.cfg ldm parameters for mounting Windows which is very unusual. Linux has been trying to add some feature to read the proprietary dynamic partitions that Windows creates when you go over the 4 partition limit with MBR, but you do not show dynamic partitions. fdisk shows them as SFS. And dynamic still do not work with Linux.

> menuentry 'Windows Vista (loader) (on /dev/sdc1)' --class windows --class os $menuentry_id_option 'osprober-chain-C630FDA730FD9E9D' {
	insmod [COLOR=#ff0000]ldm[/COLOR]
	insmod ntfs
	set root='ldm/0025eb16-4f7a-11dd-8750-e831b819f9c9/Volume2'

---

### Post by hoggsoft on 2014-01-13
Actually, I have fixed my problem. What I did was to restore /etc/grub.d/10_linux_proxy from the last backup before it all went wrong. I then ran update-grub which ran without error. Grub Customizer looks different but will save without error.

---

