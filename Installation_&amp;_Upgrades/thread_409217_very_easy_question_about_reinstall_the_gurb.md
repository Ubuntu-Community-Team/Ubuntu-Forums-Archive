---
title: "very easy question about reinstall the gurb"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by daziplqa on 2007-04-14
Hi folks,
I have a very easy question;
I have ubuntu 6.06 and winxp (dual boot), i need to reinstall winxp, of course it will rewrite the MBR.
How can i reinstall the grub using the Ubuntu 6.06 ***[I]LIVE*[/I]** CD ?
step by step please. :D

---

### Post by bulldog on 2007-04-14
Just like this :D ,

Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

---

### Post by daziplqa on 2007-04-14
thanx toooooooooooo much.

---

### Post by bulldog on 2007-04-14
> **daziplqa said:**
> thanx toooooooooooo much.

It's never toooo much :D ,but you're welcome :D

---

