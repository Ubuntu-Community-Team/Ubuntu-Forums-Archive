---
title: "Installing Gutsy without GRUB (similar to Wubi)?"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by dracura on 2007-10-18
I've been very happy with my Wubi install of 7.04 because it wouldn't destroy my MBR. The first time I dual booted, it killed my MBR and I had to end up reinstalling Windows.

My question is, can I somehow install 7.10 and add it to the NT loader the way Wubi does, or do I have to use GRUB?

---

### Post by logos34 on 2007-10-18
Try this howto (annotated with links):

[http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why](http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why)

> "GRLDR - A Simpler Approach

grldr is found in the [grub4dos distribution]("http://sarovar.org/projects/grub4dos/"), and is a patched version of regular grub. grldr can be pointed to by ntldr, thus removing the need for fiddling with dd, bootsectors and whatnot. grldr supports fat and ntfs, and employs a regular grub-style 'menu.lst'. It is particularly useful if you want to boot a linux kernel and ramdisk from your Windows partition, but may also be useful in other scenarios. Like if you want to install Linux on a machine with Windows, but no usb/floppy/cdrom. To use grldr, put grldr and menu.lst in the root of your windows partition.**[COLOR="Red"]*[/COLOR]** Then add: C:\grldr="Start Linux Loader (GRUB)" to boot.ini. That's it. Apart from editing menu.lst, that is. See the grub documentation for menu.lst syntax. (menu.lst is the same as grub.conf, but grldr looks for menu.lst.)

It is also worth mentioning that you still have to install grub during your gentoo install (and then select the -do not install to MBR- option). This will put your grub install into /boot/grub/, and from there you can use the grub.conf to add a proper entry into your C:\menu.lst."

**[COLOR="Red"]*[/COLOR]**i.e. extract **grldr** from grub4dos archive to windows C: directory.  Copy ubuntu **/boot/grub/menu.lst** after install. Replace the ubuntu kernel entry with [configfile format]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile"). 

Be sure to install Grub to the ubuntu root partition, NOT the mbr (where it goes by default).  When you come to the "[Ready to install]("http://img519.imageshack.us/my.php?image=feistydual18cv5.png")' screen, click "Advanced' button lower right and replace '(hd0)' with the ubuntu root partition '**(hd0,x)'**.

---

