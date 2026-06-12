---
title: "windows 7,windows 8 and ubuntu 12.04 triple boot?"
date: 2012-06-05
forum: Installation &amp; Upgrades
---

### Post by soumoks on 2012-06-05
I recently intsalled windows 8 release preview on my second machine,it was initially running windows 7,naturally after installing windows 8,its bootloader took over giving me an option to choose between windows 8 and windows 7,now i want to install ubuntu 12.04 on the system,what will happen to the bootloader?,will grub give me an option to choose between all the three os?please elaborate..thanks in advance..

---

### Post by carl4926 on 2012-06-06
> **soumoks said:**
> what will happen to the bootloader?,will grub give me an option to choose between all the three os?please elaborate..thanks in advance..
It should be fine
Just be sure you make backups of important data and have a windows install DVD in case you need to fix the MBR in the future

---

### Post by oldfred on 2012-06-06
Grub will only boot to one Windows or the one with the boot flag(active partition).

If both Windows installs are in primary partitions you may be able to separate them by separating boot files, repairing Windows. Windows only repairs the one with the boot flag, so you have to repair one, move boot flag and repair the other.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by carl4926 on 2012-06-06
@oldfred
Interesting. I never actually tried booting more than one windows. But AFAIK the boot flag is only important if using windows bootloader?

Windows 8 defaults to some 'hybrid hibernation/off state for fast boot'
Yuck!

Sorry if I made misleading comments earlier...

---

### Post by soumoks on 2012-06-06
> **carl4926 said:**
> It should be fine
Just be sure you make backups of important data and have a windows install DVD in case you need to fix the MBR in the future

so ur saying grub will provide an option to boot into windows 7,windows 8 and ubuntu right?ru sure?,considering the windows 8 bootloader..i still dont know,what ms are trying to prove with the windows 8 bootloader..:p

---

### Post by soumoks on 2012-06-06
> **oldfred said:**
> Grub will only boot to one Windows or the one with the boot flag(active partition).

If both Windows installs are in primary partitions you may be able to separate them by separating boot files, repairing Windows. Windows only repairs the one with the boot flag, so you have to repair one, move boot flag and repair the other.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

actually i created a separate partition for windows 8,and then installed it on that,i will be doin the same thing with ubuntu as well,so will grub take over?i looked at the links u provided but they didn't answer my question properly..sorry but could u help me out a bit more? :)

---

### Post by soumoks on 2012-06-06
> **carl4926 said:**
> @oldfred
Interesting. I never actually tried booting more than one windows. But AFAIK the boot flag is only important if using windows bootloader?

Windows 8 defaults to some 'hybrid hibernation/off state for fast boot'
Yuck!

Sorry if I made misleading comments earlier...

its ok,i am here to learn anyway..:),what ru saying about the shutdown process of windows 8?it does not shutdown completely?i usually shutdown the pc every night and pull the plug as well..is that no advised in the case of windows 8?

---

### Post by carl4926 on 2012-06-06
Here is what I think.

If you keep one Windows install completely out on it's own (say win 8) as you have it that way.
If you were to install Ubuntu to the Win7 HD, making sure this HD was sda (ie; first in BIOS boot order) and set grub to sda
When you finish, grub should load and offer Ubuntu or win7 (maybe win8, I don't know).

Now to boot win 8, enter BIOS and toggle the boot order to make win8 HD first. And so long as the boot flag is on it's boot area - you should be OK

ONLY thing is, I'm wondering if Win8 actually has it's boot code on the win7 HD, probably, in which case it's messy.

So I'd consider re-installing win8 with only that HD connected.
Fix the MBR on the win7 HD, with only that HD connected.
Then follow my idea above....

or wait and see what other words of wisdom come your way.

---

### Post by soumoks on 2012-06-06
> **carl4926 said:**
> Here is what I think.

If you keep one Windows install completely out on it's own (say win 8) as you have it that way.
If you were to install Ubuntu to the Win7 HD, making sure this HD was sda (ie; first in BIOS boot order) and set grub to sda
When you finish, grub should load and offer Ubuntu or win7 (maybe win8, I don't know).

Now to boot win 8, enter BIOS and toggle the boot order to make win8 HD first. And so long as the boot flag is on it's boot area - you should be OK

ONLY thing is, I'm wondering if Win8 actually has it's boot code on the win7 HD, probably, in which case it's messy.

So I'd consider re-installing win8 with only that HD connected.
Fix the MBR on the win7 HD, with only that HD connected.
Then follow my idea above....

or wait and see what other words of wisdom come your way.

i think the above applies if i have more than one HD, correct?,i have only one harddidk,i have currently installed win 7 and win 8 in their own respective partitions..i dont understand the part of removing win 8 HD and all,do u want me remove the partitions?

---

### Post by carl4926 on 2012-06-06
> i think the above applies if i have more than one HD, correct?
Correct

Sorry my misunderstanding...

---

### Post by soumoks on 2012-06-06
come on guys,any more suggestions,anyone's tried this or am i the only one stupid enough to do this? :)

---

### Post by oldfred on 2012-06-06
To see where everything is installed run the Boot-Info report & post link.

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.
 
Then we can make specific suggestions.

Grub does not use boot flag. Windows boots from the partition with the boot flag. The Windows boot loader really only checks which partition has boot flag and jumps to the PBR - partition boot record/sector to continue booting.  PBR in NTFS then says to use either  ntldr (XP) or bootmgr (Vista/7). A few BIOS will not even let you start to boot (assumes Windows?), so for those motherboards, even with grub you need a boot flag on a primary partition. Lilo uses boot flag but will work on logical partitions also.

---

### Post by soumoks on 2012-06-07
> **oldfred said:**
> To see where everything is installed run the Boot-Info report & post link.

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.
 
Then we can make specific suggestions.

Grub does not use boot flag. Windows boots from the partition with the boot flag. The Windows boot loader really only checks which partition has boot flag and jumps to the PBR - partition boot record/sector to continue booting.  PBR in NTFS then says to use either  ntldr (XP) or bootmgr (Vista/7). A few BIOS will not even let you start to boot (assumes Windows?), so for those motherboards, even with grub you need a boot flag on a primary partition. Lilo uses boot flag but will work on logical partitions also.

i have to install ubuntu and then try this out,right?anyway will try out,thanks..:)

---

### Post by oldfred on 2012-06-07
You can run Boot Repair from a liveCD or download it as a liveCD. If you have installed Ubuntu then you can run it from that install also.

But if you have not yet installed best to run from liveCD as We need to see what is where first.

There have been several others install Windows 8 with 7 & Ubuntu.

---

