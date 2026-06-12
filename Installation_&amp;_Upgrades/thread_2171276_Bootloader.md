---
title: "Bootloader"
date: 2013-08-29
forum: Installation &amp; Upgrades
---

### Post by BlueTiger33 on 2013-08-29
[http://paste.ubuntu.com/6042571/](http://paste.ubuntu.com/6042571/) That's the URL that the boot-repair utility gave me.

I don't have (ever did) have a windows 7 dvd. Just an Asus Laptop that came with a recovery partition that I overwrote with Wubi. Well, I uninstalled Wubi from Add/Remove programs however boot manager still listed options as Windows or Wubi. Now, however, I'm getting the 0xc0000225 errors for windows.

So I'm hoping to be able to grub into windows with this ubuntu live cd I have.

I've tried so many different things IDK what to do anymore. I really would rather stick to windows now that i'm out of the army and need many specific windows programs installed for programming. (Going to college now.)

---

### Post by mikewhatever on 2013-08-30
You don't have Grub installed, which makes it impossible to use for loading Windows. Try doing an Ubuntu installation to a small partition, perhaps Grub will find Windows, and let you use it.

---

### Post by grahammechanical on 2013-08-30
I have never used the Windows Installer (wubi.exe) but I doubt very much that you did this

> came with a recovery partition that I overwrote with Wubi.

Using wubi.exe will install Ubuntu inside Windows and run it as if it was a Windows program. We give it disk space inside the Windows Drive. But if you have deleted the recovery partition by some other method, then you have a problem.  And this 

> the 0xc0000225 errors for windows.

is a Windows problem. The boot loader is still giving you a menu that includes Windows but there is a problem loading Windows and that is happening after the boot loader has passed control onto the Windows operating sytem.

Regards.

---

### Post by oldfred on 2013-08-30
It looks like you have boot flag on sda5. Grub does not use boot flag at all, but Windows has to have it on the bootable or active partition. Move boot flag to sda1 with gparted or Windows repairCD - make active.

You also are showing grub4dos. Did you also install EasyBCD? That can confuse things, but EasyBCD can help in updating BCD or sometimes in fixing Windows.

It does look like you may have installed grub2 to sda5. But just a install of grub without a system means you have to manually create a grub.cfg with the boot stanzas you need. And now Boot-Repair has replaced grub in MBR with syslinux which is a Windows boot loader that uses boot flag.

---

