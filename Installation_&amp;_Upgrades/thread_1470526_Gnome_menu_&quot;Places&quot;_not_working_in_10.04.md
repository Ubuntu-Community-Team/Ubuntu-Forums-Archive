---
title: "Gnome menu &quot;Places&quot; not working in 10.04"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by Molydeus on 2010-05-02
I just upgraded from 8.04 to 10.04. Almost everything works great.

However the gnome menu "Places" home folder. home .documents, music, pictures and videos does not open up Nautilus. I get the error "Could not open location 'file:///home/tom'"

This should be an easy fix but I am lost.

I also am having an issue with Alt-F2 not opening up the run command. I might be having an issue with key board layout.

Thanks for any help.

Molydeus

---

### Post by Molydeus on 2010-05-02
I fixed the ALT-F2 issue. I just had to set Gnome Compatibility in CompizConfig Settings Manager.

---

### Post by myvilica on 2012-01-18
I have the exact same problem and cannot figure it out.
Nautilus is working, but i cannot open the folders directly from places.
Have you solved the problem?
Thanks, 

Marko

---

### Post by dino99 on 2012-01-18
into a terminal:

sudo dpkg-reconfigure -phigh -a
( can take a while, dont stop it before it end itself)

---

### Post by myvilica on 2012-01-19
Thanks.
I have solved the problem. I'va noticed that installing Thunar (sudo aptitude install Thunar) solved the association (with Thunar not Nautilus) so i change the association the soft way (ubuntu tweak), but it was a mater of one association (i was able to open my disk, folders and all in Nautilus, but not the panel stuff). What does actually the code you have provided do? It reconfigures what? (I'm not that good at coding, but I'm learning)
Thanks,

Marko

---

