---
title: "Application Installation Error"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by rockxstar on 2008-10-28
So I recently installed Ubuntu(Hardy Heron) and as I was attempting to install a few applications, I kept getting the same error.
After Installing Linux I have already incurred a few errors, which were easily fixed by installing items that should have been included with the system on installation.
Every time I use the command: "./configure"
I get the error: "bash: ./configure: No such file or directory"
upon the code "ls" I recieve: 
```
desktop:~/awnextras$ ls
acinclude.m4  COPYING            Makefile.c-applet       po
AUTHORS       debian             Makefile.desktop-files  README
autogen.sh    helloworld-applet  Makefile.python-applet  README.contributors
awn-plugins   INSTALL            Makefile.schemas        src
ChangeLog     m4                 Makefile.vala-applet
configure.ac  Makefile.am        NEWS
```

If anyone knows why I am receiving a "No such file" error when I clearly have the "configure.ac" file in the directory please let me know.

Just to check, I also ran "make" and "make install"
to which both gave me errors:
```

desktop:~/awnextras$ make
make: *** No targets specified and no makefile found.  Stop.
desktop:~/awnextras$ make install
make: *** No rule to make target `install'.  Stop.
```

---

### Post by Partyboi2 on 2008-10-28
Have a Read of the INSTALL file it should tell you how to compile the program.

---

### Post by oldos2er on 2008-10-28
Computers are literalists; ./configure is not the same as ./configure.ac . Seeing as how there's an autogen.sh file, I'd probably run that after reading INSTALL and README.

---

### Post by Partyboi2 on 2008-10-28
If this is you first time compiling you will probably need to install build-essential package, so from a terminal install it by
```
sudo apt-get install build-essential
```

---

### Post by rockxstar on 2008-10-28
The Install file is no help, it simply tells me to run "./configure" "make" "make install"
I have tryed "./configure.ac" and get the response..
```
desktop:~/awnextras$ ./configure.ac
./configure.ac: line 1: syntax error near unexpected token `2.53'
./configure.ac: line 1: `SAC_PREREQ(2.53)'

```
and running the autogen.sh file i get
```
desktop:~/awnextras$ ./autogen.sh
./autogen.sh: 2: intltoolize: not found

```

---

### Post by rockxstar on 2008-10-28
I installed the build-essential package, and got the same errors.

---

### Post by Partyboi2 on 2008-10-28
Compiling can be a small headache at times, another way to install the awn extras is to open a terminal and[FONT=monospace]
[/FONT]```
echo 'deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main'  |  sudo tee -a /etc/apt/sources.list
echo 'deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main'  |  sudo tee -a /etc/apt/sources.list
```then
```
sudo apt-get update
```then install awn-core-applets-bzr
```
sudo apt-get install awn-core-applets-bzr
```

---

### Post by rockxstar on 2008-10-28
The last line gives me
```
The following packages have unmet dependencies:
  awn-core-applets-bzr: Depends: libawn0-bzr but it is not going to be installed
E: Broken packages
```

---

### Post by Partyboi2 on 2008-10-29
open a terminal and
```
sudo apt-get -f install
``` this should fix the broken package. You may need to completely install awn from that repos I posted previously.
try removing the one you currently have installed. If you installed it from the ubuntu repos use
```
sudo apt-get remove avant-windows-navigator
``` if you have installed it using [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main then use
```
sudo apt-get remove  awn-manager-trunk awn-extras-applets-trunk
``` then install it again 
```
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr
```

---

