---
title: "Missing Operating System after boot repair."
date: 2014-03-24
forum: Installation &amp; Upgrades
---

### Post by Akshay_rastogi on 2014-03-24
Please help me out, I wanted to install Ubuntu on windows 8 PC but unfortunately I am not able install it on PC and i lost my window boot. This was happened after running boot repair. Here is the link, please analyze it and provide me a valid solution as soon as possible. And please me out i am not able to install Ubuntu on my PC.

[http://paste.ubuntu.com/7146170/](http://paste.ubuntu.com/7146170/)

[http://paste.ubuntu.com/7146885/](http://paste.ubuntu.com/7146885/)

I have run Boot-repair two times so as to trying to rectify myself but no success achieve.

Thank You.

---

### Post by Mark Phelps on 2014-03-25
According to the reports, all your partitions are NTFS and are shown as "SFS" -- which I believe means that you have converted them all to Dynamic Disks  This is the result when you try to force the creation of too many partitions on a drive.  Linux can't handle Dynamic Disks.

The first thing you would need to do is convert back to Basic Volumes -- which you can't do with Linux filesystem utilities.

I think you might be able to do this using the Minitool Partition Wizard Boot CD, but I don't remember if the free version includes this conversion function.

---

### Post by Akshay_rastogi on 2014-03-25
Is it possible that I get my Windows os back, cause reformatting really going to cost me lot in sense of my data stored in it. So please provide me any suitable solution to roll back to my Windows os.

Thank You.

---

### Post by oldfred on 2014-03-25
More info on dynamic.

 Microsofts offical policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from)

The free versions used to offer conversion, but they may now only offer it in the upgraded non-free versions.

 EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

---

### Post by Akshay_rastogi on 2014-03-25
But according to me this problem is caused by the boot-repair because before that it was working fine, so do you thing it can be rectify with the help of boot-repair again?

---

### Post by fantab on 2014-03-25
> **Akshay_rastogi said:**
> But according to me this problem is caused by the boot-repair because before that it was working fine, so do you thing it can be rectify with the help of boot-repair again?

Boot-Repair will NOT convert 'Basic' disk to 'Dynamic'. Like Mark pointed out this happens on a 'MBR' disk only which has a ONLY 4 Primary Partition Limit... When you force a fifth Primary then Windows will convert the Disk to Dynamic.
You never installed Ubuntu to that disk.
However, when you ran Boot-Repair it may have messed up Windows boot... 
Fix Windows boot first: [http://windows7themes.net/how-to-fix-bootmgr-is-missing-in-windows-8.html](http://windows7themes.net/how-to-fix-bootmgr-is-missing-in-windows-8.html)
Then follow Mark's and oldfred's advice to convert the Dynamic Disk to Basic... BackUp you DATA first.

Good Luck...

---

### Post by oldfred on 2014-03-25
Boot-Repair cannot even work on nor create SFS or dynamic partitions. It is just showing what you did.

It is proprietary Windows partitioning so only Windows tools can create dynamic partitions.

---

### Post by Akshay_rastogi on 2014-03-25
> **oldfred said:**
> Boot-Repair cannot even work on nor create SFS or dynamic partitions. It is just showing what you did.

It is proprietary Windows partitioning so only Windows tools can create dynamic partitions.

Yes! i know that my drives are dynamic because while running window 8, I have created one extra drive which made my drives dynamic, but that I have done four month ago, and my windows was running smoothly, but after trying to install Ubuntu on my machine i had tried boot-repair for successful installation which according to me made some changes and thereafter, I am unable to boot my windows.

---

### Post by Akshay_rastogi on 2014-03-25
> **fantab said:**
> Boot-Repair will NOT convert 'Basic' disk to 'Dynamic'. Like Mark pointed out this happens on a 'MBR' disk only which has a ONLY 4 Primary Partition Limit... When you force a fifth Primary then Windows will convert the Disk to Dynamic.
You never installed Ubuntu to that disk.
However, when you ran Boot-Repair it may have messed up Windows boot... 
Fix Windows boot first: [http://windows7themes.net/how-to-fix-bootmgr-is-missing-in-windows-8.html](http://windows7themes.net/how-to-fix-bootmgr-is-missing-in-windows-8.html)
Then follow Mark's and oldfred's advice to convert the Dynamic Disk to Basic... BackUp you DATA first.

Good Luck...

I done whatever this blog said, I am able to fix mbr but unable to repair, i says " The volume does not contain a recognized file system. Please make sure that all required file system drivers are loaded and that the volume is not corrupted."
Even after fixing mbr it doesn't given me any benefit, before it was saying that "missing operating system, No bootable device press any key" and now it only says "missing operating system."
So, do you think it is the same thing which everyone trying to say?

---

### Post by oldfred on 2014-03-25
Not all Windows repair tools work with dynamic partitions, but no Linux tools will. 
You can see if Easus or Partitionwizard tools work to fix it also.

Otherwise you may get more help with those that know dynamic better.
 [http://www.sevenforums.com/](http://www.sevenforums.com/)

---

### Post by Akshay_rastogi on 2014-03-25
Ok! i am going to follow your advice and with the help of easus i'll try to fix it.

---

### Post by Akshay_rastogi on 2014-03-25
I have fixed the error by myself, From ubuntu live usb I opened GP and there I have changed the default boot drives on just reight clicking on them, and rebuild the BCD. There is no need to change my drives to basic. Thank you everyone here for helping me out to fix this error.

---

