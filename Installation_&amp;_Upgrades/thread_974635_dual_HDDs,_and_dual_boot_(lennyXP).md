---
title: "dual HDDs, and dual boot (lenny/XP)"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by graysky on 2008-11-07
I've read quite a few posts that cover various aspects of this topic, but before I go potentially hosing a healthy XP system, I wanted to ask directly the proper way to accomplish a dual boot with two HDDs.

Disk 1 (/dev/sda) contains two partitions, both NTFS. The first is a live XP-64 system, and the 2nd is a data partition.

Disk 2 (/dev/sdb) contains one partition and freespace. The partition is NTFS and contains data. There is about 200 gig of free space I'd like to use for lenny.

My plan is to create three new partitions on Disk 2 (/, swap, and /home, all ext3 except swap), and then do an install of lenny there. Here's where it gets fuzzy... I know grub should detect my XP installation, but I have never installed lenny on a system with another O/S.

I believe I do NOT want to install grub to the MBR on disk 1, right? What is the best option here. Also, what happens if I need to reinstall XP?

Thanks!

---

### Post by caljohnsmith on 2008-11-07
> **graysky said:**
> 
I believe I do NOT want to install grub to the MBR on disk 1, right? 
Yes, that's right, it is more ideal if you can install Grub to the MBR of drive 2, and then set your BIOS to boot drive 2 on start up. If for some reason Windows isn't automatically added to your Grub's menu.lst/grub.conf, just add an entry for Windows like:
```
title Windows XP
rootnoverify (hd1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
And that should be all it takes to boot Windows, assuming you only have the two drives.
> **graysky said:**
> 
Also, what happens if I need to reinstall XP?
You will probably have no problems if you reinstall XP, because XP will just write to the MBR of its own drive, not the Linux drive. Let me know if you need any more specifics. :)

---

### Post by graysky on 2008-11-07
Hey thanks for the reply... what if I place /boot on HDD #1 and the rest of my deb system on HDD #2 (/ and swap and /home) and allow grub to write to the MBR?  In this scenario I believe there won't need to be any tinkering in the BIOS since both grub and windows are on the same physical disc and if for some reason my hdd #2 fails, I can still boot into windows.

Thoughts?

---

### Post by caljohnsmith on 2008-11-07
> **graysky said:**
> Hey thanks for the reply... what if I place /boot on HDD #1 and the rest of my deb system on HDD #2 (/ and swap and /home) and allow grub to write to the MBR?  In this scenario I believe there won't need to be any tinkering in the BIOS since both grub and windows are on the same physical disc and if for some reason my hdd #2 fails, I can still boot into windows.

Thoughts?
Actually, that's the whole reason why it is more ideal to put Grub on your 2nd drive and boot it on start up; if something happens to the 2nd drive, your first drive is untouched, and you should be able to boot into Windows without a problem. It's really not a big deal to change the order of boot drives in BIOS, so I would try that approach first if I were you.

But if you're set on just booting the Windows drive, you could put your /boot partition on the Windows drive like you say, or you could even just make a super-dinky ~10 MB partition on the Windows drive just for Grub, and not the rest of the boot files. Or what I would recommend would be to simply install Grub4DOS inside Windows, and then you don't even have to do any repartitioning. Grub4DOS even has a lot more features than the legacy Grub, and it is fully compatible with Legacy Grub, meaning your Lenny menu.lst should work fine with Grub4DOS. 

Anyway, those are some of your options. :)

---

### Post by graysky on 2008-11-07
Thanks very much for the reply.  I'm pretty much a LINUX freshman, and have no idea how to handle GRUB4DOS as it relates to the lenny installer, but that sounds pretty cool otherwise :)

---

