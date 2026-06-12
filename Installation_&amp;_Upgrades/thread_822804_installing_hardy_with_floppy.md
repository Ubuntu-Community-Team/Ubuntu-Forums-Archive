---
title: "installing hardy with floppy"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by BrainBurner on 2008-06-08
Hello,

I'm following this guide [https://help.ubuntu.com/community/Installation/WithFloppies]("https://help.ubuntu.com/community/Installation/WithFloppies") to install Hardy on a PC without CD.

The guide is pretty old (it works with Hoary).
I followed it downloading the last debootstrap and installing Dapper (because Hoary was no more on the mirrors).

It works well until I have to execute the command:
```
base-config new 
```
The command is not found.

Then I go on: I install the linux-image 2.6.15 (is it right to use this)
And I get a strange message. something like "don't you need vmlinuz?"

Then it says that it cannot read grub on the command:
```
grub-install /dev/hda
```


Do you know what do I have to do?

---

### Post by logos34 on 2008-06-08
You could try installing [Basiclinux]("http://basiclinux.com.ru/") (floppy version 3.50) to hard drive and then use this guide to install ubuntu: [https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)
(-->Procedure 2)

---

