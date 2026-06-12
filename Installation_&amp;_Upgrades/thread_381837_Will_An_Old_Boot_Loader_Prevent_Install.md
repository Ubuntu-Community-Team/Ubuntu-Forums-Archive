---
title: "Will An Old Boot Loader Prevent Install?"
date: 2007-03-11
forum: Installation &amp; Upgrades
---

### Post by toph on 2007-03-11
Hello.

I used to have a dual-boot laptop with Windows and Xandros installed (one partitioned HD). With many failed attempts, I removed Xandros. However, the boot loader is still there (and I can't seem to remove it). I have two questions:

1. Will this old boot loader get in the way of a clean install of a dual-boot (single partitioned HD) with Windows and Ubuntu?

2. Or does anyone know how to remove this boot loader?

Thanks in advance. I can't wait to get started.

toph.

---

### Post by toph on 2007-03-11
****toph's first cup of Ubuntu gets cold while waiting for a response****

I guess I'll wait until tomorrow to install. 

Please bring some ice and cream so I can have some good iced Ubuntu when it is time for me to install.

toph.

---

### Post by confused57 on 2007-03-11
> **toph said:**
> Hello.

I used to have a dual-boot laptop with Windows and Xandros installed (one partitioned HD). With many failed attempts, I removed Xandros. However, the boot loader is still there (and I can't seem to remove it). I have two questions:

1. Will this old boot loader get in the way of a clean install of a dual-boot (single partitioned HD) with Windows and Ubuntu?

2. Or does anyone know how to remove this boot loader?

Thanks in advance. I can't wait to get started.

toph.
When you install Ubuntu, grub should overwrite the old Xandros bootloader on your mbr, and will allow you to choose to boot Windows or Ubuntu.

The best way to remove an old bootloader is to overwrite it with a different functioning bootloader, either Windows IPL code, or grub from a new Linux install.

I'm supposing you just mean different partitions for Windows & Ubuntu, but on the same hard drive?

I know you're tired of waiting, thought I'd break the ice.

---

### Post by K.Mandla on 2007-03-12
I've had problems before where leftover bootloaders or partitions interfered with a new installation. I don't know that I could describe the exact circumstances or even duplicate the errors, but I make a point of low-level formatting between installations now. I don't know if that's an option for you, but I thought I would mention it. ;)

---

### Post by toph on 2007-03-12
Thanks for the replies.

> I'm supposing you just mean different partitions for Windows & Ubuntu, but on the same hard drive? - Yes. That is what I meant.

I really appreciate the help.

toph

---

