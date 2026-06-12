---
title: "XP cd won't load"
date: 2006-04-27
forum: Installation &amp; Upgrades
---

### Post by f3tus on 2006-04-27
OK, so I have some bad sectors on my windows disk, I suppose, that's why it doesn't let me boot it. It goes all the way to that loader and then just restarts. Safe mode or any other mode doesn't work either. I don't know what could have caused this, the only thing I can remember doing wrong is I unplugged the main power cable instead of the normal shut down...

Anyway, I tried to boot with my XP cd and repair it, but... It doesn't boot!
It starts reading the cd (I hear that sound everytime when I put a cd in), but just skips to grub! I tried all sorts of things in bios, I even disconnected the linux disk.

I know the windows cd works, I tried to run it with xwine and it worked.

How am I supposed to even reformat the windows partition if it's really neccessary? Damn!

Please help :/

---

### Post by Sef on 2006-04-27
> How am I supposed to even reformat the windows partition if it's really neccessary?

Why do you want or need to reformat your windows partition?  Is it to get rid of those bad sectors?  If so, have you tried scan disk set on thorough?

---

### Post by f3tus on 2006-04-27
Format is just the last case scenario. I used a win98 boot floppy and used scandsk, but it didn't even ran for 2 seconds and it returned without errors. Could I try anything else?

---

### Post by syg00 on 2006-04-27
Let's see an "fdsik -l" (from Linux) - the M$oft loaders are a bit gnarly about partition structure.

---

### Post by f3tus on 2006-04-27
```
Disk /dev/hdc: 40.0 GB, 40020664320 bytes
255 glav, 63 sektorjev/stezo, 4865 stez
Enote = cylinders od 16065 x 512 = 8225280 bajtov

  Naprava Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        4865    39078081    5  Extended
/dev/hdc5            4733        4865     1068322+  82  Linux swap / Solaris
/dev/hdc6               1        4731    38001663   83  Linux

Partition table entries are not in disk order

Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 glav, 63 sektorjev/stezo, 19457 stez
Enote = cylinders od 16065 x 512 = 8225280 bajtov

  Naprava Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS
```

Don't mind my native language ;P

---

### Post by syg00 on 2006-04-27
Everything looks sane there.
Only thing I can think of is that your S-ATA chip is not supported by the CD. I think you need to hit F6 (er,   ??? - maybe F8 ), and provide a floppy with the driver on.
Just guesswork tho'.

---

### Post by f3tus on 2006-04-27
No it can't be that, I've used the same XP cd before and it worked. I tried with 3 different XP cds, but none worked! I tried Kubuntu & Win98SE - they worked.

Why?! Any pattern anybody can think of? What's different in booting 98 and XP?

All XP cds were bootable.


I downloaded the 6 pack XP boot floppies and gave it a shot, but I get "File setupdd.sys could not be loaded. The error code is 4" on the 3rd floppy :/

---

### Post by Sef on 2006-04-27
> No it can't be that, I've used the same XP cd before and it worked. I tried with 3 different XP cds, but none worked! I tried Kubuntu & Win98SE - they worked.

Why?! Any pattern anybody can think of? What's different in booting 98 and XP?

Seems like the disk has gone bad.  Since you can boot up with Win98 and Kubuntu,  it's not your computer at all.  Therefore it must be your XP cd.

---

