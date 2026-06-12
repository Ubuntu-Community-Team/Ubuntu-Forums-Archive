---
title: "Ubuntu Installed twice"
date: 2010-04-07
forum: Installation &amp; Upgrades
---

### Post by MirSo on 2010-04-07
Hi.

I'm new to Ubuntu and not an IT-genious in any way. My problem is  as follows:

I installed Ubuntu next to my xp and failed to launch it at all after  downloads due to the insufficient space (I think). I re-installed the  Ubuntu and didn't dare to partition it myself, and let the computer do  it, resulting for the both Ubuntus being present now (at least they're  both listed in the boot).

Is my next best step to partition/combine somehow those two Ubuntu areas  or just re-install a partitioning over the two or just install a third  Ubuntu :). The initial problem is that I deleted quite many applications  to gain space and for this my wireless network don't even appear on the  desktop or anywhere. If there's a simple solution for this, I'm all  ears!

Many thanks!

---

### Post by oldfred on 2010-04-07
Does XP still boot ok. Just want to make sure you did not shrink it too much. You always should defrag XP twice after housecleaning as much as you can.

I would suggest using the liveCD and in system, applications is gparted which will show your partitions. If you know how much space you want to give XP you can shrink it some more but always leave about 20% free space or XP may not work well. If you see any locks the liveCD is using the swap ( one or both of the swaps) and you need to right click and use swapoff. You then can delete your Ubuntu and swap partitions. Then I would reinstall using the available free space option.

Of course you have backed up everything important in XP. The biggest risk is the user clicking use entire hard disk or other user issues.:)

---

### Post by duanedesign on 2010-04-07
MirSo,
I am curious if what you have is two full Ubuntu installs or two kernels. Often times Grub will show more than one kernel at boot. This is not uncommon and in fact it is recommended you keep at least two installed in case one goes south. Does it look something like this:

[IMG]http://farm5.static.flickr.com/4046/4501465608_f975e6a2ac.jpg[/IMG]

are the kernel numbers different. For instance:
2.6.28-15-generic
2.6.28-16-generic

Could you run the following command in a Terminal (Applications > Accessories > Termina) and post the results

```
sudo fdisk -l
```

---

### Post by ElPastor on 2010-04-08
Hi there,

I've had the same problem as above... The other thing is that in the updated version of the kernel I can't use the trackpad :=( I have to go to the old kernel number to have it working. Could you help me?

Here is what you asked for:

Disco /dev/sda: 120.0 GB, 120034123776 bytes
255 cabezas, 63 sectores/pista, 14593 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xf6aef6ae

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        3988    32033578+   7  HPFS/NTFS
/dev/sda2            3989       14593    85184662+   f  W95 Ext'd (LBA)
/dev/sda5            7297       12334    40467703+   7  HPFS/NTFS
/dev/sda6            3989        7205    25840489+  83  Linux
/dev/sda7            7206        7296      730926   82  Linux swap / Solaris
/dev/sda8           12335       14502    17414428+  83  Linux
/dev/sda9           14503       14593      730926   82  Linux swap / Solaris

Las entradas de la tabla de particiones no están en el orden del disco

---

### Post by MirSo on 2010-04-09
Thanks for the suggestions so far; I haven't had time to get deep into the problem yet, but I shot and attached a nice photo of the booting option for duanedesign for more details. I'll send the terminal report too later.

Oldfred, the XP is thankfully working fine (maybe some stickyness) and I've defragmented only once now. XP is still a crucial tool for me for work and special programs so I don't want to shrink it more at all. I wanted to make Ubuntu for now as small as possible, without games and such, for which I lost the wireless icon and commands :oops: I think it had to do with some bluetooth application that I removed...

Of course, if someone knows how to recover this wireless thingy, it may be easier than re-installing.

---

### Post by codemaniac on 2010-04-09
you should always create your partitions manually and feed them to the ubuntu installer rather than instruct the installer to create partitions for you..You have currently two swap partitions which is unneccesary...

---

