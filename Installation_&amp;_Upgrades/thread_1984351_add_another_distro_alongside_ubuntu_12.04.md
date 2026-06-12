---
title: "add another distro alongside ubuntu 12.04"
date: 2012-05-21
forum: Installation &amp; Upgrades
---

### Post by johnnybevo on 2012-05-21
Mageia 2 will be released in a few days and I would like to setup a dual boot. I am using ubuntu 12.04 right now. I would like to add Mageia.
Any help would be great.
here is my current setup.

And I am a complete linux newbie,

[IMG][[IMG]http://img819.imageshack.us/img819/2163/screenshotfrom201205211.png[/IMG]](http://imageshack.us/photo/my-images/819/screenshotfrom201205211.png/)

Uploaded with [ImageShack.us](http://imageshack.us)[/IMG]

---

### Post by VMC on 2012-05-21
Very simple to use gparted and click on sda1 and re-size it to allow for another partition to be added. Don't worry you can play around with gparted. nothing will be added until you apply. Create a new partition for Mageia.

Then when Mageia is available add it to the new created partition.

I'm unsure of Mageia's partition manager, but make sure it's manual  OS.

Here's a great [reference]("https://help.ubuntu.com/community/HowtoPartition") on adding partitions and for you to study before hand.

---

### Post by johnnybevo on 2012-05-21
> **VMC said:**
> Very simple to use gparted and click on sda1 and re-size it to allow for another partition to be added. Don't worry you can play around with gparted. nothing will be added until you apply. Create a new partition for Mageia.

Then when Mageia is available add it to the new created partition.

I'm unsure of Mageia's partition manager, but make sure it's manual  OS.

Here's a great [reference]("https://help.ubuntu.com/community/HowtoPartition") on adding partitions and for you to study before hand.

Hey thanks for the link I will read through it.
I guess I have to run gparted from the live cd to work, correct?
Also what about setting up the boot menu?

---

### Post by 1clue on 2012-05-21
Why dual boot?

Why not set up a virtual system and then you can run both at once?

If you're just trying out an OS and don't want to boot off a live CD then you'll only run it a few times anyway, just install onto a VM and then when you get tired of it you can just delete the VM and you're clean.  

If you're installing something just to run a specific tool, (Windows for a game) then you will start up like an app, run your tool and then quit.

If you're planning to re-install with some other OS, you'll want to play with it in 'test drive mode' to see how big to make partitions, what components to install, etc.

---

### Post by johnnybevo on 2012-05-21
> **1clue said:**
> Why dual boot?

Why not set up a virtual system and then you can run both at once?

If you're just trying out an OS and don't want to boot off a live CD then you'll only run it a few times anyway, just install onto a VM and then when you get tired of it you can just delete the VM and you're clean.  

If you're installing something just to run a specific tool, (Windows for a game) then you will start up like an app, run your tool and then quit.

If you're planning to re-install with some other OS, you'll want to play with it in 'test drive mode' to see how big to make partitions, what components to install, etc.

I had it installed a few weeks ago, but my wife insisted that ubuntu is the only os besides windows that she can use so i am setting up a dual boot so she will be happy and i can dable with something new. yes i could do the vm but this also is a learning experience for me. so the next time I want to try out a distro and maybe keep it, i will know what to do.
I like being windows free.
Wish I would have been brave enough to ditch windows a while back.

---

### Post by VMC on 2012-05-21
> **johnnybevo said:**
> Hey thanks for the link I will read through it.
I guess I have to run gparted from the live cd to work, correct?
Also what about setting up the boot menu?

After your satisfied with Mageia, you can then either use Mageia's boot menu or do a grub install from Ubuntu.

I run my own boot menu, but for you I would advise to use grub2's options.

---

### Post by johnnybevo on 2012-05-21
> **VMC said:**
> After your satisfied with Mageia, you can then either use Mageia's boot menu or do a grub install from Ubuntu.

I run my own boot menu, but for you I would advise to use grub2's options.

 how do i do a grub install from Ubuntu?
I will check back tomorrow
Thanks for the help

---

### Post by VMC on 2012-05-21
> **johnnybevo said:**
> how do i do a grub install from Ubuntu?
I will check back tomorrow
Thanks for the help

If Mageia adds Ubuntu to the menu (and it should), then boot up Ubuntu from the menu, then do the following from a Terminal:

```
sudo grub-install --recheck --root-directory=/ /dev/sda

```
then update Ubuntu's grub menu:

```
sudo update-grub 
```

---

### Post by johnnybevo on 2012-05-23
@VMV I just noticed you have the same setup as I do.
( AMD64 Athlon X2 Dual-Core - nVidia Geforce 6150 SE - 4GB DDR3 )
Have you got the additional drivers to work? 
I am still using the default.

---

### Post by OldSmoky2 on 2012-05-24
I have a similar question so I'm trying to follow this. I have two 500gb hard drives (no RAID). On one I have two partitions, with Ubuntu 12.04 on one and Kubuntu 12.04 on the other. On the other drive I have an old OpenSuse install that broke after a kernel and Nvidia update. I couldn't get it working again and lost interest in it, to be honest. I used Mandrake on an old computer a decade or more ago, liked it and would like to install Mageia. I was thinking I could just install it on the unused hard drive - it's dev/sda on my computer - the drive with Ubuntu and Kubuntu is dev/sdb. I downloaded the DVD version of Mageia 2. So can I just start the Mageia install from the DVD and specify dev/sda, the whole drive? Am I likely to encounter any boot problems with Ubuntu/Kubuntu that way?

---

### Post by johnnybevo on 2012-05-25
> **VMC said:**
> If Mageia adds Ubuntu to the menu (and it should), then boot up Ubuntu from the menu, then do the following from a Terminal:

```
sudo grub-install --recheck --root-directory=/ /dev/sda

```then update Ubuntu's grub menu:

```
sudo update-grub 
```


I have no boot menu and have no idea what to do. here is what i get after i 
sudo update-grub


Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Mageia 2 (2) on /dev/sda1
done

---

