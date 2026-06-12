---
title: "Configuration of Services that start during boot"
date: 2005-12-06
forum: Installation &amp; Upgrades
---

### Post by tomski on 2005-12-06
Hi all,
hope somone can help me.
I have breezy installed and need to stop certain services/scripts/progs from starting at boot time ie:

bluetooth support (i have no bluetooth devices)

i dont want to remove that functionality just stop it from loading at boottime/startup as i may get a device that needs this in the future
 so i need to know where/how to edit the startup procedure.

I know i can stop it by using ctrl+c when it tries to start but this is temporary & im not always in front of the box when it starts up, so there are resources being used on a service that is not needed!!

---

### Post by bonjun on 2005-12-06
check this [site]("http://doc.gwos.org/index.php/BreezyCust")

---

### Post by frodon on 2005-12-06
You should install [BUM]("http://www.marzocca.net/linux/bum.html")

---

### Post by MartinG on 2005-12-06
On Gnome you need to install BUM (boot-up manager), on KDE System Settings -> System Services (or, on command line: sudo kcmshell serviceconfig).

---

### Post by tomski on 2005-12-06
[QUOTE=bonjun]check this [site]("http://doc.gwos.org/index.php/BreezyCust")[/QUOTE]


Thanks bonjun that is exactly the advice i need particulary this :
[http://doc.gwos.org/index.php/Speed_up_boot](http://doc.gwos.org/index.php/Speed_up_boot)

i will also look at B.U.M. as that seems very easy, but i like to know what a gui is changing first so i know how to do the same via cli.
 so if all goes down the drain whilst im away i can at least ssh in and still get the job done.

cheers

---

