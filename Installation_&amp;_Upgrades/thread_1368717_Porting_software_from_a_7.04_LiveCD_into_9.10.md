---
title: "Porting software from a 7.04 LiveCD into 9.10"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by CodeTBone on 2009-12-31
Hey Guys,

So I bought this book "Hacking: The Art of Exploitation", by Jon Erickson(In case your curious :P).  It came with a LiveCD of Ubuntu 7.04 (Feisty I think) setup just for hacking.  I know that its just got a whole bunch of shell programs aimed at hacking,programming and examing code.  My assumption is that the book is aimed at people using windows exclusively with no Linux experience, and since I already have Ubuntu, why run off a LiveCD with nothing installed when I could in my already installed version of 9.10?

SO my question is, is there anyway I can port all the extra goodies included on this disc into my current file-system so that I can still follow along exactly with the book but be in my native installation rather than on a LiveCD?

Ive thought about copying the /bin without overwriting any 9.10 software, but am somewhat apprehensive of doing so I havent done it yet.

Thanks Guys, any help given is appreciated.

---

### Post by CodeTBone on 2010-01-02
Bump

---

### Post by Sef on 2010-01-02
I would look for the latest versions of the goodies.   The dependencies are not the same, so by trying to install them, it would worth more of a headache than it is worth.

---

### Post by CodeTBone on 2010-01-05
Thats what Ive been hearin, just gona work off the CD for the time being.

---

### Post by ic7805reg on 2012-03-08
> **CodeTBone said:**
> Hey Guys,

So I bought this book "Hacking: The Art of Exploitation", by Jon Erickson(In case your curious :P).  It came with a LiveCD of Ubuntu 7.04 (Feisty I think) setup just for hacking.  I know that its just got a whole bunch of shell programs aimed at hacking,programming and examing code.  My assumption is that the book is aimed at people using windows exclusively with no Linux experience, and since I already have Ubuntu, why run off a LiveCD with nothing installed when I could in my already installed version of 9.10?

SO my question is, is there anyway I can port all the extra goodies included on this disc into my current file-system so that I can still follow along exactly with the book but be in my native installation rather than on a LiveCD?

Ive thought about copying the /bin without overwriting any 9.10 software, but am somewhat apprehensive of doing so I havent done it yet.

Thanks Guys, any help given is appreciated.

CodeTBone, I bought the same book just a few days ago (newbie) and I can't copy any of the files to a USB drive. I don't have the root password - do you know it?

What a bit strange is if I type:
$ nautilus .
the file manager comes up but if I type:
$ sudo nautilus .
nothing happens except it asks my for the password.

It will let me copy files from the USB drive to Ubuntu 7.04 but I can't copy files from Ubuntu 7.04 to the USB drive.  Can you or anyone else please give me some help on this problem - thanks

---

### Post by lisati on 2012-03-10
> **ic7805reg said:**
> CodeTBone, I bought the same book just a few days ago (newbie) and I can't copy any of the files to a USB drive. I don't have the root password - do you know it?

What a bit strange is if I type:
$ nautilus .
the file manager comes up but if I type:
$ sudo nautilus .
nothing happens except it asks my for the password.

It will let me copy files from the USB drive to Ubuntu 7.04 but I can't copy files from Ubuntu 7.04 to the USB drive.  Can you or anyone else please give me some help on this problem - thanks

It might be better to wait for responses in your thread. And by the way, 7.04 is an old version of Ubuntu.

---

### Post by Iowan on 2012-03-10
> **lisati said:**
> It might be better to wait for responses in your thread....Especially since this 2+year old thread is closed.

---

