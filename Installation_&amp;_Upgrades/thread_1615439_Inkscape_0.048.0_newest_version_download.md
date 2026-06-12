---
title: "Inkscape 0.048.0 newest version download"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by .35Whelen on 2010-11-07
I am having trouble compiling the newest version of Inkscape-0.48. I have downloaded the tarball to usr/local/src . It is the classic instruction:
./configure
make
make install

1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation.

Here lies my first error:

desktop:~$ cd usr/local/src
bash: cd: usr/local/src: No such file or directory

Variations on this yielded nothing


After doing searches on this topic it seems many people have difficulty with this process. So I don't feel like a complete moron. Funny thing is, I sell computers and software, design web pages and I can't download a freakin program. Funny:P

---

### Post by JOHNNYG713 on 2010-11-07
Are you running the commands in "root' terminal? or typing "sudo" before the command ?
sudo make, sudo make install

---

### Post by .35Whelen on 2010-11-07
Thanks JOHNNY
Yes, I am in terminal here are the variations :

desktop:~$ sudo cd /usr/local/src/
sudo: cd: command not found

desktop:~$ sudo cd /usr/local/src
sudo: cd: command not found

desktop:~$ sudo cd ./configure /usr/local/src
sudo: cd: command not found

desktop:~$ sudo ./configure /usr/local/src
sudo: ./configure: command not found

---

### Post by JOHNNYG713 on 2010-11-07
type cd sudo /then/your/path/ Try that!

---

