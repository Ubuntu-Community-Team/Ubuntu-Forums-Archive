---
title: "Can't boot after ubuntu installation"
date: 2015-03-13
forum: Installation &amp; Upgrades
---

### Post by Udit_Pratap on 2015-03-13
I had windows 7 installed on my laptop. I installed ubuntu 14.04 today and i got ubuntu installation complete message. On restart it doesn't boot in to windows or ubuntu. With windows it shows message that can't find OS, with ubuntu was getting [COLOR=#000000]Busybox (inframs) error. 
After logging in via live cd i did saw all my windows drives mounted. Then upon restart with live cd one drive (sda3) was missing which had windows 7 installation. Now this drive was shown as swap in disk utility but as ntfs in fdisk command.
Also UUID for sda3 and sda5 had duplicate uuids so i changed uuid for sda5.

I tried fixing boot with boot-repair utility in live cd mode. It shown successful message and then asked to reboot. But now its not even showing boot option, not even boot from live CD. Says missing OS.[/COLOR]

[COLOR=#000000]What should i do?[/COLOR]
[COLOR=#000000]Here is my boot repair summary report : [/COLOR][http://paste.ubuntu.com/10592826/](http://paste.ubuntu.com/10592826/)[COLOR=#000000] 

[/COLOR]

---

### Post by maria14 on 2015-03-13
Go to your BIOS and check the boot order again. Then check if you have the UEFI filmware. If yes then read this [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) . I am a total noob but I did a clean installation and I had the same problems and I did some research.Just another reminder:you have to create a BIOS boot partition if your disk is GPT . 
I am not sure this will help ,it took me quite some time to figure those out.

---

### Post by oldfred on 2015-03-13
It is showing SFS which is dynamic partitions which are proprietary to Windows and do not work with Ubuntu.
And then it looks like you overwrite at least part of that dynamic partitioning. Windows uses dynamic instead of the more common primary, extended & logical partitions that work for both Windows & Linux.

I do not know if any Windows repair tools can undo the mix of partitions you now have. 
If you did not have good backups of Windows & your data, and you can see anything be sure to back that up now.

       Microsofts offical policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from)

   Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

   Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Partition wizard repaired NTFS partition table that gparted could not see with disk label error
[http://ubuntuforums.org/showthread.php?t=2112005](http://ubuntuforums.org/showthread.php?t=2112005)

   EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

---

### Post by Udit_Pratap on 2015-03-14
I can access both SFS partitions but issue is with sda3 which it shows as NTFS but cant mount it as it gives error that it looks swap area.

---

### Post by oldfred on 2015-03-14
Swap is Linux overflow for not enough RAM or also used for hibernation. But it often it is used by live installer to speed things up. Do not boot live installer as that may overwrite data in that area.

As far as I know Linux tools will not let you recover data. You need to try the Windows tools.

For Linux and in general we often suggest testdisk and/or photorec. Testdisk restores old partitions and photorec just scans a hard drive for anything that looks like a file. Photorec can take a very long time, I used it and ran it overnight on a smaller drive.

But those that also use Windows suggest Windows tools for NTFS:
 An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam.

---

