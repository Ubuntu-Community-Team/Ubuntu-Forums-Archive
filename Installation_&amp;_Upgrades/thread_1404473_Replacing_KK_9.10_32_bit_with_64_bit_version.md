---
title: "Replacing KK 9.10 32 bit with 64 bit version"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by Muchoaliento on 2010-02-11
Hi there,

I am intending of replacing my Karmic Koala 32 bit installation with 64 bit version.
In my HDD I have several partitions:
* KK 32 bit (to be replaced) as ext 3 (20 Gb)
* Windows xp pro 32 bit as NTFS (26 Gb)
* Fileserver as NTFS running with NTFS-3G driver or something like that
* Swap as swap (slightly less than 1 Gb)
 
My physical mem is of 2 Gb and I want to reduce WXP partition's size in favour of KK 64 bit.

1) Using Gparted from LiveCD, do I simply delete the 32 bit partition, reduce size of WXP partition and install 64 bit in the empty space ?
2) Do I need to increase swap space ?
3) Should I use ext4 filesystem instead of ext3 ?

TIA, regards,

---

### Post by .nedberg on 2010-02-11
> **Muchoaliento said:**
> 
1) Using Gparted from LiveCD, do I simply delete the 32 bit partition, reduce size of WXP partition and install 64 bit in the empty space ?

Yes, don't forget to resize the new KK partition!
> **Muchoaliento said:**
> 
2) Do I need to increase swap space ?

No, not if you don't want to. I think it is recommended to have at least the same as your RAM if you want to suspend your computer.
> **Muchoaliento said:**
> 
3) Should I use ext4 filesystem instead of ext3 ?

I see no reason why you should not!

---

### Post by howefield on 2010-02-11
> **Muchoaliento said:**
> do I simply delete the 32 bit partition, reduce size of WXP partition and install 64 bit in the empty space ?

Run the defragmenting program in Windows prior to resizing.

---

### Post by Muchoaliento on 2010-02-11
Thx howefield and .nedberg for your prompt responses.

---

