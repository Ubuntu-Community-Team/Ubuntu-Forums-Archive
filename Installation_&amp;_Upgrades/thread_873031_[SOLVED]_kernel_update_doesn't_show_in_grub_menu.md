---
title: "[SOLVED] kernel update doesn't show in grub menu"
date: 2008-07-28
forum: Installation &amp; Upgrades
---

### Post by glendavee on 2008-07-28
I recently upgraded to 2.6.24.19 and installed it using upgrade manager, but when I boot ...24.19 isn't listed in the grub menu, only ....24.18 and the earlier versions. Also if I use gedit to look at the grub listing in a terminal, I don't see any mention of version 24.19 . Does this mean I'm still running version 24,18, and if so, how do I get to run 24.19?

---

### Post by Potatoj316 on 2008-07-28
try this
```
uname -r
```
it will tell you what kernel version your using.  Arent there verions after 19 avaliable?  I think im using 20 (not on ubuntu at the moment)

---

### Post by glendavee on 2008-07-28
looks like I'm using version 2.6.24.18 generic.

davdavid@david-desktop:~$ uname -r
2.6.24-18-generic

I believe you are correct, version 2.6.24.20 is out there, but my update manager didn't find it??

---

### Post by Elfy on 2008-07-28
It's in proposed at the moment - but be aware that some have had problems, that said it's ok for me.

Is the -19 kernel actually in /boot if it is you could try to update grub

```
sudo update-grub
```

---

### Post by zvacet on 2008-07-28
@ g**lendavee**

How many kernels do you have installed?Go to the synaptic and in search box type **linux-image** and delete all kernels with lower number then  2.6.24.18 generic.Kernel 2.6.24-20 is from proposed so if you want it system>admin>software sources>updates>check proposed.Reload.After this you should be able to see and use 2.6.24-19 or 2.6.24-20.

---

### Post by glendavee on 2008-07-28
thanks, Forestpixie. Update-grub did the job. I'll stick with 2.6.24.19 for the moment

---

### Post by Elfy on 2008-07-28
glad to help - can you mark thread solved please

---

