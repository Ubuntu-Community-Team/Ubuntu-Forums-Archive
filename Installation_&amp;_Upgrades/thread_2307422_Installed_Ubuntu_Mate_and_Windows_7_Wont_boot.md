---
title: "Installed Ubuntu Mate and Windows 7 Wont boot"
date: 2015-12-24
forum: Installation &amp; Upgrades
---

### Post by kyle68 on 2015-12-24
I tried to install Ubuntu Mate alongside windows 7 but now windows wont boot. It gives me the option in grub but just hangs on a black screen when I select. I ran boot repair and it gave me a second windows 7 boot option in grub but neither still work.

[http://paste.ubuntu.com/14203313/](http://paste.ubuntu.com/14203313/)

---

### Post by Vladlenin5000 on 2015-12-24
Hi and welcome.

Was your Windows working before? If so, please describe how have you installed Ubuntu.

---

### Post by kyle68 on 2015-12-24
HI, yes windows was working before. I installed ubuntu selecting the "install alongside windows" option. I can still access all my windows files so I didnt overwrite them.

---

### Post by MAFoElffen on 2015-12-25
> **Vladlenin5000 said:**
> If so, please describe how have you installed Ubuntu.
Just a short disclaimer. Ubuntu Mate is a branch distribution in which the Base System is derived from Ubuntu. Their community's support forum is located at:
[Ubuntu-Mate Community]("https://ubuntu-mate.org/community/")

Having said that... Since Ubuntu Mate is not in the direct family of Ubuntu (Not officially supported from this forum) and is a branch distribution derived from, then the first question might be what the ISO name of the install was done from? That may give a clue to target device arch and operating system core version. Since Ubuntu Mate supports installation of their branch to devices such as Raspberry Pi, also important would be what device it was installed to?

Basically the answers and direction to help the OP will be the same: 
- Ask how Ubuntu(-Mate) was installed beside Windows) Hopefully it was installed in free space of the disk and not over an old Win system partition...
- Ensure that the Windows partition is marked as bootable. 
- Mount the installed instances system with a LiveCD. 
- Rerun grub update and make sure Grub 2 saw the instance of Windows.

---

