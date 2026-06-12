---
title: "i have a problem when i'm trying to install deb's from ntfs partition"
date: 2010-03-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-03-18
i keep my deb's on ntfs partition because unfortunally i need to erase and install ubuntu more times then i care to so i backup my files there but if i try to install from there i get a messege file not found which make me wonder what happen to webui users and not like me who does install on ext4 partition but never the less it would be great if this problem be fixed.

if anyone know why or how i would like to hear about it.

thanks in advance.

---

### Post by kurros on 2010-03-18
Wubi installs to an ext4 volume. It just happens to be stored in an file on the NTFS volume. Think of it like a VirtualBox or VMWare disk image.

I just tried to reproduce your problem and can't. Maybe its a permissions issue. How are you trying to use the .debs?

---

### Post by aviramof on 2010-03-18
just by double clicking it that's all:

---

### Post by dcstar on 2010-03-19
> **aviramof said:**
> i keep my deb's on ntfs partition because unfortunally i need to erase and install ubuntu more times then i care to so i backup my files there but if i try to install from there i get a messege file not found which make me wonder what happen to webui users and not like me who does install on ext4 partition but never the less it would be great if this problem be fixed.

if anyone know why or how i would like to hear about it.


If the .deb is unpacked on the NTFS volume then all bets are off.

NTFS does not support all Linux filesystem requirements - especially for folders/files with a leading "." Bottom-line is don't execute Linux things on non-Linux filesystems.

Move it to a Linux filesystem and see what happens.

---

