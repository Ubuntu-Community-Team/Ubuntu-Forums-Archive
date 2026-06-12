---
title: "Boosting performance on slow computer"
date: 2005-02-01
forum: Installation &amp; Upgrades
---

### Post by ssyn on 2005-02-01
I'm very happy I found a solid working linux distro for my old laptop. Im really new to linux and have a few question on making my system run faster/smoother. To start off my laptop specs are:

[list]166mhz[/list] 
[list]64mb ram[/list] 
[list]2.1 gb harddisk[/list] 
Ubuntu runs without any problems, except that things go quite slow. I started 'system monitor' to see how my hardware responds to different actions. Memory seems okay, because i'm mostly using like 50-60%. But my cpu goes wild sometimes, even when im just moving a window around the screen my cpu goes up to 90% usage.

I installed Abiword (because Openoffice takes 5 minutes to start) but scrolling inside a document goes very slow, I mean very slow (almost impossible).

I was wondering how I could boost the performance of my system, ofcourse it will never run smooth like my 1800mhz will, but somewhat faster should be possible I guess. I've got a few thoughts on this:

[list]I've heard about Xfce 4.2, which is lighter than what ubuntu runs right now, but would it really make much difference?[/list] 

[list]How about uninstalling some application (like OpenOffice)? Or wouldnt make that thing faster?[/list]

[list]Any other tweaks to make the system more smooth?[/list]

Any help is appreciated, but please keep in mind that I'm really new :)

Thanks

Ps my laptop is not connected to the internet

---

### Post by hndrcks on 2005-02-01
Alas, I think you are not gonna wring much more from that laptop. XFCE may halp a little, but it won't be much. The only thing I see that might have a good chance of improving performance would be to expand the RAM; I expect you are taking a big swap hit with only 64. Unfortunately, two problems:

1. Likely you are limited to 96 / 128 MB of ram 
2. It will be ferociously expensive to upgrade.

I had the same problem at home - solution was to install Ubuntu on a 'white box' PC with wireless and use the laptop as a dumb terminal with PXES. Performance isn't so bad when the heavy lifting is transferred to the server...

PXES terminal client at pxes.sourceforge.net (there are boatloads of thin clients that can access VNC / GDM / Windows Terminal Services)

---

### Post by Buffalo Soldier on 2005-02-01
In GNOME Help (click at the life-jacket icon besides the evolution icon).

Go to: Desktop -> System Administration Guide -> Improving Perfomance.

---

### Post by az on 2005-02-01
I have pretty much the same laptop, I just have a bit more memory.

I recommend the thin client approach.  I bought a 16-bit pcmcia wireless card on ebay for fifteen bucks.

Otherwise, I do not use the ubuntu desktop but icewm and xfe (a file manager).  Firefox is a bit slow.  I use abiword but I guess I do not open large documents on this machine.

No, removing openoffice will not make your machine run faster, since it does not run until you launch it.  It does free up disk space to remove it, though.

---

### Post by ssyn on 2005-02-01
Hi, thanks for the fast replies. I got abiword working (way) better by switching of smooth scrolling. 

Buffalo Soldier: Very usefull, it runs slightly faster now. Is there any other toturial for making such tweaks ?

hndrcks & azz: I guess you mean the same thing right? But, I want to use my laptop on my way to school aswell (in the train), so I guess that aint't an option.

---

### Post by poofyhairguy on 2005-02-01
[QUOTE=ssyn]
[list]I've heard about Xfce 4.2, which is lighter than what ubuntu runs right now, but would it really make much difference?[/list] [/QUOTE]


I would say so. Its a LOT lighter than Gnome. Try it out, its easy to get!
[/QUOTE]

---

### Post by ssyn on 2005-02-02
I was already trying to install it. But the additional .deb files (where xfce depends on) I had to install had some depency problems, but i'll fix it.

Thanks for the reply.

[list]How about mini-ram? is that usefull for slow computers?[/list]

---

### Post by mirtux on 2005-02-02
Hi,
    you can try to improve perfomances using **blackbox **windows manager. I used it with my old laptop and it was surely faster than Xfce. You can find it in Warty repositories or here [http://blackboxwm.sourceforge.net/]("http://blackboxwm.sourceforge.net/") with tons of informations and addons.
  
  Regards,
  MC

---

### Post by Buffalo Soldier on 2005-02-02
[QUOTE=ssyn]Buffalo Soldier: Very usefull, it runs slightly faster now. Is there any other toturial for making such tweaks ?[/QUOTE]
Sorry, none that I know of. Anybody here have seen such tutorial? If I do come across one, I'll post it here.

---

### Post by ssyn on 2005-02-02
Mirtux: thanks for letting me know about blackbox. 

But I don't seem to be able to install it. I get this report when typing ./configure -->

```
koen@koenlaptop:~/blackbox-0.65.0 $ ./configure
creating cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... no
checking for cc... no
configure: error: no acceptable cc found in $PATH
``` 

What does it mean?

---

### Post by mirtux on 2005-02-02
[QUOTE=ssyn]Mirtux: thanks for letting me know about blackbox. 
        
        But I don't seem to be able to install it. I get this report when typing ./configure -->
        ```
koen@koenlaptop:~/blackbox-0.65.0 $ ./configure
        creating cache ./config.cache
        checking for a BSD compatible install... /usr/bin/install -c
        checking whether build environment is sane... yes
        checking whether make sets ${MAKE}... yes
        checking for working aclocal... missing
        checking for working autoconf... missing
        checking for working automake... missing
        checking for working autoheader... missing
        checking for working makeinfo... missing
        checking for gcc... no
        checking for cc... no
        configure: error: no acceptable cc found in $PATH
``` 
        What does it mean?[/QUOTE]
        Ok, first of all:
        the last three line indicate the lack of **C compiler** (gcc and cc). You must install it whatever thing you want to compile from scratch I think this is one of the most important program you must have in your linux box :cool:, for example for kernel recompiling. You can download it from Warty repositories using Synaptic. Be warned that is a quite big download (but sorry i don't remember how much).
  
  However if you want to avoid such things as compiling, since *blackbox* is available, you can take it also from Warty repositories, or with Synaptic or with apt.
   
   Regards,
   MC

---

### Post by ssyn on 2005-02-02
Thanks for the help,

But what I don't get is why I always have to get packages something depends on. My laptop is not on a internet connection so I have to manually install them all. But as I see it now:

Blackbox, for instance depends on package_a, package_a depends on package_b and _c, package _b depends on package _d and _e and _f and go on go on. Everything depends on each other, now i have to install like 40 packages that all depend on each other for just blackbox. There got to be a more simple option isnt there ? Something like a graphic installer with all packages inside it?

---

### Post by mirtux on 2005-02-03
Hi,
 unfortunately as far as i know there is no way in getting this without satisfying all the dependecies.... There is one possibility: not all the requirements are *stringent*. You can force to install one package with **dpkg --force** .... but it's difficult for me to predict the results....
  
  Regards,
  MC

---

