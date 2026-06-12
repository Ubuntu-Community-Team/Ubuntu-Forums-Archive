---
title: "In need of update regarding multi-boot"
date: 2019-03-06
forum: Installation &amp; Upgrades
---

### Post by aajax on 2019-03-06
Have been reviewing articles regarding multiboot with Ubuntu.  This is something I've been doing for a long time now but haven't setup multiboot with both Windows and Ubuntu since Windows XP.  I am aware that the boot process in Windows 7 and subsequent versions of Windows is quite different than XP.  Also, this need comes about as a result of acquiring a new computer that is my first that uses UEFI rather than BIOS.  I should also point out that from the articles I've seen it looks like the term multiboot ought not be confused with dual boot.  My intention is to allow multiple instances of either or both Ubuntu and Windows but limited to the versions of Windows that use a Windows Boot Manager partition.

I'm currently running some machines with multiple instances of Ubuntu only.  This involves running a minimal size Linux, in my case Debian based, system that serves as the boot manager.  In that, the only thing it is used for is boot management.  This makes each of the Ubuntu systems independent of each other.  In that, there is no dependence of any Ubuntu system on another to boot.

I've seen some articles that describe revising the Windows Boot Manager to reference a Linux system rather than itself but this implies, at least to me, that Grub (?2 or Legacy) must then be capable of booting these new Windows systems via some mechanism other than chain loading.  To me chain loading means duplicating the ability of BIOS to find and load the boot sector of the active MBR partition on a drive.  I have no idea whether such a concept might work on a UEFI based computer.  I suppose the question becomes can Grub do more than chain load when it comes to supporting Windows?

Might it be possible to boot Windows without using any partition of the type that Windows would call a System (i.e., Windows Boot Manager) partition?  Possibly I'm asking if Grub can be such a System partition?

A lot of the Ubuntu documentation that I've seen so far seems to focus on Windows 7 which normally installs into but one target partition and then updates whatever System partition it finds.  However, I've now learned enough about Windows 10 to know that the installer is a very different beast.  It seems that rather than install into a designated partition it needs unallocated space in which it will always create 3 new partitions.  This doesn't fit well with the idea of chain loading along with the possibility of more than one instance of Windows 10.  I'd really like to learn how Ubuntu multiboot deals with that problem.

---

### Post by VMC on 2019-03-06
I also have been using mbr computers for the last 30 years, and I just got a new one. EFI, a world of its own. [Oldfred]("https://ubuntuforums.org/showthread.php?t=2147295") has a tips blog with a ton of info. It help me. I got sidetraced reading all the links and some on my own. Its best at least to clone/backup your hard drive, just in case.
edit:thanks to 1fallen :)

---

### Post by #&amp;thj^% on 2019-03-06
You probably meant "clone" instead of "clown",Clowns scare me a bit.:)

---

### Post by DuckHook on 2019-03-06
In what must count as an absurdly useful coincidence, this solution was just posted in another thread: [https://ubuntuforums.org/showthread.php?t=2414018](https://ubuntuforums.org/showthread.php?t=2414018)

It may be relevant to your issue. Since I have not run Windows for years, I know nothing about it other than what I skimmed over on the EasyBCD website.

---

### Post by oldfred on 2019-03-06
Generally Windows in UEFI mode is somewhat like the old BIOS mode. Most recent install overwrites the /EFI/Microsoft boot files in the ESP - efi system partition and then adds other Windows to the BCD to allow booting all copies of Windows. I do not multi-boot Windows so do not know all the details.
But I have seen one or two users create a second ESP (removing boot flag from first one), so second Windows has its boot files in a different ESP partition, and a BCD only for that install. From UEFI you can only boot one UEFI install of Windows, or change boot flag to boot other install. But grub does not know or care and searches for /EFI/Windows boot files & creates an entry for that. I then think grub can directly boot two copies of Windows. 

Only other issue is grub only boots working Windows. And Windows 8 or 10 will turn fast start up back on, and then grub will not boot it. Direct boot from UEFI or boot using Windows repair disk is only alternative to fix Windows before grub can then boot it again.

Grub will directly boot most other Linux installs by using os-prober to find kernels. A few cases it does not get boot parameters correct and manual config is required. 
Another grub2 feature is the configfile which is like a chain load in old grub legacy. It allows one grub to load another grub, so it has all of that other installs grub menu. I have multiple Ubuntu installs, no Windows and often use a configfile entry using partition label. I turn off os-prober as it finds some old obsolete installs that I have not yet erased.

---

