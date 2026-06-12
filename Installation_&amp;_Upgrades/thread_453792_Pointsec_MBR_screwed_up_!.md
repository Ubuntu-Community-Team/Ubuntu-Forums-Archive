---
title: "Pointsec MBR screwed up !"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by seba-baires on 2007-05-24
Hi gurus all over the world!

I have installed Ubuntu on an external USB disk, using a Live CD as a source.
Despite I'd checked that the Hard Drive of my IBM T43 was mounted in read-only mode, the Installer program stamped Grub on its MBR, overwriting PointSec boot loader. Therefore, no more XP on my Company's laptop...  :{

Does anybody know if Ubuntu makes a MBR backup prior installing Grub ??
If it is so (and I'm praying for that), where is it stored??

Thanks in advance !!

---

### Post by eapache on 2007-05-24
As far as I know it doesn't back it up, but grub should detect Windows and provide a boot option for that anyways... You should still have access to XP.

---

### Post by seba-baires on 2007-05-25
Yes, that's true, but not with an encrypted drive. It always needs this funny driver to be loaded before the O.S.
So, it seems I'm lost...
But thanks for your quicke reply anyway !! ;-)

---

### Post by rillip on 2007-05-25
This is a common issue.  Got a windows recovery or install disk?

Go to the recovery console.  Run fixmbr and fixboot.  Done, Windows boot loader reenabled, no more grub.

---

### Post by seba-baires on 2007-05-25
Hey !
I had nothing to lose, so I tried it and ...guess what ??? It worked !!
Seems that Pointsec stores its driver not in the MBR but in the boot sector of the encrypted partition (Thanks God!!)
So thanks a lot  for the solution buddy !! 
:D

---

### Post by wpshooter on 2007-05-25
Now if you can get them to take PointSec off of there you will have a good computer !!!

---

### Post by seba-baires on 2007-05-27
Never mind! 
I've successfully installed Ubuntu on an external USB disk, so, no longer need to boot the Laptop Drive to use the computer on my own purpose !! Moreover, I'm thinking about booting that drive inside a Virtual Machine in Ubuntu. (Putting WinCrap inside a cage ;) )

---

### Post by ba5e on 2007-10-14
hi Seba - what did you do to install it on a seperate USB drive without mashing the main MBR? can you point me to your source?? ;)

---

