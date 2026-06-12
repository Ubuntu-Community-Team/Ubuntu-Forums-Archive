---
title: "GRUB - Messed it up..."
date: 2005-06-10
forum: Installation &amp; Upgrades
---

### Post by robertobech on 2005-06-10
Not exactly an installation problem, but it's similar. I've re-created a Windows partition, and then Grub stopped working... 

Whenever I boot I get an "error 17"... how do I fix it? And If i Re-install Windows, what should I do to get Grub working again?

---

### Post by mingus on 2005-06-10
Probably the simplest thing to do is to re-generate grub's control file (/boot/grub/menu.lst) and reinstall the boot loader.

But sounds like you can't boot into Ubuntu at all, 'cause grub is hosed?

Then boot from the installation CD and use "rescue" instead of "linux".  You will be taken thru a serious of setup screens (like you did when you installed), it will ask you which partition your / (root) is on, and then drop you to a command prompt as root.

Do:
#update-grub
#grub-install

this assumes you had/want to have grub in your Master Boot Record, and will get to Windows from your Ubuntu grub menu.

If this doesn't work, get back in and in the shell do:
#cat /boot/grub/menu.lst
make a copy and post it back here for a look-see.

---

### Post by robertobech on 2005-06-10
Thank you, Mingus. I'll try it tonight, and then I'll post the results here.

---

### Post by robertobech on 2005-06-24
I'm sorry, I'm a bit late...

Mingus, it worked. In fact, I had tried to use a partitioning tool and messed it all up. So the partition table was altered, and grub was looking for thing in the wrong places.

I also had to change a few things... on the same day I posted this a list that I sunscribe sent me an email of a guy with a similar problem. He solved it, and I had to do some of the things he suggested to get it fixed. It's in portuguese, but it's kind of easy to figure out what he did:

"Pra consertar, vc tem que dar boot no micro via CD de instalação no rescue
mode (leia na tela de boot, lá tem instrucoes). Depois entre como root, e
execute o comando 'grub'. Lá dentro, digite:
find /boot/grub/stage1
ele vai retornar pra vc como (hd0,2). Ai é só digitar:
root (hd0,2)
setup (hd0)
Saia do grub, reboot e teste."

Also, since the partition table was changed, as soon as GRUB loaded again I had to change the menu entry, so that it would point to the right devices. Thanks a lot!

---

