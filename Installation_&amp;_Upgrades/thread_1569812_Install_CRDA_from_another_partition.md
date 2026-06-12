---
title: "Install CRDA from another partition"
date: 2010-09-07
forum: Installation &amp; Upgrades
---

### Post by TraderLars on 2010-09-07
Hey I need to boot a live disk and reinstall CRDA to the hard disk. I'm pretty sure I need to mount the partition and copy over files. If anyone knows the commands to do this and the location of the CRDA on my live disk then please help me if possible. 

Thanks.

---

### Post by TraderLars on 2010-09-08
well no one promised great support, or any support for that matter.

---

### Post by TraderLars on 2010-09-09
does anyone know how to install this one package from the live disk. i need to do this to save my broken 'buntu installation.

THANKS!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by TraderLars on 2010-09-16
does anyone mind spending five seconds to give me a clue here?

i need someone to point me in the right direction. I have to reinstall the CRDA package from a live disk to a broken buntu partition.

AAAANNNYYYOOOONNNNEEEEE??????

---

### Post by WanabeTux on 2010-09-20
You broke it, CRDA is part of the Linux kernel itself, if you delete it you know what happens, well now you do. The easiest thing to do is a reinstall, if you have not backed up your important stuff you can run the live cd and go to the file system and copy the things you want to a thumb drive, you may have to change permissions on some folders. Also I like to keep a backup of .thunderbird and .mozilla, they can be found in your home folder but you have to check show hidden folders under view. You could try to copy CRDA from /sbin off the live cd and paste it into /sbin on your file system, you may have to change permission on the folder here to, and restart. I doubt it works the kernel has decided its broke. If it does consider yourself one lucky you know what. Hope this helps.

---

