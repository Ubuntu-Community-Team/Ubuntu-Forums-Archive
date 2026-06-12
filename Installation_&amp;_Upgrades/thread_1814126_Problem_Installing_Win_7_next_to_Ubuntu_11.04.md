---
title: "Problem Installing Win 7 next to Ubuntu 11.04"
date: 2011-07-29
forum: Installation &amp; Upgrades
---

### Post by Swashy on 2011-07-29
Whenever I get to the installation screen for windows 7 I try to install it on the second partition next to my Ubuntu installation on the single hard drive I have on my **Asus Eee PC 1215t Netbook**, I get the same old tired problem. Everywhere I look on the internet this problem is supposedly caused by multiple drives being present on the computer or "dynamic" drives being dynamic or "RAID" drives (whatever the **** those are) being "RAID" drives.

I have none of these. I have a hard drive and an YUMI ubuntu and Windows 7 ISO on a bootable thumb drive. This **** comes up time after time.

```
Setup was unable to create a new system partition or locate an existing system partition. See the setup log files for more information.
```

I've used Gparted to make a NTFS drive. I've used it to make unallocated space so the retard that is windows 7 can make its own stupid little retard baby partition but I *still* get the same problem. I've tried locating the SATA ACHI drivers for my netbook and browsing to them and it still gives me the same ****.

I don't know what to do. Someone please help me. I don't want to erase my Ubuntu OS.

---

### Post by Quackers on 2011-07-29
Please post a screenshot of your Windows Disk Management screen.
It seems your partitions may have changed from simple volumes to dynamic disks.
This normally happens if you try to create a fifth primary partition on the hard drive. Have you done that?

---

### Post by Swashy on 2011-07-29
[IMG]http://i.imgur.com/ybf0f.png[/IMG]
That wouldn't make sense because if its unallocated space theres no way it can be miscontrued as a "dynamic" drive... right? How can I tell if something is dynamic with Gparted?

Perhaps YUMI "pendrive linux" is making my thumb drive dynamic?

And thanks so so much for your help.

edit: Oh; the *windows* disk management screen. Well unfortunately I don't have a camera..
I'm told that I have to make a new primary partition but the windows disk manager won't let me.

---

### Post by Quackers on 2011-07-29
You don't appear to have any unallocated space anywhere.
You do have a partition of "unknown" type at sda5. In gparted right-click on that partition and select "information" and see what that tells you.
That partition is currently inside an extended partition (sda2). Although Windows may install to an extended partition it will not boot from one.
I suggest that you delete the sda5 partition (if it will let you) and reduce the size of the extended partition so that the swap space just about fits in it.

As to how many primary partitions Windows will use, that depends on how you intend to install it (ie recovery discs or installation disc).
You also may have another problem.
At installation, Windows may not see your Linux partitions, so may inadvertently over-write part of one. This is one of the reasons it is better to install Windows first.

---

### Post by Swashy on 2011-07-29
Like so?
[IMG]http://i.imgur.com/XiA4L.png[/IMG]

Windows does recognize the partitions though so I can avoid wiping ubuntu. I plan on restoring ubuntu's mbr after I install windows.

---

### Post by Quackers on 2011-07-29
That looks better :-)
See if Windows will now install in that unallocated space.

---

