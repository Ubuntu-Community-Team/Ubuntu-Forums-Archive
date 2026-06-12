---
title: "Need Advice from the experts!!!!!"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by rey1321 on 2010-05-17
Hi Guys,
I have a 160gb Hard Drive**, **I partitioned like this:

1.- First partition 16GB, ext4, mounted / I have my Lucid filesystem on this partition  and boot flagged.
2.-Second partition 112GB (extended- 110gb as /home, and 2gb as swap memory)

my disk list:
```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1946    15631213+  83  Linux
/dev/sda2            1947       15647   110053282+   5  Extended
/dev/sda5            1947        2274     2634628+  82  Linux swap / Solaris
/dev/sda6            2275       15647   107418591   83  Linux

```

 I have my system upgraded from Karmic 9.04(automatic  distro upgraded), but I have too many problems with this upgrade, (nvidia video card not working properly, I can't mount my mp3 player(sansa), and another issues with sounds, etc.)

Since I have a separate /home partition, and separate / partition, I would like to do a fresh install of lucid on my first partition (/dev/sda1), thinking of maybe it will fix all my problems with a fresh install from a Lucid CD,

MY QUESTIONS ARE:
1.--If I do a fresh install on /, will I be able to access my home folder on the extended partition?.

2.--If I do a fresh install on /, the Lucid installer will recognise my /home partition,
     or will install everything again?. (meaning another home folder), I don't want 2
     home folder, 
3.-- Am I going to have a permission problems between the fresh install and all my 
       stuff in /home partition?

Please any advice will be appreciated,
Thanks\\:D/

---

### Post by jbrown96 on 2010-05-17
You shouldn't have any problems. 
When you get to the partitioning section on the new install, choose manual.

Select your current / partition (/dev/sda1) and change to ext4 then choose to format it. Select your /home partition (/dev/sda6??) and choose ext4 (I'm guessing this is ext4, but you didn't say; make sure to choose the same type that it is) but MAKE SURE THAT FORMAT IS UNSELECTED!! Proceed with the install.


You might run into a permission problem in there is more than one user on the current system and you are not the first user. By default Ubuntu makes the first user have ID 1000. If you are not 1000 then you could have problems, but they are easily solved. Check on your current install with ```
cat /etc/passwd | grep $USER
``` I get > justin:x:1000:1000:justin,,,:/home/justin:/bin/bash and you can see that I am group 1000 and user 1000. If yours differ, then I can help you fix it.

---

### Post by rey1321 on 2010-05-18
Thanks Jbrown!
and yes, I'm the only user, and after running the
CAT code, it shows that I'm a 1000, so I shouldn't have any problem
with permissions.(by the way my /home is also ext4)

my other concerns is; if the installer is capable of seen that I already have a /home partition(with home folder)?  otherwise it will install everything in the first partition and probably I'll ended up with 2 home folder, 2 music folder, to doc folder, to video folder, etc. etc. 

since my first partition is 16GB, there is plenty room to install
everything on it. Im afraid that I gonna have a full system with home folder and everything in the firs partition, and my old /home folder in the second partition.

thanks

---

### Post by jbrown96 on 2010-05-18
Just to clarify on my earlier post. 

When you setup your /home partition. 
1) Set it as ext4
2) DONT FORMAT IT
3) Mount point is /home

You won't have any problems with duplicate /home folders. I've done this for the last 4 Ubuntu version; just be sure that you keep straight which partition is / and which is /home, so you don't format the wrong one.

---

### Post by rey1321 on 2010-05-20
Thanks , I kind of busy right now copying and pasting
my most important doc. from my /home folder, (just in case)
something goes wrong, and I will try this weekend, the fresh instal.

One last question, 
is there any aplicattion that i can copy
all my costum application to the new
fresh install??

you Know all my installed application?
I don't wanna go installing all of themm one by one (like avidemux, k9copy, deluge, etc etc.)

thanks

---

### Post by rey1321 on 2010-05-21
Thanks jbrown96!
I did the fresh install and it went smooth,
didn't solve my problem thou, mounting my sansa clip+
but at least I learned something new.

creating a separated /home keep you safe and you
can reinstall your system at any time, w/o loosing
you data.:P

thanks, now I gotto go back and try to mount my mp3 player:(
of course I will post in audio thread.:guitar:

---

