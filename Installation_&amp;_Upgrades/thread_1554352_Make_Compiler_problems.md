---
title: "Make Compiler problems"
date: 2010-08-16
forum: Installation &amp; Upgrades
---

### Post by Kangarooo on 2010-08-16
programm i want to install is rarcrack following instructions [http://www.ubuntu-unleashed.com/2008/04/howto-crack-rar-7z-and-zip-files-with.html](http://www.ubuntu-unleashed.com/2008/04/howto-crack-rar-7z-and-zip-files-with.html)
installation hgot from sourceforge same version as in instructions there was the only one
```
tar xvjf rarcrack-0.2.tar.bz2
cd rarcrack-0.2
sudo apt-get install libxml2-dev
make ; sudo make install
```
didnt work got many errors
installed autoconf automake
didnt help but less errors

installed build-essentials
on make getting error more less errors
```
rarcrack-0.2$ make ; sudo make install
gcc -pthread rarcrack.c `xml2-config --libs --cflags` -O2 -o rarcrack
rarcrack.c: In function ‘crack_thread’:
rarcrack.c:206: warning: comparison between pointer and integer
rarcrack.c:205: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
rarcrack.c: In function ‘init’:
rarcrack.c:283: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘char (*)[300]’
rarcrack.c:317: warning: ignoring return value of ‘fscanf’, declared with attribute warn_unused_result
install -s rarcrack /usr/bin
mkdir -p /usr/share/doc/rarcrack
chmod 755 /usr/share/doc/rarcrack
install -m 644 -t /usr/share/doc/rarcrack CHANGELOG LICENSE README README.html RELEASE_NOTES

```
btw in help theres line // you need gcc or any C compiler (edit Makefile CC=YOUR_C_COMPILER)
what then is my compiler? do i need to change that?

---

### Post by realzippy on 2010-08-17
Edit: gcc should be installed when installing build-essential


BTW,there is a .deb file which you could try if compiling still not works:

[rarcrack_0.2-1_i386.deb]("http://files.myopera.com/mazwarbz/blog/rarcrack_0.2-1_i386.deb")

Edit2,BTW:

generally it is  a good idea to install for compiling besides **build-essential**

[B]libtool cmake
[/B]

---

