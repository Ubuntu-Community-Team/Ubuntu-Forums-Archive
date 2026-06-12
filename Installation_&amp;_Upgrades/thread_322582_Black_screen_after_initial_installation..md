---
title: "Black screen after initial installation."
date: 2006-12-20
forum: Installation &amp; Upgrades
---

### Post by bsprowl on 2006-12-20
This is my first Linux installation.    

I installed 6.10 using the alternate disk onto my old 400 MHz Pentium II with a Intel SE440BX2 motherboard, 256MB of ram and a CD-Rom.  The 12 GB hard disk had only 3 GB in use.  I'll pulled all of the files I wanted to protect of of it.

After a  slow start (the CD-rom would not read my Ubuntu DVD - duhhh) I had a problem free installation until I got to the first boot after installing GRUB.

Chose the first option, Ubuntu, got the userid and password screen, entered those and got a black screen with just a white mouse pointer.  The pointer moves but nothing happens.

So now what?

Added: Booted into the recovery mode and got some text ending in "root@ubuntu1:~#" and a blinking cursor.  Is this the command line prompt?

Bob

---

### Post by K.Mandla on 2006-12-20
Hmm. If you got a pointer but nothing else, you might have some sort of video driver issue. It's odd that you get that much but nothing else. 

400Mhz is rather slow for Ubuntu. Have you tried Xubuntu? It might be a case where Gnome is so weighty that it's taking forever for the desktop to fire up. Still, kind of odd though.

What kind of computer is this? Is it an onboard graphics card, or a plugged-in card?

And yes, that's the command line prompt. If things are ever completely broken, that's where you go to try and minimize the damage. :biggrin:

---

### Post by bsprowl on 2006-12-20
I have a ATI Radeon AGP 9100 with 128 MB video card in this system.  It has nice, crisp display page for the sign on screen.

The disk drive is a Quantum Bigfoot, kinda slow if I remember the specs right.  Just checked them they are awful with a 15ms average seek time,  3600 RPM, and a 128 KB bufffer.

I let it run while I ate dinner and it still had a black screen.

---

