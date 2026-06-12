---
title: "Help removing grub from ubuntu live &quot;cd&quot;"
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by k0sm0 on 2011-02-05
So here's the thing, I installed ubuntu from a usb, it installed ubuntu good, but i had some problems with drivers ATI and I tought that maybe was because of the usb, so I've decided to wait to get my dvd-burner back, because I have an original cd of ubuntu 10.04 and I was going to use it, so I uninstalled ubuntu from windows 7  (... I just deleted the partition for ubuntu) now I'm having problems at the boot because the grub still there, for the moment I don't have dvd-burner and because of that I can't repair windows 7

What I can do maybe: Install ubuntu again from the usb, that should fix the grub giving me the ability of select OS but, there is nothing that I can do in ubuntu to uninstall the grub?

sorry for the engrish and thanks for any help :p:p

---

### Post by steveneddy on 2011-02-05
Boot into Windows if possible and open a command line.

Type into the console:

```
fix mbr
```

---

### Post by presence1960 on 2011-02-05
Boot the ubuntu Live USB and choose try ubuntu. When the desktop loads open a terminal and run ```
sudo apt-get install lilo
```Ignore warnings and proceed. this will install lilo to Live Session.

next in terminal run ```
sudo lilo -M /dev/sda mbr
```This will put a generic windows boot loader on MBR and reset it to boot windows. Reboot without Ubuntu Live USB and you should boot right to windows.

---

### Post by k0sm0 on 2011-02-05
ermmm, i can't join windows thats the main problem, thanks anyways, trying your method [presence1960]("http://ubuntuforums.org/member.php?u=657448").

---

### Post by k0sm0 on 2011-02-05
Thanks a lot it worked, now im gonna install 10.04 I didn't had problems with drivers with that version and I was able to update it. Anyways thanks again!

---

