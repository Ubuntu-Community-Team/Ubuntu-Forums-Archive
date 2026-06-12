---
title: "How to change Boot"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by miguelpires on 2011-05-04
Hello,
I'm new to Linux, and i was playing around with wubi for some time, and now i made a fresh instal of 11.04 64bits, no problems so far! But one thing was change, the boot system. My computer is used by me and my daughter (7years old), and when i was using the wubi instalation when booting she only see Wyndows 7 and Ubunbtu, . Now with this fresh instalation, i think is grub o takes control, she have a hard time to try to enter in W7, because of all "offers" from their. 
So my question is, can i change the boot system to w7 control (like with wubi)?
Sorry for the bad english
Regard's
Miguel

---

### Post by oldfred on 2011-05-04
Many have suggested this.

HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

I have just done it manually by editing grub.

But Grub 2 also lets you use the title. Suppose your Windows title is "Windows Vista (on /dev/sda1)". Then you can use in /etc/grub/default, and you won't have to edit Grub after kernel updates.

find your windows entry in grub.cfg and copy to grub default like this Vista entry - If you edit your windows command use the edited copy as this must match the title exactly:
gedit /boot/grub/grub.cfg
and copy into grub_default line here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new line:
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

---

### Post by miguelpires on 2011-05-05
Hello!
Thanks, for your anwser. I'l try this when i get home.
Regard's
Miguel

---

