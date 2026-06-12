---
title: "install makemkv help"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by kevlar93 on 2010-03-28
I am trying to install makemkv 
[http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224](http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224)

I tried to intsall makemkv and I used the first command to install the tools and libraries. sudo apt-get install build-essential libc6-dev libssl-dev libgl1-mesa-dev libqt4-dev
I then try to use:
make -f makefile.linux
sudo make -f makefile.linux install

and I get:
kevin@kevin-desktop:~$ make -f makefile.linux
make: makefile.linux: No such file or directory
make: *** No rule to make target `makefile.linux'. Stop.
kevin@kevin-desktop:~$ sudo make -f makefile.linux install

I dl both files and extracted them in the download folder with the tar files. What am I doing wrong? I have never compiled anything before.

---

### Post by stlsaint on 2010-03-28
It looks like you are in your desktop dir instead of your download directory.

---

### Post by kevlar93 on 2010-03-28
how do i change that?

---

### Post by kevlar93 on 2010-03-28
ok so i changed the directory and i got it install and now I can not find it. After installing it I got:
rm -f /usr/bin/makemkvcon
rm -f /usr/bin/cddump
install -t /usr/bin bin/i386/makemkvcon

---

