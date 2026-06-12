---
title: "Triple boot, is it dangerous or something?"
date: 2012-07-31
forum: Installation &amp; Upgrades
---

### Post by rebelplankton on 2012-07-31
I'm getting bound to have 3 operating systems on my laptop and choose which to use at booting (Ubuntu 12.04, BackTrack 5 R2 and Windows 7). I used to use vmware player but now i can't, because it's not efficient anymore to do so, i must install them directly. Is there any risk or something I should be aware of before doing this?

Thank you.

---

### Post by Vakman on 2012-07-31
What sort of risks?

---

### Post by hakermania on 2012-07-31
No, there's nothing wrong with it. I have done exactly the triple boot you mentioned with Backtrack R5 gnome032 bit edition.

I would just suggest this installation order:
Windows 7
Backtrack R5
Ubuntu Linux

Also, you have to edit your bootloader so as to distinguish easily between Backtrack and Ubuntu, because, at least in my case, both showed up as 'Ubuntu'.

---

### Post by rebelplankton on 2012-07-31
> **Thisislaw said:**
> What sort of risks?

I don't know...that's what i am asking about...memory usage maybe?

---

### Post by rebelplankton on 2012-07-31
> **hakermania said:**
> No, there's nothing wrong with it. I have done exactly the triple boot you mentioned with Backtrack R5 gnome032 bit edition.

I would just suggest this installation order:
Windows 7
Backtrack R5
Ubuntu Linux

Also, you have to edit your bootloader so as to distinguish easily between Backtrack and Ubuntu, because, at least in my case, both showed up as 'Ubuntu'.

Why that order?...I already have Ubuntu, it's the one I have for personal use and I wanted to install the other two then. Please explain why the order is important.

---

### Post by QIII on 2012-07-31
The OSes not running will not be using any memory if you are doing an actual multi-boot.  This is not the same as running virtual machines.

---

### Post by hakermania on 2012-07-31
> **rebelplankton said:**
> Why that order?...I already have Ubuntu, it's the one I have for personal use and I wanted to install the other two then. Please explain why the order is important.

I recommend this order so as to save you from extra trouble:
If you install windows last, they don't detect anything, they boot only to themselves, they are egoists! And I think Ubuntu is more careful for more OSes than Backtrack, that's why I recommend it to be installed last.

But, no matter the order, you can always fix everything that may goes bad if you get your hands a little bit dirty.

---

### Post by rebelplankton on 2012-07-31
> **hakermania said:**
> I recommend this order so as to save you from extra trouble:
If you install windows last, they don't detect anything, they boot only to themselves, they are egoists! And I think Ubuntu is more careful for more OSes than Backtrack, that's why I recommend it to be installed last.

But, no matter the order, you can always fix everything that may goes bad if you get your hands a little bit dirty.

And what do you think about:
1.Ubuntu
2.Windows
3.BackTrack
?

---

### Post by hakermania on 2012-07-31
> **rebelplankton said:**
> And what do you think about:
1.Ubuntu
2.Windows
3.BackTrack
?

It's OK, but with no further action you will not have access to ubuntu after windows installation till you install backtrack which will detect both windows and ubuntu.

Also, you have to be careful not to overwrite ubuntu while installing windows!

---

### Post by rebelplankton on 2012-07-31
> **hakermania said:**
> It's OK, but with no further action you will not have access to ubuntu after windows installation till you install backtrack which will detect both windows and ubuntu.

Also, you have to be careful not to overwrite ubuntu while installing windows!

Thanks a lot, hakermania!

---

### Post by Vakman on 2012-07-31
> **rebelplankton said:**
> I don't know...that's what i am asking about...memory usage maybe?

No, this is not possible. You will use more hard drive space but that is all :).
As hakermania said, you should do the installations that way. As you already have Ubuntu installed, Backtrack last would be best.

---

### Post by rebelplankton on 2012-07-31
Sorry for being so nosy but...after the  3 installations I can delete any of them at any time I wish without messing around any of the two others, right?

---

### Post by ajgreeny on 2012-07-31
You can delete the partitions of the OS you don't want, but just be sure to have another OS supply the boot configuration before you delete anything.

For example if ubuntu is the final OS installed of the three, it will supply the grub bootloader and the configuration files for it.  If you then delete the ubuntu partition you will not be able to boot the machine at all until you have restored a new bootloader either from backtrack or windows.

PS: I have five OSs on my machine with no problems of any sort, so there is no reason to worry over the things that you asked about.

---

### Post by oldfred on 2012-07-31
You also have the issue of primary partitions. Windows will only boot from a primary NTFS partition with the boot flag or active partition in Windows. So if you have already installed Ubuntu did you use more than one or two primaries? You will have to have an extended partition to have the installs you want.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

### Post by hakermania on 2012-07-31
> **rebelplankton said:**
> Thanks a lot, hakermania!

Forgot to mention that the last time I did a triple boot (with backtrack installed last) it named itself and ubuntu as '_Ubuntu kernel_version (on /dev/sdaX)_' which I found weird, because it was not easy to distinguish between them.

Anyway, you will not have any problem editing the entries so as to be more realistic!

---

