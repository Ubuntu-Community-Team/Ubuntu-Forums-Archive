---
title: "Installing Ubuntu on SSD Raid + Win7"
date: 2015-05-22
forum: Installation &amp; Upgrades
---

### Post by Serguei_Alleko on 2015-05-22
Hello,

I have a desktop with a 1TB hard drive and a 2 SSD Raid (64GB total). There is Win7 installed on the first hard drive.

I was able to install Ubuntu on the raid and even Grub with the help of this [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) instruction.

When I boot from the SSD Raid, the Grub has both OSes listed, but fails to boot either Win7 or Ubuntu. Win 7 says there is no system drive and Ubutnu goes to initramfs.
If I boot from the HDD, Win7 still boots fine.

Could you please help me to configure Grub properly? Boot-repair Pastebin is [http://paste.ubuntu.com/11292701/](http://paste.ubuntu.com/11292701/) 

Thanks upfront!

---

### Post by oldfred on 2015-05-23
You have dynamic partitions on your hard drive, shown as SFS. Linux does not work with dynamic. It used to be though that you could not even install if any dynamic partitions were seen.
Since you seem to only have 3 partitions, not sure why it converted to dynamic. The dynamic is a proprietary Windows work around for the 4 partition limit with basic MBR partitions.

       Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

Ubuntu used to only install to RAID with server and with 12.04 the alternative installer, not desktop. But after 12.04 they eliminated the alternative installer and said they would add LVM & RAID capability to desktop gui installer. LVM was only added a couple of versions ago and many new users now incorrectly select it. And slowly RAID is working. It used to not be seen by install, then  it would install, but grub would not. 

Not sure what Boot-Repair did, you do need RAID drivers for everything to work.
Are you getting grub menu? If so then you are booting beyond what Boot-Repair can fix and it may just be a driver issue. And video driver issues are common particularly with nVidia.
Often nomodeset is required.

      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

