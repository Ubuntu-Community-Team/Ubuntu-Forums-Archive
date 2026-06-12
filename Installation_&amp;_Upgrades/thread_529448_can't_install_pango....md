---
title: "can't install pango..."
date: 2007-08-19
forum: Installation &amp; Upgrades
---

### Post by penguinux on 2007-08-19
hey!
I can't install pango !!
I need to install it in order to install gtk +
but when I compile pango this is the error I get

configure: error:*** didn't find any of freetype, x11, atsui or win....

i install freetype but I am still getting this error.
can someone help me out?

I am actually tying to install xfce4 but it has taken me all the way here :(
hope you guys can help.

---

### Post by penguinux on 2007-08-19
okay guys!
seems like I had to install libx11-dev in order to install pango
so, I just used the "sudo apt-get install libx11-dev" 
and that fixed the problem :)

---

### Post by penguinux on 2007-08-19
jesus !
this is insane I had to install all this inorder to install gtk on ubuntu 

a)Install xlib-dev-1.7.1.1ubuntu6.2 from SPM
b)Install libxrender-dev-1.0.9.10ubuntu1 from SPM
c)Install libpng-1.2.16 for Cairo from [http://sourceforge.net/project/showfiles.php?group_id=5624](http://sourceforge.net/project/showfiles.php?group_id=5624)
d)Install zlib-1.2.3. for Cairo [http://sourceforge.net/project/showfiles.php?group_id=5624](http://sourceforge.net/project/showfiles.php?group_id=5624)
e)Install cairo
f)Install fontconfig-2.4.2 for pango from [http://packages.debian.org/stable/utils/fontconfig](http://packages.debian.org/stable/utils/fontconfig)
g)Install pango
h)Install atk
i)Install gtk

---

### Post by penguinux on 2007-08-19
okay!
i haven't completely installed gtk+
but I am getting real close!

now i can't install Cairo!!!!!
i am getting the same error I was getting when trying to install pango!!!
configure error: cairo requires at least one font backend.
please install freetype and fontconfig

they are allready installed!!!

---

### Post by penguinux on 2007-08-19
okay 
figure out an easier way to install cairo :)

sudo apt-get install libcairo2-dev

---

### Post by penguinux on 2007-08-19
okay all this is bs
I just had to use this command to install gtk+ 
 sudo apt-get install build-essential  libgtk2.0-dev

---

### Post by penguinux on 2007-08-19
what an idiot!
i just had to use this command to install xfce4

sudo aptitude install xfce4

problem fixed!

---

### Post by narenvenkat on 2007-08-23
thnx bro ,got good help from ur narration of installation

thnku very much 

:lolflag:

---

### Post by W8eR_CZech on 2007-11-04
what's thah xlib library? I didn't find like that. I'm offline, so apt-get doesn't help. Thanx for help in advance

---

### Post by fiqbal on 2008-05-17
:KS:KS:KS:KS:KS:KS

Marvolous... This thread really solved my prob.... many thanks to pangunix:)

---

