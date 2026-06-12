---
title: "make /make install not working for me?"
date: 2005-08-19
forum: Installation &amp; Upgrades
---

### Post by floyd27 on 2005-08-19
Hi.
up till now i have been ablr to install nothing from source....
I have tired and read but nothing..
when it comes to the "make" stpe it all falls apart on me.
i downloaded and extracted the files on the desktop.
i cd to the desktop and type make

roderick@ubuntu:~$ cd /home/roderick/Desktop
roderick@ubuntu:~/Desktop$ make
make: *** No targets specified and no makefile found.  Stop.
roderick@ubuntu:~/Desktop$ make install
make: *** No rule to make target `install'.  Stop.
roderick@ubuntu:~/Desktop$

i have no idea wht to do from here.
any help please

thanx

---

### Post by krusbjorn on 2005-08-19
You need to do "./configure" first.

---

### Post by floyd27 on 2005-08-19
Tried that before with no luck...

roderick@ubuntu:~$ ./configure
bash: ./configure: No such file or directory
roderick@ubuntu:~$ cd /home/roderick/Desktop
roderick@ubuntu:~/Desktop$ ./configure
bash: ./configure: No such file or directory
roderick@ubuntu:~/Desktop$

---

### Post by krusbjorn on 2005-08-19
Then did you extract the tarball and enter the directory? The files in a tarball usually are contained in a folder. When you extract it, you extract the whole folder into the current directory.

---

### Post by floyd27 on 2005-08-19
this is what i did.
1- downloaded to the desktop---------then termaial cd to desktop...
2 - bzip2 -d <file name>
3 - tar -xvf <file mane>

thats it.
then did the make 
but that doesnt work?
am i missing something

---

### Post by krusbjorn on 2005-08-19
[QUOTE=floyd27]this is what i did.
1- downloaded to the desktop---------then termaial cd to desktop...
2 - bzip2 -d <file name>
3 - tar -xvf <file mane>[/QUOTE]

4. ls (Check the name of the folder you just extracted.)

5. cd <name of folder>

6 ./configure
7 make
8 sudo make install
9 get coffee

---

### Post by az on 2005-08-19
Are the files you unpacked in the current directory?

type

ls

---

### Post by floyd27 on 2005-08-19
ok i just tried to add the fliue name to the directory and that worked, to do the conf..
however the make still does nothing..

checking for libpng... -lpng -lz -lm
checking for libjpeg6b... no
checking for libjpeg... -ljpeg
checking for perl... /usr/bin/perl
checking for Qt... configure: error: Qt (>= Qt 3.1 (20021021)) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.
roderick@ubuntu:~/Desktop/kaffeine-0.7$ make
make: *** No targets specified and no makefile found.  Stop.
roderick@ubuntu:~/Desktop/kaffeine-0.7$ sudo make
Password:
make: *** No targets specified and no makefile found.  Stop.
roderick@ubuntu:~/Desktop/kaffeine-0.7$

---

### Post by krusbjorn on 2005-08-19
To compile (make) you need to get through the ./configure without errors.

Do "sudo apt-get install build-essentials".

---

### Post by floyd27 on 2005-08-19
roderick@ubuntu:~$ sudo apt-get install build-essentials
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package build-essentials
roderick@ubuntu:~$





seems my problems just keep appearing????
I have the extra repositories? and the latest kde aswell if that helps..

---

### Post by floyd27 on 2005-08-19
roderick@ubuntu:~$ sudo apt-get install build-essentials
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package build-essentials
roderick@ubuntu:~$





seems my problems just keep appearing????
I have the extra repositories? and the latest kde aswell if that helps..

---

### Post by krusbjorn on 2005-08-19
Did you "sudo apt-get update" since you edited the sources.list file?

---

### Post by Velox Letum on 2005-08-19
[QUOTE=floyd27]roderick@ubuntu:~$ sudo apt-get install build-essentials
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package build-essentials
roderick@ubuntu:~$





seems my problems just keep appearing????
I have the extra repositories? and the latest kde aswell if that helps..[/QUOTE]
 If you have the extra repositories, try running *sudo apt-get update*.

---

### Post by ow50 on 2005-08-19
[QUOTE=floyd27]roderick@ubuntu:~$ sudo apt-get install build-essentials
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package build-essentials[/QUOTE]
It's not plural. The package name is "build-essential".

---

