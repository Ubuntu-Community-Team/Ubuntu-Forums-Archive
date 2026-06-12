---
title: "Guide how to install dual boot Windows 7 and Ubuntu 10.04 on Raid0 (FakeRaid)."
date: 2010-09-03
forum: Installation &amp; Upgrades
---

### Post by Mr0wyx on 2010-09-03
**Hello!**

I am writting this guide hopping that for someone it would be useful and that I wont forget these steps after my partitions go down after some time.:D

It took long time for me searching for solution, how to install dual boot Windows 7 and Ubuntu 10.04 (Lucid Lynx) on my Raid 0 (stripe set) FakeRaid (Intel bios raid) partition. I wanted to install it without touching Windows installation, which I had installed earlier. Ubuntu installation process was fine until it reaches Grub installation and showed fatal error. It was unable to install it on my Raid partition. I tryed different guides how to fix that. CD/USB boot loaders, installing MBR from live CD, etc and all of them failed. I finally found EasyBCD as a solution.

**1.** First of all you need to install Windows 7 on your raid. Partitioning is as follows. It takes 100MB for system reserve, **x** MB for your windows installation and leave some **x** MB for your ubuntu installation (swap and /). (Or you can partition from working windows with Acronis Disc Director Suit for example. And resize partition.)

**2.** When you have working windows prepair [Ubuntu Alternate]("http://www.ubuntu.com/getubuntu/downloadmirrors") or [Ubuntu Desktop]("http://www.ubuntu.com/desktop/get-ubuntu/download") CD, USB or whatever you prefer better. Steps to do after to solve problem with grub are almost the same for both.

**3.** Boot Ubuntu CD/USB. Accept to install RAID/SATA drivers during setup. At hard drive partitioning step in installation process be cearfull, **don't touch your windows partiton**. Use Guided partitioning, using free space. At grub installation it mostly will give error at grub install. Choose not to install it.

**4.** Restart and boot to Ubuntu Desktop live CD. Mount your boot partition *ls /boot* and write down full names of initrd.img and vmlinuz. (eg vmlinuz-2.6.32-24-generic, initrd.img-2.6.32-24-generic) Run *blkid* and write down your UUID. 

**5.** Boot to Windows 7. Download [EasyBCD]("http://neosmart.net/dl.php?id=1") and install NeoGrub. Lounch EasyBCD ->  Add new entry -> NeoGrub -> Install -> Configure. It will open menu.lst. Add there entry for your Ubuntu. 

In my case:
```

# NeoSmart NeoGrub Bootloader Configuration File
#
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst
# Please see the EasyBCD Documentation for information on how to create/modify entries:
# http://neosmart.net/wiki/display/EBCD/

title		Ubuntu 10.04, kernel 2.6.32-24-generic
uuid		196d48a9-5402-42a4-979a-199ff277cc0b
kernel		/boot/vmlinuz-2.6.32-24-generic root=UUID=196d48a9-5402-42a4-979a-199ff277cc0b ro 
initrd		/boot/initrd.img-2.6.32-24-generic
quiet

```

Replace kernel, initrd and uuid with yours from step 4 and save.

Reboot and you are ready to boot your ubuntu.

Good luck, hope it will be usefull. ):P

---

