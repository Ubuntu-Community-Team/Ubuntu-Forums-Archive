---
title: "Hard drive doesnt load all of the partitions"
date: 2014-08-25
forum: Installation &amp; Upgrades
---

### Post by farbod2 on 2014-08-25
Hi,
Im trying to install ubuntu on my ASUS n56J laptop and I have a problem.

I have a partition for my windows with 62GB space.
25GB free space.
a rest of my hard is a partition.

now I only need a partition for some of my files and the rest of my hard is not important and i can format but in ubuntu partition manager i can only see this :
dev/sda1 1MB
dev/sda2 104MB
dev/sda3 62GB
dev/sda4 937GB 

btw my HDD is 1Tb.

no where is my free space that i created and even if I shrink or make a new partition again I see these thing !

what can I do now?
tnx

---

### Post by nerdtron on 2014-08-25
Post the screenshot of the partition manager of windows.

---

### Post by farbod2 on 2014-08-25
Here u go
[ATTACH=CONFIG]255826[/ATTACH]

---

### Post by farbod2 on 2014-08-25
and btw the installed windows is win8 if there's a way that I can replace ubuntu with win8 I'll be happy to know it ...

---

### Post by nerdtron on 2014-08-25
You're using a Dynamic Disk and unless an experts corrects me here, I think you should convert your disk format to a normal Disk which you will need to repartition and reformat your hard drive. Then you can install both windows and ubuntu successfully.

> if there's a way that I can replace ubuntu with win8 I'll be happy to know it

Windows 8 is already installed and you still want to install windows 8? Can you clear this up?

---

### Post by oldfred on 2014-08-25
If you want to keep Windows you have to undo the dynamic partitions.
Microsoft has no way to undo it other than full backup delete everything and reinstall/restore from backup.

There are third party tools that may convert back if you have 4 or fewer partitions. But to install Linux you need one of the 4 primary partitions to be the extended partition which then is a container for as many logical partitions as you want.

       I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
       [http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
    
 EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

---

### Post by farbod2 on 2014-08-26
> **nerdtron said:**
> You're using a Dynamic Disk and unless an experts corrects me here, I think you should convert your disk format to a normal Disk which you will need to repartition and reformat your hard drive. Then you can install both windows and ubuntu successfully.



Windows 8 is already installed and you still want to install windows 8? Can you clear this up?

> **oldfred said:**
> If you want to keep Windows you have to undo the dynamic partitions.
Microsoft has no way to undo it other than full backup delete everything and reinstall/restore from backup.

There are third party tools that may convert back if you have 4 or fewer partitions. But to install Linux you need one of the 4 primary partitions to be the extended partition which then is a container for as many logical partitions as you want.

       I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
       [http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
    
 EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

Tnx for your answers.
I dont want to keep win8 I just want to delete it.
ok i will try it ...
I will get a backup and correct me if im wrong .... after backup I should format my hard disk and then convert my dynamic disc to basic disc with a 3rd party software like partition magic as you mentioned . right ?

---

### Post by fantab on 2014-08-26
Right.

However, I'd say dual boot and keep both Win8 and Ubuntu. Keep Win8 atleast until such time you don't need it.
Backup... change partitions back to 'Simple' and lets us know if you want to dual boot.

---

### Post by farbod2 on 2014-08-26
Its a good idea but you said I should format my hard disk !
So you think its better to install windows again and then ubuntu ?

---

### Post by oldfred on 2014-08-26
Do you have recovery disk that you have to create from Windows backup or Vendor recovery?
If you totally erase drive the vendor recovery that is on hard drive is also erased. Of when hard drive fails do you have a way to restore Windows?
Some later want to sell PC and want to restore Windows, If you have full vendor set of DVDs then it is easy, otherwise...

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by farbod2 on 2014-08-28
Hi,
I've got a backup from my files and deleted all of my partitions and converted my hard disk to basic and now everything is fine ^_^

tnx for ur prefect answers

---

