---
title: "Feisty Fawn boots only after hitting Ctrl+Alt+F1"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by gauravp55 on 2007-06-15
Ok I had earlier posted this.. [http://ubuntuforums.org/showthread.php?t=470675](http://ubuntuforums.org/showthread.php?t=470675). and I tried a suggested solution. So only after I hit Ctrl+Alt+F1 I was able to log on.. Why is that so?? Here's a look at menu.lst :


```

title		  Ubuntu, kernel 2.6.20-15-generic
root		 (hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=6c722ba0-63b2-4ebf-9310-d19bef274127 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=6c722ba0-63b2-4ebf-9310-d19bef274127 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

title		Other operating systems:
root

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Thanks.

---

### Post by dreadlord_chris on 2007-06-15
if you remove the **quite splash** from the lfirst kernel option you'll actually be able to see, while it is booting up, where things are hanging

---

### Post by gauravp55 on 2007-06-15
> **dreadlord_chris said:**
> if you remove the **quite splash** from the lfirst kernel option you'll actually be able to see, while it is booting up, where things are hanging

Thanks!! It's booting fine now. It showed the complete booting process.. But could you let me know why the Boot  screen wasn't graphical as it is in Windows? Because I've seen some graphical ubuntu  boot screen videos.

---

### Post by dreadlord_chris on 2007-06-15
> **gauravp55 said:**
> Thanks!! It's booting fine now. It showed the complete booting process.. But could you let me know why the Boot  screen wasn't graphical as it is in Windows? Because I've seen some graphical ubuntu  boot screen videos.

did you remove **quite spalsh**? That would be why....

---

### Post by gauravp55 on 2007-06-15
I removed **quiet splash** because you asked me to. After removing quiet splash ubuntu booted just fine and I didn't have to hit Ctrl+Alt+F1 as I had to earlier before removing **quiet splash**. My question to you was whether it's possible to have a GRAPHICAL Screen while booting up as it does in Windows?

---

### Post by dreadlord_chris on 2007-06-16
> **gauravp55 said:**
> I removed **quiet splash** because you asked me to. After removing quiet splash ubuntu booted just fine and I didn't have to hit Ctrl+Alt+F1 as I had to earlier before removing **quiet splash**. My question to you was whether it's possible to have a GRAPHICAL Screen while booting up as it does in Windows?

re-add splash to the kernel line

---

### Post by gauravp55 on 2007-06-16
> **dreadlord_chris said:**
> re-add splash to the kernel line

Doesn't work!! In fact after adding splash I need to hit Ctrl+Alt+F1 again or else I get a blank screen!!

---

### Post by dreadlord_chris on 2007-06-16
> **gauravp55 said:**
> Doesn't work!! In fact after adding splash I need to hit Ctrl+Alt+F1 again or else I get a blank screen!!

hmmm... that's odd - not sure what to tell ya then....

---

