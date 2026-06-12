---
title: "How can I remove the GRUB while preserving everything on my HD?"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by mesh2005 on 2008-08-28
I've Ubuntu 7.04 and WinXP on my machine. My WinXP crashed (as usual) and I need to re-install it. It hangs each time I try to install WinXP and the tech support believe that it is because of the GRUB. Now, I need to remove the GRUB, install WINXP then put GRUB back again. How?

I've heard of fdisk /mbr but I also found a warning that it may damage hard disks with more than four partitions. I have around 6 partitions and I don't wanna loose anything, any help please?

Thank you

AM

---

### Post by coffeecat on 2008-08-28
> **mesh2005 said:**
> It hangs each time I try to install WinXP and the tech support believe that it is because of the GRUB. Now, I need to remove the GRUB, install WINXP then put GRUB back again. How?

In my opinion, any tech support person who says that grub is preventing installation of Windows clearly knows the square root of nothing at all about grub. And possibly knows only a very little more about installing Windows. The problem is the other way around. When you install Windows, it overwrites grub stage 1 on the mbr so that if you want to be able to boot into Linux, you need to reinstall grub.

And I've never heard of fdisk /mbr damaging more than four partitions, although this has the faint whiff of plausibilty about it. Grub stage 1, or the Windows bootloader, occupies the first 400 bytes or so of the main HD and the partition table comes immediately after. The command fdisk/mbr comes from msdos/Win95-98 days. Perhaps it is incompatible with extended partitions - but I really wouldn't know. For Windows XP, you use the fixmbr command, but this will only rewrite the mbr. I really think your Windows installation problem lies elsewhere.

Can you describe what happens when you try to install Windows? How far do you get? Perhaps someone will be able to help.

Having said all that, you could boot up the Windows XP install disc and go into the recovery console. Then try 'FIXMBR'. I can't remember whether you have to put an option after the command, but it will soon tell you if you need to. If you are successful, then try installing Windows - and if you are successful with that I'll take back my words about tech support and square roots. :wink: However, I have succesfully installed Windows XP to a drive that still had grub stage 1 on the mbr, so I doubt whether I will be taking back my words.

---

### Post by caljohnsmith on 2008-08-28
> **coffeecat said:**
> In my opinion, any tech support person who says that grub is preventing installation of Windows clearly knows the square root of nothing at all about grub. 
+1 I totally agree, I think that tech support person is clueless. I like your way of saying it though, coffeecat. :biggrin:

---

### Post by mesh2005 on 2008-08-28
Thank you guys. When I try to install WinXP, it simply hangs at the first step which displays three options: Enter to install, R to repair and F3 to quit! It totally hangs that I have no option but to press the power button.

The mainboard has no PCI cards on it, the VGA and sound are built-in. I tried different CDs but it always hangs at the first step, any ideas?

---

### Post by pgatrick on 2008-08-28
> **mesh2005 said:**
> Thank you guys. When I try to install WinXP, it simply hangs at the first step which displays three options: Enter to install, R to repair and F3 to quit! It totally hangs that I have no option but to press the power button.

The mainboard has no PCI cards on it, the VGA and sound are built-in. I tried different CDs but it always hangs at the first step, any ideas?

Have you thoroughly cleaned the insides of your computer? Also make sure RAM and such are all well seated in their slots.
Last time I had this problem I'm pretty sure it was related to dust and loose connections.

---

### Post by caljohnsmith on 2008-08-28
> **mesh2005 said:**
> Thank you guys. When I try to install WinXP, it simply hangs at the first step which displays three options: Enter to install, R to repair and F3 to quit! It totally hangs that I have no option but to press the power button.

The mainboard has no PCI cards on it, the VGA and sound are built-in. I tried different CDs but it always hangs at the first step, any ideas?
If I remember correctly, having your Win XP install hang is a bug with the Windows installer (or maybe Microsoft calls it a "feature" :roll: ) caused by the *mere presence* of your Linux partitions. And unfortunately I'm not being facetious when I say that. If this is truly your problem (which I can't be sure), the fix is relatively easy. Just boot into Ubuntu (either on your HDD or from a Live CD), and you have to temporarily "hide" all your linux partitions. So first you have to figure out which are your Ubuntu partitions (both main and swap) if you don't know all ready:
```
sudo fdisk -lu
```
If your Ubuntu partition is sda2 for example, in Grub's Convoluted World that is (hd0,1). So then to hide that partition, you would:
```
sudo grub
grub> hide (hd0,1)
```
Do that for both swap and the main Ubuntu partition, and try and reinstall Windows. When you are ready to unhide your Ubuntu partitions, just use "unhide" instead of "hide" above. Let me know how it goes. :)

---

