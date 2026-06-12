---
title: "installing tar.gz?"
date: 2007-08-28
forum: Installation &amp; Upgrades
---

### Post by higashi on 2007-08-28
I have never before installed a tar.gz file. I searched google and forums for around 2 days now and I finally found [this tutorial]("http://www.tuxfiles.org/linuxhelp/softinstall.html"). Everything was going well until the "make" or "make install" part. I'm trying to install 2 files at the moment: lives-0.9.8.6 and Ktoon-0.8. What should I do??
PS: when I type "make", it says something like no target specified and no makefile found... so I tried stuff like "make ktoon-0.8" and "make install" but it didn't work. (I did get the build-essential thing)

---

### Post by dreadlord_chris on 2007-08-28
> **higashi said:**
> I have never before installed a tar.gz file. I searched google and forums for around 2 days now and I finally found [this tutorial]("http://www.tuxfiles.org/linuxhelp/softinstall.html"). Everything was going well until the "make" or "make install" part. I'm trying to install 2 files at the moment: lives-0.9.8.6 and Ktoon-0.8. What should I do??
PS: when I type "make", it says something like no target specified and no makefile found... so I tried stuff like "make ktoon-0.8" and "make install" but it didn't work. (I did get the build-essential thing)

what happened when you started with:
```

./configure

```
If you *did* start with that, *and* _make_ doesn't work - then there must have been some errors output from _configure_

---

### Post by 13warrior on 2007-08-28
i guess you mean to say extract tar.gz file.

The command is 

```
tar -zxvf filename 
```

or

```
tar -zxvf file -C path to where you want to extract
```.


Coming to second part ..
you can issue  inside the exctracted directory

```
./configure
```

then
```
make && make install 
```

---

### Post by higashi on 2007-08-28
Here's what it looks like:
```
me@my-desktop:~$ cd /home/me/ktoon-0.8
me@my-desktop:~/ktoon-0.8$ make
make: *** No targets specified and no makefile found.  Stop.
me@my-desktop:~/ktoon-0.8$ ./configure
scripts/global: line 52: -query: command not found
scripts/global: line 65: [: too many arguments
scripts/global: line 70: -query: command not found
 *  Using Qt:
 *  Checking for aspell... no.
 *  Checking for sound... no.
 *  Checking for gif... no.
 *  Checking for ffmpeg 0.4.9... no.
 *  Checking for ming... no.

**************************************
 *  KToon is configured, if you want to clean configuration, execute 'make -f Makefile.common confclean'
**************************************

me@my-desktop:~/ktoon-0.8$ make -f Makefile.common confclean
cd configure.tests 
cd configure.tests/ffmpeg && make clean && make distclean  
make[1]: Entering directory `/home/george/ktoon-0.8/configure.tests/ffmpeg'
make[1]: *** No rule to make target `clean'.  Stop.
make[1]: Leaving directory `/home/george/ktoon-0.8/configure.tests/ffmpeg'
make: *** [confclean] Error 2

```
:(

---

### Post by dreadlord_chris on 2007-08-28
there appear to be errors with configure - that being the case _make_ isn't going to work...

got a question for you though - why are you trying to compile an app that already exists in the repositories?

wouldn't it be much easier to:
```

sudo apt-get install ktoon

```

---

### Post by higashi on 2007-08-28
are you sure it's in the repositories?

```
me@my-desktop:~$ sudo apt-get install ktoon
password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ktoon
```

---

### Post by dreadlord_chris on 2007-08-28
it is in mine:
```

chris@HAL421:~$ sudo apt-get install ktoon
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  ktoon
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 2531kB of archives.
After unpacking 6316kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com gutsy/universe ktoon 0.8-1ubuntu1 [2531kB]

```
do you have all your repositories enabled? It's in the Universe repo....

---

### Post by louieb on 2007-08-28
Your not alone. Googled  **ktoon on Ubuntu **one of the developers replied to this thread [http://ubuntuforums.org/showthread.php?p=1817318](http://ubuntuforums.org/showthread.php?p=1817318) also there is a package in the Debian unstable repository. It is not in any of the official Ubuntu repositories.  That kinda strange because i found int here  [http://ftp.cica.es/pub/Linux/ubuntu/ubuntu/pool/universe/k/ktoon/](http://ftp.cica.es/pub/Linux/ubuntu/ubuntu/pool/universe/k/ktoon/)

---

### Post by rsambuca on 2007-08-28
> **dreadlord_chris said:**
> do you have all your repositories enabled? It's in the Universe repo....It's only in Gutsy repos, not Feisty.

---

### Post by dreadlord_chris on 2007-08-28
> **rsambuca said:**
> It's only in Gutsy repos, not Feisty.

LOL.... well, I guess that explains that....

the binary package can be downloaded here:
[http://download.berlios.de/ktoon/ktoon0.8-ubuntu6.06.tar.gz](http://download.berlios.de/ktoon/ktoon0.8-ubuntu6.06.tar.gz)

---

### Post by higashi on 2007-08-28
Look, I'm a real noob when it comes to installing things, and, no offence, but none of these replies really helped me...

I know where to download it, but it's the installing that's the problem.
Also, I wouldn't really mind if I don't end up getting ktoon, but I'm looking for the most simple to use animation tool... but not for animated gifs.. I mean like films. I already have synfig and gap (not that I know how to use it).

Well, thanks for your help so far

---

### Post by dreadlord_chris on 2007-08-28
the binary package from my last post requires no compiling - just download it , extract it, and run it....

here:
```

wget http://download.berlios.de/ktoon/ktoon0.8-ubuntu6.06.tar.gz
tar xzf ktoon0.8-ubuntu6.06.tar.gz
cd ktoon
./ktoon

```

---

### Post by higashi on 2007-08-28
wow thanks! Well, that solves my problem... ( I got packman which had lives in it)

well thanks for all your time and effort to help me ^____^

---

