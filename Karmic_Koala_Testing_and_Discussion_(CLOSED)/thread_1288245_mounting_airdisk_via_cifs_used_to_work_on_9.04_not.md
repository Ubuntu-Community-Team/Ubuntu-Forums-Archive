---
title: "mounting airdisk via cifs used to work on 9.04 not on 9.10"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by neoneddy on 2009-10-11
I should clarify, it appears to work, but in a useless way.

in my ftsab I have 
> //10.0.1.1/Home /airdisk cifs password=*****

I'm doing a fresh 9.10 beta install.

it mounts fine, no errors, however if I do an ls command on the mount point it shows nothing.  However if I cd into a directory I know is there, it works, and if I do an LS there, again nothing.

As best I can tell the airdisk mounts fine, but something is stopping it from listing the contents.

my 9.04 install was from an old 8.04 install, been upgraded and was acting, funny decided to rebuild.  Regretting it a bit now, might roll back to 9.04.. any ideas?

Below is some oft he commands I threw at it, I even did one I knew was not there, and it did show that directory did not exist.

> //10.0.1.1/Home on /media/airdisk type cifs (rw,mand)
shawn@MyhthTV:/media/airdisk$ ls
shawn@MyhthTV:/media/airdisk$ cd Music
shawn@MyhthTV:/media/airdisk/Music$ ls
shawn@MyhthTV:/media/airdisk/Music$ cd ..
shawn@MyhthTV:/media/airdisk$ cd Movies
shawn@MyhthTV:/media/airdisk/Movies$ ls -a
.  ..
shawn@MyhthTV:/media/airdisk/Movies$ ls
shawn@MyhthTV:/media/airdisk/Movies$ cd nothing
-bash: cd: nothing: No such file or directory

---

### Post by bapoumba on 2009-10-11
Moved to karmic.

---

### Post by neoneddy on 2009-10-19
It worked for a few brief moments, now nothing again, bleh.

---

