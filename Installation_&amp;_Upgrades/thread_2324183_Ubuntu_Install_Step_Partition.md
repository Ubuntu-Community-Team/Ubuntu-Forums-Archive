---
title: "Ubuntu Install Step Partition"
date: 2016-05-11
forum: Installation &amp; Upgrades
---

### Post by tecknomage on 2016-05-11
Need clarification of Partition step in **14.04 to 16.04 UPGRADE** (*see screenshot, not from upgrade*)

[IMG]http://i1266.photobucket.com/albums/jj534/tecknomage1/Ubuntu_16-04_InstallStep.jpg[/IMG]

---

### Post by oldfred on 2016-05-11
Linux will not mount NTFS partitions that need chkdsk or are hibernated. This is to prevent damage to the NTFS that then chkdsk could not fix, or damage to the hibernation.

And after a resize, NTFS always needs chkdsk. 
So we normally suggest resizing NTFS with Windows and reboot immediately so it can run chkdsk. Before there sometimes were issues with NTFS after an install, so better to use Windows tools for Windows. Do not shrink Windows too much, NTFS really likes 30% or more free space. At 10% free it gets very slow.

And all versions of Windows 8 or later use fast start up or always on hibernation. That will keep all NTFS partitions mounted/hibernated, so you need to make sure fast startup is off in Windows.

       Fast Startup off (always on hibernation)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

I normally partition in advance with gparted, and then use Something Else to choose(change button) each partition for my install. If swap already created then it auto finds it also. The auto install options use some logic for allocating between / & swap, but I typically want to control those sizes. I do not need large swap as I have lots of RAM.

---

### Post by grahammechanical on 2016-05-11
Dragging the divider does not work because there is no unallocated space to expand the Linux Ubuntu partition into. But dragging the divider towards the right might let you shrink the Linux/Ubuntu partition. Does that work?

Regards

---

### Post by oldfred on 2016-05-11
Just noticed it is a vbox drive.

I do not know virtual installs, but why dual boot in one vbox. 

And the entire 34GB is not generous for Windows 10. It may not have room to shrink.

When I upgraded my one Windows 8 to Windows 10, I had to expand from 50GB to 100GB so it would have lots of room. Not sure it would have fit even in my original 50GB. Windows needs 30% free space in a NTFS partition to work well. At 10% free you just about cannot run a defrag as it has no working room.

---

