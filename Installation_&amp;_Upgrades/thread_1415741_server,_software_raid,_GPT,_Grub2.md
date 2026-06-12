---
title: "server, software raid, GPT, Grub2"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by sucram on 2010-02-25
Hi there!

I would like to setup a fileserver with software raid.
I'm using the server install cd for 9.10

I manually configured 2 raid devices:
/dev/md0 - / - ext4
/dev/md1 - swap - swap

The setup uses automatically GPT partition table ...

During the install process, grub2 setup fails with error "embedding not possible ..."

Do I have to setup a bios boot device for grub?
If yes, on which drive, or any other suggestions how to do it right?

Thanks for your help,
sucram

---

