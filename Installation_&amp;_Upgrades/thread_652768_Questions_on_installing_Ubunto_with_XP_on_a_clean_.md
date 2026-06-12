---
title: "Questions on installing Ubunto with XP on a clean HD"
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by m i k e on 2007-12-29
I'm in the process now of backing up important files as I want to format my hard drive with XP and install Ubunto and Windows XP with a dual boot.  I'm pretty sure I understand the process however I have two questions.

Should I delete my current partition prior to reinstalling XP or is it fine to just let the Windows installer format the drive?

Also, I've been hearing about a swap partition.  Could someone please explain what that is.

Thanks!

---

### Post by Fed on 2007-12-29
Hi mike.

First thing, yes you should probably delete the current partition. It will most likely be NTFS, and span the entire drive, that sound about right? If that's the case, my recommendation would be to delete it, and when installing Windows create a new one that doesn't take up your whole drive. The proportions allocated to the Windows partition and to the Ubuntu one really depend on what you plan on installing, so I can't make that call for you. Just as an example, you could have 100GB to the NTFS partition with Windows, 19GB to Ubuntu and a 1GB swap partition. That way you can store any media on the NTFS partition which will be accessible from Windows and Ubuntu as well for example. Again your plans and needs should determine the allocation.

The swap partition is something Linuxes use to improve performance. As far as I know it's basically like the pagefile that Windows uses, if you've heard of that. Long story short, you're better off with one and 1GB is a decent size for it.

Hope that helps.

---

### Post by m i k e on 2007-12-29
That was very helpful thanks.  One further question.

If you recommend deleting my current partition before the reinstall of Windows XP how should I go about doing that?  To do something like this previously I would always just go into "Disk Management" in Windows.  However, deleting the partition will also delete my OS so I doubt I can use Windows to delete the partition.

---

### Post by Fed on 2007-12-29
No worries on that front, when you launch the install for Windows it will show you your drives and partitions, and you can just delete the existing one there and re-create the new smaller one.

Good luck!

---

