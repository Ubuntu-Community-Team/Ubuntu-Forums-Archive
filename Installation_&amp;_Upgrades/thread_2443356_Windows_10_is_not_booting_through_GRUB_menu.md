---
title: "Windows 10 is not booting through GRUB menu"
date: 2020-05-14
forum: Installation &amp; Upgrades
---

### Post by notkash on 2020-05-14
Hello Ubuntu Community,

I installed Ubuntu 20.04 on my Lenovo Flex 2 (i7-4500u, 8GB Ram, 500GB HDD, Intel HD) and intended it to run a dual boot computer. However, after installing Ubuntu, I have not been able to run Windows on my computer. I have the option of Ubuntu and Windows through the GRUB menu, but when I try to boot my computer into Windows, it reboots back into the GRUB menu. I installed GParted to show my partitions to make sure I did not install Ubuntu on my hard drive itself and only in the partition and it seems that Ubuntu is running through the partition and my Windows partition is separate. I have tried to install a clean copy of Windows 10, but before I do that I want to see what is the reason why my computer will not boot into Windows. I also have access to my Windows partition, but I wonder if there is a way during the install of Ubuntu I could have replaced my Windows OS while keeping the files and only have Ubuntu running. Any help would be appreciated. Thanks in advance!

---

### Post by oldfred on 2020-05-14
Grub only boots working Windows. Or Windows cannot need chkdsk nor have fast start up on which sets hibernation flag. 
And Windows likes to turn fast start up back on with updates.

But you have another issue. LDM or dynamic partitions on gpt partitioned drive.
Have seen one or two LDM systems, how did you get converted as most Windows installs are just standard gpt partitioned.

It used to be that you could not even see dynamic partitions from Linux. You can now see them, and maybe even mount them. But they really do not work with Linux. And they do not always work with everything in Windows. The use of dynamic partitions with old BIOS/MBR was a work around for the MBR limit of 4 partitions. Windows did not often use the primary, extended & logical partitions that Linux uses. But with gpt you have 128 partition limit, so no need for LDM.

[http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)
Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Shown as SFS in fdisk, Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx) & 
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from)
[https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv)
[http://manpages.ubuntu.com/manpages/trusty/man1/ldmtool.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/ldmtool.1.html)

---

### Post by notkash on 2020-05-16
@oldfred I tried to convert my partition into a basic partition but there is not a way to do it without using Windows and since I can not access it, I am at a loss. I also tried to disable secure boot and fast boot as you mentioned, but it says my disk is dirty and in order to fix it, I have to run Windows on my machine. Thanks for the help though.

---

### Post by oldfred on 2020-05-16
If UEFI system, you should be able to directly boot Windows from UEFI.
You may need f8 right after UEFI/BIOS screen to get into Windows internal repair screen.
But if that does not work, you need your Windows repair/recovery flash drive.

The repair disk does not have to be from your system, just a similar 64 bit (or 32) bit version.
Windows 10 repair disk
[https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795](https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795)
[https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html](https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html)
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)

---

