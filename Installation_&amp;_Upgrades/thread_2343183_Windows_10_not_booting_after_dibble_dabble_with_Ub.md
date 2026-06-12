---
title: "Windows 10 not booting after dibble dabble with Ubuntu"
date: 2016-11-14
forum: Installation &amp; Upgrades
---

### Post by alex4478 on 2016-11-14
Hi,

It seems my laptop is well goosed. Windows 10 (upgraded from Win7) is unable to boot. An error is reported along the lines of 'bootable device inaccessible'. I've tried Boot Repair and that didn't work. The URL given to me by the app is 

[http://paste.ubuntu.com/23475012/](http://paste.ubuntu.com/23475012/)

Could someone please have a look at this and help me out. It's a works laptop and if it doesn't get fixed I'm going to be looking for a new job, just on the run up to Christmas!!!

---

### Post by yancek on 2016-11-14
The boot repair output shows a standard MBR install but there is no Grub boot code in the MBR and no Grub boot files show on your partition.  If you scroll down the boot repair output page, you will see numerous error messages regarding windows partitions being in an unsafe state.  That means you left windows 10 hibernated or with fastboot on so nothing can be done.  Your output also shows that you have Dynamic partitions for windows which is incompatible with Linux.  You don't have Grub properly installed or maybe installed at all so there is no menu from which to boot anything.  You might be able to modify this by changing from Dynamic partitioning and turning off hibernation but since it's not your computer., your employer may not appreciate that.  You'll need to wait for someone else to post on this as I don't use Dynamic partitioning and am not sure how you would change this.

The next time you want to 'dabble' with another OS, use a DVD or flash drive if you are using someone else's computer.  That's why the different Linux developers created them.

---

### Post by oldfred on 2016-11-14
You show SFS or dynamic partitions not the standard basic partitions.
It used to be that Ubuntu/Linux would not even see the partitions, but driver updates not see the partitions, but do not work with them.

       [http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)
Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from)

You also show Windows fast start up or hibernation on. Linux NTFS driver cannot mount hibernated partitions.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

