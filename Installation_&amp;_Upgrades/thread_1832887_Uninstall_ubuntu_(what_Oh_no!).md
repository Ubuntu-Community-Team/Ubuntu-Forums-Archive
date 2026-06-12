---
title: "Uninstall ubuntu (what? Oh no!)"
date: 2011-08-25
forum: Installation &amp; Upgrades
---

### Post by dESAI on 2011-08-25
I have never had to do this before :)

But I'm giving my laptop to my mother when my new one arrives and I need to remove the ubuntu installation and get the disk space back.

A few months ago the install stopped working. I can't remember what the error said... and tbh I can't be bothered to reboot twice to read it, but it has to be removed now anyways.

Had a look in windows to see if I can do anything in the disk manager, but it appears I can't.

Oh wise ones, please, which path should one take?

---

### Post by dino99 on 2011-08-25
go for a fresh new install ;)

---

### Post by dESAI on 2011-08-25
> **dino99 said:**
> go for a fresh new install ;)

Yeah I probably will.

Should I be able to see the ubuntu partition in the Win7 Disk Manager?

I'm wondering if ubuntu stopped working because windows filled up. Isn't there an option to reduce the size of the ubuntu partition dynamically if windows needs more? If so, would that automatically delete the ubuntu partition?

---

### Post by ottosykora on 2011-08-25
>Should I be able to see the ubuntu partition in the Win7 Disk Manager?<

well yes, but it will not be marked as such , it will be just seen as some partition but with no additional info.

>I'm wondering if ubuntu stopped working because windows filled up. Isn't there an option to reduce the size of the ubuntu partition dynamically if windows needs more? If so, would that automatically delete the ubuntu partition?<

no definitely not, windows is not able to automatically go and remove or modify partitions of linux.
Windows itslef can use dynamic partitons, the may then adjust according to needs by itself, but ext3 or similar partitions can not be accessed by windows without some special program to be installed.

To remove ubuntu is unfortunately not so simple, I mean it is not possible just to delete the partition. If you use grub (I assume so) then part of it is in the ubuntu partition and so if you delete it , you might not be able to boot anything at all.

Best have windows repair disk ready, you can create it from within w7. This will then help you to restore the master boot record so it boots straight to windows then.

---

