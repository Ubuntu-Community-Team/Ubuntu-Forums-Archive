---
title: "Dual boot with Fedora"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by brothertroy on 2010-06-04
What is the best way to dual boot ubuntu 10.04 with fedora 13?  Fedora first then Ubuntu?  Will the Ubuntu installation repartition or will I need to do that with Gparted?

---

### Post by brothertroy on 2010-06-04
I decided to stay straight Ubuntu for now. Fedora doesn't "see" Ubuntu and Ubuntu doesn't "see" Fedora. I am just going to hang with Ubuntu and if I want to dabble in Fedora, I will us a live cd.

---

### Post by wojox on 2010-06-04
I installed Fedora first, then Ubuntu. That way Ubuntu can see Fedora when you log in to it and run:

```
sudo update-grub
```

As you can see I have openSUSE on mine:

```

wojox@wojox-desktop:~$ sudo update-grub
[sudo] password for wojox: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.34-5-generic
Found initrd image: /boot/initrd.img-2.6.34-5-generic
Found memtest86+ image: /boot/memtest86+.bin
Found openSUSE 11.2 (i586) on /dev/sda1
done


```

---

