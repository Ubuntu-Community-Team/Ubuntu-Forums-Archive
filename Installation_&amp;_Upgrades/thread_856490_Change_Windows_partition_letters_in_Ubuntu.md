---
title: "Change Windows partition letters in Ubuntu"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by apche93 on 2008-07-11
Hi,

I was wondering if there was a specific order of partitions that affected the windows partition drive letter. 

For example,

/dev/sda2 might correspond to C: in windows vista

is there such a pattern that one could use?

[http://ubuntuforums.org/showthread.php?t=855931](http://ubuntuforums.org/showthread.php?t=855931)

That is my previous post which includes the partitions i have. Please help, i reallly need my vista back soon!

---

### Post by Pumalite on 2008-07-11
Check:
sudo fdisk -lu
Windows will be ntfs.

---

### Post by apche93 on 2008-07-11
> **Pumalite said:**
> Check:
sudo fdisk -lu
Windows will be ntfs.

[IMG]http://i260.photobucket.com/albums/ii30/apche93/Screenshot-1.png[/IMG]

Okay, first of all, i deleted all my previous partitions except the recovery vista partition.  Then i made the partitions shown above.  So, windows vista is almost completely gone from my OS.  I was wondering if settting a partition at /dev/sda2 meant that it would be equivalent to the C: drive in windows.  This is b/c when i go thru the recovery of vista, it says that my C: is missing or too small.

---

### Post by Pumalite on 2008-07-11
sda2 is an extended partition. sda3 and sda4 are probably what you are looking for.

---

### Post by apche93 on 2008-07-11
> **Pumalite said:**
> sda2 is an extended partition. sda3 and sda4 are probably what you are looking for.

I dont know if u understand my dilemma...

I think that Windows Recovery thinks that /dev/sda2 is C:


I was wondering if thats true or if there is a certain drive correspondence.

Plus Windows REcovery did not recognize sda3 & sda4.


I have an old Windows XP cd, and when i tried to install that, it said that the hd could not be read or something.

---

### Post by Pumalite on 2008-07-11
Double posting is no good.
[http://ubuntuforums.org/showthread.php?t=855931](http://ubuntuforums.org/showthread.php?t=855931)
Read post # 2 again.

---

