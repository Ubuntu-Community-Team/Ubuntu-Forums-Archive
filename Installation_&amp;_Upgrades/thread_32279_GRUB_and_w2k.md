---
title: "GRUB and w2k"
date: 2005-05-06
forum: Installation &amp; Upgrades
---

### Post by DKnight768 on 2005-05-06
I need help. I had ubuntu warty installed on my pc, wich had windows 2000(w2k) in another partition. After installing ubuntu hoary with the same partition layout, w2k wont boot. It says ntoskrnl is missing. :? 
After some research, i think i found the problem; boot.ini on w2k installation is pointing to the wrong partition number. To my surprise, w2k recovery console **doesnt have any text editor** ](*,)  , and the partition is NTFS, so i cannot modify boot.ini.
I suposse the easiest way to solve this is to reinstall w2k, but that will overwrite my mbr and delete my grub... 
I know from experience that LILO can be launched after this move and rewrite the mbr using the options located in /etc/lilo.conf ; my question is-> how can I do this with GRUB??? I dont want to make experiments and lose my data...
Anyone knows the solution to this?
thank you

---

### Post by jon_hill987 on 2005-05-06
This is a long shot, download Knoppix live. It should boot from the CD and alow you to mount you w2k partion so you can edit your boot.ini

hope that helps.

---

### Post by DKnight768 on 2005-05-07
isnt NTFS write support experimental? I dont want to lose my data.
I only want to know how can i launch grub once i reinstall windows again.

---

### Post by jon_hill987 on 2005-05-07
Knoppix comes with some recovery tools ment for fixing windows, I must admit that with an ntfs partition it may not work but I doubt you would lose your data. another thing you could try is mounting the partition read only from ubuntu and copying your data accross.

---

### Post by DKnight768 on 2005-05-07
Thanks for your help. Ive finally solved the problem (ill post the solution to help anyone in similar circumstances)
I installed libntfs from Synaptic, and then added an entry for my NTFS partition in /etc/fstab, so i could read it and backup some files.
I made a Grub boot floppy disk using the HowTo that is in the wiki, and reinstalled windows 2000. It wiped the mbr, so i booted ubuntu with the floppy and restored grub on the mbr by doing:
$sudo grub
grub> root (hd0,0)
grub> setup(hd0)
I had to edit the /boot/grub/menu.lst because windows changed its partition number from hda3 to hda2.
BTW, hoary is great, see you ;-)

---

