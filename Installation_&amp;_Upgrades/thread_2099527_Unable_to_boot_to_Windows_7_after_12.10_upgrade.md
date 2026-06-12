---
title: "Unable to boot to Windows 7 after 12.10 upgrade"
date: 2012-12-29
forum: Installation &amp; Upgrades
---

### Post by nexusvergil on 2012-12-29
Hi everyone,

I recently upgraded to 12.10 and can no longer boot into Windows 7.  When I select the Windows 7 partition in grub I get "error: device format "ldm... invlaid: must be (f|h)dN, with 0<= N < 128" (... is a bunch of numbers and characters) then I press any key and get "a disk read error occured, press ctrl+alt+del to restart".  I have done a little research and this bug seems to be similar to mine [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255)

I have Ubuntu 12.04 on a usb that I can boot into for boot repair ("Workaround 3" in the above post), I just want to make sure that other people think that is a good idea, because I am fairly new to Ubuntu/grub.  Thanks for any advice!

---

### Post by oldfred on 2012-12-29
Welcome to the forums.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by nexusvergil on 2012-12-29
Thanks for the quick response.

[http://paste.ubuntu.com/1477507](http://paste.ubuntu.com/1477507)

---

### Post by oldfred on 2012-12-29
Did you convert Windows back from UEFI to BIOS? It is unusual to have the vendor repair partition to have efi files and be sda5.

Also you grub also is a bit unusual in that it is directly looking for core.img in the partition. Normally that is in the sectors after the MBR and before first partition. I would use Boot-Repair to update grub.

Windows looks like it has all its boot files, but NTFS partitions are real sensitive to any changes. They have to have the PBR - partition boot sector have correct info. Boot script generally says it is ok, but it does not check all the details. You may need to run chkdsk from a Windows repairCD or make other repairs from the Windows repairCD.
       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

    
       How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

---

### Post by nexusvergil on 2012-12-29
Thanks so much for the help, oldfred!

I ran boot repair, and I am now able to boot into my Windows 7 partition.

---

### Post by oldfred on 2012-12-29
It must have been related to how grub was loading. I was sure that it was something in Windows. :)

Glad you got it working.

---

