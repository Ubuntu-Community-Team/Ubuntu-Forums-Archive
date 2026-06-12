---
title: "Need help changing menu.lst"
date: 2006-10-11
forum: Installation &amp; Upgrades
---

### Post by Keymaster on 2006-10-11
In GRUB I have a config like this

```
## ## End Default Options ##

title		Select Your Operating System:
root

title		Ubuntu Linux
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda6 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Winblows Xtra Problems Massive Crash Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

How can I make Windows the default choice, and also make "Select Your Operating System" not able to be selected in the menu? (AKA just a label/title type thing)  This is for a public use ternminal, and is kind of important.  Thanks

---

### Post by taurus on 2006-10-11
Near the top of your /boot/grub/menu.lst, there is a line that says

```
default         0
```
Change the 0 to 1 if you want to make Windows as your default OS...

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Keymaster on 2006-10-13
Thanks but how do I make the ```
title		Select Your Operating System:
root


``` not able to be selected?

---

### Post by taurus on 2006-10-13
Just remove those two lines since they are not pointing at anything...

---

### Post by Coelocanth on 2006-10-14
Keymaster, I just have to say 'thank you'. This is the first time I've ever read this:

> Winblows Xtra Problems Massive Crash Edition

Made me laugh out loud. :-D

---

### Post by Keymaster on 2006-10-15
> **taurus said:**
> Just remove those two lines since they are not pointing at anything...
 It is just a title bar that gives some basic instructions.  Selecting it does nothing, so I thought there might be a way to make it unselectable, but still there.  Normally when installing Ubuntu on an XP machine it says "Other operation systems" or something like that before it says "Windows whatever version"

---

### Post by Keymaster on 2006-10-15
> **Coelocanth said:**
> Keymaster, I just have to say 'thank you'. This is the first time I've ever read this:



Made me laugh out loud. :-D

It used to say "Windows XP Media Center Edition" but I had to change that lol

---

