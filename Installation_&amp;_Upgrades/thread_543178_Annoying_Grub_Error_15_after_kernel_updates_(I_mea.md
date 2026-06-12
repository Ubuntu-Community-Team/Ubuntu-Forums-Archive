---
title: "Annoying: Grub Error 15 after kernel updates (I mean Always)"
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by Prisma on 2007-09-04
Hello guys, I have a very annoying problem with Ubuntu 7.04. I am having the same problem every time I apply official updates of the kernel. this is how my boot/grub/menu.lst was before the last update: 

```
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=80b08035-b454-4a2f-a569-e341a7b24c92 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=80b08035-b454-4a2f-a569-e341a7b24c92 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

```


Now this is what looked like after the update:
```

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=80b08035-b454-4a2f-a569-e341a7b24c92 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=80b08035-b454-4a2f-a569-e341a7b24c92 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```

as you can see with every update ```
root		(hd0,5)
``` its automatically replace with ```
root		(hd0,6) 
``` and therefore grub always failed giving me error 15 and so its impossible to load Linux. The solution for me was to restart the computer with an Ubuntu disc. Access my computer's grub file and modify the menu.list file 

In terminal I typed: 

```
sudo gedit media/boot/grub/menu.lst
```

and then in gedit I replaced the lines```
 root		(hd0,6)
``` with```
 root		(hd0,5)
```

This problem is really annoying even though I know the solution, its tedious to do this every time an official update is ready for download. Does anybody knows if this is a known Bug? Or do you guys think I should fill a report?

Thanks.

---

### Post by Pumalite on 2007-09-04
You have to change the line in #groot= (hd0,5) for the kernel updates not to affect you.

---

### Post by Prisma on 2007-09-04
> **Pumalite said:**
> You have to change the line in #groot (hd0,5) for the kernel updates not to affect you.

Where is that line? #groot (hd0,5) is in the menu.lst?

Thanks

---

### Post by Prisma on 2007-09-04
this lines you mean?

```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)
```

Thanks

---

### Post by Pumalite on 2007-09-04
Yes; see my editing above.

# groot=(hd0,5)

---

### Post by Prisma on 2007-09-04
thank you man, I replaced this:

```
# groot=(hd0,6)
```

with this:

```
# groot=(hd0,5)
```

I hope i will not have any other problems in the future.

---

### Post by Pumalite on 2007-09-04
You are welcome. I hope it stays put.

---

