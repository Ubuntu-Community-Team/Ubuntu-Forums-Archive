---
title: "Keeping Windows XP and installing 5.04"
date: 2005-08-27
forum: Installation &amp; Upgrades
---

### Post by Thorpe on 2005-08-27
[FONT=Trebuchet MS]I received the Ubuntu Linux CDs today and one of them is for installing it rather than running off a LiveCD. How do I get Windows XP to remain but with Ubuntu Linux installed? Is it possible to allocate a certain amount of hard drive space as well or is that not possible since it is probably all allocated to Windows XP. I know it did mention about installing in "Expert" mode if you want to keep your previous operating system but I'm still a little confused. Any help would be greatly appreciated.[/FONT]

---

### Post by frodon on 2005-08-27
The ubuntu install CD will allow you to to create  a partition for linux (if you need to create one, it seems to be the case for you) with the free space of your hard drive (you can choose the size you want), then just follow the install CD steps and you will have a double boot system, each time you will start your computer you will have the choice ... windows or ubuntu.
So don't worry, installing ubuntu will not erase windows  :wink:

---

### Post by doronunu on 2005-08-27
just dont install the bootloader on the mbr

---

### Post by KurtB on 2005-08-28
- I first partitioned my HD using partition magic (first did backup of my data, which was very necessary...)

- I unallocated one of th ntfs partitions

- booted PC with ubuntu disk -> when I came to the partitioning-step I selected to automatically partition the FREE SPACE...

- I did install bootloader GRUB on the MBR...

And it works fine for me now   ;-)

---

### Post by manicka on 2005-08-28
[QUOTE=doronunu]just dont install the bootloader on the mbr[/QUOTE]
 I'd recommend doing the opposite. You'll find the mbr easier to restore of you change your mind about ubuntu. Install the bootloader on the mbr
KurtB steps are probably the easiest way to do it. Make sure that you create the free space before starting.

---

