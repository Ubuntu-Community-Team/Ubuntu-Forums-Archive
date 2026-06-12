---
title: "i want to see my drives"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by FaReSALandloS on 2007-08-16
[CENTER][SIZE=3]hello every body[/SIZE]
 
[SIZE=3]this is my first question[/SIZE]
 
[SIZE=3]i have windows xp and vista at my PC[/SIZE]
 
[SIZE=3]then i installed ubuntu as a new user [/SIZE]
 
[SIZE=3]and i do it [/SIZE]
 
[SIZE=3]the boot is working[/SIZE]
[SIZE=3]i have 3 OS [/SIZE]
 
[SIZE=3]but ubuntu can't see my HD[/SIZE]
[SIZE=3]i mean my windows HD Drives[/SIZE]
[SIZE=3]fat 32 or NTfs[/SIZE]
 
[SIZE=3]any help?[/SIZE][/CENTER]

---

### Post by merlinus on 2007-08-16
Welcome, but please do not use centered text.  It is easier to read if left-aligned.

When you say ubuntu cannot see your windows drives, do you mean vista does not come up on the startup menu?  

Or you cannot see them whilst running ubuntu?

-merlin

---

### Post by stchman on 2007-08-16
> **FaReSALandloS said:**
> [CENTER][SIZE=3]hello every body[/SIZE]
 
[SIZE=3]this is my first question[/SIZE]
 
[SIZE=3]i have windows xp and vista at my PC[/SIZE]
 
[SIZE=3]then i installed ubuntu as a new user [/SIZE]
 
[SIZE=3]and i do it [/SIZE]
 
[SIZE=3]the boot is working[/SIZE]
[SIZE=3]i have 3 OS [/SIZE]
 
[SIZE=3]but ubuntu can't see my HD[/SIZE]
[SIZE=3]i mean my windows HD Drives[/SIZE]
[SIZE=3]fat 32 or NTfs[/SIZE]
 
[SIZE=3]any help?[/SIZE][/CENTER]

Yes no center text.

You need to mount the drives via the fstab.

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

When you have finished editing your fstab type:

sudo mount -a

---

### Post by dansen926 on 2007-08-16
I'm no expert, but the easiest tool I found was "ntfs-config"

It's a nice program that will run from your linux desktop.

Installation is really easy, too. Just open up Konsole and type: sudo apt-get ntfs-config ...
and voila! You have it installed.

---

### Post by FaReSALandloS on 2007-08-18
> **merlinus said:**
> Welcome, but please do not use centered text.  It is easier to read if left-aligned.

When you say ubuntu cannot see your windows drives, do you mean vista does not come up on the startup menu?  



-merlin
ok no center again

that what i mean
Or you cannot see them whilst running ubuntu?

i can see  them now 
i don't know how
what ever
the new problem 
that i can't open any media like mp3

that is the message
> 
you do not have a decoder installed to handle this file. You might need to install the necessary plug

and thanks dansen926' stchman
for ur answer

---

