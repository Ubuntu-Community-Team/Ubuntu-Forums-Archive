---
title: "HP touchpad not responding"
date: 2009-03-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by LordVeovis on 2009-03-12
I just purchased a new HP laptop and imediately installed Ubuntu on it.  I have the Alpha on 3 other machines at the moment, and I wanted to test it here as well.  The mouse pad, or touch pad, drivers do not seem to be installed.  Any suggestions?

---

### Post by alexv75 on 2009-03-12
Try adding i8042.noloop to your "/boot/grub/menu.lst" at the "kernel" line.

Example:

```
kernel		/boot/vmlinuz-2.6.28-9-generic i8042.noloop root=UUID=1efa3e68-523b-450b-abb5-9da054f111ec ro quiet splash 
``` It fixed my touchpad troubles on the M912M netbook.

---

### Post by Teamgeist on 2009-03-12
You need to install the xserver-xorg-input-all Package.
It was missing on the Alpha 3 CD.

```
sudo apt-get install xserver-xorg-input-all
```

---

### Post by LordVeovis on 2009-03-12
> **Teamgeist said:**
> You need to install the xserver-xorg-input-all Package.
It was missing on the Alpha 3 CD.

```
sudo apt-get install xserver-xorg-input-all
```

I believed I used the Alpha 5 install CD, I will test the above 2 responses later tonight and reply though, thanks!

---

