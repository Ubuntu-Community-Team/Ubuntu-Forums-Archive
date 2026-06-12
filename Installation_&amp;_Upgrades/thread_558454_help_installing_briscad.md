---
title: "help installing briscad"
date: 2007-09-24
forum: Installation &amp; Upgrades
---

### Post by Bethrine on 2007-09-24
I downloaded BRISCAD for Linux from their website...

[http://www.bricscad.com/](http://www.bricscad.com/)

 and it won't install. I can choose either RPM or TGZ, but have no idea what those are. It also says for Fedora or Red Hat. Can I run it in Ubuntu? Do I need to upgrade? Please help. Thanks!

---

### Post by zvacet on 2007-09-24
First of all install build-essential if you don´t have it instaled yet.

```
sudo aptitude install build-essential
```

Download TGZ file.Right click on it and choose **extract here**.That will create Briscard folder.Go inside of it 

```
cd /foldername
```

Read **Read me** and **install** file.

---

### Post by Bethrine on 2007-09-24
> **zvacet said:**
> First of all install build-essential if you don´t have it instaled yet.

```
sudo aptitude install build-essential
```

Download TGZ file.Right click on it and choose **extract here**.That will create Briscard folder.Go inside of it 

```
cd /foldername
```

Read **Read me** and **install** file.

Thanks! Build essential was already installed.  I have the TGZ downloaded on my desktop and read the read me including it's install section and libc is updated to 6 and wine is now installed and I am stuck again. How do I install the TGZ from my desktop, do I use wine? in the terminal? And then I assume I use the terminal with code "wine bricscad" to run it?

---

### Post by zvacet on 2007-09-24
If you want to run it with wine you need exe. file.You have TGZ file.I belive you need to compile it.
```
cd Desktop
```

Then go inside of folder

```
cd /foldername
```

foldername = exact bricscard folder name

1. ./configure
2.make
3.sudo make install

---

### Post by Bethrine on 2007-09-25
> **zvacet said:**
> If you want to run it with wine you need exe. file.You have TGZ file.I belive you need to compile it.
```
cd Desktop
```

Then go inside of folder

```
cd /foldername
```

foldername = exact bricscard folder name

1. ./configure
2.make
3.sudo make install

:~/Desktop$ ls
bricscad                            firefox.desktop  pidgin-2.1.1.tar.bz2
Bricscad-6.0.0020-1.en_US.i386.tgz  pidgin-2.1.1
:~/Desktop$ cd Briscad-6.0.0020-
bash: cd: Briscad-6.0.0020-: No such file or directory
:~/Desktop$ cd Bricscad-6.0.0020-1.en_US.i386.tgz
bash: cd: Bricscad-6.0.0020-1.en_US.i386.tgz: Not a directory
:~/Desktop$ cd /Briscad
bash: cd: /Briscad: No such file or directory
:~/Desktop$

I'm new to this so please bear with me, I need a little help here? :)

---

### Post by ali_bongos_dad on 2007-09-28
I got Bricscad working on Feisty by first installing Wine, Version: 0.9.41-0ubuntu2~feisty1 (wine), by using Applications > Add/Remove and selecting Wine.

Next I downloaded Bricscad-6.0.0021-1.en_US.i386.tgz to my desktop and checked the checksum.

Then right clicking on the downloaded file and selecting "Extract Here"
This created a folder "bricscad" on the Desktop.

To start Bricscad I opened the this folder and double clicked the shell script file "icad" and "Run".
then selected "Run Trial Version" and I was away, there was no need for
1. ./configure
2.make
3.sudo make install

---

