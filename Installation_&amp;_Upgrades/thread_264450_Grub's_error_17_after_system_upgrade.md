---
title: "Grub's error 17 after system upgrade"
date: 2006-09-24
forum: Installation &amp; Upgrades
---

### Post by Gustavo Narea on 2006-09-24
Hello.

I installed Kubuntu on my laptop yesterday and everything was perfect... Until today, when I upgraded the system using synaptic: Now I get the famous error 17.

I've already read all of the threads that contain "error", "17" and "grub" in their titles, but nothing works. Here's what I've done so far:

1st try:
Using the (kubuntu) live cd:
```

$ sudo grub
grub> find /boot/grub/stage1
**Error 15: File not found**

```

2nd try:
Using the (kubuntu) live cd, after I realized my hard disk was at */dev/sda*:
```

$ sudo mkdir /mnt/hd
$ sudo mount /dev/sda1 /mnt/hd
$ sudo grub
grub> find /boot/grub/stage1

**Error 15: File not found**

grub> find /mnt/hd/boot/grub/stage1

**Error 15: File not found**

```

3rd try:
I edited the file */mnt/hd/boot/grub/menu.lst* to replace "root (hd0,0)" by "root (sd0,0)", but after reboot I was still getting the same error... Later I also tried "root (sd0,1)", but didn't work either.

What should I do? [-o< 

Thanks in advance!

---

### Post by Gustavo Narea on 2006-09-25
Any idea? ](*,)

---

