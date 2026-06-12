---
title: "What am i supposed to do with this .tar.bz2 file?"
date: 2007-09-24
forum: Installation &amp; Upgrades
---

### Post by kh1116 on 2007-09-24
i want this file to install (the tarball)
[http://hendrik.kaju.pri.ee/screenlets/?q=node/13](http://hendrik.kaju.pri.ee/screenlets/?q=node/13)

i would do it with the repository, but the server is down. what exact commands do i do to install this file? its downloaded on my desktop.

---

### Post by rsambuca on 2007-09-24
You first need to unpack the file to a directory:```
tar -jxvf <filename>
```
Then move to that directory and have a quick read through the install and readme files for a quick rundown.  Basically you will be running three commands.

./configure
make
sudo make install

You can also use 'sudo checkinstall -D' instead of the last command to make a .deb package which you can then click on to install.  The benefit of this is that it will then show up in your Synaptic Package Manager for easier updates and removal.

---

### Post by kh1116 on 2007-09-24
why am i getting this message?
```
kevin@kevin-desktop:~/Desktop$ sudo make install screenlets-0.0.10.tar.bz2
make: *** No rule to make target `install'.  Stop.
```

---

### Post by rsambuca on 2007-09-24
You have to do the tar command first!

Then move to the directory.

Then ./configure

Then make

Then sudo make install

---

