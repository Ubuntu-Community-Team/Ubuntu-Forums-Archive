---
title: "No Desktop Effect"
date: 2009-09-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2009-09-08
Hi,

I am not able to use desktop effect. First it just said that desktop effect could not be enabled now it is able to enable but desktop effect makes my computer sluggish. Please help. I am using Dell Inspiron 6400/E1505.

Regards,
SK

---

### Post by Shibblet on 2009-09-08
I don't know where Karmic is for graphics drivers, but does your Inspiron have an intel graphics adapter?

Secondly, try running compiz-check, that usually works for me.

---

### Post by steeleyuk on 2009-09-08
Yes, the 6400 has an Intel graphics chip. I'll have a check on mine in a minute, see if I have the same problems...

---

### Post by TrueTom on 2009-09-08
Check for a process called 'gconfd-2'. If it's using a lot of CPU time, kill Metacity...

---

### Post by steeleyuk on 2009-09-08
Just had a quick play now, everything seems to be OK on my laptop. Compiz running well, even the cube is playing nicely with decent performance... something I couldn't say about Jaunty.

---

### Post by donniezazen on 2009-09-08
When i enable my desktop effect my computer gets so slow that it hangs.

This is my compiz-check result

Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

Thanks a lot guys-
SK

---

### Post by Shibblet on 2009-09-08
> **steeleyuk said:**
> Just had a quick play now, everything seems to be OK on my laptop. Compiz running well, even the cube is playing nicely with decent performance... something I couldn't say about Jaunty.

I have an Inspiron 1545, and an MSI Wind U100.  Both of which have Intel Grpahics chipsets.  I am anxiously awaiting the release of Karmic Koala.  

But I can't ever pull myself to play with Alpha-bits.  So, I wait... impatiently... but I wait.

I will say this about Canonical though, they have a time frame.  I really want to give Moblin a whirl on my Netbook, but they've been in beta for a while, and have no discernible time frame.

---

### Post by donniezazen on 2009-09-08
> **TrueTom said:**
> Check for a process called 'gconfd-2'. If it's using a lot of CPU time, kill Metacity...

gconfd-2 seems to be the problem. But how to kill metacity. my system becomes unusable when i enable desktop effect.

Thanks,
SK

---

### Post by loweehahn on 2009-09-27
My desktop effect works. But last time when I was using 8.10 the fading effect (when you open or close a window) was smooth but after I upgraded to 9.04 the effect is not smooth any more.

---

### Post by andrewabc on 2009-09-27
> **loweehahn said:**
> My desktop effect works. But last time when I was using 8.10 the fading effect (when you open or close a window) was smooth but after I upgraded to 9.04 the effect is not smooth any more.

What is your computer specs?
If you have intel video, the reason is because they screwed up intel graphics for 9.04. It is fixed for 9.10

---

### Post by NCLI on 2009-09-27
> **soham_1207 said:**
> gconfd-2 seems to be the problem. But how to kill metacity. my system becomes unusable when i enable desktop effect.

Thanks,
SK
Try running 

metacity --replace

and then

compiz --replace

---

