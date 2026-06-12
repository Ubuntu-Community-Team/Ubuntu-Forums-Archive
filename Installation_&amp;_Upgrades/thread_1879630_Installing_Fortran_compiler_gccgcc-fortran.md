---
title: "Installing Fortran compiler gcc/gcc-fortran"
date: 2011-11-11
forum: Installation &amp; Upgrades
---

### Post by zerow33 on 2011-11-11
Hi

I am new to Linux and I just installed Lubuntu on an old machine (Intel Celeron 450MHz, with 255MB ram) with the alternate CD. What I wanted to do on this machine is to compile a Fortran 77 code so that I can use it on a cluster (which runs on Unix). However, I am having lot of problem with installing the compiler. Being the first time user on Linux, I have search through the web to figure out that I need to install g77 or gfortran. Now I got a copy of gcc-fortran-4.6.2.tar.bz2 on my desktop, but I have no idea on how to install it&#8230;&#8230;. I tried sudo apt-get install gcc-fortran-4.6.2 but that doesn&#8217;t work. What exactly do I need to do to get the fortran compiler install on my Linux system? By the way this Linux machine have no connection to internet.

Any help would be greatly appreciated and many thanks in advance.

The version of lubuntu that I have installed is 11.10

---

### Post by Rodney9 on 2011-11-12
> **zerow33 said:**
> Hi

I am new to Linux and I just installed Lubuntu on an old machine (Intel Celeron 450MHz, with 255MB ram) with the alternate CD. What I wanted to do on this machine is to compile a Fortran 77 code so that I can use it on a cluster (which runs on Unix). However, I am having lot of problem with installing the compiler. Being the first time user on Linux, I have search through the web to figure out that I need to install g77 or gfortran. Now I got a copy of gcc-fortran-4.6.2.tar.bz2 on my desktop, but I have no idea on how to install it&#8230;&#8230;. I tried sudo apt-get install gcc-fortran-4.6.2 but that doesn&#8217;t work. What exactly do I need to do to get the fortran compiler install on my Linux system? By the way this Linux machine have no connection to internet.

Any help would be greatly appreciated and many thanks in advance.

The version of lubuntu that I have installed is 11.10

I maybe not be much help here as I don't even know what fortran is.

However I know a little, sudo apt-get install gcc-fortran-4.6.2 wont work if you don't have a Internet connection, although I think there is some way of setting up a cd repository... [https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

The tar.bz2 just needs right clicking on it and it will offer to extract it for you, but I think you will hit dependencies problems.

It would be much, much easier to be connected to the net and use Synaptic.

Rodney

---

### Post by MG&amp;TL on 2011-11-12
I agree; it would be much easier to connect to web, but:

[http://packages.debian.org/search?keywords=gfortran&searchon=names&suite=all&section=all]("http://packages.debian.org/search?keywords=gfortran&searchon=names&suite=all&section=all") You can download it from there, but you will probably need to satisfy a load of dependencies. Download it on another computer, then do something a long the lines of this. Copy the files onto a memory stick, then transfer it onto the other computer:

```
sudo mkdir /mnt/usb
sudo mount /dev/sdb/ /mnt/usb
cp /mnt/usb/*.deb ~/
sudo dpkg -i *.deb
```

Although using the alternate install is not easy; why are you using it? There are good reasons, I'm just checking them. Also, I'm not familiar with the laternate install; do you have a desktop or is it a command-line?

---

### Post by amjjawad on 2011-11-12
I know what Fortran is but because I don't do programming, I have no idea how to install any programming language but I think some google search should come in handy.
I'll have a look and let you know :)

Thanks!

---

### Post by MG&amp;TL on 2011-11-12
> **amjjawad said:**
> I know what Fortran is but because I don't do programming, I have no idea how to install any programming language but I think some google search should come in handy.
I'll have a look and let you know :)

Thanks!

Just FYI, you don't install a programming language as such, you install a compiler which produces a program. You can produce (almost) identical programs with many different languages, but you need different compilers. Unless it's python or java or another interpreted language, but fortran isn't one. I'm googling too. :) 

for OP: Why do you want to run fortran without an internet connection anyway? I suppose if manually downloading stuff isn't helpful, you could see if you get a statically-linked gfortran and copy it to /usr/bin or something. IDK, just a thought.

---

### Post by MG&amp;TL on 2011-11-12
> **zerow33 said:**
> Hi
 Now I got a copy of gcc-fortran-4.6.2.tar.bz2 on my desktop, but I have no idea on how to install it&#8230;&#8230;. 

Reading between the lines a bit here...can you unzip the archive, then either:

a) post the output of:

```

#see what's in the folder for more info
cd <folder containing unzipped gfortran>
ls -a
```

or (gamble here):

b)
```

#autoconf system
./configure
make
sudo make install
```

or (this would be brill) post the README file in gfortran. If there is one.

---

### Post by Rodney9 on 2011-11-12
I downloaded the said file , two folders 

libgfortan
gcc

No read me files except gfortran.info , a little large to post here, line count is 16192


Rodney

---

### Post by MG&amp;TL on 2011-11-12
in libgfortran? Where did you get it from, apt-get source seems to get some sort of virtual package.

---

