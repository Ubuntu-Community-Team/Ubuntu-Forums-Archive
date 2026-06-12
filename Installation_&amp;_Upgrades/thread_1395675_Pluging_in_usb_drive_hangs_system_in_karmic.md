---
title: "Pluging in usb drive hangs system in karmic"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2010-02-01
The upgrade from the 2.6.31-16 to the 2.6.31-17 kernel hung my system. I then read that this was related to external usb file system. When I disconnected these drives, everything was ok. This leaves me without any external usb file systems; my printer and my usb mouse work ok.

I searched in the forums, but seem to be the only person experiencing this.


 When I plug in one of the external usn drives I have on the running system, everything freezes and the only way to get the system back is to unplug the drive and reboot. There are no error in the logs (see attached syslog).

I have also attached the ouput from dmesg and greped for usb

Thanks

---

### Post by lister171254 on 2010-02-04
While this is not a showstopper, I'd still appreciate some help. Maybe I'm in the wrong forum?

Thanks.

---

### Post by wkulecz on 2010-02-04
The kernel update should have left a grub2 entry for your 2.6.31-16 kernel.  Can you boot it and see if the problem is gone?   

If it is, file a bug report on Launchpad, although I think a new kernel update came out yesterday or this morning, you could try it before filing a bug report.

--wally.

---

### Post by lister171254 on 2010-02-04
Thanks, but have already tried to boot into the 2.6.31-16 kernel. The result is the same so I guess its not the kernel upgrade.

Maybe its one of the other packages that was part of the update. Could it be GDM/nvidia related?

I'm only saying this as the systems does not hang when I boot into receovery mode and the plug in a USB disk. Mind you, that also means that in that circumstance I'm not using the USB mouse. I have a PS2 keyboard.

Cheers

---

### Post by dabl on 2010-02-04
It would be good to learn more about what is really going on -- "hung" is not very useful for troubleshooting.  With the system running, can you open a console window and enter ```
top
```

Put this window where you can keep an eye on it.  Then watch it while you plug in your USB drive. It should become obvious which process is using up all the resources, and that will give some insight (hopefully) into what's wrong.

It occurs to me that the filesystem type on the USB drive might be relevant to the problem.  What is it?

---

### Post by lister171254 on 2010-02-05
When this happens, the system 'freezes'. That means no keyboard  or mouse or remote access.

One thing I have noticed, however, is that I have just set my BIOS to Failsafe mode, rebooted and the problem is gone.

I'll keep investigating.

---

### Post by NickHurnay on 2010-02-05
Hello,

I have the same problem, each USB Key - 1, 2, 4 and 8 GB - or USB Hard Disk (160 GB - 500 GB) are crashing the system when plugged in any of the USB readers.

No problem with the computer or the USB drives, Windows 7 (dual boot) don't crash and allow access to the keys / drives.

Hope we will find a solution !

Nick.

---

### Post by NickHurnay on 2010-02-07
Problem dosen't appear with the 2.6.28-15 Generic Kernel !

Since Kernel 2.6.31-14, my comuter crash on USB storage plug... And you ?

---

