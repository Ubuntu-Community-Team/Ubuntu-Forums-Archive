---
title: "grub-installation"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by noodles_x on 2007-05-05
hey
I've searched forum for similar question but I didn't find any...

i have XP, edgy and feisty on the same computer.
feisty was installed last,and because I was unsure will it work, I kept edgy.
During feisty installation I didn't install GRUB, i kept edgy's GRUB and modified menu.lst so I can boot feisty.
now i want to remove edgy, but if I do that, GRUB won't work anymore,because i will format sda2 and boot/grub/menu.lst is in it.
so i would like to install grub from feisty...
i found information how to restore grub if it was removed from MBR (for example after XP reinstallation), but my problem is- how to install grub from feisty?

thanks

---

### Post by confused57 on 2007-05-05
You should be able to use the live cd to install Feisty's grub to the mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by noodles_x on 2007-05-05
yes, i know that.
but "Only a small part of grub is located on the mbr, the rest of grub is in your boot folder. Grub needs those files to run the setup.", 
and my boot folder is in sda2, I have edgy on that partition,and I want to format that partition and keep feisty on sda4. get it?:-) on sda4 i have empty boot/grub, because when I installed feisty i didn't installed grub!

this guide showes how to recover grub to MBR, if it was deleted by for example windows xp, it doesnt show me how to completely install grub, to feistys sda4 /booT7grub and to mbr?

i hope i explained it better now.....

---

### Post by confused57 on 2007-05-05
> **noodles_x said:**
> yes, i know that.
but "Only a small part of grub is located on the mbr, the rest of grub is in your boot folder. Grub needs those files to run the setup.", 
and my boot folder is in sda2, I have edgy on that partition,and I want to format that partition and keep feisty on sda4. get it?:-) on sda4 i have empty boot/grub, because when I installed feisty i didn't installed grub!

this guide showes how to recover grub to MBR, if it was deleted by for example windows xp, it doesnt show me how to completely install grub, to feistys sda4 /booT7grub and to mbr?

i hope i explained it better now.....
Yes, I see what you're saying...I personally have never done this myself, but you'd probably need to chroot into your Feisty & install grub.  The only thing that I could find was a post by Herman, who chrooted into his Ubuntu and installed lilo:
[http://ubuntuforums.org/showthread.php?t=221396&highlight=chroot](http://ubuntuforums.org/showthread.php?t=221396&highlight=chroot)

I wish I could give you an easier way, but it's the only suggestion I can offer...good luck.

Added:  I don't know if you can just boot into Feisty, then"
```
sudo apt-get install grub
```
or use Synaptic?

---

### Post by bapoumba on 2007-05-05
Please check this thread:
[http://ubuntuforums.org/showthread.php?p=2570728]("http://ubuntuforums.org/showthread.php?p=2570728")

[http://www.gnu.org/software/grub/manual/grub.html]("http://www.gnu.org/software/grub/manual/grub.html")

---

### Post by noodles_x on 2007-05-05
sudo apt-get install grub.....

now thats a good idea......!

ofcourse i can boot to feisty, in edgy i modified menu.lst...but i would like to format edgy...

i will try it! it colud work...I just hope it does automaticaly all the work like during the normal install,and i don't have to manualy do things...

after i try it, I'll reply if it works or not...

thanks

---

