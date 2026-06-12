---
title: "ZSNES installation on Ubuntu 10.10 amd64"
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by BlacqWolf on 2011-02-05
Hello,

I would like to install ZSNES in Ubuntu 10.10 x64, however I cannot get it to run.

The one from the repository says it is not compatible with because I am running the wrong architecture operating system, and I do not wish to go back to Ubuntu x86.

I tried the version from the ZSNES website. I  couldn't figure out how to run it though, as it did not want to run. I tried the ZSNES.desktop, but it wouldn't do anything either. I tried running ZSNES.desktop in terminal, but it told me that it was the wrong architecture as well.

Any help would be much appreciated  :D

---

### Post by JackSchnippes on 2011-02-06
you should run zsnes from a terminal an see what error you get...

I just tried a debpackage from this site, but I get a segmentation fault when runnging zsnes: [https://rohieb.wordpress.com/2010/10/06/zsnes-on-amd64-ubuntu/](https://rohieb.wordpress.com/2010/10/06/zsnes-on-amd64-ubuntu/)

---

### Post by BlacqWolf on 2011-02-08
I tried running ZSNES in terminal any way I know. It told me I was running the wrong architecture. 

The text from the terminal is as follows:

/home/benjamin/zsnes_1_51/src/linux/zsnes.desktop: line 1: [Desktop: command not found
/home/benjamin/zsnes_1_51/src/linux/zsnes.desktop: line 5: syntax error near unexpected token `('
/home/benjamin/zsnes_1_51/src/linux/zsnes.desktop: line 5: `Comment=SNES (Super Nintendo) emulator that uses x86 assembly'

When I open ZSNES.desktop directly through nautilus, I get:

Details: Failed to execute child process "zsnes" (No such file or directory)

At the Desktop Properties window, I could see it was trying to run with command 'zsnes' as if it was installed just like any other application (I don't know if that would qualify as 'installed,' but the way you install an app like .deb or through software center). However, I do not know what file to change the command to, as I am fairly new to Linux. 

I do know that .sh are a type of executable file (I think), but every .sh (autogen.sh, install-sh) would not run. 'autogen' would run briefly, creating more files in the zsnes_1_51/src directory, I believe. However, I tried to run it again so I could paste the text here from the terminal, and all I got was

/home/benjamin/zsnes_1_51/src/autogen.sh: 6: sdl-config: not found
/home/benjamin/zsnes_1_51/src/autogen.sh: 6: aclocal: not found
/home/benjamin/zsnes_1_51/src/autogen.sh: 7: autoconf: not found
/home/benjamin/zsnes_1_51/src/autogen.sh: 17: ./configure: not found


I tried installing the .deb from your link, and I got

Dependency is not satisfiable: libao2 (>= 0.8.8)

but I cannot find it in the repos.

I ran configure.sh in terminal, I got

checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking for nasm... no
configure: error: You need NASM installed to compile ZSNES


So I think I know what we have to do here. (At least I hope I do.)

---

### Post by BlacqWolf on 2011-02-08
I tried configure.sh after installing NASM. This is the text from the terminal:


benjamin@ubuntu:~$ '/home/benjamin/zsnes_1_51/src/configure' 
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking for nasm... nasm
checking for sdl-config... no
checking for SDL - version >= 1.2.0... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: SDL >= 1.2.0 is required

And I could not find SDL anywhere. The only thing I could find is sdlbasic, which evidently did not work.

---

