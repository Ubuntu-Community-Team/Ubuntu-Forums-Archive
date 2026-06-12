---
title: "I want to dual boot - again"
date: 2010-12-15
forum: Installation &amp; Upgrades
---

### Post by idontknowme on 2010-12-15
For the past few years i have used ubuntu off and on. I have some experience installing less common configs different on computers (like quad boot). But now i need you guy's help. My laptop is running Win7 x64. I want to be able to dual boot the newest version of ubuntu (in x64). Here is my problem.

  My entire drive is encrypted using TrueCrypt. I know i must first decrypt the entire drive and then shrink the partition to allow installation of said ubuntu. However i do not want to have a ton of loaders on my computer. I have tried installing GRUB with the TrueCrypt loader in the past. But there was some sort of conflict that would not allow me to do this (it was "long" ago and do not remember the exact problem). I would also like to encrypt the ubuntu volumes (EXT4,SWAP). Is it possible for me to have all the partitions encrypted and still be readable by the boot loader (preferably the TC loader)? If so Will it be read automatically? Or will i need to run separate loaders for each os? I looked around in the forums briefly and saw no exacting information regarding my situation. 

  Thanks much in advance, idontknowme

---

### Post by Herman on 2010-12-15
:D Unless you're a masochist and you want to torture yourself with a time consuming and challenging gauntlet of problems, I'd leave the Windows7 x64 TrueCrypt installation as it is and remove the hard drive from the laptop. Then I'd buy a whole fresh new HDD or SSD and use that one for installing Ubuntu in. Hard disk drives aren't cheap, but they're quite a lot more affordable than they were a few years ago.
It only takes a minute or two to remove a HDD and swap it for a different HDD in most laptops.

This installation guide will work for an internal hard disk drive if you just ignore the parts of it that refer to flash memory,  [Ubuntu Encrypted Flash Memory Installation]("http://members.iinet.net/%7Eherman546/p19.html"), and you would be able to ignore the advice about installing GRUB to the USB drive's MBR and simply let it be installed in the same disk, (since it will be the only disk in the laptop anyway).

Or, you could use the same procedure to install to an external HDD, but I recommend flash memory or SSD drives for portable external drives because of its durability. (Resistance to shock, less temperature problems, low power demand, and so on.  :)

---

