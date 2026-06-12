---
title: "No boot with HP elite book 8440p with any distro"
date: 2017-09-20
forum: Installation &amp; Upgrades
---

### Post by boscarlu on 2017-09-20
Hi all, I'm trying to install Ubuntu on this notebook in legacy mode.
The first time I tried with Xubuntu and it went well, but I didn't like it, so I went for Lubuntu... And nothing worked anymore, not even Xubuntu which used to work!
Basically, when I try to install from a flash drive, it goes to find the api's in the CD... Then it stops. I solved it with a netinstall and everything looks fine, but just desn't boot... Only black screen with a dash.
Since at the beginning it was working, it might be my mistake... maybe on the bios?
PLEASE HELP! I need it for university next week!!

---

### Post by sudodus on 2017-09-21
My experience is that similar HP Elitebooks can boot from a USB flash drive, that is **cloned** from an Ubuntu or Ubuntu community flavour iso file.

**Cloning tool in Ubuntu 16.04 LTS and newer versions**

- The Ubuntu Startup Disk Creator in Ubuntu 16.04 LTS and newer versions. In older versions, this tool is not a cloning tool and it is buggy.

**Cloning tools in Linux**

- Disks alias gnome-disks

- mkusb, [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

**Cloning tool in Windows**

- Win32 Disk Imager, [Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

---

### Post by boscarlu on 2017-09-21
I made the memory stick both with unetbootin and startup disk creator from iso (on acer aspire one with bios and lubuntu) and was working only live!

At the end, I used a live version on the HP for to make another memory stick, with startup disk creator and iso file... sorted!

I don't really know what i've done, but i'll keep this memory stick as a sacred grahal =P

---

### Post by sudodus on 2017-09-21
I'm glad you have a working memory stick now :-)

If you feel that your problem is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

