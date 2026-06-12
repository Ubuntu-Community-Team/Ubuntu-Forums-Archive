---
title: "Help with grub, dual booting 7.10 and Vista Buisness"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by Bviper on 2008-03-03
Alright so I just got a brand new shiny laptop Dell Vostro 1400. I'm using the alternate install disk due to the fact the regular will not boot with the video card I have. 

First a little background, the laptop came with 4 partitions (although when installing ubuntu it reports 5) wanting to leave those all intact I shrunk the main OS parition down 20 gigs to be used for the linux. It installs fine, but when it asks for to install grub is will not work. I've tried flat out not installing grub, and installing it to (hd0,6)  I've now installed Ubuntu three times trying to get grub to work, but each time it overwrites Vistas bootloader, which means I have to recover it using Vista's CD. I'm trying to use easyBCD to add the option to boot grub but each time it either fails to find grub or grub fails to load Ubuntu. 

I've searched and searched and cannot find anything. So I figured I better post and ask for help before I managed to screw anything up beyond repair.

FYI this isn't my first time round the block with linux just dual booting and Ubuntu in particular.

Thanks for any help.

---

### Post by Bviper on 2008-03-03
Ok somehow Grub was installed onto the swap partition which was considered 6, even though when installing Ubuntu it was considered 7. 

Is there any way to move Grub from the swap parition to the main partition without screwing anything up?

---

### Post by confused57 on 2008-03-03
You could try reinstalling grub to the Ubuntu root partition, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

You would have to "setup (hdx,y)", or whatever "find /boot/grub/stage1" shows.  EasyBCD should work with grub installed to the root partition:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

---

