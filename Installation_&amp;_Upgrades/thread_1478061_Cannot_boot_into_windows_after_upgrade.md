---
title: "Cannot boot into windows after upgrade"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by dblock110 on 2010-05-09
I have searched and searched but cannot find someone with the exact problem as me. I upgraded to LL today. During the installation it asked me which parts to install grub to. I should have just checked all the boxes, but i cant remember wat i pressed.

Now my grub menu look like 

-ubuntu
-ubuntu memtest
-windows 7

when i choose windows 7, it just goes straight back to the grub menu . . .

any help would be appreciated.

TiA

---

### Post by dizzykittystudios on 2010-05-09
I've got WinXP and it was doing that to me as well.  [Click here]("http://ubuntu-ky.ubuntuforums.org/showpost.php?p=8930595&postcount=3") for a solution from one of the forums that has worked for many folks.  

That solution didn't work for me personally, I ended up having to insert my XP disc and running fixmbr and fixboot.  But I would try the above solution first since the fixboot completely erases GRUB and you end up having to reinstall it (which I have yet to do).

---

### Post by bcbc on 2010-05-09
Here's a [resource page]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector") setup by the same person that wrote the post dizzykittystudios linked too. It contains instructions for win7 too and also more information including correct diagnosis.

Note - there is a typo for the windows 7 command. Should be bootrec (not bootrect).
Also, make sure you do the diagnosis before trying to fix.

Finally, just a clarification - the boot sector fix doesn't remove the grub bootloader. But if you do the "bootrec.exe /fixmbr" command this will remove it. In that case, [this link]("http://ubuntuforums.org/showthread.php?t=1014708") shows how to reinstall grub (just the bootloader part).

---

