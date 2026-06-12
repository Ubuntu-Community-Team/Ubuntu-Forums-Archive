---
title: "Uninstalling - partition problems"
date: 2007-09-29
forum: Installation &amp; Upgrades
---

### Post by whereami on 2007-09-29
i recently tried to uninstal kubuntu from my machine (previously dual booting xp and kubuntu) and all went well untill i tried to remerge the partitions.

i had my partitions set up where windows was on one NTFS partition, kubuntu was on its own partition and inbetween them was one large FAT32 partition with all my files, accesable from both OSs.

after i used my windows instal disk to resotre the MBR, i used partition magic to delete the kubuntu partitions,  add that extra space into my FAT32 partition, then make my NTFS partition a little smaller now that i had more room on the FAT32 one. 

when i rebooted my machine however and it was performing the partitioning, it had an error and i have not been able to boot back into windows since then. i recieve a STOP 0X24 error every time.

any suggestions?

---

### Post by Pumalite on 2007-09-29
Do you have any OS in the system?

---

### Post by jbuc89 on 2007-09-30
Here is a description of your error.  Something bad probably happened when you were resizing your NTFS partition.

Stop    0x00000024 or NTFS_FILE_SYSTEM

The Stop 0x24 message indicates that a problem occurred within Ntfs.sys, the driver file that allows the system to read and write to NTFS file system drives. A similar Stop message, 0x23, exists for the file allocation table (FAT16 or FAT32) file systems.

You will need to either boot into safe mode or into the recovery console to run the chkdsk program on your hard disk containing the NTFS partition.

Safe Mode
When Windows boots, you press the F8 key to enter a special boot menu that contains the safe-mode boot options. You typically choose from three safe-mode variations: Safe Mode, Safe Mode With Networking, and Safe Mode With Command Prompt. Standard safe mode comprises the minimum number of device drivers and services necessary to boot successfully.

Just  chose Safe Mode with Command Prompt.  If you get a command prompt, execute the chkdsk program.  If you can't boot into Safe Mode then you will have to try the Recovery Console.

Recovery Console
When you boot a system from the Windows CD or boot disks, you eventually see a screen that gives you the choice of either installing Windows or repairing an existing installation. If you choose to repair an installation, the system prompts you to insert the Windows CD (if it isn't already loaded in the system's CD drive) and then to choose among two repair options: to start the Recovery Console or to initiate the emergency repair process. If you press the F10 key at the Setup Welcome screen, you bypass the menu options and take a shortcut directly to the Recovery Console.

When you get a command prompt, execute the chkdsk program.

Hope this helps.

---

