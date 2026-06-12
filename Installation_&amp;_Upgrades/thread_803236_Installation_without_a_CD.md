---
title: "Installation without a CD"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by cameraman on 2008-05-22
I'm trying to install 8.04 to a laptop that has a dodgy CD drive. The bios doesn't allow booting from USB, but I've managed to install Damm Small Linux and transferred the CD image and setup Grub exactly per the documentation Installation without a CD / Installation/FromLinux.

When I boot and choose installer from the grub menu I get an error message 'No Setup signature found...' and there it hangs.

If it's complaining about not finding md5sum.txt it is in the root of the install image. Does anyone have any ideas?

---

### Post by Herman on 2008-05-22
Maybe it's looking for something in your .disk directory. 
Have you checked to make sure you copied the .disk directory? :)
(It's a 'hidden' file).

---

### Post by Sef on 2008-05-22
Check out [Installation/Netbook]("https://help.ubuntu.com/community/Installation/Netboot").

---

### Post by cameraman on 2008-05-22
> **Herman said:**
> Maybe it's looking for something in your .disk directory. 
Have you checked to make sure you copied the .disk directory? :)
(It's a 'hidden' file).

Yes I copied the .disk directory. I actually followed the instructions to a 'T' which is why I can't understand why I have this problem.

---

### Post by zvacet on 2008-05-22
Look if [this]("http://ubuntuforums.org/showthread.php?t=782603&highlight=iso") is of any help to you.

---

### Post by cameraman on 2008-05-24
I've found the problem, even though I installed a recent version of damm small linux it used a rather old version of grub 0.91 which has a problem booting the install process. Thanks to zvacet I tried  the install he mentioned which died the same way which then had me thinking it was to do with grub. I downloaded super grub and manually entered the boot parameters entered boot and away it went.

Thanks for those who helped

---

