---
title: "Need help with partition management"
date: 2015-11-15
forum: Installation &amp; Upgrades
---

### Post by Anupam_Sobti on 2015-11-15
Hi Everyone

These are my current settings on the Windows 10 setup I'm using.

 [ATTACH=CONFIG]265595[/ATTACH]

The unallocated space is where I'd like to install Ubuntu (15.10). However, G: (Anupam) is also empty at the moment.

The computer is UEFI enabled and the partitions are all Dynamic. When I use the ubuntu installer, all I see is a ~600GB partition which has D: + G: + free space, which I can't use since I need to retain the data in D:

Please guide on how to proceed!

Thank You

Anupam

---

### Post by Vladlenin5000 on 2015-11-15
> **Anupam_Sobti said:**
> (...) the partitions are all Dynamic.

^^^^
This is your problem. Dynamic partitions are a Microsoft proprietary "thing". 

[https://technet.microsoft.com/en-us/library/cc776315%28v=ws.10%29.aspx](https://technet.microsoft.com/en-us/library/cc776315%28v=ws.10%29.aspx)

---

### Post by oldfred on 2015-11-15
Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

---

### Post by Anupam_Sobti on 2016-02-02
Thanks for the reply folks. The primary problem right now would be that I don't have a disk I could backup this data on. So, seems like I'm stuck for now.

---

### Post by gordintoronto on 2016-02-03
If you don't have backup, that's a lot more important than whether you can install Ubuntu.

---

