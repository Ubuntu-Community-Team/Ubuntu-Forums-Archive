---
title: "Can grub boot to xp from a different HD?"
date: 2006-02-21
forum: Installation &amp; Upgrades
---

### Post by archis on 2006-02-21
I have set up a multi-boot system across two HDs - three operating systems controlled by two boot loaders; a Windows-Ubuntu dual-boot on the internal IDE drive and a second *nix OS on the external USB HD. One boot loader is on the internal drive's MBR and the other is on the USB HD. I can bring up each boot loader by booting into the respective HD. To illustrate:

[ATTACH]6317[/ATTACH]

I would like to have all 3 operating system choices on each of the two boot loaders. But I only have 5 at the moment - Windows won't boot from the USB boot loader. The menu.lst entries for Windows are 

MBR grub

[FONT=Lucida Console][COLOR=Olive]title              Microsoft Windows XP
root              (hd0,0)
savedefault
makeactive
chainloader     +1
[/COLOR][/FONT]
USB grub

[FONT=Lucida Console][COLOR=Olive]title              Microsoft Windows XP
root              (hd1,0)
savedefault
makeactive
chainloader     +1[/COLOR][/FONT]


The MBR boot loader boots into Windows but the boot loader located on the USB just hangs. I've tried changing the syntax on the USB grub to [FONT=Lucida Console][COLOR=Olive]chainloader (hd1,0)+1[/COLOR][/FONT] but no joy. I'm beginning to suspect that grub cannot boot into Windows if the boot loader is not located on the same volume as the Windows partition. Is this correct?

In other words, can I use a grub boot loader to boot into a windows partition located on a different volume?

---

### Post by lha on 2006-02-21
USB grub

title              Microsoft Windows XP
root              (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader     +1

---

### Post by archis on 2006-02-21
Thanks, works like a charm.

I noticed there is a file called device.map in the grub folder as well. On both drives, it maps the BIOS drives to OS devices as

[FONT="Lucida Console"][COLOR="DarkOliveGreen"][INDENT](hd0)	/dev/hda
(hd1)	/dev/sda[/INDENT][/COLOR][/FONT]

What if I flipped those around in the USB's grub folder?

---

