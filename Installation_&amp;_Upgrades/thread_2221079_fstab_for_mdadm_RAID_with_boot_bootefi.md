---
title: "fstab for mdadm RAID with /boot boot/efi"
date: 2014-04-30
forum: Installation &amp; Upgrades
---

### Post by hardwaremonkey on 2014-04-30
I am finally getting around to setting up RAID on my existing Ubuntu 12.04 box. In the past, I have relied on hardware RAID. This is my first time with mdadm and I have read several tutorials and I believe I have the RAID part nailed down (running on sda3 and sdb3 for root partition; no swap partition exists). I have not reboot to check things because I have run into a roadblock.

I modified my fstab to reflect the UUID of the RAID for the root partition. This is the only partition I have setup for RAID. But, the fstab is configured to use UUIDs that are mount points for sda for the /boot and /boot/efi partitions (running Grub 1.99).
```
# <file system>                           <mount point>   <type>  <options>            <dump>  <pass>
proc                                       /proc           proc    nodev,noexec,nosuid 0        0
UUID=455cf8f6-532c-442c-814c-b8c4d280d170  /               ext4    errors=remount-ro   0        1
/dev/mapper/server2-swap_1                 none            swap    sw                  0        0
UUID=ae67b87a-53b0-4689-9971-1e8417cb5bfd  /boot           ext2    defaults            0        2
UUID=4B56-F26C                             /boot/efi       vfat    defaults            0        1
```

I am not certain how to handle this. Would I create a different fstab for each drive, and then somehow exclude this from the RAID? That would be a pain to remember for maintenance. 

My objective: I would like to be able to pull the cable from one hard drive and have the system start up although the RAID is degraded, regardless of which drive is dead. How can I handle this with the fstab?

Thanks!!

---

### Post by hardwaremonkey on 2014-04-30
Are others perplexed or is this a really stupid question?

---

### Post by hardwaremonkey on 2014-05-02
Can anyone be a hero here? 

I am stuck. ](*,)I found an almost identical question on Ask Ubuntu that does not have an answer:
[http://askubuntu.com/questions/439090/server-13-10-raid1-lvm-efi-booting-on-2nd-disk/458966#458966](http://askubuntu.com/questions/439090/server-13-10-raid1-lvm-efi-booting-on-2nd-disk/458966#458966)

I am starting to think that the only option is to not mount the /boot or /boot/efi at all. Then, have the /boot/efi replicated on both drives manually (run an rsync with a temp mount). Lastly, point the bios to the /boot/efi of the working drive. Of course, this will not auto-recover from a reboot after a failed drive in the RAID.

Does that make any sense? It does not make much sense to me.:confused:

---

