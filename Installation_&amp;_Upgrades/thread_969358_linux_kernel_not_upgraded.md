---
title: "linux kernel not upgraded"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by Ewan the moomintroll on 2008-11-03
Hi there,
I started a topic on a problem I have:
[http://ubuntuforums.org/showthread.php?p=6071414#post6071414](http://ubuntuforums.org/showthread.php?p=6071414#post6071414)

and decided that it was worth starting a new thread because the problem now seems to be that ubuntu did not upgrade to 8.10 properly (probably my fault).

In system monitor it says I still have linux kernel 2.6.24-21-generic, even though in the release notes it says 8.10 should have 2.6.27.
when the upgrading it asked me whether I wanted to replace menu.lst among others and I said no because I didn't know what it meant.

Any help on upgrading the kernel would be greatly appreciated,

Ewan
):P

---

### Post by CrazyMonkey77 on 2008-11-04
I would probably check the /boot/ folder to see if you've got a initrd-2.6.24-21-generic.img file first.  If you have then I would make a backup of my /boot/grub/menu.lst by using the command

sudo cp /boot/grub/menu.lst /home/bob (or whatever your username is)

then create a new menu.lst using the command

sudo update-grub

You should get prompted to overwrite your menu.lst.  say "Y" to this. Then open the newly created menu.lst and check you've got some 2.6.24-21 entries in there.  if you have, reboot.  If you haven't copy back your original menu.lst

---

### Post by Ewan the moomintroll on 2008-11-04
Thanks for replying,
in the /boot/ menu i see:
[IMG]http://img124.imageshack.us/img124/8402/97199567no1.jpg[/IMG]

and when i type "sudo update-grub" i get:

[COLOR="black"][I]Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

[/I][/COLOR]

---

### Post by roger_1960 on 2008-11-04
Hi

That looks like it will work on reboot with the new kernel.

---

### Post by CrazyMonkey77 on 2008-11-04
Ah yes, it looks like you have the necessary image files.  apologies for confusing you, they're named slightly differently in Ubuntu (I use RedHat Linux a lot as well).

As Roger says, it looks ok to go, but I'd just check my menu.lst file to check that it has bootable entries by opening a terminal and using the command

sudo gedit /boot/grub/menu.lst

each bootable entry should look (something) like:

title Ubuntu 8.10, kernel 2.6.27-7-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.27-7-generic root=/dev/hda3 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic
savedefault
boot

if you've got those - you're good to go.. :)

---

### Post by Ewan the moomintroll on 2008-11-04
wow, thanks for all the help,
but no i don't have that. worryingly it says:
title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=be8deb13-2d60-4498-9b41-90d6767fd9be ro quiet splash acpi=off apm=power_off
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

something went very wrong when i installed 8.10.

---

### Post by CrazyMonkey77 on 2008-11-04
you could try deleting your menu.lst file (if you made a copy of it).  Using the command

sudo rm /boot/grub/menu.lst

then re-run 

sudo update-grub

and see if it recreates a new menu.lst - if it fails, you can at least copy the old one back.

---

### Post by Ewan the moomintroll on 2008-11-04
That worked very well. Thankyou!

It still hangs on shutdown though. :(

---

