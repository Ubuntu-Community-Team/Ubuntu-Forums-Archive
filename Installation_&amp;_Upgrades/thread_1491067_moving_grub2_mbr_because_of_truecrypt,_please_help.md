---
title: "moving grub2 mbr because of truecrypt, please help"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by dex87 on 2010-05-23
After having encrypted my windows partition, truecrypt overwrote my mbr, and now I can't access grub during boot, not even when I press escape :(

I was thinking of restoring my original mbr with the truecrypt rescue cd, boot into ubuntu and copy the mbr to the ubuntu partition, but I'm really not sure how to do it. I'm still learning and any help would be greatly appreciated. When you do this, truecrypt supposedly loads grub when you press escape.

To give you an idea of how my drive is partitioned, pls see the attachment.

Thanks in advance!

---

### Post by roomey on 2011-02-04
> **dex87 said:**
> After having encrypted my windows partition, truecrypt overwrote my mbr, and now I can't access grub during boot, not even when I press escape :(


this worked for me (until a GRUB update overwrote the MBR without confirmation)

Leave the truecrypt boot loader on the MBR.

[LIST=1]
[*]Boot using ubuntu live disk
[*]Check which is the main ubuntu partition using: sudo fdisk -l /dev/sda(or gparted)
[*]You need to install grub on a logical partition.
[*]If the Main Ubuntu partition is extended and not logical,  grub will not boot up properly, so you have to use a logical partition
[LIST]
[*] install gparted to help you with this:sudo aptitude install gparted
[*] Some dell laptops seem to have takend the first partition as a  small utilities area: give it the boot flag (truecrypt likes grub having  a boot flag.)
[/LIST]
 
[*] Mount the main linux partition: sudo mount /dev/sdaX /mnt
[*] Install grub2 on the partition (either the main one or the  one you just took)```
: sudo grub-install --force --root-directory=/mnt  /dev/sdaX
``` (in my case it was sda1).
[*] Restart your computer. In my case I can press escape when it  asks for my passphrase, and then I get GRUB menu, or I can put in my  passphrase, and then I still get the grub menu (which is strange) but  when I pick windows it boots fine)
[/LIST]
BE CAREFUL with this, use at your own risk, installing GRUB on a partition not a disk is not recommended. But as I said, this worked well for me.

PLEASE NOTE ON THE INSTRUCTIONS ABOVE.

After you move GRUB to a new partition, run
```
dpkg-reconfigure grub-pc
```This SHOULD stop your MBR being lost during a future update. 

Even so, once you have it all set up take a copy of the MBR so you can restore easily 
Use (Be carful of using dd)
```
dd if=/dev/sda of=/boot/mbr.bak bs=[COLOR=#ff0000]512[/COLOR] count=1
```

 NB. if you do install GRUB2 on an extended partition, it will boot once, but will fail after. 
 NNB. Don't do this without backing up 
  NNNB. If you dont put in the password, and then boot windows, you end up  in the recovery program. I am no expert on windows, but I am guessing  if you try to recover, you will kill your encrypted win partition.

---

### Post by Turpin on 2011-02-04
oops, failed to read original post.  Edited.

---

