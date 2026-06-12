---
title: "In need of update regarding multi-boot"
date: 2019-03-06
forum: Installation &amp; Upgrades
---

### Post by aajax on 2019-03-06
Sorry it looks like I got distracted and then lost track of the fact that I apparently had already posted this.  Couldn't figure out how to delete duplicate.  My apologies.

Have been reviewing articles regarding multiboot with Ubuntu.  This is something I've been doing for a long time now but haven't setup multiboot with both Windows and Ubuntu since Windows XP.  I am aware that the boot process in Windows 7 and subsequent versions of Windows is quite different than XP.  Also, this need comes about as a result of acquiring a new computer that is my first that uses UEFI rather than BIOS.  I should also point out that that from the articles I've seen it looks like the term multiboot ought not be confused with dual boot.  My intention is to allow multiple instances of either or both Ubuntu and Windows but limited to the versions of Windows that use a Windows Boot Manager partition.

I'm currently running some machines with multiple instances of Ubuntu only.  This involves running a minimal size Linux, in my case Debian based, system that serves as the boot manager.  In that, the only thing it is used for is boot management.  This makes each of the Ubuntu systems independent of each other.  In that, there is no dependence of any Ubuntu system on another to boot.

I've seen some articles that describe revising the Windows Boot Manager to reference a Linux system rather than itself but this implies, at least to me, that Grub (?2 or Legacy) must then be capable of booting these new Windows systems via some mechanism other than chain loading.  To me chain loading means duplicating the ability of BIOS to find a load the boot sector of the active MBR partition on a drive.  I have no idea whether such a concept might work on a UEFI based computer.  I suppose the question becomes can Grub do more than chain load when it comes to supporting Windows?

Might it be possible to boot Windows with any partition of the type that Windows would call an EFI System partition?  Possibly I'm asking if Grub can be an EFI System partition?

A lot of the Ubuntu documentation that I've seen so far seems to focus on Windows 7 which normally installs into but one target partition and then updates whatever EFI system partition it cam find.  However, I've now learned enough about Windows 10 to know that the installer is a very different beast.  It seems that rather than install into a designated partition it needs unallocated space in which it will always create 3 new partitions.  This doesn't fit well with the idea of chain loading along with the possibility of more than one instance of Windows 10.  I'd really like to learn how Ubuntu multiboot deals with that problem.

---

### Post by deadflowr on 2019-03-06
Duplicate thread
Other here: [https://ubuntuforums.org/showthread.php?t=2414154]("https://ubuntuforums.org/showthread.php?t=2414154")
Thread Closed

---

