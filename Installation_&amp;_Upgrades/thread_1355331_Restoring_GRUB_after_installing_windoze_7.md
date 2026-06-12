---
title: "Restoring GRUB after installing windoze 7"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by hariks0 on 2009-12-14
Hi all,

I today installed windoze 7 in my pc with 9.10 and it killed the grub as usual. I used a 9.04 live cd to restore grub with the commands like 

find /boot/grub/stage1
root (hd0,7)
setup (hd0)
quit

but the grub has no menu items on reboot. Only a black command prompt is there.

Did I miss anything or it is grub2 that causes the problem ? If any of you guys has a menu.lst file, please let me know if I can use it by copy, paste.

---

### Post by phillw on 2009-12-14
> **hariks0 said:**
> Hi all,

I today installed windoze 7 in my pc with 9.10 and it killed the grub as usual. I used a 9.04 live cd to restore grub with the commands like 

find /boot/grub/stage1
root (hd0,7)
setup (hd0)
quit

but the grub has no menu items on reboot. Only a black command prompt is there.

Did I miss anything or it is grub2 that causes the problem ? If any of you guys has a menu.lst file, please let me know if I can use it by copy, paste.

menu.lst is Grub legacy - you'll be on Grub2. So, you need a 9.10 LiveCD - 9.04 is grub legacy.

hi, you should be able to reset Grub2 with Win here --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If it's borked your Grub2 installation totally, just re-install Grub2, it looks scary, but is a walk in the park, instead of scratching your head, trying different 'tweaks' --> [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

Hopefully, the 1st thread will get you running, if not - the 2nd one certainly will
(Speaks from personal experience --> [http://www.vpolink.com/blog.php?b=2](http://www.vpolink.com/blog.php?b=2)   Go have a giggle)

Phill.

---

### Post by hariks0 on 2009-12-15
Thank you very much. I got the Windoze boot loader back as per the instruction in the first link. I will try to get the GRUB too.

Thank you once again.

---

