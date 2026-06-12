---
title: "Moving a wubi partition to its own"
date: 2012-02-09
forum: Installation &amp; Upgrades
---

### Post by jimbabka on 2012-02-09
On the basis of this quote from the Wikipedia article on WUBI, I decided that it was the way to go:

"While Wubi does not install Ubuntu directly to its own partition this can also be accomplished by using LVPM, the Loopmounted Virtual Partition Manager, to transfer the Wubi-generated Ubuntu installation to a dedicated real partition, including a bootable USB keydrive."

I had a really bad experience trying to install RHEL 6.2 to this separate partition - grub could boot Linux, but when I tried to boot the partition labeled "Other", it gave me an immediate error saying that it could not find a system to boot. I tried manually reinstalling grub, and that rendered my system totally unbootable.

So I wanted something that preserved the Windows bootloader and thus preserved my ability to boot either Linux of Windows. Thus, WUBI seemed perfect.

So I installed WUBI and like it. I am now ready to take the leap described in the article and create a separate partition for it on my hard drive. I have shrunk my Windows 7 (64-bit) partition in preparation, but now I'm trying to find instructions that will leave me in the same state I am now - the only difference being that Ubuntu is running from its own partition instead of the Windows disk image file. I still want to be able to boot to Windows (I'm not ready to cut the cord yet).

Anyway, I can find instructions for copying the WUBI file out to a new partition, but they all seem to assume that when you make this move, you never need Windows again. They all say to install grub, but I know that grub can't boot Windows on my system. I want to still use the Windows bootloader, because I know **that** works with Windows on my system.

By the way, I'm guessing that one of these issues is part of my problem with grub:

1. When I did boot RHEL from a DVD, it decided that /dev/sda was my external (USB) hard drive. My primary internal hard drive was /dev/sdb, and my secondary internal drive was /dev/sdc. When RHEL booted from the hard drive, the primary was /dev/sda and the USB drive was /dev/sdc.

2. My system is new enough that it doesn't have BIOS - it has UEFI. I know that this causes havoc for many of my older programs that get involved in booting (e.g. Acronis 10).

So, can anyone point me to instructions that will allow me to move WUBI to a separate partition and yet still boot Win7?

---

### Post by Frogs Hair on 2012-02-09
See the link . [http://ubuntuforums.org/showthread.php?t=1519354&highlight=wubi+partition](http://ubuntuforums.org/showthread.php?t=1519354&highlight=wubi+partition)

---

### Post by jimbabka on 2012-02-09
> **Frogs Hair said:**
> See the link . [http://ubuntuforums.org/showthread.php?t=1519354&highlight=wubi+partition](http://ubuntuforums.org/showthread.php?t=1519354&highlight=wubi+partition)
This is one of the posts I saw before. Notice that there is no mention of being able to boot Windows afterwards, and it talks about using grub. My concern is that, the last time I tried to fix grub after it would not boot Windows, it destroyed my Windows partition and I had to reinstall from a backup (which took 2 hours). So I'm really gun shy about using grub again. If it's the only way to do this, then fine, but I would greatly prefer that someone can tell me that they have a similar setup (two internal and one external drives) and grub does work for them.

---

### Post by oldfred on 2012-02-09
If you have multiple drives, then I suggest you keep each operating system on a separate drive and keep its boot loader on the same drive. Then either drive is independently bootable in case the other does not work. You do have to use manual install (Something Else) to get a choice on where to install the bootloader.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

Herman also has lots of info on dual booting on one drive.
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

Install 11.10 with screenshots of Unity, gnome3, & gnome fallback - Not everything is necessary, but shows how to do many things
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Frogs Hair on 2012-02-09
I started with Wubi and went a dual boot with Win 7 shortly after . I think backing up the ubuntu data to a removable device and dual booting is a much better Idea  . I post the link when people ask for instructions to migrate Wubi installations .

I realize that some people don't have a dvd or usb  drive available and IMHO that is the only circumstance that warrants  the use of the migration instructions .

---

