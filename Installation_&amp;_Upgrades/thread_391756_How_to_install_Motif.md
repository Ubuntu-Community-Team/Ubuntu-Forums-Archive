---
title: "How to install Motif"
date: 2007-03-23
forum: Installation &amp; Upgrades
---

### Post by Jubufreak on 2007-03-23
Hi everyone , i m sort of new to linux and i was wondering how can i get Motif to work on ubuntu....i used synaptic package manager to find suitable files....but it still doesnt work...i dont know...maybe it gets installed on the wrong directory....cos i was searching under /usr/X11R6 but there are only files like :
bin , include , lib which were there at the beggining....

Hmmm thanks for all ur help!

Cheers

---

### Post by zvacet on 2007-03-23
I don´t know if this is answer to your qestion,but
[http://www.opera.com/linux/docs/plugins/install/motif/]("http://www.opera.com/linux/docs/plugins/install/motif/")

---

### Post by jrusso2 on 2007-03-23
That won't work on Ubuntu.  Seems the library's needed for motif and not in the repository and the Debian ones are too old to work on Ubuntu.

I have tried but I have not found a solution to this problem.

Jeanette

---

### Post by zvacet on 2007-03-24
That is the way I installed Motif.Just take what you need.

---

### Post by Jubufreak on 2007-03-24
Hmm well i installed xlibs_dummy.deb package...but i dont know...it still doesnt work... (?)

---

### Post by Jubufreak on 2007-03-26
Well i finally got it to work...
Honestly i dont know what i did cos i was installing all sort of stuff, and in between i was running and testing if by any change i got it to work.

Basically what i think i done , so that i got it to work are the following things:

- first i installed files to auto make ... basicall i entered auto* in package manager and installed all the packages i was offered ( i m new to this so i really didnt know which to install and which not to install)
- then i installed alien tool to create *.deb file out of latest (i think openmotif-2.1.30-4_MLI.i386.rpm ... which i converted to openmotif-2.1.30-4_MLI.i386.deb)
- then i installed  	lesstif-0.95.0.tar.gz

I also had to do some sort of linking....(i dont know if that was neccessary but still)

root@coltrane >  cd /usr/local/lib/
        root@coltrane >  ln -s ../LessTif/Motif1.2/lib/libXm.a libXm.a
        root@coltrane >  ln -s ../LessTif/Motif1.2/lib/libXm.la libXm.la
        root@coltrane >  ln -s ../LessTif/Motif1.2/lib/libXm.so libXm.so
        root@coltrane >  ln -s ../LessTif/Motif1.2/lib/libXm.so.1 libXm.so.1
        root@coltrane >  ln -s ../LessTif/Motif1.2/lib/libXm.so.1.0.2 libXm.so.1.0.2
        root@coltrane >  ln -s ../LessTif/Motif2.0/lib/libXm.so.2 libXm.so.2

Because compiling was ok , but when i had run the program i got an error that libXm.so.2 is missing or no such directory etc.


So basically what i m wondering if someone can please check my steps...or correct them.

Thank you!

---

### Post by zvacet on 2007-03-26
On Motif.deb right click and install with Gdebinstaller.You will get the massage that you missing dependencies and will tell you wich ones.Just find that and install no matter how old they look.that is exact way I installed Motif and had troubles until find the way.Don´t use rpm file,because once you install you will see in synaptic that Motif is described as rpm file but convert to deb.Don´t give yourself hard time if you don´t have to.

---

### Post by Jubufreak on 2007-03-27
Ok i have a small question...where do i get Motif.deb file...i imagine its part of the package or is it stand alone well Motif.deb package (?)

(It not that important but still im eager to get the easyest way possible .... )

Thanks!

---

