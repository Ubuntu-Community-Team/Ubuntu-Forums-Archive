---
title: "Upgrading From Gaim 2.0b3 To Gaim 2.0b5"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by compengi on 2006-12-09
I'm going to guild you through the upgrade from the original source file.

1. First of all you need to download software dependencies in order to compile a new Gaim 2.0b5 this is done by:

~$ sudo apt-get build-dep gaim

2. When dependencies are downloaded you need to download the original source of the gaim from: [http://sourceforge.net/project/showfiles.php?group_id=235&package_id=253](http://sourceforge.net/project/showfiles.php?group_id=235&package_id=253)

Note: You should download the source file which is either  	gaim-2.0.0beta5.tar.bz2 or gaim-2.0.0beta5.tar.gz

3. Now extract the package in your home folder, open your terminal and enter the extracted package using it. Now compiling steps begin:

a.The first step is to run a configure command:

~$ ./configure

b.Second step is to run make:

~$ ./make

c.The final one is to make install:

~$ sudo make install

Note: If you want to install Gaim in a specific directory you should do the following step:

~$ sudo make install DEST=/home/your/path/here

Now restart your Gaim and enjoy your new one.

---

