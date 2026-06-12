---
title: "Intrepid 8.10 install/boot bug."
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by theduffman on 2008-10-18
After installing 8.10 beta in vmware using guided partitioning it booted fine.  so i thought i`d try it out on my laptop for real.  
Installed using alternate x86 and used this partion scheme
/boot = 150MB
/ = 4.5 GB
swap = 1.1 GB
/rest = 40 GB

8.04 installs fine with this partitioning scheme btw..

installs ok then comes to boot for the first time and i get this.

[IMG]http://www.duffydack.karoo.net/boot810.jpg[/IMG]

---

### Post by cariboo on 2008-10-18
Could you post the output of:

```
sudo fdisk -l
```

This will help determine what your boot partition is.

Jim

---

### Post by theduffman on 2008-10-18
love to, but, 1: I cant boot into it, and 2: i dont have it installed anymore.
I can see that it`d be an error in grubs menu.lst pointing to the boot partition or something, but still, its a bug in 8.10 installer, so thought i`d point it out..
I will hold off 8.10 till final

---

### Post by Rocket2DMn on 2008-10-18
Moved to Intrepid Ibex Testing and Discussion

---

