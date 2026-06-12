---
title: "Repair Wubi installation with boot repair problem"
date: 2014-08-18
forum: Installation &amp; Upgrades
---

### Post by imed.mabrouk on 2014-08-18
Hi,
Please, I need help to avoid a re-installation:

Here is what I've been doing with my laptop (dell inspiron, Windows 64 bits):
-months ago, I Installed ubuntu from windows (wubi) => grub broken => repaired with windows CD
So since then I had a healthy windows with an inaccessible ububntu system so I decided to fix it with boot repair cd.

The problem is that I did that with a 32 bits version of boot repair :( 
I noticed that only after the repair step was done.

Here is the boot info file
[http://paste.ubuntu.com/8074170/](http://paste.ubuntu.com/8074170/)

I copied all my documents (from boot repair live cd) to the safe data partition ([COLOR=#000000]/dev/sda4 in the file)[/COLOR]
So I could reinstall windows on [COLOR=#000000]/dev/sda2 & [/COLOR][COLOR=#000000]/dev/sda3 (C: and ubuntu I guess) which are now unallocated, then reinstall ubuntu.
However I want to learn how to fix this kind of problems.
[/COLOR][COLOR=#000000]
PS. windows cd repair failed, Now I have a black screen with something like :)[/COLOR]Operating System not found


[COLOR=#000000]
[/COLOR]Any help would be appreciated.
Thank you

---

### Post by Mark Phelps on 2014-08-18
WUBI does not use GRUB and in (apparently) forcing its installation, you have "broken" Windows.  WUBI is also no longer supported as it was dropped from support when Windows 8 came out.

What I suggest you try is repairing the partitions, and you might be able to do this with the Minitool Partition Wizard Boot CD -- a Windows partitioning tool.  Download and burn that to a CD (using another PC), boot your PC with it, and see if it can repair the Windows filesystem partitions for you.  IF it does, you should then be able to reboot into Windows.

---

### Post by imed.mabrouk on 2014-08-18
Ok. Thank you @Mark Phelps.
Well I didn't know Wubi has all these issues.
Any way, I retrieved all my data into an external hard drive (via boot repair live cd).
Now I am re-installing windows, then I'll install ubuntu 14.04. I had to because I needed my laptop :(

Thanks again.

---

### Post by oldfred on 2014-08-18
Boot-Repair shows drive was converted to dynamic partitions, shown as SFS by fdisk.

Linux does not work with dynamic partitions. It is a Windows proprietary way to work around the 4 primary partition limit, where everyone else uses one primary as an extended partition and logical partitions inside the extended.

Best to backup any valuable data to another drive as reinstall may remove the SFS/dynamic partitions and then no data will be available.
Or undo the dynamic first before reinstall.

       Microsofts offical policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.


 EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

---

