---
title: "How to setup Dual OS"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by breaker84 on 2007-06-29
i'm sorry if my question is too common...
i have read all the article in several website but i did not see the solution..
i am new in using linux OS...
actually there is no problem with the dual OS selection page..but after i uodate the OS..
the selection OS for Ubuntu was duplicate..

[[IMG]http://img412.imageshack.us/img412/9012/dualosls1.th.jpg[/IMG]](http://img412.imageshack.us/my.php?image=dualosls1.jpg)

so, i want to remove it...
can some one help me..
i know i must be something in the "sudo gedit /boot/grub/menu.lst"
but which line should i delete...

---

### Post by Tsen on 2007-06-29
The Ubuntu line isn't actually a duplicate, you just have two different kernels.  Basically, the core of the system has been upgraded, but you still have the option of booting with the old one.
Anyway, to get rid of it, just use the command you mentioned,
```
sudo gedit /boot/grub/menu.lst
```

Then delete the lines starting with 
```
title		Ubuntu, kernel 2.6.20-15-generic
```
and going until the line
```
initrd		/boot/initrd.img-2.6.20-15-generic
```

Basically, just remove the two paragraphs with 2.6.20.15 in them.

It's important to note, though--this doesn't actually do anything but make your boot menu look nicer.  The kernels are still present, you aren't actually deleting them or saving any space (other than three or four bytes from the text, but that isn't really a sizeable change).

Basically, don't worry about it, it's meant to be that way.

---

### Post by Lamez on 2007-06-29
looks like you already have a windows boot loader.

run dos and type this line fdisk /MBR

or type fixmbr in command prompt

---

### Post by Tsen on 2007-06-29
But he doesn't want to get rid of ALL the Ubuntu entries, only the old kernels.

---

### Post by breaker84 on 2007-06-29
mm...
yeh..
 i just want to remove the old kernal...
one more thing can we make some modification those kernal...
i mean to rename it all...??

thanks for your guide Tsen....

---

### Post by avalook on 2007-07-03
This works for me. First check what kernel (the oldest) you want to remove. it will have a number something like this: 2.6.12-10-386

Then open a terminal and type:

```
sudo aptitude remove linux-image-2.6.20-10-386
```

obviously replacing 2.6.20-10-386 with the number of the kernel you want to remove.

--Jean

---

