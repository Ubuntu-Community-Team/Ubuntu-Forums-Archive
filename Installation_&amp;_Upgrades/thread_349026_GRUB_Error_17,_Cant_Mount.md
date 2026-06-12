---
title: "GRUB Error 17, Cant Mount"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by pixelboy on 2007-01-29
Hi Guys,

Yes its another grub issue, I've searched but haven't been able to totally fix my problem.

I have a dual boot system and I was in XP the other day sorting out a problem with my external USB drive using partition magic and I think its screwed my ext3 partitions...

When I left XP to boot back to Ubunbtu (Edgy amd_64) I got error 17 before grub prestented the OS choice. I followed some good advice from this forum and was able to restore grub to the point where I now see the OS list and am able to boot to XP but when I choose Ubunbtu I get error 17 again?

I have both my XP and Ubuntu ext3 partitions on the same SATA drive.

I suspect there is something wrong with my ext3 partition and I cant just delete it as I need to recover some data. Id also prefer not to re-install ubuntu if possible.

Is there anything I can do to recover this partition? I have my install CD I can boot to if needed.

Thanks in advance

---

### Post by Iarwain ben-adar on 2007-01-30
Hi,

please post the contents of these commands

```
sudo  fdisk -l (a lowercase L)
sudo cat /boot/grub/menu.lst
```

This should help us :D


Iarwain

---

### Post by pixelboy on 2007-01-30
Thank you Iarwain ben-adar for your reply but it became urgent to access the data from that drive and I found a windows utility that would let me access it.

Ive re-installed windows and have got what I needed to do done.. 

Ill re-install ubuntu soon.

Thanks and sorry if I wasted your time.

---

