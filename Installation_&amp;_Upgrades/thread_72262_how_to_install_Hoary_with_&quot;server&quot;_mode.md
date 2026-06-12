---
title: "how to install Hoary with &quot;server&quot; mode?"
date: 2005-10-05
forum: Installation &amp; Upgrades
---

### Post by cristianommxp on 2005-10-05
Hi,

I have a historical Pentium 100 with 64MB RAM and 4GB HD.

I'm trying to install Ubuntu by Network using "grub.exe" to start the install process by network.

I'm installing Ubuntu for this way:

1) I create a 200MB DOS free space formated in my 4GB HD and I call it "C:".

2) To "C:\" I copy 2 files from "/install/netboot/ubuntu-installer/i386" folder in UBUNTU HOARY INSTALL CDROM:

	linux
	initrd.gz

3) To "C:\" I too copy more 2 files:

	grub.exe (a DOS version of GRUB software)
	menu.lst (the GRUB configuration file)

Inside "menu.lst" I have this:

# -----------------------------------
# File: menu.lst
# -----------------------------------
color black/cyan yellow/cyan

timeout 60

default 0



title DOS/Win9x/Me/NT/2K/XP on (hd0,0)

root (hd0,0)

chainloader +1



title Ubuntu Internet Installer on (hd0,0)

kernel   (hd0,0)/linux vga=normal ramdisk_size=149720 root=/dev/rd/0 rw --

initrd   (hd0,0)/initrd.gz
# -----------------------------------

4) I started "grub.exe":

	C:\>grub.exe

5) The install process start in the "desktop" mode


Ok, the install process works fine and at about 4 ou 5 hours I have a Ubuntu instance running in this machine.

But this method to install Ubuntu I don't think so is the best solution to me.

The operational system when installed is "too heavy" and "too slow". 

And I don't need for this computer softwares like Gnome, Nautilus, Firefox, Games, OpenOffice and others...

I think if I install Ubuntu using the "server" install mode maybe it can be better, doesn't it?

But, now I have a question: How to start the install software using "server" mode and using "grub.exe"?

When the install program started, it doesn't give any choice.

I don't know, I'm not any "expert" user, but I think to start the install process in "server" mode I should need write some option in "kernel" command line in "menu.lst" file: 

	kernel   (hd0,0)/linux <SOME_OPTION=SOME_VALUE?> vga=normal ramdisk_size=149720 root=/dev/rd/0 rw --       

Well, if I am right, what option do I need write to start the install process in "server" mode?

If I am wrong, what can I do to start the install process in "server" mode using network install with "grub.exe"?


10ks

Cristiano


p.s.: I can't use CDROM in this machine. It's impossible. I just have the option to install by network.

---

