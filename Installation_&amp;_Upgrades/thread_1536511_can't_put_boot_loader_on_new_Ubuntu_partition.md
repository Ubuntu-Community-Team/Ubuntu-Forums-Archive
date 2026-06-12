---
title: "can't put boot loader on new Ubuntu partition"
date: 2010-07-22
forum: Installation &amp; Upgrades
---

### Post by corona79 on 2010-07-22
I am tying to add Ubuntu 10.04 desktop i386 to my Windows 7 PC.  I** do not **want to mess with the Windows  boot loader, so as the sentence from the guide at the bottom states,  tried to put GRUB onto the newly created partition for Ubuntu.  I could  not because upon choosing the device (which turned out to /dev/sda5) ,  the "OK" button was disabled  :sad:    

"Manual" option was chosen above - on a second try, I chose "use  all available free space" and Ubuntu created #5 and #6 on SCSI1 (0, 0, 0).   The new device was /dev-sda-1, but again, Ubuntu would not put the boot  loader on it.


[COLOR=Magenta][COLOR=Red]"If you have a problem with changing the MBR code, you might prefer to   just install the code for pointing to GRUB to the first sector of your   Ubuntu partition instead."[/COLOR]
[/COLOR] 
[SIZE=4]How?[/SIZE]

---

### Post by stlsaint on 2010-07-22
View the Grub2 link in my sig to see the official grub2 doc which will show how to install grub in various ways.

---

### Post by kansasnoob on 2010-07-22
> **corona79 said:**
> I am tying to add Ubuntu 10.04 desktop i386 to my Windows 7 PC.  I** do not **want to mess with the Windows  boot loader, so as the sentence from the guide at the bottom states,  tried to put GRUB onto the newly created partition for Ubuntu.  I could  not because upon choosing the device (which turned out to /dev/sda5) ,  the "OK" button was disabled  :sad:    

"Manual" option was chosen above - on a second try, I chose "use  all available free space" and Ubuntu created #5 and #6 on SCSI1 (0, 0, 0).   The new device was /dev-sda-1, but again, Ubuntu would not put the boot  loader on it.


[COLOR=Magenta][COLOR=Red]"If you have a problem with changing the MBR code, you might prefer to   just install the code for pointing to GRUB to the first sector of your   Ubuntu partition instead."[/COLOR]
[/COLOR] 
[SIZE=4]How?[/SIZE]

> do not [/B]want to mess with the Windows  boot loader

One way or another you must! You could use Easy BCD, but even that amounts to "messing with" the bootloader.

> The new device was /dev-sda-1, but again, Ubuntu would not put the boot  loader on it.


It's very doubtful that Ubuntu would be on sda1!

I'm somewhat unsure what your intentions are. You said:

> as the sentence from the guide at the bottom states,  tried to put GRUB onto the newly created partition for Ubuntu

I see no link to any guide????????????????

---

### Post by corona79 on 2010-07-23
The sentence is from[ the dual-boot guide at ubuntu.com]("https://help.ubuntu.com/community/WindowsDualBoot"). 
I know about EasyBCD, and that's what I wanted to use, but it serves no purpose unless the Ubuntu installer behaves nicely, which **it does not**.  :mad:

To say that the instructions for putting GRUB elsewhere failed is *the understatement of the miillenium*.
](*,)


Given that Ubuntu is supposed to be an especially easy to use Linux distribution, 
[SIZE=4]why is it so hard to set up a dual-boot system on a Windows PC[/SIZE]?

---

