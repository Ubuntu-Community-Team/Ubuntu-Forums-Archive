---
title: "Can i hide some options on the Grub screen?"
date: 2012-02-27
forum: Installation &amp; Upgrades
---

### Post by Muramasa on 2012-02-27
I currently have Ubuntu and windows 7 installed on my laptop, when i boot the laptop the Grub screen gives me 6-7 options with Ubuntu at the top and Windows 7 at the bottom, is it possible to hide all the other options leaving only Ubuntu and Windows?

---

### Post by wojox on 2012-02-27
Sure you just need to purge some of the old kernels. See this how-to [HOWTO: Remove Older Kernels via GUI (or CLI)]("http://ubuntuforums.org/showthread.php?t=1587462")

---

### Post by josephmills on 2012-02-27
yes there are a ton of ways about doing this. 
!!!!!!!!!!!!!!!BACKUP FIRST !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
one find out what kernel you are using. in terminal (ctrl+alt+t)enter 
```
uname -r 
```
this will give you the kernel version that you are using. 
then open up synaptic package manager and search for "linux-image"
now find all the old ones that are install and remove them. then run 
```
sudo update-grub
```

that is one way the to do this there are others. Then there is BURG read more about BURG here   [http://www.unixmen.com/how-to-install-burg-in-ubuntu/](http://www.unixmen.com/how-to-install-burg-in-ubuntu/)

Hope this helps

---

### Post by Muramasa on 2012-02-27
Thanks for the fast replies, however i am not trying to remove an old version, i should have made it more clear.

The list basically looks like this: (this is from memory, i can get full details if needed)

Ubuntu
Ubuntu (recovery mode)
Previous Linux versions
memory test
memory test
Windows recovery
Windows 7

I am not trying to delete anything i just want to hide all the options between Ubuntu and Windows 7 if possible.

---

### Post by josephmills on 2012-02-27
> **Muramasa said:**
> Thanks for the fast replies, however i am not trying to remove an old version, i should have made it more clear.

The list basically looks like this: (this is from memory, i can get full details if needed)

Ubuntu
Ubuntu (recovery mode)
Previous Linux versions
memory test
memory test
Windows recovery
Windows 7

I am not trying to delete anything i just want to hide all the options between Ubuntu and Windows 7 if possible.

[http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/](http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/)

I would also look into burg 
Hope that this helps

---

### Post by stn21 on 2012-02-27
You could manually edit /boot/grub/grub.cfg and delete all menu-items you don't want.

If they appear again, for example after an update, edit again. Back up grub.cfg first.

---

### Post by oldfred on 2012-02-27
Two ways to customize:

HOWTO: Grub Customizer Updated for grub 1.99
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html) 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
The Grub 2 Guide (formerly Grub 2 Basics) manual way
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

