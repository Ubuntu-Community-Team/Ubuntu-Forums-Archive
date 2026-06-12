---
title: "Windows XP Gone."
date: 2005-02-13
forum: Installation &amp; Upgrades
---

### Post by L1nVx on 2005-02-13
Hey i installed ubuntu set up dual booting and all that and did grub on the master boot and well unlike knoppix (were it had both on the boot loader and i could choose either) i get to the grub thing and windows xp is there but i go to it and it starts booting says like hd 0,0 or something then savedefault and some other stuff (i do not remember i will check if you ned it) then it has a flashing - thing and i check the comp lights and it's doing nothign after like two minutes.  So now i can't get to Windows XP i am wondering why this is happening... any ideas?

---

### Post by Adrenal on 2005-02-13
Hmm, did you get all of it?
Kidding, hmm, try reinstalling grub

---

### Post by L1nVx on 2005-02-13
how do i reinstall grub (i have it on the MBR)

oh and here's what it says when trying to lold up xp

root (hd0,0)
filesystem type unknown partition type 0x7
savedefault
makeactive
chainloader + 1

---

### Post by Xian on 2005-02-13
[QUOTE=L1nVx]how do i reinstall grub (i have it on the MBR)
[/QUOTE]
Here's a quick how-to: [Retore Grub](http://www.sorgonet.com/linux/grubrestore/)
Post back with any questions.

---

### Post by L1nVx on 2005-02-13
okay i will try that sometime :) when i get a chance.

---

### Post by dewey on 2005-02-13
I'm having the exact same problem now, except I'm using Win2k(which is still NTFS)

I tried to reinstall grub like you said, but I would get weird errors about parsing and the like.  Aswell as the old "Partition type 0x07" message.
Here's my partition scheme as outputted by "sudo fdisk -l"
```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       62029    31262458+   7  HPFS/NTFS
/dev/hda2           62029      155061    46888223    f  W95 Ext'd (LBA)
/dev/hda5           62029      113906    26145756    b  W95 FAT32
/dev/hda6          153078      155061      999904+  83  Linux
/dev/hda7          113907      129407     7812472+  83  Linux
/dev/hda8          129408      153077    11929648+  83  Linux

Partition table entries are not in disk order

```

And here is relevant information from my grub menu.lst

```
title		Windows2k
root		(hd0,0)
makeactive
chainloader	+1

title		Ubuntu, kernel  
root		(hd0,6)
kernel		/boot/vmlinuz root=/dev/hda7 ro console=tty0 quiet splash
initrd		/boot/initrd.img
savedefault
boot

```

---

### Post by dewey on 2005-02-14
Nobody has any ideas?  I would really like to be able to boot into windows...
I even did an FDISK Verify, to make sure something wasn't totally wrong, with this as the output.
```

Command (m for help): v
1003 unallocated sectors

```

Please help.

---

### Post by Xian on 2005-02-14
[QUOTE=dewey]Nobody has any ideas?  I would really like to be able to boot into windows...[/QUOTE]
If you can't re-install grub for whatever reason you will either have to install an alternate bootloader such as lilo, or you can just re-set the MBR back to the original settings. In XP this is done by loading the install CD, starting a restore session and entering the command "fixmbr". This may not be the same for your Win2K, but there is certainly a similar resource that would enable you to accomplish this function. 

Here's another how-to on restoring grub that perhaps is easier to follow: [Restoring Grub in Linux](http://geodsoft.com/howto/dualboot/grub.htm#install)

---

### Post by dewey on 2005-02-14
I followed the second set of grub instructions you posted, and it seemed to work, although it kept all the old config files and such (I assume all the instructions did, was reinstall it in the mbr and on the boot sector of my linux partition) so it still didn't work, the exact message I get when booting to windows is.
```

     Booting 'Windows2k'
root (hd0,0)
  Filesystem type unknown, partition type 0x7
makeactive
  Chainloader +1

```
With a flashing _, and it just hangs there.

I'm looking into a Win2k Recovery Bootdisk at the moment.

---

### Post by Xian on 2005-02-14
Try to set the hard drives to LBA or large access mode in the computer's BIOS. 
It is important that the hard disk values not be set to "AUTO".

You can definitely get this error is such a setting does exist.

---

### Post by L1nVx on 2005-02-14
well when i had knoppix on there windows xp loaded fine so i don't think it's that.

---

### Post by dewey on 2005-02-14
Good lord man, I was close to just wiping the whole drive!

I went into my bios, and changed my ide settings from "auto" to "LBA" and it worked like a charm!

Can't believe it was such a small problem, that caused so much grief, many thanks!

---

### Post by L1nVx on 2005-02-14
i got the same error... can someone tell me why that is the problem and will the hd run slower with LBA not Auto?

---

### Post by Xian on 2005-02-14
[QUOTE=dewey]I went into my bios, and changed my ide settings from "auto" to "LBA" and it worked like a charm! Can't believe it was such a small problem, that caused so much grief, many thanks![/QUOTE]
The devil is in the details. :) 
I'm glad you got things running.

---

### Post by Xian on 2005-02-14
[QUOTE=L1nVx]i got the same error... can someone tell me why that is the problem and will the hd run slower with LBA not Auto?[/QUOTE]
The partitioning tool parted probably wrote an incorrect partition table. This can happen if the BIOS and Linux see different disk geometries and if the first hard disk partition ends on cylinder 1024 or beyond this point. When you boot the computer, Windows may use the values in the partition table, which causes a failure.

I'm unaware of any speed reductions in the HD.

---

### Post by L1nVx on 2005-02-14
and will changing the setting slow my computer down in any way?

---

### Post by Xian on 2005-02-14
[QUOTE=L1nVx]and will changing the setting slow my computer down in any way?[/QUOTE]
As I said, I'm not aware of any speed reductions but I've done no strict comparisons.

---

### Post by cliff58 on 2005-02-23
After toying with Ubuntu in MS VirtualPC for a couple of days, I just had to put it on my hard drive for a dual boot machine.  :grin: 

No more Windows XP  :-x 

But that switching to LBA in the BIOS just saved my arse!  :mrgreen:

Thanks, Xian!

---

### Post by movery on 2005-02-23
what about if you can't set it to LBA mode in the bios?  I only have two options, Auto, or disabled.. :(

---

### Post by Useless on 2005-02-23
what kind of bios do you have?

---

### Post by BOBuntu on 2005-02-24
[QUOTE=movery]what about if you can't set it to LBA mode in the bios?  I only have two options, Auto, or disabled.. :([/QUOTE]
I have the same problem too.

---

### Post by Useless on 2005-03-07
[QUOTE=BOBuntu]I have the same problem too.[/QUOTE]
 is this an old bios/system?

---

