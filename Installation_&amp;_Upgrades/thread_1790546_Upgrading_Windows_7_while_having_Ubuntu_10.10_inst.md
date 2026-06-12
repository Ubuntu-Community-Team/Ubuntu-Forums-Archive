---
title: "Upgrading Windows 7 while having Ubuntu 10.10 installed"
date: 2011-06-25
forum: Installation &amp; Upgrades
---

### Post by fotphys on 2011-06-25
Hi all,this is my first post.
I have windows 7 Home Premium 32 bit installed on my PC,dual boot with Ubuntu 10.10. The boot screen is the windows one,not GRUB.Recently,i noticed that i am eligible via MSDNAA to a free copy of windows 7 pro 64 bit.Needless to say i downloaded it,since i have an i5 750 CPU and 4GB of RAM.I want to know if I can install it in the windows partition without hurting the Ubuntu install at all,since I have some important files there.The only thing I am afraid of is that since the boot screen is windows, it may cause a problem at a new install,causing it to not recognize the Ubuntu partition(same hard drive by the way).Is that possible,or can I go ahead and install?

---

### Post by westie457 on 2011-06-25
> **fotphys said:**
> Hi all,this is my first post.
I have windows 7 Home Premium 32 bit installed on my PC,dual boot with Ubuntu 10.10. The boot screen is the windows one,not GRUB.Recently,i noticed that i am eligible via MSDNAA to a free copy of windows 7 pro 64 bit.Needless to say i downloaded it,since i have an i5 750 CPU and 4GB of RAM.I want to know if I can install it in the windows partition without hurting the Ubuntu install at all,since I have some important files there.The only thing I am afraid of is that since the boot screen is windows, it may cause a problem at a new install,causing it to not recognize the Ubuntu partition(same hard drive by the way).Is that possible,or can I go ahead and install?

Hi. Welcome to the Fora.
How you installed Ubuntu is going to be the deciding factor.

If you did a Wubi install inside Windows then installing your new Windows over the old one is probably to definitely going to wipe everything.

If you did a normal install of Ubuntu ie. using a separate partition then go ahead and install after backing up all your private files (docs, photos and such-like) just in case it goes wrong. After the install boot into a LiveCD and use that to upgrade Grub. Just ask in the Forum for instructions on how to do this and you will get them.

---

### Post by Alwimo on 2011-06-25
You should always have backups of the important files you referred to. :)

---

### Post by fotphys on 2011-06-25
> **westie457 said:**
> Hi. Welcome to the Fora.
How you installed Ubuntu is going to be the deciding factor.

If you did a Wubi install inside Windows then installing your new Windows over the old one is probably to definitely going to wipe everything.

If you did a normal install of Ubuntu ie. using a separate partition then go ahead and install after backing up all your private files (docs, photos and such-like) just in case it goes wrong. After the install boot into a LiveCD and use that to upgrade Grub. Just ask in the Forum for instructions on how to do this and you will get them.

I did a normal install using the CD i had burnt the ubuntu image into.It is in a separate partition,so i guess it should be ok.Thanks for your response.

---

