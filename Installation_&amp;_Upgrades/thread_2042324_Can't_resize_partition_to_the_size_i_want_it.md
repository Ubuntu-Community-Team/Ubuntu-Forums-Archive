---
title: "Can't resize partition to the size i want it"
date: 2012-08-14
forum: Installation &amp; Upgrades
---

### Post by MorrisseyJ on 2012-08-14
Hi, 

I have just received a replacement machine from Lenovo. 

I am trying to install 12.04 on it but am struggling with Windows 7's native partitioning tool, to generate a partition into which to install ([http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)).

Trying to shrink C, i get the dialogue which says:

```
Total size before shrink in MB: 289743
Size of available shrink space in MB: 143733
Enter the amount of space to shrink in MB:
Total size after shrink in MB: 146010
```The dialogue won't let me enter more than 143733 into the box to shrink the partition by. If i put in a larger figure the 'Total size after shrink in MB' reads: 0.

I have tried defragging the disk and now it says that says that the disk is 0% fragmented. So i don't think there is an immovable file further up the partition.

I was hoping to use the window's native client as my machine has no optical drive and thus no recovery CD - which might be necessary if i use GParted. Instead it only has a  recovery partition. I haven't been able to work out how to use this yet, without restoring the windows install to the entire HDD.

If anyone has any idea what the problem is i'd be very much appreciated.

j

---

### Post by oldfred on 2012-08-14
I think this still applies:

Resize Vista partition
If problems, try disabling system restore, pagefile, (in advanced settings in computer properties) and hibernate option (in power management). Don’t forget to turn them on back later.
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
[http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html](http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html)

If you have to use gparted, then be sure to have a Windows repairCD or USB. Windows will need to run chkdsk and maybe fixBoot, but if it cannot run it while booting then you have to use repairCD.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by MorrisseyJ on 2012-08-14
Hi Oldfred, 

Thanks for getting back to me. 

Just before getting your message i went ahead and forced things with GParted, thinking that i would just use the recovery partition if i needed to. 

In the end windows booted after running chkdsk and fixBoot, and then booted fine. 

So i only partially got this solved, but am now writing this from a clean install. 

Thanks very much.

j

---

