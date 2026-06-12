---
title: "Problem with a server with 8GB RAM"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by ricardo13 on 2010-01-06
Hi folks,

I'm trying to install UBUNTU SERVER 64 bits in a machine with 8GB RAM.
The problem's that not initialize !!! 
The BIOS recognize 8GB of RAM, but software (UBUNTU) doesn't !!!

Somebody have this problem ??

Ricardo

---

### Post by ricardo13 on 2010-01-06
I need you !!!
I need to solve this problem !!

Ricardo

---

### Post by ricardo13 on 2010-01-06
When I add the fourth memory card (2GB), ubuntu doesn't boot !!
It's work only 6GB !!

Ricardo

---

### Post by earthpigg on 2010-01-06
hi,

can you give us more detail?

does ubuntu install or boot up at all?

if so, please copy/paste the output of this command so we can see it:

```
free -m
```

and this one:

```
uname -a
```

---

### Post by ricardo13 on 2010-01-07
Hi,

I can add more 1GB, but 8GB doesn't boot !!

#free -m
             total       used       free     shared    buffers     cached
Mem:          6899       2338       4561          0          7        434
-/+ buffers/cache:       1895       5003
Swap:         9569          0       9569


#uname -a
Linux frontend 2.6.28-11-server #42-Ubuntu SMP Fri Apr 17 02:45:36 UTC 2009 x86_64 GNU/Linux

Thank you
Ricardo

---

### Post by ricardo13 on 2010-01-07
hi,

I added more 1GB, but 8GB doesn't boot !!

#free -m
             total       used       free     shared    buffers     cached
Mem:          6899       2338       4561          0          7        434
-/+ buffers/cache:       1895       5003
Swap:         9569          0       9569


#uname -a
Linux frontend 2.6.28-11-server #42-Ubuntu SMP Fri Apr 17 02:45:36 UTC 2009 x86_64 GNU/Linux

Thank you
Ricardo

---

### Post by earthpigg on 2010-01-07
interesting. try this:

put the potentially bad stick of ram in, and run [memtest86]("http://www.memtest86.com/")

---

### Post by ricardo13 on 2010-01-08
hi,

memtest+86 ran perfectly !!!
Any idea ??

Ricardo

---

### Post by earthpigg on 2010-01-08
can you show us what exact motherboard you have?

```
sudo lshw
```

this is the part we want:

```
  *-core
       description: Motherboard
       product: P6T DELUXE V2
       vendor: ASUSTeK Computer INC.

```

---

### Post by ricardo13 on 2010-01-14
Hi,

Sorry, I traveled and can't reply.

The output is:

*-core
       description: Motherboard
       product: P35C-DS3R
       vendor: Gigabyte Technology Co., Ltd.
       physical id: 0
       version: x.x

Ricardo

---

### Post by earthpigg on 2010-01-14
is it ddr2 or ddr3?

are you mixing and matching memmory types?

[http://www.gigabyte.us/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=2749&ProductName=GA-P35C-DS3R](http://www.gigabyte.us/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=2749&ProductName=GA-P35C-DS3R)

---

### Post by ricardo13 on 2010-01-19
I'm using only DDR2.
It's funny !! The machine doesn't work with 8GB, but works with 7GB !!

Thank you
Ricardo

---

