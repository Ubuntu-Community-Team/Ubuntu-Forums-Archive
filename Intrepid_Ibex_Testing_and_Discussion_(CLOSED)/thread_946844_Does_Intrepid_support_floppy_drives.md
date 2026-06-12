---
title: "Does Intrepid support floppy drives?"
date: 2008-10-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by phoenix_snake on 2008-10-13
Alright so I tried Intrepid beta on 2 machines and on both of them it didn't detect the floppy drives whereas hardy heron did!

so could this be a bug? :confused:

---

### Post by perlluver on 2008-10-13
> **phoenix_snake said:**
> Alright so I tried Intrepid beta on 2 machines and on both of them it didn't detect the floppy drives whereas hardy heron did!

so could this be a bug? :confused:

The kernel appears to have floppy support, however I am not sure, as I haven't ripped it apart.  Nor do I have a floppy drive.

---

### Post by phoenix_snake on 2008-10-13
yeah I found a few bug reports that have been triaged? does that mean developers don't give a crap?

---

### Post by perlluver on 2008-10-13
> **phoenix_snake said:**
> yeah I found a few bug reports that have been triaged? does that mean developers don't give a crap?

Not sure what that means.

---

### Post by Sef on 2008-10-14
> Alright so I tried Intrepid beta on 2 machines and on both of them it didn't detect the floppy drives whereas hardy heron did!

so could this be a bug?

Maybe when it's stable, your floppies will work.    

What do you need a floppy drive for?

---

### Post by Efros on 2008-10-14
[QUOTE=Sef]

What do you need a floppy drive for?[/QUOTE]


I hear they make wonderful noises when thrown against a wall! :-D

---

### Post by lukjad on 2008-10-14
I don't know about phoenix_snake, but I have a class that makes us test out the older forms of technologies.

---

### Post by Sef on 2008-10-14
> I don't know about phoenix_snake, but I have a class that makes us test out the older forms of technologies.

I have to use a floppy twice a year for work.  Have to put some reports on a floppy.

---

### Post by phoenix_snake on 2008-10-14
u see, I am setting up an older computer and I would like everything to work, I don't use it but so what? it should work shouldn't it? or does anyone here think just because it doesn't work I should probably convince my self I don't need it.

---

### Post by alienexplorers on 2008-10-14
Just open a terminal and type:
> sudo modprobe floppy
when done load the floppy drive using:
> sudo mount /dev/fd0 /media/floppy0

---

### Post by heavensblade23 on 2008-10-14
> **phoenix_snake said:**
> yeah I found a few bug reports that have been triaged? does that mean developers don't give a crap?

It means it's on the list to fix eventually.

---

### Post by phoenix_snake on 2008-10-14
> **heavensblade23 said:**
> It means it's on the list to fix eventually.

thanks for the first reply that actually helps, all the other posters were more like "if something on your machine convince your self it isn't important" :p

> 
Just open a terminal and type:

sudo modprobe floppy

when done load the floppy drive using:

sudo mount /dev/fd0 /media/floppy0


I will try this and reply, thanks.

---

### Post by heavensblade23 on 2008-10-14
> **phoenix_snake said:**
> thanks for the first reply that actually helps, all the other posters were more like "if something on your machine convince your self it isn't important" :p


Yeah, that's absolutely no excuse for hardware not working.

---

### Post by Slim Odds on 2008-10-14
> **Sef said:**
> I have to use a floppy twice a year for work.  Have to put some reports on a floppy.

You must work for the government.....

---

### Post by ktraglin on 2008-10-23
I want to thank you, as well.  For those of you who may not be aware, some motherboards (like mine) require a floppy to update the BIOS.  The only alternative would be to install Windows and use the Windows utility to do it.

---

### Post by Bert Mariën on 2008-10-29
Also, you can not make a backup boot floppy without a working floppy drive.:lolflag:

---

