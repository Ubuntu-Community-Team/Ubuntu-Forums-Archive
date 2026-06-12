---
title: "3 + Gb memory ?"
date: 2006-03-23
forum: Installation &amp; Upgrades
---

### Post by dextermovies on 2006-03-23
I tried to install ubuntu as well as other linux distros when I have 3 gb of memory installed on my pc, I also tried the live versions of all the distros I tried to install. None of them worked, but I removed 1 gb of memory and now all the linux distros run fine ... any reason for this ? I really to know why this is happening becaus  I am going to be upgrading and will be using 4 gb of memory after the upgrading ...

---

### Post by dermotti on 2006-03-23
My guess is the default ubuntu kernel is not enabled to run more than 1gb ram. You could compile your own kernel and flag the 1-4gn ram option and it should work fine.

**[http://ubuntuforums.org/showthread.php?t=84174&highlight=vanilla+kernel](http://ubuntuforums.org/showthread.php?t=84174&highlight=vanilla+kernel)**

Thats a howto.

---

### Post by Darkriser on 2006-03-23
dermotti, I installed Ubuntu 5.10 with 1.5GB RAM and works perfectly. The max. RAM limit is maybe a little bit higher ;)

---

### Post by frodon on 2006-03-23
I beleive that the i386 kernel can't manage more than 2Go of RAM memory, maybe it's the problem here.
You should use the i686 or k7 kernel depending on the processor you use.

---

### Post by nocturn on 2006-03-23
Hmm...  Maybe try a kernel that is specific to your processor instead of 386, or use an SMP kernel, they should have support for 4 GB I think.

---

### Post by dextermovies on 2006-03-23
ok thanks ... I am still new to linux .. so I am unsure about all  this stuff  ... and I used the 64 bit edition .. as I have an amd 64 processor

---

### Post by rmjokers on 2006-03-23
Another thing you might try is running memtest to make sure the other memory chip isnt bad.

---

