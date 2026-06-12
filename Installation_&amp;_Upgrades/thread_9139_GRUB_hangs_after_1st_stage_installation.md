---
title: "GRUB hangs after 1st stage installation"
date: 2004-12-24
forum: Installation &amp; Upgrades
---

### Post by western on 2004-12-24
During installation everything works fine.
but after first reboot - grub fails to load.
it just keeps looping the word GRUB on the screen.
what do i do to set up the bootloader properly? please help.
maybe i set up my pertitions wrong;

first pertition is swap - 512M- set format on.
second pertion is root (/) - 19.9Gb (rest of hd)- format on, and boot flag on. (reiserfs)

as far as i understand grub installs itself on hda0.

thanks in advance. :)

---

### Post by aToaster on 2004-12-24
There are a couple of other threads with this issue.  You aren't the only one having the problem, but it seems like no one can figure out why this is so.  Can you post more details on your computer?  Do you have another hard drive?  Is linux the only OS on your computer?  Is the hard drive an SATA drive?  Thanks,

,aToaster

---

### Post by ebonflame on 2005-01-23
I too am having this problem, but with the latest Hoary DVD from the internet.  I've installed Warty in both the AMD-64 and i386 flavors and had no problems with GRUB, but with Hoary, it's not working.

---

### Post by GyroFry on 2005-01-23
I'm also having this problem (with Hoary installer 1/22/05 - warty works fine).

Grub is installed to MBR of ATA drive hda
hda1 = Windows
hda2 = ext3 /boot
hda5 = ext3 /

There's also an ATA hdb with a fat32 partition and 2 ATA CD-ROM drives.  I have no SATA drives.  Motherboard is an ASUS K8V SE Deluxe.  I started the installer with no special parameters except "expert"

First stage installation goes fine, and grub seems to install with no errors (in fact, I executed a shell during 1st stage and examined /target/boot/grub/menu.lst and it appeared to be configured normally - 4 ubuntu stanzas with (roughly from memory):

> title           Ubuntu, whatever
> root            (hd0,1)
> kernel          /vmlinuz-whatever root=/dev/hda5
> initrd          /initrd.img-whatever
> savedefault
> boot

and 1 windows xp stanza with:

> title           Windows XP
> root            (hd0,0)
> savedefault
> makeactive
> chainloader     +1

When I select reboot from the installer, GRUB hangs at "Loading Stage 1.5"

---

### Post by ebonflame on 2005-01-23
[QUOTE=ebonflame]I too am having this problem, but with the latest Hoary DVD from the internet.  I've installed Warty in both the AMD-64 and i386 flavors and had no problems with GRUB, but with Hoary, it's not working.[/QUOTE]

A little more detailed information:

Version of Ubuntu: Hoary DVD iso 1/15/05
Motherboard/CPU/Memory:  Asus K8V SE Deluxe, AMD64 3200+, 256 MB
Hard drives:
HDA: HDA1: Windows XP
HDB: HDB1: NTFS
	HDB2: 10.5 GB Ext3 /
	HDB5: 498 MB Swap

Originally I had the i386 Ubuntu installed.  I booted with the DVD, formatted the old Ubuntu partition and installed Ubuntu.  It went through the motions, but when I rebooted, GRUB just gave me the message:  GRUB Loading Stage 1.5 and it hung.

I then booted with my XP cd and used the fixmbr so I could wipe grub and get back into windows.  I then tried to reinstall the Hoard DVD.  At the end when it "said" that GRUB was installed, the system simply booted back into windows.  GRUB was not loaded at all.

Not giving up so easily, I decided to use Warty AMD64 and just apt-get distro-upgrade from the DVD to get Hoary running.  Warty installed Grub, but upon reboot, I get the usual Loading Stage 1.5 and one more line "Loading, please wait" and then nothing again.

An interesting aside:  the AMD-64 Warty release does NOT detect my XP system when it installs.  Hoary does.

---

### Post by GyroFry on 2005-01-23
[QUOTE=ebonflame]An interesting aside:  the AMD-64 Warty release does NOT detect my XP system when it installs.  Hoary does.[/QUOTE]
I experienced the same thing on my system.

---

### Post by ebonflame on 2005-01-25
After more experementing, I think I may have stumbled upon something, but the developers will probably need to look further into it.

In the course of my many attempts to get Ubuntu 64 working, I've done various partition configurations (boot as a seaparate partition near the beginning of the HD is the main thing that I've tried).  On both the pressed Warty that I got through the Ubuntu free CD offer and the Hoary DVD, GRUB refuses to load.  I happen to have a copy of pre-release Warty that I decided to try as a last resort, and lo and behold, not only did it install, but GRUB works without a hitch!  The rest of the install goes fine and I'm left with a functional Ubuntu. 

Now my question is this:  Is the version of GRUB on the pre-release Warty different from the ones on the official Warty and the Hoary disks?

---

### Post by xkfu on 2005-01-25
I am having grub problem too.

I have AMD 64bit machine with 40G HD. Already have Windows XP installed on partiotion 1.

Partition 1: Windows XP 20G
Partition 2: Data 10G

Installed ubuntu 64bit version. During the installation, it asked where I want ubuntu be installed and I specified the last 7.2G of the hard disk. It performs partition for ubuntu automatically. ubunu installed fine as well as grub from the CD. When the machine reboots, I had the following error:
Grub stage 1.5

Error 17

and hangs there.

Used a grub boot floppy. Grub boots fine from the floppy. Used "find" command under grub prompt and entered "root (hd0,2)", then "cat /boot/grub/menu.lst". The default entry in the menu.lst has:
root (hd0,2)
kernel /boot/vmlinuz root=/dev/hda3 ro console= tty0 quiet splash
initrd /boot/initrd.img
boot

I entered the same lines and it boots! I can get to ubuntu login screen.

So, the problem here is grub cannot boot from hard disk, but boots from floppy fine. I have tried using grub commands "setup (hd0)", "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,2)/boot/grub/stage2 /boot/grub/menu.lst", and in linux, "/sbin/grub-install", all told me installed OK, but I still have the same grub error when reboots.

Although I can get to ubuntu using the grub floppy, but cannot use Windows XP, and every time to boot ubuntu, I have to type several commands.

While someone suggested the boot loader should always been in the first partition but I have seen people install Windows XP in the first partition. Plus, if there is such a restriction, the installation should fail rather than proceed since it detects I am installing ubuntu in the third partition.

I believe there is something wrong with my grub setting. I have spent quite sometime and no luck. Please help!

---

### Post by xkfu on 2005-01-25
OK, the problem is resolved by changing BIOS HD setting to LBA from auto. Everything works fine now. Though I still don't understand the relationship between LBA and Grub stage 1.5 Error 17. According to the menual, error 17 is unrecognized file system.

xkfu

[QUOTE=xkfu]I am having grub problem too.

I have AMD 64bit machine with 40G HD. Already have Windows XP installed on partiotion 1.

Partition 1: Windows XP 20G
Partition 2: Data 10G

Installed ubuntu 64bit version. During the installation, it asked where I want ubuntu be installed and I specified the last 7.2G of the hard disk. It performs partition for ubuntu automatically. ubunu installed fine as well as grub from the CD. When the machine reboots, I had the following error:
Grub stage 1.5

Error 17

and hangs there.

Used a grub boot floppy. Grub boots fine from the floppy. Used "find" command under grub prompt and entered "root (hd0,2)", then "cat /boot/grub/menu.lst". The default entry in the menu.lst has:
root (hd0,2)
kernel /boot/vmlinuz root=/dev/hda3 ro console= tty0 quiet splash
initrd /boot/initrd.img
boot

I entered the same lines and it boots! I can get to ubuntu login screen.

So, the problem here is grub cannot boot from hard disk, but boots from floppy fine. I have tried using grub commands "setup (hd0)", "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,2)/boot/grub/stage2 /boot/grub/menu.lst", and in linux, "/sbin/grub-install", all told me installed OK, but I still have the same grub error when reboots.

Although I can get to ubuntu using the grub floppy, but cannot use Windows XP, and every time to boot ubuntu, I have to type several commands.

While someone suggested the boot loader should always been in the first partition but I have seen people install Windows XP in the first partition. Plus, if there is such a restriction, the installation should fail rather than proceed since it detects I am installing ubuntu in the third partition.

I believe there is something wrong with my grub setting. I have spent quite sometime and no luck. Please help![/QUOTE]

---

