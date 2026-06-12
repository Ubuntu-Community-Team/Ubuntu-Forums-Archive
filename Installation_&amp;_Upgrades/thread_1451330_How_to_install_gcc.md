---
title: "How to install gcc"
date: 2010-04-10
forum: Installation &amp; Upgrades
---

### Post by hmvartak on 2010-04-10
How to install gcc?

I've Ubuntu 9.10. gcc version is 4.4

I've tried this code
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```But no luck.

---

### Post by rtilson on 2010-04-10
try sudo apt-get install gcc...or search for gcc in synaptic package manager

---

### Post by takisan on 2010-04-10
What he said should work. I'd get both GCC and G++.

---

### Post by Sef on 2010-04-10
> How to install gcc?

I've Ubuntu 9.10. gcc version is 4.4

I've tried this code
 	Code:
 	sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential 
But no luck.

That only works, if I remember correctly, if you use the alternate cd.

>  		try sudo apt-get install gcc...or search for gcc in synaptic package  manager 	

Not quite correct.  One should update the repositories first, so one gets the most up-to-date applications.

```
sudo apt-get update && sudo apt-get install build-essential
```

---

### Post by partloer on 2010-04-10
I think this should be install by default.  You can check your version by

```
gcc --version
```

I think the latest version is 4.4.1

---

### Post by hmvartak on 2010-04-13
My version is 4.4.1

Whenever I try to compile program I get this error.

[IMG]http://img41.imageshack.us/img41/5373/screenshotdt.png[/IMG]

What else I need to do here?

---

### Post by lisati on 2010-04-13
I think conio.h is an ms-dos file which you don't need in Ubuntu. (Someone else will probably correct me if I'm mistaken)

---

### Post by hmvartak on 2010-04-14
Now it says unexpected "(".

[IMG]http://img91.imageshack.us/img91/9625/screenshotos.png[/IMG]

---

### Post by lisati on 2010-04-14
It would be better if you use copy and paste from your terminal, and wrap your code with [noparse]```
 and 
```[/noparse].

Instead of running the program with sh, type the following in at the terminal:
```
./a.out
```

---

### Post by hmvartak on 2010-04-14
> **lisati said:**
> It would be better if you use copy and paste from your terminal, and wrap your code with [noparse]```
 and 
```[/noparse].

Instead of running the program with sh, type the following in at the terminal:
```
./a.out
```
Now it's working. Thanks!

---

