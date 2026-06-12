---
title: "Fresh install not adding MSDOS7 partition to grub menu"
date: 2012-05-31
forum: Installation &amp; Upgrades
---

### Post by yyyc186 on 2012-05-31
I did a fresh install.  I have both Windows XP and MSDOS7 as primary boot partitions and Ubuntu in extended partition.  Windows XP was added to grub menu, DOS was not.  The instructions I found on-line do not seem to work.  Does anybody have the entry they created to make DOS boot with the grub found on 12.04 LTS?

---

### Post by oldfred on 2012-06-01
I have not booted DOS since DOS days. But boot entry should be same chainload entry. Grub2's os-prober is probably not set to look for FAT partition with DOS.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

This is my entry, my UUID is optional if set root is correct and only if booting from a different drive might you need the drivemap command. 
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    insmod part_msdos
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 04b05b70b05b6768
    drivemap -s (hd0) ${root}
    chainloader +1
}

For dos you may need insmod fat

menuentry "DOS (on /dev/sda2)" {
    insmod fat
    insmod part_msdos
    set root=(hd0,2)
    chainloader +1
}

---

### Post by yyyc186 on 2012-06-01
Thanks,

boot-repair uses a different probe and found the partition.

---

