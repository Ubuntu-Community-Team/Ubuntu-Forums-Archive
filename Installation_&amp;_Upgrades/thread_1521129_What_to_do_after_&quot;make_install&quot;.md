---
title: "What to do after &quot;make install&quot;"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by pato wlmc on 2010-06-30
Well i installed a program, supose it's name is "myprogram"

So the base folder of the program is my desktop. So i did: ```
patowlmc@patowlmc-desktop:~$cd /home/patowlmc/Desktop/myprogram

patowlmc@patowlmc-desktop:~$ ./configure

patowlmc@patowlmc-desktop:~$  make

patowlmc@patowlmc-desktop:~$ sudo su

root@patowlmc-desktop:/home/patowlmc#  make install

```

Everything on the desktop.

But now what should i do with that folder? Move it?  if so, to where should i move it?

I's actually the first program i install this way so i don't really know what to do xD

Thanks for your answers, i'm really a newbie to ubuntu, so please don't be rude jeje

---

### Post by squaregoldfish on 2010-06-30
make install should have installed the program in the system directories (/usr/bin or /usr/local/bin), so you should be able to simply run the program from the command line.

You don't really need to keep the source directory any more, but I would suggest you keep it somewhere safe just in case you need it in the future.

Steve.

---

### Post by steveneddy on 2010-06-30
> **pato wlmc said:**
> Well i installed a program, supose it's name is "myprogram"

So the base folder of the program is my desktop. So i did: ```
patowlmc@patowlmc-desktop:~$cd /home/patowlmc/Desktop/myprogram

patowlmc@patowlmc-desktop:~$ ./configure

patowlmc@patowlmc-desktop:~$  make

patowlmc@patowlmc-desktop:~$ sudo su

root@patowlmc-desktop:/home/patowlmc#  make install

```

Everything on the desktop.

But now what should i do with that folder? Move it?  if so, to where should i move it?

I's actually the first program i install this way so i don't really know what to do xD

Thanks for your answers, i'm really a newbie to ubuntu, so please don't be rude jeje

First of all you didn't have to do

```
sudo su
```

because 

```
sudo <command>
```

executes the command with root privileges. What you just did was redundant.

I assume you meant the folder that came with the downloaded application. Delete the folder - the computer needs it no more.

---

### Post by pato wlmc on 2010-06-30
Thanks, both of you, problem solved jeje.

---

