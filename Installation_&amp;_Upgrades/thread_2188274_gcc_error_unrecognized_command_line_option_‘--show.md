---
title: "gcc: error: unrecognized command line option ‘--showme:link’"
date: 2013-11-16
forum: Installation &amp; Upgrades
---

### Post by ajitnair90 on 2013-11-16
I was asked to install certain packages, when opening the terminal. After installing those packages, when i opened the terminal it showed _**gcc: error: unrecognized command line option ‘--showme:link’**_ , can you please help me with this. And i am a beginner, so help me with some steps. And one more error which i got when i was working openfoam

                                                 _** blockMesh: error while loading shared libraries: libmpi.so.0: cannot open shared object file: No such file or directory**_

I felt both the errors are linked :confused:. Can anyone kindly help to resolve these issues as soon as possible :(.

---

### Post by steeldriver on 2013-11-16
Hello and welcome to the forum

You will likely get help quicker if you explain what "certain packages" you installed, and the exact steps you made (e.g. editing your ~/.bashrc) - if you were following online instructions, post a link to them

---

### Post by ajitnair90 on 2013-11-17
The packages which i was asked to install were,

sudo apt-get install libopenmpi1.6-dev
sudo apt-get install libopenmpi-dev
sudo apt-get install libmpich2-dev
sudo apt-get install libmpich1.0-dev
sudo apt-get install libmpich-mpd1.0-dev
sudo apt-get install libmpich-shmem1.0-dev
sudo apt-get install lam4-dev
These packages were shown as missing in the first lines of terminal, when i opened the terminal.And is there any link between the first error anf 2nd which i had mentioned in my post.

---

### Post by loalaa2 on 2014-01-10
> **ajitnair90 said:**
> I was asked to install certain packages, when opening the terminal. After installing those packages, when i opened the terminal it showed _**gcc: error: unrecognized command line option ‘--showme:link’**_ , can you please help me with this. 
In order to solve this problem, you should check this link:
[http://www.openfoam.org/download/ubuntu.php](http://www.openfoam.org/download/ubuntu.php)

Typing:
```
 sudo update-alternatives --list mpi 
```

If your system has MPICH libraries, you will see two lines, the second one is the MPICH path in where it was installed.
In order to fix the problem, typing:
```
 sudo update-alternatives --set mpi /usr/lib/openmpi/include 
```

Regards.

---

