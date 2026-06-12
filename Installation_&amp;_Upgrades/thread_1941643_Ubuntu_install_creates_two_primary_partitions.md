---
title: "Ubuntu install creates two primary partitions"
date: 2012-03-16
forum: Installation &amp; Upgrades
---

### Post by Mezentine on 2012-03-16
This is a truncated version of a question I asked elsewhere on this forum: I'm hoping that now that I've narrowed down the problem I can rephrase it in a way that may make more sense and be something more standardized. It appears that when I install Ubuntu it creates two primary partitions: one for Ubuntu proper and one extremely small one that gets inserted at the top of my partition table.

Question 1: is this normal? Does this sound like something that's supposed to happen?

The problem comes from the fact that since I'm running both Mac and Windows as well the creation of this small partition puts me over the 4 Primary partition limit (Small partition, EFI, Mac, Windows, Ubuntu), and so whatever Primary partition is on the bottom of my list gets kicked into being free space, making it impossible to boot to all three operating systems. I've tried it with both Windows installed in the bottom partition and with Ubuntu installing in the bottom partition: whichever one is there ends up being converted into free space.

Question 2: does anyone know how to stop this from happening?

---

### Post by darkod on 2012-03-16
Since you are using efi mac and windows, I assume the disk is gpt. Why would the primary limit matter, it doesn't exist on gpt?
On the other hand, windows can't boot with efi unless on gpt.

That small partition is probably the bios_grub partition. With gpt table, the disk layout is not the same as with msdos and grub2 doesn't have space to install on MBR fully. That's why it needs a small 1MB partition WITHOUT any filesystem, with a flag called bios_grub set on it. Then it knows where to put grub.

To have more control, you can create this partition yourself, and also during the ubuntu install use the manual method and create the ubuntu partition(s) as logical. Provided we are not talking about gpt since there is no logical in gpt.

There is a lot of conflict in your question, I think your problem is something else, not the 4 primary limit.

First confirm if you are using gpt partition table in which case forget about any primary limit. All partitions are primary and you can have 128 maybe even more.

---

### Post by Mezentine on 2012-03-16
Alright, thanks for the start. Where should I check to see the current scheme? (I can still boot to Ubuntu from a CD)

---

### Post by darkod on 2012-03-16
If you prefer a GUI, you can open Gparted in live mode.

But in this situation the command line might give you more info. You can print all partitions in terminal with:
sudo parted /dev/sda print

That will also have info if the table is msdos or gpt. And it will print all the flags too, partition types, etc. Post the output if you want some advice on it.

---

### Post by Mezentine on 2012-03-16
Okay, so I am in the GPT style. Which makes my problem make even less since to me, since I have *repeatedly* seen that installing Ubuntu converts whatever partition is currently designated as the fourth Primary into free space.

EDIT: Although not in this Partition table. This partition table seems to show the four correct ones:
```

ubuntu@ubuntu:~$ sudo parted /dev/sda print
Model: ATA TOSHIBA MK2555GS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 1      20.5kB  210MB   210MB   fat32        EFI System Partition  boot
 2      210MB   85.3GB  85.1GB  hfs+         Foundation
 3      85.4GB  235GB   150GB   ntfs         EMPIRE
 4      235GB   249GB   14.0GB  ext4

```

I'm going to go grab the info from the other two operating systems...

---

### Post by darkod on 2012-03-16
Post the output of parted if you don't mind, lets see it.

What might be hapenning is that it doesn't create the new partitions correctly, hence the issue you are seeing. Lets see what you have right now, and how to go forward.

---

### Post by Mezentine on 2012-03-16
Yup, Parted output is above. I also inserted my windows installation CD and checked out the Partition Table they have there for manual installation and that one distinctly lists the 14G partition for Ubuntu as being free space (and the four primary partitions as being the initial small partition, EFI, Mac and Windows) (I'm beginning to suspect that the Windows disc doesn't know how to analyze GPT?)

The current functional problem is now that selecting Linux from my bootloader (I'm using rEFit) boots into the Windows installation instead.

(Possibly useful tangent: I had a similar issue when I had all three systems working in the past where selecting either Windows or Linux would launch GRUB, but it wasn't an issue since I could successfully select Windows from GRUB. That no longer works: over the course of several installations trying to boot Windows from GRUB has produces everything from "Windows failed to load" to "operating system missing")

---

### Post by darkod on 2012-03-16
If you are using windows disc to compare, remember it doesn't understand linux partitions. So, for the 14GB ext4 partition it can make up so many different (all of them wrong) info... :)

However, you have another issue: EFI. Using gpt alone is not an issue, but EFI dual boot with windows is. In your case it's triple boot, so you need to investigate even more.

From what I have heard here, there is (was) a bug in grub and during EFI dual boot install it was deleting the windows boot files from the EFI system partition and leaving only grub files. So you had to be prepared and copy them first, then put them back. I think that was enough to work, but I have no experience with gpt + efi myself.

Focus your investigation on this topic, efi dual or triple boot. And how to do it properly. That's the key.

---

### Post by Mezentine on 2012-03-16
Thanks for the help. My boot loader rEFit is already supposed to be designed for EFI triple booting but I'll investigate further. The most infuriating part of this whole thing is that six months ago I installed all three of these just fine in less then two hours and now when I try to do it again some mysterious arbitrary thing has changed making it difficult.

---

### Post by darkod on 2012-03-16
No one is saying rEFIt is not working. It seems there is a grub bug with EFI installs.

That might be a reason why you installed 6 months ago, it was different version. As far as I know, you still need to install grub2 somewhere so that rEFIt can use it. And if the bug in grub2 deletes your other EFI files for the other OSs, the install will probably not work.

---

### Post by akhilblue on 2012-03-17
Hey. i wanted to try out ubuntu so i downloaded 11.10 disk image. then i made a live usb and installed from that. the installation did not show any error. but however it does not boot. the first time i tried installing i only got windows to boot. upon reinstalling grub all i got was a blinking cursor. then the same thing happens everytime. i had to use boot repair to reinstall MBR( recommended repair also did not work) to get windows to boot again. i used easy bcd to add a grub boot, but that did not work. Wubi also does not work. on the first reboot i get a black screen. i would like to successfully dual boot ubuntu, but i dont seem to be able to get it to install. Help would be appreciated.

---

### Post by darkod on 2012-03-17
> **akhilblue said:**
> Hey. i wanted to try out ubuntu so i downloaded 11.10 disk image. then i made a live usb and installed from that. the installation did not show any error. but however it does not boot. the first time i tried installing i only got windows to boot. upon reinstalling grub all i got was a blinking cursor. then the same thing happens everytime. i had to use boot repair to reinstall MBR( recommended repair also did not work) to get windows to boot again. i used easy bcd to add a grub boot, but that did not work. Wubi also does not work. on the first reboot i get a black screen. i would like to successfully dual boot ubuntu, but i dont seem to be able to get it to install. Help would be appreciated.

The blank screen is usually related to video problems. There is a sticky about it on top of the threads list. Don't keep reinstalling things because you might have complicated it further.
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

