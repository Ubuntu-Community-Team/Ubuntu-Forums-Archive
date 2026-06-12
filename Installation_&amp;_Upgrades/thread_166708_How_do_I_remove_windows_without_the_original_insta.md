---
title: "How do I remove windows without the original installation disk?"
date: 2006-04-26
forum: Installation &amp; Upgrades
---

### Post by Talruk6 on 2006-04-26
How do I remove Windows XP without the original installation disk?  I want to  remove it so I can replace it with Ubuntu, but I just realized the computer manufacturer (Emachines) screwed me out of the proper disk.

Also, does Ubuntu offer the option to change the format of the hard drive, or does that need to be done seperately as well?  If so, how?

Thanks.

---

### Post by Sef on 2006-04-26
> How do I remove Windows XP without the original installation disk? I want to remove it so I can replace it with Ubuntu, but I just realized the computer manufacturer (Emachines) screwed me out of the proper disk.

When you get to the partitioner, you can press enter for the default which will delete XP and install Ubuntu.  Or you can do a manual partition and just delete XP and install Ubuntu.

> Also, does Ubuntu offer the option to change the format of the hard drive, or does that need to be done seperately as well? If so, how?

During the partitioning, If you press enter for the default install, it will install ext3.  If you do a manual install, you will have the option of choosing the file system you want.

---

### Post by Qrk on 2006-04-26
You can use the Ubuntu install disk to somply overwrite Windows. I don't think the Windows CD even gives the option of uninstalling Windows, but at any rate, you don't need it.

Ubuntu's installation disk has a built in partitioner that will take care of formating for you as well.

---

### Post by Scunizi on 2006-04-26
If you don't care about wiping out windows entirely from the harddrive, it's fairly easy.  Run the install CD for Ubuntu and when you get to the diskpartitioning portion of the install, choose manual, delete the windows partition and any other partitions on the hd, then tell the partitioner to automatically partition the "new" single partition that's available.  It will split it into a couple of partitions, one for the system and one for swap.  If you manually do this you can limit the swap partition to a few gig leaving the remaining portion of the HD for the new system and files.  I hope this helps!

---

### Post by az on 2006-04-27
[QUOTE=Talruk6]but I just realized the computer manufacturer (Emachines) screwed me out of the proper disk..[/QUOTE]

[https://wiki.ubuntu.com/WindowsDualBootHowTo](https://wiki.ubuntu.com/WindowsDualBootHowTo)

Have you tried asking for one?

[QUOTE=Talruk6]
Also, does Ubuntu offer the option to change the format of the hard drive, or does that need to be done seperately as well?  If so, how?

Thanks.[/QUOTE]
Well it can reformat any partition to any filesystem you want.  It cannot convert one filesystem to another while keeping the data on it.

---

### Post by tc10b on 2006-04-28
Ubunutu will ask you if you want to wipe the Windows partition, but this means wipe as in no data will be left on it except Ubuntu.

If you're worried about that use a back up program such as Norton Ghost to back up your entire partition. It's long and can take a lot of CD's/DVD's depending on your hard drive but it means that later if you want to, you can put Windows back on exactly how you left it before, including all your documents, settings etc.

If you do that you don't have to worry about a Windows disk and if you don't care about any of that just let the Ubuntu installer do it's thing and you'll be set to go.

---

