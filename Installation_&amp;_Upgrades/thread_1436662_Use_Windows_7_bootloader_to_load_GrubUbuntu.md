---
title: "Use Windows 7 bootloader to load Grub/Ubuntu?"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by floepie on 2010-03-22
There are many tutorials regarding how to restore GRUB into the MBR following a Windows install, even how to make a dedicated GRUB partition.  However, I have installed Ubuntu after Windows, and I am now presented with GRUB upon boot, as GRUB was written to the MBR.  Is it possible to restore the W7 bootloader into the MBR and add a boot option for Ubuntu as one of the options in the W7 bootloader?

---

### Post by wilee-nilee on 2010-03-23
I would ask over at Windows seven forums they would have the answer.
[http://www.sevenforums.com/](http://www.sevenforums.com/)

---

### Post by stlsaint on 2010-03-23
So heres the deal. In all practicality NO you SHOULD not use the win7 bootloader to handle ubuntu. Others will tell you to use easybcd or maybe neoboot or somthing of that nature. In my many installation experience easybcd is about reliable as its user...Windows!! You MAY for some weird config be able to see the ubuntu install momentarily but pretty soon it will fail and crash your system. I HIGHLY suggest sticking to grub as it handles ubuntu and windows very well.

---

### Post by Gregorybekkers on 2010-03-23
Use GRUB or Bootit NG i like the 2nd one myself..

---

### Post by Mark Phelps on 2010-03-23
> **floepie said:**
> ... Is it possible to restore the W7 bootloader into the MBR and add a boot option for Ubuntu as one of the options in the W7 bootloader?

Yes ... it's possible .. but you have install a third-party app (one example of which is EasyBCD) which will then install GRUB4DOS (a GRUB equivalent that will install into an NTFS partition) and add an Ubuntu entry to the Win7 BCD.

If course, folks here are going to tell you NOT do use that approach, but I have tried it out on a laptop machine running Win7 and Ubuntu, and in 9 months of daily use, have never had it fail even once.

As to WHETHER you should use GRUB or EasyBCD ... it's really your call.

If you want to take the EasyBCD approach, go the the NeoSmart Technology forums.  They have tutorials and how-to's covering what you want to do.

---

### Post by Slim Odds on 2010-03-23
> **stlsaint said:**
> So heres the deal. In all practicality NO you SHOULD not use the win7 bootloader to handle ubuntu. Others will tell you to use easybcd or maybe neoboot or somthing of that nature. In my many installation experience easybcd is about reliable as its user...Windows!! You MAY for some weird config be able to see the ubuntu install momentarily but pretty soon it will fail and crash your system. I HIGHLY suggest sticking to grub as it handles ubuntu and windows very well.

I have to respectfully disagree.

There is absolutely nothing wrong with using the Windows 7 (or others) boot loader to load linux. There is not a ton of magic going on with boot loaders.

Here's what I do to dual boot Windows 7 and Ubuntu, and it's really quite easy. It is based on having a working Windows install and a free partition for linux (there are tons of other places to find out how to do that).

A) Install linux into its own partition and make sure to put GRUB on **that partition** and **NOT **the MBR (typically something like, /dev/sda1)

B) Boot using the Live CD and create a boot sector file from the linux partition by doing this:
```
sudo dd bs=512 count=1 if=/dev/{your linux partition} of=linux.bin
```and copy that file to your windows "C:" partition (you can find that in places the menu based on the label for your windows partition).

C) Create a new boot entry using the bcedit program.

D) Use a partition of "C:" and a path of "linux.bin"

E) Create a description, if you like

Now you can boot windows or linux.

---

