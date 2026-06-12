---
title: "Looooong time to Grub2 menu"
date: 2009-08-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by autocrosser on 2009-08-27
Just updated to this evenings grub2 & maybe it's a problem with the kernel fix or a <new> problem with grub2----After restart it takes 1~2 minutes to get thru the first grub screen info & another 1~2 minutes to get to the menu--all with a great amount of drive thrashing to even get there---This is with a i7-920/SATA2 system that has zipped thru this before & had no problem until the last update---Anyone else have this happen?  If I get enough yes(s)--looks like bug report time...........

---

### Post by dino99 on 2009-08-28
same trouble here: having 2 lines comments "minimal bash-like line ..." with a noisy hdd before grub menu pop up. Seem that searching kernels is a problem: this is new since last grub2 upgrades.

I'm waiting to install the new kernel coming up ( 31-8 ) before reporting bug.

---

### Post by autocrosser on 2009-08-28
I pushed the -8 kernel thru & grub2 is still having a problem--I'll wait to see if more people have a problem before I report a bug--could still be just a temporary glitch that the next grub update will remove...I only reboot every couple of days with this unit......

---

### Post by Regenweald on 2009-08-28
my problem is actually after kernel selection. between selection of rc8 and the beginning of system loading, i look at the cursor blinking for about 15-25 seconds.

---

### Post by dino99 on 2009-08-28
problems are still there with 31-8.
Last grub2 upgrades need to be fixed.

---

### Post by pulpo69 on 2009-08-28
i can confirm the problem with grub2. here too.

---

### Post by autocrosser on 2009-08-28
Sounds good---I'll do a bug report in about 4~5 hours from now unless someone wants to before me (at slavejob)......

---

### Post by autocrosser on 2009-08-29
Bug Report filed:   [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)

---

### Post by jocko on 2009-09-04
Is this fixed with today's grub-pc update (to version 1.97~beta1-1ubuntu4)?
I did some experimenting with switching my sata cables around and managed to get rid of the lag, but afterwards I noticed that there was a grub-pc update either sometime before I started experimenting or during my experimenting (I did install some updates both before and during my experiment but didn't notice any grub-pc update, so I'm not sure what fixed it).

Anyway, if it wasn't the update that fixed it, I posted my possible workaround in the bug report (post 15).

---

### Post by ayates on 2009-09-04
> **jocko said:**
> Is this fixed with today's grub-pc update (to version 1.97~beta1-1ubuntu4)?
I did some experimenting with switching my sata cables around and managed to get rid of the lag, but afterwards I noticed that there was a grub-pc update either sometime before I started experimenting or during my experimenting (I did install some updates both before and during my experiment but didn't notice any grub-pc update, so I'm not sure what fixed it).

Anyway, if it wasn't the update that fixed it, I posted my possible workaround in the bug report (post 15).

I don't think today's update fixed the problem, so I tried your workaround(installed grub to the same drive where the boot folder is located and booted from that drive - no more delay). It seems
to be something with grub on one drive and boot folder on another for sure.

---

### Post by autocrosser on 2009-09-05
I differ a bit--it has reduced the lag by about 50% on my system--I did not do the "workaround" for testing & went from 4~5 minutes to about 2~3 minutes--not good, but better than it was--For reference, my grub is on /sda & /boot is on /sdc--so differing locations is the problem.

---

### Post by jbernardo on 2009-09-05
I wonder if different locations for / and /boot is indeed the problem. I was hit with it when trying to go from grub to grub2 on a eeepc 1101ha. I admit I think it is the same - I never had the patience to wait 2-3 minutes for the chainloaded grub2, gave up after 15-30 seconds and booted using the old grub entries. Time to see if with the grub2 and grub-pc updates it is still there and is indeed the same problem.

---

### Post by jbernardo on 2009-09-05
Ok, it seems my problems with grub2 are more serious. It won't ever get to the menu. And I made the mistake of trying to use it stand alone, instead of chainloading to see if it would help. Now, after reinstalling grub, it won't work if I use UUIDs (and I triple checked if the UUIDs are right). It will only boot if I use devices in the kernel line (/dev/sda5) and "root (hd0,4)". Seems like grub/grub2 don't like very much the partitioning strategy of the Asus eee... :(

---

### Post by bennachie on 2009-09-05
My problem on my eeePC-1000H is that the latest iteration of Grub2 will neither recognise Windows nor any other Linux installation (the previous version was equally dismissive of Linux, but at least recognised that I had a Windows partition, and allowed me to boot into it). 

I had assumed that this was simply because Grub2 is not ready for prime time - and the Ubuntu 9.10 Alpha series is presumably the first really thorough spell of testing the new system has had - but perhaps there is actually something peculiar about our excellent little machines.

9.10 alpha 5 otherwise runs fine for me (I was quite impressed really, although I could do without the advertising during the installation - but at least the installer respects the screen dimensions). However, denying me access to my other operating systems is a deal-breaker. I've returned to 9.04 for the moment. Never thought I'd be grateful for Grub1.

---

### Post by jbernardo on 2009-09-05
@bennachie: does it at least show you a menu, or do anything else other than just hang? I even tried to add "set debug=all" at the start of grub.cfg, and it won't show anything, just the "welcome to grub" string.

---

### Post by jocko on 2009-09-05
> **jbernardo said:**
> I wonder if different locations for / and /boot is indeed the problem.
I don't think the problem is different locations for / and /boot as I have /boot as a normal folder on the / partition. My problem was that I had grub installed to the mbr of one hard drive but the / filesystem (including the /boot folder) was on a different hard drive.

Since you have a netbook, you probably only have one hard drive, in that case you can't have the same problem as us.
Or perhaps it's got some kind of solid state drive plus a normal hard drive?

In that case, how have you set up ubuntu? If you have either the / partition or a separate /boot partition on a different drive than the one with grub on it you could very well have the same problem. In that case it may be good if the developers were notified, as I guess it could help them to know if it's the location of the /boot folder or the / partition (or both) that causes the lag. Or even if the lag gets shorter or longer depending on the location of all three relative to each other (i.e which physical drive has an mbr with grub, which has the / partition and which has the /boot folder/partition).

---

### Post by jbernardo on 2009-09-05
I think my problem is probably a different one - indeed this notebook only has one hd (160GB sata), and the fdisk -l output is:
```

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cilindros of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6e762533

Dispositivo Boot Início Fim Blocos Id Sistema
/dev/sda1   *           1       10812    86847358+   7  HPFS ou NTFS
/dev/sda2           10813       18813    64268032+   5  Estendida
/dev/sda3           18814       19451     5124735   1c  FAT32 Win95 Escondida (LBA)
/dev/sda4           19452       19457       48195   ef  EFI (FAT-12/16/32)
/dev/sda5           10813       12636    14651248+  83  Linux
/dev/sda6           12637       18570    47664823+  83  Linux
/dev/sda7           18571       18813     1951866   82  Linux swap / Solaris

```

I only used the space of the previously existing second ntfs partition to install ubuntu (/, /home and swap), and left the rest of the partitions (1-4) unchanged.

---

### Post by bennachie on 2009-09-05
Yes, I get a menu,and quite promptly  but only containing 9.10 pointers (the usual collection). BTW, my eeePC-1000H has a single 160GB hard disk, which is pretty much standard netbook fare these days. Incidentally, 9.10 runs just fine on my original eeePC 701 4G, but multiple-boot environments are a bit out of the question there ...

---

### Post by jbernardo on 2009-09-06
My problem seems to be UUID related. If I have in menu.lst "uuid ...." it won't boot any linux entry. If I have "root (hd0,4)" it will boot. I can still pass "root=uuid=..." to the kernel.
Also, the EF partition doesn't seem to have a uuid, I wonder if it is related:
```
$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2009-09-06 17:32 0480dcc8-f665-4bc5-869b-6210798c90d2 -> ../../sda7
lrwxrwxrwx 1 root root 10 2009-09-06 17:32 98B4757BB4755CA6 -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-09-06 17:32 CCED-990E -> ../../sda3
lrwxrwxrwx 1 root root 10 2009-09-06 17:32 d6024f98-7625-491a-b8af-34d879d8b8b8 -> ../../sda6
lrwxrwxrwx 1 root root 10 2009-09-06 17:32 d6fd38ae-05ca-4858-9091-5ee51989bde1 -> ../../sda5
```

---

### Post by autocrosser on 2009-09-06
I know that they just enabled disk-by-UUID not long ago--looks like this is a separate bug that had better be reported.....If you report it--I'll confirm it for you.

---

### Post by jbernardo on 2009-09-06
Ok, I'll do it in a couple of hours, have to leave now. I've been googling trying to find anything, any grub problems with this type EF partition, but nothing.

---

### Post by jbernardo on 2009-09-06
> **autocrosser said:**
> I know that they just enabled disk-by-UUID not long ago--looks like this is a separate bug that had better be reported.....If you report it--I'll confirm it for you.

Done - [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/425359](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/425359)

---

### Post by autocrosser on 2009-10-10
I went ahead & totally changed my system last nite...Installed the beta release to the first partition on the first drive & so now grub2 is on the same as the MBR---result: Grub2 now takes 5sec to menu & boots at once to the selected kernel--I would say that this will be a big headache when 9.10 is released.....Anyone with a multi-boot/multi-disk system will have a varied problem with boot-to-menu times, my case most likely shows the extreme--Grub2 was on the 3rd drive/1st partition in a 1.5TB system. I have not heard back from the Grub2 developer (Vladimir) in a couple of weeks now & got tired of the 5+min wait to GDM.

---

