---
title: "Moving GRUB from Going-Bad Hard Drive to Another"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by wklang on 2008-05-23
Ref: Ubuntu 8.04

Three hard drives on my system:
#1 is an old UDMA drive containing data
#2 is a SATA drive with Windows XP
#3 is Ubuntu 8.04

When I installed Ubuntu, I (apparently) chose not to put a boot sector on drive #3 and installed GRUB on drive #1.

This dual-booting has worked fine for several weeks.  Now on boot up my bios S.M.A.R.T. utility tells me that drive #1 is going bad.

What I'd like to do is install GRUB on one of the other hard drives and take #1 out of the system.

I've tried using G.A.G. v4.9 and when I try to boot Ubuntu, I get the message "Sector boot not found or invalid"  I assume this is becuase I didn't put a boot sector on drive #3 when I installed Ubuntu.

I tried the 'sudo grub-install....." and got an error...

Is there a way - short of reinstalling Ubuntu - of restoring a dual-boot environment when I take drive #1 out of the system?

As you can tell, I feel very unsure about this.

Thanks,

Wes

---

### Post by Herman on 2008-05-23
:) Hello Wes,
One thing you need to understand is that there's a difference between the MBR in a hard disk, (the first sector of a hard disk), and the boot sector of a partition, (the first sector of a partition).

GAG Boot Manager normally boots the partition, (boot sector), so we need a boot loader, (normally GRUB or LiLo), installed in the partition boot sector in order for GAG Boot Manager to be able to boot Linux.

GRUB can 'chainload' any hard disk's MBR, or any partition's boot sector if we use the 'chainloader +1' command, but either GRUB or some other boot loader needs to be installed in the boot sector or MBR before GRUB can chainload successfully too.

While your old UDMA drive containing data is still plugged in, boot Ubuntu and open a terminal and install GRUB to your #3 hard disk's MBR. [Re-install GRUB with a GRUB shell]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")
 (That link tells you how to install GRUB to a partition, (hd0), but you may install GRUB to (hd2) instead, which should be the MBR of your #3 hard drive.

After that, if you remove the old UDMA drive and boot up again, you should still have GRUB.
If not, you may need to [Change the hard Disk Boot Priority ]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority")in your BIOS.

---

### Post by meierfra. on 2008-05-23
In addition to what Herman advised you to do, you will also have to edit  the file "menu.lst"

```

gksudo gedit /boot/grub/menu.lst
```

Look for the line

#groot (hd2,3)
(of course the numbers might be different for you)
Change the first number to "0"  but do NOT change the second number:

#groot (hd0,3)

Save the file. Then

```
sudo update-grub
```


(this assume that you installed grub to the  ubuntu drive and also set your  bios to boot from the ubuntu drive)

---

