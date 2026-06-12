---
title: "Unable to boot Windows &lt;UEFI&gt; using grub even after boot-repair"
date: 2014-01-11
forum: Installation &amp; Upgrades
---

### Post by harisishere on 2014-01-11
Hi,

As mentioned in the Ubuntu community, I tried Ubuntu 13.04 64bit , and went ahead with the installation after making sure that the live session was loaded without ay issues. But after the installation I was not able to boot windows (I could do that by changing the boot option in BIOS , to boot from Windows boot loader). So, as described in the community, I went with the Boot-Repair.

The URL i got was [http://paste.ubuntu.com/6722678/](http://paste.ubuntu.com/6722678/)

Please help me out. Thanks in advance.

---

### Post by oldfred on 2014-01-11
Your Windows is in BIOS mode and Ubuntu is in UEFI mode.
You must have a newer system that supports UEFI, but Windows was BIOS.
The only way you can dual boot if from UEFI/BIOS as once you start booting in one mode you cannot switch or grub menu will not ever work.

But you have another issue, in that your install in sda has been converted from basic partitions to dynamic. Linux does not read nor work with dynamic partitions. Also some Windows tools do not work as it is a logical partition overlay over the physical or basic partitions. If in Windows you still have a one to one logical to physical you can unconvert with third party tools. But if you have 5 or more dynamic partitions it may not work.

       Microsofts offical policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

    
 Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)


 Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

---

### Post by harisishere on 2014-01-11
Thans a lot oldfred for coming up with such a detailed explanation. I will explore the options that you suggested and get it working.

---

### Post by oldfred on 2014-01-11
Since it is easier to convert Ubuntu to BIOS than convert Windows to UEFI, you can use Boot-Repair to convert. It un-installs grub-efi and installs grub-pc. You will need to add a 1 or 2MB unformatted partition with the bios_grub flag to have grub install correctly on a gpt partitioned drive. Boot-Repair will not create that for you.
Then you can dual boot from grub menu if you want and have removed the SFS or dynamic partitions from Windows so Linux tools can correctly see the NTFS partitions. 

Or you can dual boot from UEFI/BIOS or one time boot key which most systems have.

---

