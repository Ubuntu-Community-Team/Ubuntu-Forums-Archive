---
title: "GRUB no booting XP"
date: 2005-06-02
forum: Installation &amp; Upgrades
---

### Post by kochab on 2005-06-02
Hi,
I had this setup:

partition 1= win xp professional
partition 2= win xp home

and the system used to boot from 1st partition.
now I've installed ubuntu on the first partition, it works fine but I cant manage to boot xp home.
actual configuration:

partition 1=ubuntu
partition 2=swap
partition 3=win xp home

I've tried adding to menu.lst

title 		Windows XP Home SP2
rootnoverify 	(hd0,2)
chainloader 	+1

but the error is 
Error 12: Invalid device requested

someone knows how to solve it?
Thanks!

---

### Post by BeeZ on 2005-06-02
[QUOTE=kochab]Hi,
I had this setup:

partition 1= win xp professional
partition 2= win xp home

and the system used to boot from 1st partition.
now I've installed ubuntu on the first partition, it works fine but I cant manage to boot xp home.
actual configuration:

partition 1=ubuntu
partition 2=swap
partition 3=win xp home

I've tried adding to menu.lst

title 		Windows XP Home SP2
rootnoverify 	(hd0,2)
chainloader 	+1

but the error is 
Error 12: Invalid device requested

someone knows how to solve it?
Thanks![/QUOTE]
 yup, I had the same problem, and I just formated my whole hdd, installed windows xp on a
primary partition, and left some space for other partitons,
after that I installed my ubuntu partitons...  when u reboot ur system then it ask what OS, partiton u want to use...
and when u edid ur fstab file u can even use ur XP partion files in ur ubuntu OS... just add
this line to ur  fstab file: /dev/hda1 /media/windows ntfs umask =0222 0 0
and that file can be adited with :  sudo gedit /etc/fstab

---

### Post by kochab on 2005-06-02
I hope there is a way to recover the windows system without formatting,
anyone knows?
thanks

---

### Post by bored2k on 2005-06-02
[QUOTE=kochab]I hope there is a way to recover the windows system without formatting,
anyone knows?
thanks[/QUOTE]
 A million ways
1. Load your windows disc > recovery console > type fixmbr
2. Use tools like ultimatebootcd (.com) to do your worker (a bit more complicated, but better).

And btw, if you format, you wont recover data, you'll just lose it.

---

### Post by mingus on 2005-06-02
[QUOTE=kochab]Hi,
I had this setup:

partition 1= win xp professional
partition 2= win xp home

and the system used to boot from 1st partition.
now I've installed ubuntu on the first partition, it works fine but I cant manage to boot xp home.
actual configuration:

partition 1=ubuntu
partition 2=swap
partition 3=win xp home

I've tried adding to menu.lst

title 		Windows XP Home SP2
rootnoverify 	(hd0,2)
chainloader 	+1

but the error is 
Error 12: Invalid device requested

someone knows how to solve it?
Thanks![/QUOTE]
 The Windows "system partition" *must* be on the first partition.  This partition is simply the boot loader (ntldr), the control file (boot.ini) and the hardware detection script (ntdetect.com).  The rest of XP (Windows/system32) can be on any other partition, boot.ini will point to it.

If you had two copies of Windows installed on partitions 1 and 2, then your Home on p2 was booting from the system partition installed with Pro on p1.  Removing that is why you cannot boot Home now.

I am not aware of any way around this Windows requirement.

You have an additional problem.  I'm not sure how you got Home from hda3 to hda2, but be advised that that in your Windows Home registry there are a gazillion pointers to the drive letter Home was/is on.  If you try to just copy this partition back to partition 1, it will break.

Several options to consider:
1.  Remove Ubuntu from hda1, reformat, reinstall Home there, reinstall Ubuntu on hda3
2.  Remove Ubuntu from hda1, reformat, place Windows "system partition" files on hda1 (there is a KB article on the MS support site), change boot.ini to point to hda3, do >fixmbr, reinstall Ubuntu on a new partition.
3.  Remove Ubuntu from hda1, using a bit imaging backup tool like Ghost make an image of Home, reformat hda1, restore the image to hda1, run a tool like PartitionMagic's DriveMapper which will change all the drive letter pointers (must be done within the Recovery Environment), do >fixmbr, reinstall Ubuntu.  *Only if you really know what you are doing!*

No doubt there are other methods, too.  Bottom line, at the minimum you've got to get the Windows boot loader into the first partition.

---

