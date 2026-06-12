---
title: "Feisty 7.04 : Kernel 2.6.20 don't allow me install"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by adam0509 on 2007-04-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/107417](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/107417) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi,


I got an annoying error with feisty

When I try install my Xubuntu 7.04 Feisty, Linux boot, and then I got something like :

```
ata2.00 : exception Emask 0x0
cmd
ata2: port failed to respond (30 secs, Status 0xd0)
ata2.00 revalidation failed
```

I try to install edgy (server option to gain time) then upgrade to Feisty, but it's the same, even the edgy kernel gets in trouble when the system is upgraded.


Seems that 2.6.20 kernel is a mess, I think i'll see another distro, like debian or something...

---

### Post by adam0509 on 2007-04-20
Ok, I just installed ubuntu (server) with another CD DRIVE, It didn't work perfectly thus, I got a big error when he tries to install the GENERIC kernel, so I have to install the LINUX IMAGE kernel... :/



I finish install, rebooted once, seems ok (I got strange message about PBLK but don't matter)

Then I halt to  plug again my CD-ROM (it's a MITSUMI CR-4801TE by the way), and then again I got the error... :/



Is there a way to set-up the kernel so that he don't take care of my ata2 (CD drive) ??

---

### Post by adam0509 on 2007-04-20
See something intersting in arch linux forums :


> in /etc/mkinitcpio.conf :

replace the module ligne by :
MODULES="ide_generic"

In "hooks", I delete "sata" and I replace "pata" by "ide".

then I get in fstab /etc/fstab and replaced sdaX by hdaX.

then redo a kernel :
mkinitcpio -g /boot/kernel26.img.

Seems good, by I don't have any "mkinitcpio.conf" !!!

---

### Post by adam0509 on 2007-04-21
My config :


PIII 533Mhz
192Mo RAM
Primary Master : FUJITSU (10Go)
Primary Slave : STC.... (4Go)
Secondary Master : MITSUMI CR4801-TE
Secondary Slave : none
Floppy drive

Geforce 256 DDR

---

### Post by adam0509 on 2007-04-23
Ok, I reflected a little about the trouble I got, so here is solutions that sould work :




1rst) Install the server installation (by alternate or somthing) from a different CD-Drive


2.1) Install a custom kernel :
=> check tutorials


2.2) Install a 2.4 kernel :
=> Sorry, but I absolutely don't know how to do it on feisty :D


Thus, installing nvidia/ati/propriotary drivers with a custom kernel is a complete mess. I tryed once, and it's very complicated




For the moment, I decided to test a little debian etch (2.6.18 kernel) on my machine to see if my PIII 533Mhz will be faster on it with debian and XFCE...

...but it's not :|


Ubuntu is a good distribution, installing ati/nvidia drivers and others things is very simple, but since the basic 2.6 linux kernel owns 30.000+ drivers by defaut (rofl), it will never works for 100% of the PC without compilating. The windows kernel is basic, but since it don't own any driver, it works for most PCs... (that's because constructor makes PC for Windows too...).

---

### Post by Arjan Kon on 2007-05-01
What i did: installed ubuntu 6.10

Installed a custum kernel. kernel 2.6.21 fixed the problem for me. One can try these:
stack.nl/~ak/ubuntu/linux-headers-2.6.21_386_i386.deb
stack.nl/~ak/ubuntu/linux-image-2.6.21_386_i386.deb
(Vanilla kernel compiled with the config file from ubuntu Feisty)

Upgrade to Feisty. And then it works. (with 2.6.21 kernel)

---

