---
title: "Triple Boot Config Advice (kinda complicated)"
date: 2010-08-19
forum: Installation &amp; Upgrades
---

### Post by d3mncln3r on 2010-08-19
I know this isn't strictly an Ubuntu question, but I figured users on this site would have some good knowledge regarding this type of configuration.

I would like to have a triple boot set-up on my Sony VAIO. I want to install Windows 7 64 bit, Windows Vista 32 bit, and Ubuntu (prob 64 bit).

The reason for this is, when I purchased my computer it had Vista 32 bit installed. I bought Windows 7 64 bit later and did a clean install. Many of the features were missing, or not working properly, and I've tried everything to get them up again, i.e. webcam, track-pad, "S" buttons, etc.

I have two hard drives that were originally set up in a RAID, which I undid, so I could have Windows 7 on one drive, and Ubuntu on another drive (because I couldn't get Ubuntu to install over the RAID.)

I'm thinking I should have Windows 7 and Ubuntu each 64 bit on one hard drive, and put Vista on the other hard drive, partitioning the remaining space for storage.

Does this set-up sound reasonable? What order should I install the operating systems? I'm thinking Vista first, then Windows 7, then Ubuntu.

Any advice on a triple boot of this type of config? Thanks ahead of time!

---

### Post by oldfred on 2010-08-19
Windows will want to combine its boots into one active (boot flag) partition. If you want to directly boot either windows you have to hide the first install from the second by removing boot flag.

I like to keep a boot loader in the same drive as the operating system and set BIOS to boot the Ubuntu/grub drive as it lets me choose all systems to boot.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

If you had RAID you may still have metadata on drive that can confuse things. DO NOT run this if you want to keep raid.
Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discussion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by pharcycle on 2010-08-19
hi,

Do you really need vista? 

If so, i'd partition one of your hdds in 2 for vista and ubuntu (or what ever ratio you want depending on how much you're going to use it) during the vista install process. Then install win 7 on the other hdd and finally ubuntu on the remaining space of the other drive. This avoids all the fuss of re configuring bootloaders, which i prefer as i'm lazy and relatively inexperienced compared with the gurus here! This obviously works best with blank hdds

Grub, installed at the end of the ubuntu install will pick up the other OS's and let you boot your chosen OS.

I just found out yesterday how to update grub to let me add my xp install to the grup top menu at boot time 

```

sudo update-grub
```this reference was quite handy!

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Why not go try OSx86 (mac on a pc) while you're at it... ran one for a while, great until you have to update!

Sorry if you know all this already, hope it helps a bit.

---

### Post by d3mncln3r on 2010-08-19
Excellent advice, thank you both, I will probably work on the project tonight after work.


> **pharcycle said:**
> hi,
Do you really need vista? 


Haha... the only reason I'm doing this is to restore my factory settings mainly so I can use the webcam, which I've had a hell of a time trying to get working with W7 64-bit.

> Grub, installed at the end of the ubuntu install will pick up the other OS's and let you boot your chosen OS.

If this is true, I'll likely follow your methodology for triple booting the OS's, it seems rather simple. Thank you for the links oldfred, learning about bootloads and BIOS configs is something that I really need to get a handle on for the future anyway. 

I'll let you know how it goes!

Oh and as for running OS X, I already have a macbook pro running snow leopard (and XP in boot camp), I love it but I don't really see the need to put it on my PC...


EDIT:

Pardon my ignorance but can you describe to me the process of "removing the boot flag?" Is it as easy as unchecking a "boot flag" tick mark?

---

### Post by pharcycle on 2010-08-19
The disadvantage with my method is that grub will load before the vista bootloader if they're on the same hdd so if you want to get rid of ubuntu you'll still need grub to load vista. Win 7 would always work without ubuntu however because its on separate physical disk (if you do what i suggested).

When you install ubuntu, there's an 'advanced' or equivalent button just before you finish the installer, if you hit that you can select where grub puts the bootloader. You should select the ubuntu drive here so that you can always boot your win 7 install without the other drive.

As both your drives are the same, make sure to note it when you choose the install drive just to be sure!

My way just avoids doing any manual editing of system files so its by no means optimal!

---

### Post by pharcycle on 2010-08-19
> **d3mncln3r said:**
> 
Oh and as for running OS X, I already have a macbook pro running snow leopard (and XP in boot camp), I love it but I don't really see the need to put it on my PC...

Yeah, that would probably be a better solution!

---

### Post by oldfred on 2010-08-19
You can edit boot flag with gparted, right click or with system, admistration, Disk Utility or with command line.

---

### Post by pharcycle on 2010-08-20
I recently found out about the Gparted LiveCD which I have to say is pretty useful. You can do the same and mroe with a ubuntu liveCD (as gparted is included) but the gparted liveCD boots faster as its much more lightweight. 

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

It doesn't mount any of your volumes so you can mess with the partitions a bit safer if you need to. I imagine it would be an easy way of changing the boot flags as old fred suggested although i haven't done that myself so can't confirm.

I've added it to my collection of emergency cd's.
David

---

### Post by d3mncln3r on 2010-08-20
> **oldfred said:**
> To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it.

Oldfred-- that information kind of contradicts the info I gleaned from the thread you posted about the user who successfully got 2 versions of Windows and Ubuntu all to appear in the GRUB bootloader.

The advice given in that post recommends to install the older version of windows in a primary partition, then, using GParted, **set boot flag to off**. Then, install the new version of Windows in a seperate partition. And finally, install Ubuntu on a third partition. Ideally, GRUB will be the bootloader and give you three options to choose from.

In your above advice, you suggest to set each boot flag **on**.

Perhaps I am misunderstanding one of the two of you. Would you care to elaborate? Thanks

---

### Post by oldfred on 2010-08-20
Sorry if I confused you. The set boot flag on is for the new empty partition that you are installing the second windows into. Or turn it off on the initial install.

You can (or should) only have one boot flag per drive. The boot flag can only be on primary partitions. Ubuntu/grub do not use boot flag. Windows, Lilo and maybe a few others do use the boot flag but then have to have additional boot code in the partition boot sector or PBR.

---

### Post by d3mncln3r on 2010-08-20
> **oldfred said:**
> Sorry if I confused you. The set boot flag on is for the new empty partition that you are installing the second windows into. Or turn it off on the initial install.

You can (or should) only have one boot flag per drive. The boot flag can only be on primary partitions. Ubuntu/grub do not use boot flag. Windows, Lilo and maybe a few others do use the boot flag but then have to have additional boot code in the partition boot sector or PBR.


Ok, so would you recommend that I put Vista and 7 each in their own partition, and each on a **separate** drive? Then using the remaining space on one drive install Ubuntu (last)?

This is as opposed to installing all three OS's on one drive, and using the second drive as storage.

---

### Post by oldfred on 2010-08-20
Total space is the same however you  want to do it. But I like to have an operating system on every drive and that operating system's boot loader in the MBR of that drive. Since grub2 lets me also boot other systems I use it as my default boot loader.

---

