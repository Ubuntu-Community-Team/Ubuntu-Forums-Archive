---
title: "Installing without installing GRUB? (or whatever bootloader it uses)"
date: 2012-09-06
forum: Installation &amp; Upgrades
---

### Post by Psythik on 2012-09-06
I don't want to go into details, but I have a somewhat complicated boot configuration due to the way my system is setup. I would prefer to not go through the trouble of figuring out how to redo it in GRUB.

Ideally I'd like to install Ubuntu without it laying a finger on Win7's bootloader, then go and add it in later. I know it's possible to use Windows' bootloader with Ubuntu, but is the other part possible too?

I'm a major nub when it comes to *nix, so please try to explain things in terms that a Windows power user can understand. Thanks!

---

### Post by sudodus on 2012-09-06
First of all, please backup your drive before installing Ubuntu. Something might go wrong ...

When you run the installer and get the question about partitioning (how to install Ubuntu), select

***'Something Else'***.

This means manual partitioning, or to install Ubuntu into some already prepared partition(s).

[SIZE="3"]And here is the critical point: Select how to install grub![/SIZE]

Do ***not *** install the grub bootloader into the boot sector ([FONT="Courier New"][SIZE="3"]/dev/sda[/SIZE][/FONT] for the first drive). Instead you can install it to Ubuntu's partition.

For example if you install Ubuntu to partition number 9 or the second drive [FONT="Courier New"][SIZE="3"]/dev/sdb9[/SIZE][/FONT], *** install grub into the same partition***. Then it will sit there and do nothing, so your Windows bootloader will still work.

---

### Post by Mark Phelps on 2012-09-06
> **Psythik said:**
> ...I know it's possible to use Windows' bootloader with Ubuntu, ...

One easy way to do this is to install EasyBCD from Neosmart Technologies in MS Windows -- and then use the option to add a Linux OS entry.  That will allow you to boot into Ubuntu from the MS Windows OS selection menu.

---

