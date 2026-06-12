---
title: "editing grub from live CD session"
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by SpikeyMike on 2007-01-26
Hi

I have installed ubuntu and windows server on one hard drive and now I want to edit the grub menu to add windows to it, I booted from the CD and mounted the partition where ubuntu is installed using: 
     
[I][COLOR="Red"]mkdir /temporary
mount -t auto /dev/sda5 /temporary[/COLOR][/I]

Then I tried to open the grub menu using the following command:

[COLOR="Red"]*sudo gedit /temporary/etc/grub.conf*[/COLOR]

I also tried:

[COLOR="Red"]*sudo gedit /temporary/boot/grub/menu.lst *[/COLOR]

but I just get the error message below and then the grub menu window opens but it is empty

[I][COLOR="Red"](gedit:29222): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
[/COLOR][/I]


Any advice on this would be greatly appreciated.

---

### Post by housam on 2007-01-26
Try to use the super grub disk , it may help fix it.
[http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/")

---

### Post by taurus on 2007-01-26
```
sudo nano -w /temporary/boot/grub/menu.lst 
```
<Ctrl>x to exit and Y to save it.

---

### Post by SpikeyMike on 2007-01-26
> **taurus said:**
> ```
sudo nano -w /temporary/boot/grub/menu.lst 
```
<Ctrl>x to exit and Y to save it.

Hi

that worked perfectly, thanks for that :) 

Spikey

---

