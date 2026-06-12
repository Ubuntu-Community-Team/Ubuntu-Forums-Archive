---
title: "Windows 8 won't boot after ubuntu-secure-remix install"
date: 2013-01-01
forum: Installation &amp; Upgrades
---

### Post by RabidWeezle on 2013-01-01
I installed from secure remix after hearing that uefi can mess with an ubuntu install. It worked pretty well, boots up and such. Now when I try to boot any windows uefi entry after running Boot Repair, it can't find the efi files.

Boot repair - Boot info summary:
[http://paste.ubuntu.com/1485382/](http://paste.ubuntu.com/1485382/)

---

### Post by oldfred on 2013-01-01
Are you using the new efi entries that Boot-Repair added. The entries by grub2's os-prober still have the bug.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
    

The one's added by Boot-Repair have efi in the description. Your files all look normal and should work. If not can you directly boot from UEFI menu?

You do have one issue. Not sure if it matters much. The protective MBR partition table is just to prevent old tools from not knowing the drive is gpt partitioned. But the entry in your MBR table is wrong.

> /dev/sda1 ends after the last sector of /dev/sdagdisk is in the repository and is the fdisk replacement for gpt partitioned drives.
sudo apt-get install gdisk

You may be able to just run gdisk and it may just fix the entry or you may have to have it write the partition table which would then also update the MBR entry.

The gpt table itself does not need fixing.
       repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

---

### Post by oldfred on 2013-01-01
Boot-Repair just had some updates. 

Some computers directly boot Windows efi entries just fine even with grub installed, others have to have grub's file as the Windows boot file and Boot-Repair backs up the Windows file & uses that to boot Windows. 

       How Boot-Repair works with UEFI systems - post 687 Dec 15, 2012
[http://ubuntuforums.org/showthread.php?t=1769482&page=69](http://ubuntuforums.org/showthread.php?t=1769482&page=69)

            Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)

---

