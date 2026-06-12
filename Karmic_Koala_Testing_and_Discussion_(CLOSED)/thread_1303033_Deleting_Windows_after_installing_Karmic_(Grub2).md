---
title: "Deleting Windows after installing Karmic (Grub2)"
date: 2009-10-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by flipper9 on 2009-10-27
Hello All,

I've decided to just delete my Win7 (RC) install and just keep my currently installed Karmic.  However, I'm worried that if I delete the two partitions (they are first on the drive), will Grub2 be able to recognize this?  Right now, I'm in the Live CD version of Karmic, running GParted getting ready to delete the two Windows 7 partitions and resize my Karmic partition to take up all available space.

Any pitfalls to what I am about to do?  What will go wrong?  How do I do it correctly? (Hopefully without a lot of cryptic commands on the command line, LOL)

---

### Post by ronacc on 2009-10-27
the only thing you should look out for is that when you resize your karmic partition(s) the UUID may change so before you reboot look at your   /boot/grub/grub.cfg and make sure that the uuid that grub(2) is pointing to is correct , you will probably have to hand edit it . There are instructions here in the forum about how to do that .

---

### Post by lovinglinux on 2009-10-27
I guess, but I'm not sure, that you just need to do run **update-grub** after deleting the partition. Grub should detect what OSs are still there and update the entries automatically.

---

