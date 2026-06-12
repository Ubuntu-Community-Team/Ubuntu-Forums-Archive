---
title: "cant do mem test????"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by letitworknow on 2007-05-29
when i do a memtest i get a message that says     

error 28 selected item cannot fit into memory

any ideas ????

---

### Post by earobinson on 2007-05-29
Spam

---

### Post by letitworknow on 2007-05-29
everything is brand new never been hooked up to the net

---

### Post by dve on 2007-06-21
I have the same problem. Googling it points to the new grub being too large. However I haven't been able to solve it either

EDIT: Sorry, "grub too large" was nonsense from other forum. The grub can load 1.3M vmlinuz so there is space. Something else is wrong here.

Juha

---

### Post by dreaswar on 2008-07-20
Hi, 
im having the same problem
I run a dual bot with Xp. 
My computer has two hard disks and Ubuntu 7.10 is on the second.

it has been working fine and last week .. i dunno what happened.. while booting, Grub loads allright. Then the Ubuntu graphic with progress bar appears and then stops progressing.

I ran the Memtest to recieve the error that its too large to fir in memory.

i ran recovery mode and it took a long time .. as figures kept scrolling past .. i waited for an hour before shutting down as it never seemed to end. Is this the way the recovery mode behaves?? I have never tried it before !!  

the grub shows two kernels now). Both dont boot                       ( generic/recovery). Xp boots all right. 

What could be wrong??
I have tried Super grub Disk... no sucsess

Please help.
thanks.

---

### Post by dreaswar on 2008-07-21
hi,
just a day after posting the error i had worked on it and one solution worked. 

it had been a problem with the hardware(RAM)
Just took it out .. sort of cleaned it and dusted it and put it back on. 

that worked . 

I started to have suspicions as my Ubuntu live cd and and other linux cds wont boot also and they also seemed to stuck in the same place in the progress bar as the Ubuntu disk install did when booting up. 

i did a verbose mode in the boot option and found it was getting stuck at the "Loading Hardware Driver" stage. 

Strangely though Windows Xp worked and CD and DVD drive also worked with Xp. Strange.... if the RAM was at fault it should have affected both OS's similarly. i wonder why.. 

Also when i finaly logged on to ubuntu it said previous update has been interrupted and it gave a few errors. I then did a complete update. Could this have lead to the booting problems?


now everything is all-right though. 

thanks

---

