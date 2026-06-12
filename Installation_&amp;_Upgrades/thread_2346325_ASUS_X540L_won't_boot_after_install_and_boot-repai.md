---
title: "ASUS X540L won't boot after install and boot-repair recommended repair"
date: 2016-12-13
forum: Installation &amp; Upgrades
---

### Post by viktor-tolnai on 2016-12-13
Hi Guys,

I hope you can tell what's the solution what I've experienced. My pastebin URL is the following: [http://paste2.org/sg92Kts8](http://paste2.org/sg92Kts8)

Thanks in advance, if I need to give any more detail to able to solve this situation please let me know.

Regards,
Viktor

---

### Post by oldfred on 2016-12-13
It says grub re-installed correctly.

If you hold shift key from BIOS until grub menu appears, does menu appear?

Is this an UEFI system, but you have reinstalled in BIOS/MBR configuration?

If UEFI is secure boot off in UEFI? BIOS system will not boot with UEFI secure boot on.

Several Asus models have needed boot parameter pci=nomsi which you manually add to linux line when in grub menu. Use e to open edit and scroll to linux  line. Replace quiet splash to test if that parameter works. We can make it permanent if needed.
 Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[https://ubuntuforums.org/showthread.php?t=2327570](https://ubuntuforums.org/showthread.php?t=2327570) 


 How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by viktor-tolnai on 2016-12-15
Hi,

I pressed shift key, grub menu is appeared

It is an EFI system yes, I already tried to install Ubuntu in EFI only mode (when I turn off Compatibility Support Mode) with same result. The main reason why I tried to install in MBR mode to install because I checked with gparted the old HDD what I removed when I installed the SSD. It has the same partitions just I wanted to try because EFI is failed.

Yes, EFI secure boot is disabled

I tried pci=nomsi switch, but nothing changed. empty black screen is what I saw.

I really don't want to replace back the HDD, cause it is too slow. BTW I tryed to install windows 8.1 in CSM enabled but installation is failed, I tried again with CSM disabled, but the result was the same.
I was curious and because of this I've connected the old HDD via an external SATA bay, and after I choose it in the boot menu, the ubuntu is booted up from the old HDD.

Any other idea what can I try to solve this situation?

---

### Post by oldfred on 2016-12-15
Did you replace quiet splash with the pc=nomsi? That may start to show something?

Grub is saying something about labels.
With grub labels are really whether drive is gpt or MBR(msdos).
And if not correctly converted from gpt to MBR, then Linux tools get confused.

Windows does not correctly see Linux partitions. 
You either have to have a NTFS primary partition with boot flag, if MBR. 
With UEFI it wants a variety of partitions, so often best to install it first.

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--]("https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference")

---

### Post by viktor-tolnai on 2016-12-16
Yes, I deleted queiet splash option from the linux line and inserted pci=nomsi. After that when I pressed F10 to boot, it was just a blank screen nothing more.

My target is just a clean Ubuntu install without anything else. The windows installation was just a try, but I really don't need it.

Could you explain the labels please? What I did: I removed all partitions from the SSD, and after that I created a new partition table in msdos. As I remember I didn't made any changes after that, just I installed the Ubuntu from a Live CD. Am I missed something with the labels?

---

### Post by oldfred on 2016-12-16
I used to think labels meant just the partition labels you can add. And with gpt it has another label.
And with fstab and inside grub menu you can mount partitions with labels.

But we have see systems where grub says label error and it did not make sense to me.
It turns out it also is calling the type of partitioning gpt(GUID) or MBR(msdos) a label.

So you may have a partition type error or a misconfigured grub entry if using root=label=xxxx.

Windows has been known to incorrectly convert a gpt drive to MBR, leaving the backup gpt partition table at end of drive. MBR does not have a backup.

       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

If only using Ubuntu there are some minor advantages of gpt whether BIOS or UEFI. 
But Windows will only boot from gpt with UEFI, so if wanting to use gpt then you must install in UEFI boot mode.
 

 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

---

### Post by viktor-tolnai on 2016-12-16
Hmm, it is quiet interesting for me what you've wrote. 
In the grub menu, I mean after I press 'e' I see similar like this:
linux /boot/vmlinuz-....... root=UUID=blahblahblah

I don't know partition tables, maybe my question too stupid: can be a possible problem if the partition table is msdos, but somehow the partitions using GPT scheme instead of MBR? 

UUID means this is a GUID for me.

---

### Post by oldfred on 2016-12-16
UUID is a partition ID. Unique to a partition so system will always boot that partition.
GUID is a gpt partition ID. That make a unique type of gpt partition.

       GPT info
[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)
[http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

Old versions of fdisk immediately told you that you had both MBR & gpt. But now fdisk works with gpt and does not give the same error message.

See what this says, but make no changes.

 [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda

---

### Post by viktor-tolnai on 2016-12-19
I've downloaded a Linux Mint, I disabled the CSM in the BIOS/EFI. The installation went fine (as Ubuntu as well) and after everything works. The boot problem are gone. Is anybody knows what's different between Ubuntu 16.04.1 and Linux Mint 18.1?

---

