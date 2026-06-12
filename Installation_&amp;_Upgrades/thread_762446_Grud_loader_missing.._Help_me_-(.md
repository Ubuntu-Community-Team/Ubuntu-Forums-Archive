---
title: "Grud loader missing.. Help me :-("
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by ann pic on 2008-04-22
i got 2 operating system in my cpu. I re-format my windows due to some un-avoided problems. Now i cannot enter to Linux because the grud loader is missing or maybe delibrately un-installed. I cannot choose either windows or linux already. Once i boot my cpu it will directly go to windows operating system. Help me, now i cannot go into Linux environment.

---

### Post by ann pic on 2008-04-22
i didn't do anything to my linux partition. And i already check my windows partiton is still the same like before. How i can install the grub loader? or am i need to re-install my linux ubuntu?

---

### Post by Inferied on 2008-04-22
I don't know, you may be able to replace your grub using live cd if windows didn't screw everything up too much... Or just reinstall Ubuntu, it will probably be easier.

By the way, could you please use proper terminology and grammar on these forums? Things like "re-format windows" and "operating system on cpu" make your posts very confusing.

---

### Post by ann pic on 2008-04-22
oh..sorry for the grammar mistakes. How i want to install the grub loader from ubuntu live cd?

---

### Post by Cotopaxi on 2008-04-22
Ann Pic,

You "re-formated" your windows (partition?). In this case, I believe that you did also deleted the Master Boot Record, that was installed in this partition.

Try to boot your computer from a Linux Live CD and then re-install the GRUB. Make sure that the Master Boot Record is installed into the Windows partition.

---

### Post by lswest on 2008-04-22
i wrote a how-to on restoring bootloaders (second line in my sig) should tell you what you need to know.  Also has a link to a more detailed how-to on re-installing GRUB (i focused on just giving the basics for re-installing Vista, XP and GRUB bootloaders, not being detailed).

---

### Post by Herman on 2008-04-22
> You "re-formated" your windows (partition?). In this case, I believe that you did also deleted the Master Boot Record, that was installed in this partition.

Try to boot your computer from a Linux Live CD and then re-install the GRUB. Make sure that the Master Boot Record is installed into the Windows partition.Sorry, but I think it's important to correct you on this, as if the misinformation spreads it can lead to others making mistakes which can cause problems for them.

It's important to realize that the MBR (Master Boot Record) is not part of any partition.
The Master Boot Record is in the first sector of a hard disk.
The first partition doesn't begin until after the first track, (63 sectors), which is empty and reserved for boot loaders.

The first sector of an operating system partition can also have boot loader code installed in it, and so it is often called the boot sector. Windows always boot loader code in its boot sector, Windows can't boot without it, but for a Linux operating system it's optional.

You are right that Windows will always try to take over control of the MBR and install it's boot loader to it and delete GRUB every time Windows is re-installed.
The MBR doesn't belong to Windows, but Windows tries to claim it.
Any boot loader can be installed in the MBR and as long as Windows boot sector is left alone, Windows can be booted by any third party boot manager.

The reason why we need to be careful to make sure people know the difference between the MBR and Windows boot sector is because it's okay to install GRUB to MBR, but never to Windows boot sector.
If we lead people to believe that the MBR is part of Windows, then there is a danger that someone will become confused and try to install GRUB to the Windows partition and damage their Windows installation.
It would be simple to reverse the damage, (with the FIXBOOT command), but it might cause someone some inconvenience, especially if they don't know what to do.

SO, the Master Boot Record belongs to the hard disk and is independant of any partition, (indeed, it contains the partition table itself).
The Windows partition has a boot sector, which does belong to Windows.

Regards, Herman :)

---

### Post by Cotopaxi on 2008-06-23
Herman,

sorry I am replying so late, but I just found your post now! I just wanted to thank you for the correction! :)

---

