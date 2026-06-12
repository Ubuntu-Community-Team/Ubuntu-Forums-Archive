---
title: "How to reinstall ubuntu on a 20gb partition?"
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by Macfunky on 2009-12-24
I installed ubuntu onto a 20gb partition of my parents computer so i could use it when i visited. Problem is they no longer have broadband in the house so an upgrade is out of the question. I would like to reinstall the ubuntu install with karmic koala but i am not sure how to install to that partition manually. I used the simple dual boot install option when i initially installed it. Is there any easy way to install a fresh copy of karmic koala onto that partition that would be safe for me to do without getting too complicated? Any help would be appreciated. Thanks

---

### Post by oldfred on 2009-12-24
If you choose manual install then you just have to select which partitions to use for / and swap and others if you have them. It will overwrite everything so if you want to save anything make sure you have backups. 

With a Karmic new install it will install grub2 and take over the booting of the computer. Do you now have old grub presenting a menu or a hidden default to windows for your parents. grub2 is a lot different than old grub.

In the grub file you can set windows to boot but the info in the quotes has to be exactly as grub found it:

find windows entry in this and copy to 
gedit /boot/grub/grub.cfg
and copy here
gksudo gedit /etc/default/grub 
GRUB_DEFAULT="[COLOR=DarkRed]Windows Vista (on /dev/sda1)[/COLOR]"

I have seen some posts about ways to do offline updates but did not save any references as I do not have that problem

---

### Post by Macfunky on 2010-01-03
Bump. Any help?

---

