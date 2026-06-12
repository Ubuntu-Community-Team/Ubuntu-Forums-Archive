---
title: "Ubuntu dual boot  uninstall ?"
date: 2013-01-13
forum: Installation &amp; Upgrades
---

### Post by offgridguy on 2013-01-13
Hello:  I have a dual boot, ubuntu 12.04 and windows7,  I would
like to know the safe way to uninstall ubuntu without corrupting
the windows MBR ?

I have read this.

[http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/](http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/)
 
The last time i removed ubuntu, i corrupted the MBR and had to
restore windows from the recovery partition, using the recovery
disks, which i have,  obviously i don't want to go through that again.

This is something that i want to learn, more than something that i have too do.  I will probably reinstall ubuntu again, perhaps
a different version.

I do have a live CD of boot repair, will it work to restore the windows bootloader ?

Thank you.

---

### Post by darkod on 2013-01-13
To be technically precise, you didn't corrupt anything. You had a dual boot with grub2 bootloader on the MBR. Grub2 depends on its config files to load the menu, so if you delete the ubuntu partition before restoring a windows bootloader, it will break grub2 since it doesn't have its config files any more. That is normal behavior when it doesn't have its config files, not a corruption of any kind.
And just for information, you can easily boot windows from the grub rescue prompt that shows in such cases. This only shows the superiority of the grub bootloader compared to windows bootloader.

Having said all that, looking at the boot-repair page:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

in the Main Options tab there is option to Restore MBR. After selecting that the MBR Options tab should become enabled where you can select to which disk to write the MBR and which partition has your windows boot files. So, it seems you can easily restore the MBR using boot-repair. Do this first, check windows is booting fine, and after that there is no problem to delete all ubuntu partitions. Of course, get all data that you need out first.

---

### Post by offgridguy on 2013-01-13
Thanks darkod for the clarification,  one thing though, when i previously deleted my
ubuntu partitions all i could get on startup was; operating system not found.

    I don't recall a grub rescue prompt ?

I thought boot repair would work for windows but wasn't sure.  I now do backups
having learned "the hard way". :D

Would it make a difference if windows 7 was set as default boot in the grub menu ?
{which it is}
 Thanks again.

---

### Post by YannBuntu on 2013-01-14
Hello
To remove an OS:
- if you have already deleted the Ubuntu partitions via Gparted, use Boot-Repair's Recommended Repair to fix the bootloader.
- else, use [OS-Uninstaller]("https://help.ubuntu.com/community/OS-Uninstaller"). It will format the OS, then fix the bootloader.

[IMG]http://pix.toile-libre.org/upload/original/1340275988.png[/IMG]

---

### Post by darkod on 2013-01-14
> **offgridguy said:**
> Thanks darkod for the clarification,  one thing though, when i previously deleted my
ubuntu partitions all i could get on startup was; operating system not found.

    I don't recall a grub rescue prompt ?

I thought boot repair would work for windows but wasn't sure.  I now do backups
having learned "the hard way". :D

Would it make a difference if windows 7 was set as default boot in the grub menu ?
{which it is}
 Thanks again.

You can use the program Yann mentioned, just to address your questions:
1. No, it doesn't matter whether windows or ubuntu was the default OS. You are deleting grub and all its config, which was the default OS in grub doesn't matter.

2. The 'OS not found' message is bios message, not grub. You correctly noticed it's not from grub. The reason why it happened is that many bioses look for a partition with the boot flag on, because windows can't work without one. So, years ago, that's how they designed them I guess. If there is no boot flag it thinks there is no OS, although you could have a perfectly working linux because it doesn't need and use the boot flag. But the board won't even try to boot the computer not seeing a boot flag. In this case you would set a boot flag on any partition, just to avoid this.

Since you plan to keep windows and that needs the boot flag, you don't need to do anything about this.

---

### Post by offgridguy on 2013-01-14
Thank you, YannBuntu and darkod, for the explanation and the help.
Much appreciated. :D

---

### Post by offgridguy on 2013-01-30
Update;  I have successfully uninstalled ubuntu, windows is booting flawlessly.:D

I followed the advice of darkod, reply # 2

> in the Main  Options tab there is option to Restore MBR. After selecting that the MBR  Options tab should become enabled where you can select to which disk to  write the MBR and which partition has your windows boot files. So, it  seems you can easily restore the MBR using boot-repair. Do this first,  check windows is booting fine, and after that there is no problem to  delete all ubuntu partitions. Of course, get all data that you need out  first. 		                   		  		  		 		 			 				___

Thanks darkod.    The OS-Uninstaller as suggested by YannBuntu looks good as well, i think i will download that and give it a try someday.  Altogether a pleasant
experience. :D:D

---

