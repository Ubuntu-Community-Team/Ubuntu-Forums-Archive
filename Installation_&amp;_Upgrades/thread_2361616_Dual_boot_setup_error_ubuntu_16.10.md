---
title: "Dual boot setup error ubuntu 16.10"
date: 2017-05-18
forum: Installation &amp; Upgrades
---

### Post by supaboi on 2017-05-18
I am trying to setup dual boot on my system. 
I downloaded the file made the live USB and started the installation but where I am supposed to create partitions the space I free is not showing on the list as "free space" like it should.

---

### Post by ajgreeny on 2017-05-18
Are you using a BIOS system with all four partitions already in use?  What OS do you have installed at present?

From the live installer run gparted and show us a screenshot of the gparted window.

Please save the screenshot to disk, even if a live system, then use the paperclip icon in the toolbar of the **Reply to Thread** window, browse to the saved image and upload it here in your reply.

---

### Post by supaboi on 2017-05-21
i am using windows 10 right now i am what you would call a noob.
yes all the 4 partitions are in use but when i was trying to install ubuntu i made some space using the windows disk management 
but when it was showing to be unusable space and another even partitioning it wasnt shown seperately
idk what gparted is i checked it up and i didnt use it
[ATTACH=CONFIG]275221[/ATTACH]

---

### Post by xpeaceservant on 2017-05-21
I recently made a partition and had success doing so watching this instruction and using this software.

[https://youtu.be/ujqqE4QCYdo](https://youtu.be/ujqqE4QCYdo)

The software for the partition is called Gparted Live. It's free to use after download.

I should add that the Gparted Live has great visual tools indicating how much space the partition has.

---

### Post by Bucky Ball on 2017-05-21
Welcome. Bit off-topic but throwing in before you get much further. I wouldn't bother with 16.10. It only has a couple of months of support left. Go for the long term and very stable 16.04 LTS (supported until 2021) or the newest interim release 17.04 (supported for nine months from April 2017).

16.10 is not a good place to start as you'll be reinstalling or upgrading the OS in five minutes! Just saying. :)

(PS: Your screenshot shows your disk is full of partitions. You need to shrink or delete one to make free, unallocated space to install Ubuntu. I think you are wanting to install to the big healthy one? Ubuntu doesn't use NTFS file system for the OS. Just delete the partition because *you need free, unallocated space* to install the Ubuntu OS to. NO partition. :))

(PPS: Don't try installing Ubuntu again until you know you have free space to install it to as you run the risk of wiping out valuable data. You should have that backed up before doing this in any case, as I'm sure you have. ;))

---

### Post by oldfred on 2017-05-21
Besides having all NTFS partitions which Ubuntu cannot install into, but can read, you converted drive from basic to dynamic partitions.
That is a Windows proprietary partitioning system that does not work with Linux.
And Microsoft considers it a one way conversion. The make it easy to convert to dynamic but impossible to convert back.
Some third party tools do work, usually but have good backups (which you should have anyway, if installing new system).

       [http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)
Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Shown as SFS, Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html) 
    
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

---

### Post by supaboi on 2017-05-24
[ATTACH=CONFIG]275276[/ATTACH][ATTACH=CONFIG]275277[/ATTACH]


at first i tried using gparted in ubuntu itself(the trial version)
then deleted the volume from disk management in windows 10 then i tried in ubuntu again 
but in both cases Gparted shows it two volumes to be mixed or one volume and the space i freed in windows disk management
is it because i tried to dual boot once before and then made the volumes again??
what should i do for DUAL BOOT now!!!!!!!!!!!!!!??????????

---

### Post by oldfred on 2017-05-24
You have to remove the dynamic partitions.

Use Windows tools to shrink NTFS partitions and always reboot after a change.
But never use Windows to create partitions for Linux as it cannot create Linux type partitions.
And it can convert to dynamic like happened to you.

Either totally backup and reinstall Windows.
Or backup and see if the third party tools convert partitions.
If any partitions are empty, best to delete with Windows before conversion.

---

