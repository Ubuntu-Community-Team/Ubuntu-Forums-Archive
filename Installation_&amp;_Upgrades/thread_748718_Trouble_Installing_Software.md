---
title: "Trouble Installing Software"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by azurepancake on 2008-04-07
I am new to Linux and currently trying to learn the system thoroughly. Because of this, I am trying to force my self not to use GUIs too much, especially for downloading and installing software. I am having fun in the process and it's been quite an adventure so far.

So to my main problem. There have been a couple programs I've downloaded from the internet that I am trying to install and have had trouble doing so. Here is what I've been trying to do step-by-step.

1. Download .tgz package
2. Run tar xzvf package.tar.tgz
3. Navigate to decompressed directory
4. Run ./configure (returns **bash: ./configure: No such file or directory**)
5. Run make (returns **make: *** No targets specified and no makefile found.  Stop.**)
6. Attempt make install (returns **make: *** No rule to make target `install'.  Stop.**)

Excuse my ignorance, but I just lack the knowledge to go any further at the moment. If anyone knows what I am doing wrong or what my problem might be, I'd greatly appreciate it. The programs I am trying to install are both audio programs. [PaulStretch]("http://hypermammut.sourceforge.net/paulstretch/") and [Cryosleep]("http://cryosleep.yellowcouch.org/"). If you need anymore important information that I left out, just let me know.

Thanks

---

### Post by Pumalite on 2008-04-07
This might help:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by azurepancake on 2008-04-07
Hm, I just viewed the readme.txt file that came with the program and it states:

Requirements:
    - audiofile library
    - libvorbis
    - fltk library
    - portaudio library
    - libmad (for mp3 input)
    - not required, but you can use the FFTW library

Would not having one or more of these requirements result to my problem?

---

### Post by Pumalite on 2008-04-07
Do you have build-essential installed?
sudo aptitude install build-essential

---

### Post by azurepancake on 2008-04-07
Yeah, I actually installed this previously when I first started having the problem. 

I've noticed there doesn't seem to be any "configure" script for ./configure.

---

### Post by Pumalite on 2008-04-07
These tarballs come with a README file. Take a look for instructions on how to install.

---

### Post by Nameless_one on 2008-04-07
In the CryoSleep website is stated: 
> The first step is to download the software from the ftp site [ftp://cryosleep.yellowcouch.org/cryosleep/](ftp://cryosleep.yellowcouch.org/cryosleep/)
To compile the program the qt4 libraries and qt4 development files are necessary. The location of these programs should be placed in the defines file. Once this is done typing 'make' should suffice. To start the program start cryosleep in the current directory. There is currently no installation into the filesystem, the binary cryosleep is all that is necessary. When you started the program you can load one of the tubes found in the tubes directory. These are example sounds.

There is no configure script here, it seems. 

I also downloaded PaulStretch, and there are scripts (.sh files) to install it. There are two, I don't know the difference between them, but one of them should install the program (they mught have different rerequisites). 

Usually, programs for linux have 'configure' scripts and are built with make, but these don't seem to adhere to that standard.

---

