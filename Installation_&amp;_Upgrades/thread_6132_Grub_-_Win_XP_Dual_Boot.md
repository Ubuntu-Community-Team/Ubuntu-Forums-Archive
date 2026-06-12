---
title: "Grub - Win XP Dual Boot"
date: 2004-11-25
forum: Installation &amp; Upgrades
---

### Post by Useless on 2004-11-25
I am new to linux so bear with me.  I had a pc with a HD formatted and partitioned.......55gig for winxp (already formatted and installed) and 25 gig for ubuntu (Not yet formatted nor installed).  I installed xp first then decided to install ubuntu afterwards.  Now, when i get to grub, it detects my win xp installation (Win 2000/xp) but when i select it and hit enter...the computer just reboots and it all starts over again.  And yes....my hard dirve is set to LBA.

---

### Post by Magneto on 2004-11-25
[QUOTE=Useless]I am new to linux so bear with me.  I had a pc with a HD formatted and partitioned.......55gig for winxp (already formatted and installed) and 25 gig for ubuntu (Not yet formatted nor installed).  I installed xp first then decided to install ubuntu afterwards.  Now, when i get to grub, it detects my win xp installation (Win 2000/xp) but when i select it and hit enter...the computer just reboots and it all starts over again.  And yes....my hard dirve is set to LBA.[/QUOTE]
 can you post the contents of /boot/grub/menu.lst

which partitions contain which operating systems-  do a  #cfdisk  to see your partition layout

---

### Post by Useless on 2004-11-25
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1





Thats what it says for the windows install.

---

### Post by Magneto on 2004-11-25
[QUOTE=Useless]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1





Thats what it says for the windows install.[/QUOTE]
 without the other information I can't help you 
If grub is setup  incorrectly I can't troublehoot it with you without knowing the layout of all your partitions

if you do

sudo cfdisk

you will see how your partitions are setup 

mainly what is hda1 and is the word boot in the column Flags

---

### Post by Useless on 2004-11-25
[SIZE=5]Name       Flags      Part Type  FS Type          [Label]        Size (MB)
------------------------------------------------------------------------------
hda1        Boot        Primary   NTFS             []              58720.28*                                          
 Pri/Log    Free Space                     0.10*    
hda2                       Primary   Linux ext3                       21306.00[/SIZE]

---

### Post by Useless on 2004-11-25
that was it, verbatim.  Does it look ok to you?  I thought it did.

---

### Post by Magneto on 2004-11-25
yeah looks right- you might wanna try to run setup from grub's commandline and see if that fixes it-  I was thinking the boot flag was missing from the xp partition cuz I know that will stop xp cold.

---

### Post by Useless on 2004-11-27
run setup?  Im not so sure what you mean or how to do it.....sorry, still very new to this all.

---

### Post by Magneto on 2004-11-27
[QUOTE=Useless]run setup?  Im not so sure what you mean or how to do it.....sorry, still very new to this all.[/QUOTE]
 you can install grub from the commandline just type "sudo grub" and you will get a "grub >  " prompt
then install it here are the directions

[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html)

---

### Post by Useless on 2004-11-29
[QUOTE=Magneto]you can install grub from the commandline just type "sudo grub" and you will get a "grub >  " prompt
then install it here are the directions

[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html)[/QUOTE]


Magento, i would like to thank you.  I think i have figured it out.  I was about to scrap it all but after you have been so kind as to help me i am now determined to stick with ubuntu.  Once again, thank you for helping out a linux/newb in need.

---

### Post by Magneto on 2004-11-29
Can you boot to XP now? Glad to help

---

### Post by Useless on 2004-11-30
[QUOTE=Magneto]Can you boot to XP now? Glad to help[/QUOTE]


Yes, everything has worked itself out now.  Thanks!   :D

---

