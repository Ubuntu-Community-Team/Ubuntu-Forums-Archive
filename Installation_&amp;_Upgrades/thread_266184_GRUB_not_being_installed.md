---
title: "GRUB not being installed?"
date: 2006-09-26
forum: Installation &amp; Upgrades
---

### Post by LordMaiku on 2006-09-26
Hello,

I just tried installing Ubuntu on a new hard drive. I have Windows XP (for .NET programming and gaming) on a totally separate drive. Also, I set the Ubuntu drive to have highest priority in BIOS. To get to the point, after installing and rebooting, no OS loads. It's like GRUB didn't install.

Even if I unplug all but the Ubuntu drive, Ubuntu doesn't load. (If I set the Windows drive to first priority, Windows loads correctly).

There is no RAID or otherwise non-standard configuration involved. All drives are SATA (and recognized in the partitioner in the Ubuntu installer).

Any suggestions? I can reinstall Ubuntu as many times as I need to get it right. . .

Thanks in advance :)

---

### Post by Mr Frosti on 2006-09-26
When Ubuntu is installed, the GRUB boot manager should replace the Windows boot manager. The boot manager is very specific about where it is installed to. It has to be the first sector of the first hard drive. 

If you can boot straight into Windows, and not into Ubuntu at all, I would change the order of your SATA chain (if any) to make the Ubuntu hard drive first. This way, the BIOS will point to GRUB, and then you select from there.

---

### Post by confused57 on 2006-09-27
> **LordMaiku said:**
> Hello,

I just tried installing Ubuntu on a new hard drive. I have Windows XP (for .NET programming and gaming) on a totally separate drive. Also, I set the Ubuntu drive to have highest priority in BIOS. To get to the point, after installing and rebooting, no OS loads. It's like GRUB didn't install.

Even if I unplug all but the Ubuntu drive, Ubuntu doesn't load. (If I set the Windows drive to first priority, Windows loads correctly).

There is no RAID or otherwise non-standard configuration involved. All drives are SATA (and recognized in the partitioner in the Ubuntu installer).

Any suggestions? I can reinstall Ubuntu as many times as I need to get it right. . .

Thanks in advance :)

You can try reinstalling grub to the mbr of the Ubuntu drive, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by LordMaiku on 2006-09-27
> **confused57 said:**
> You can try reinstalling grub to the mbr of the Ubuntu drive, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

I tried this, and unfortunately it didn't work. Even with the Ubuntu drive set to be first in the Sata chain. . .

EDIT: would it make a difference if I changed the physical order that the drives are plugged in? I have the Windows drive in SATA1 and Linux in SATA4, but the Linux drive still shows up as sda and Windows as sdc. . .

---

### Post by LordMaiku on 2006-09-27
Well, I changed the physical order of my drives, and GRUB actually shows up now. . . but it only loads Ubuntu (which is much better than nothing). When trying to boot to Windows it said "NTLDR is missing. Press Ctrl-Alt-Delete to reboot." :( 

I was afraid to use the Recovery Console to fixboot, because I didn't want GRUB messed up. . . Ubuntu is on the first SATA master, and I'm not sure if fixboot will try writing to fsm even though Windows is on second sata master,

Any ideas for this new dilemma?

Thanks again for the help :)

---

### Post by LordMaiku on 2006-09-29
Well, I was able to solve the problem. Here is my method:

Unplug every drive except the one for Ubuntu. Make sure that drive is on First SATA master. Install Ubuntu, erasing the entire drive. 

Plug in the Windows drive in second SATA master (or wherever it will show up as hd1). Boot into Ubuntu, and open the GRUB menu.lst file:

```

cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
gksudo gedit /boot/grub/menu.lst

```

I then added an entry for the Windows partition below the Linux entries:

```

title           Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
chainloader (hd1,0)+1

```

If you have more drives to plug back in, do it now. If one of them has another install of Ubuntu on it, format it first (see below).

Things that help if you want this to work:
[LIST][*]If you already have Ubuntu installed on another harddrive, unplug it. GRUB seems to get confused in this case.[*]Make sure the Ubuntu drive is plugged into the first SATA master port (SATA1) on the mobo. Changing the boot order doesn't seem to help.[*]If at first you fail, try, try again.
[/LIST]

I hope this helps someone. . . 

Good luck :)

---

