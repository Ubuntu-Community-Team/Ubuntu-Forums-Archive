---
title: "Boot loader on Ubuntu/XP system"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by Superorb on 2008-01-25
I've been using Ubuntu at work, but finally took the plunge on a new machine and installed it at home. I've got one drive running XP and another separate drive running Ubuntu 7.10. I'd like to not touch the XP drive and put a Boot loader thing on the Ubuntu drive that would allow me to select from XP or Ubuntu on boot. How do I do this?

---

### Post by bwtranch on 2008-01-25
Afraid Linux is going to mess with your windoze? Might be just the opposite.

---

### Post by Superorb on 2008-01-25
I'd just rather not touch the XP drive. I hate Windows just as much as the next guy, but I still need it for stuff. Can you recommend anything?

---

### Post by confused57 on 2008-01-25
Here's how I set up my system:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

You could probably do it without disconnecting your XP drive...set your bios to boot first to the drive you're installing Ubuntu on before you boot the Desktop live cd.  Make a note of how the installer/partitioner designates your Ubuntu drive(sda, sdb, etc), then I think it's the last step, you can click on the "Advanced" button in the lower right portion of the screen...then type in /dev/sdb(or however the drive is designated), instead of the default (hd0), as the location(mbr) to install grub's IPL.

---

### Post by Superorb on 2008-01-25
I had read that thread earlier. Mine are both SATA and Ubuntu and XP are both already istalled on their respective drives. Right now the only way to boot into windows is to change the boot drive order i nthe BIOS which is just a PITA that way.

---

### Post by confused57 on 2008-01-25
> **Superorb said:**
> I had read that thread earlier. Mine are both SATA and Ubuntu and XP are both already istalled on their respective drives. Right now the only way to boot into windows is to change the boot drive order i nthe BIOS which is just a PITA that way.
Sorry, I misread your original post that you already had Ubuntu installed on your 2nd drive...try adding the Windows entry in the thread I gave you to your menu.lst...this should work, if your Windows is on the first partition...you would need (hd1,1), if Windows is on the 2nd partition.

You can determine this by entering in the terminal:
```
sudo fdisk -l
```
-l is a lowercase "L"

---

### Post by Superorb on 2008-01-26
Ok, I added everyhting into my list file. One thing though, my XP boot drive is listed as "sda1" instead of "hd0". What do I do about this?

---

### Post by confused57 on 2008-01-26
> **Superorb said:**
> Ok, I added everyhting into my list file. One thing though, my XP boot drive is listed as "sda1" instead of "hd0". What do I do about this?
Try following the directions in the thread for editing your menu.lst & add the following Windows entry:
```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```
you can add the entry to the very end of your menu.lst, if you prefer.

(hd0), (hd0,0), etc are designations grub uses for your mbr & partitions.

Ubuntu designates your partitions as sda1, sda2, sdb1, sdb2, etc.

Here's an excellent explanation of how grub designates partitions:
[http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System](http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System)

---

### Post by Superorb on 2008-01-26
Ok, I'll give it a shot.

---

### Post by Superorb on 2008-01-26
Ok, I had the XP option, but when I tried that it said, "Error 13, invalid executable" or something similar. My list file looks ike this:

```

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=495baf03-ea19-435b-bb69-551a4f7d1aa7 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=495baf03-ea19-435b-bb69-551a4f7d1aa7 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title              Windows XP
root               (hd0,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

```

---

### Post by confused57 on 2008-01-26
Try copying & pasting the Windows entry I gave you in my last reply to the very bottom of your menu.lst.

---

### Post by Superorb on 2008-01-26
> **confused57 said:**
> Try copying & pasting the Windows entry I gave you in my last reply to the very bottom of your menu.lst.

Awesome, that worked! Thanks! Next in line is getting the thumb button to work in linux.

---

