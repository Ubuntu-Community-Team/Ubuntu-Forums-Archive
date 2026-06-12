---
title: "AUTO 07 Fortran Compiler Installation"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by nabeels on 2009-12-16
Hello everybody
I'm currently working on installing AUTO 07 software which is based on continuation method and can be use as a tool to analyze dynamic system in many scientific fields. This version requires installation of Fortran 95 compiler for the ubuntu Linux environment. Can I know how and from where I can install the compiler of Fortran 95?
Do I have to search for it in the interent or it is available ubuntu website?
Below is the result for running the command ./configure
===========================================================

nabeels@ubuntu:~/Downloads/auto/07p$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking whether we are using the GNU Fortran compiler... no
checking whether  accepts -g... no
checking for Fortran flag to compile .f90 files... unknown
configure: error: Fortran could not compile .f90 files


===========================================================

Thank in advance for the help

---

### Post by mionescu on 2009-12-16
If you search for "fortran" in Synaptic, you will see the package gfortran with the description "The GNU Fortran 95 compiler". Install it and you should be good to go.

---

### Post by nabeels on 2009-12-16
> **mionescu said:**
> If you search for "fortran" in Synaptic, you will see the package gfortran with the description "The GNU Fortran 95 compiler". Install it and you should be good to go.

I found it and it status is "installed". I'm not sure why it can't seen by the software?!!!
Any idea?
Thanks for the help

---

### Post by mionescu on 2009-12-16
What version of Ubuntu and gfortran do you have? I have downloaded and compiled just fine Auto 07. I am using Ubuntu 9.10 with gfortran 4.4.1. I installed other libraries as well (motiff, and others described in the documentation) and it worked.

---

### Post by nabeels on 2009-12-16
> **mionescu said:**
> What version of Ubuntu and gfortran do you have? I have downloaded and compiled just fine Auto 07. I am using Ubuntu 9.10 with gfortran 4.4.1. I installed other libraries as well (motiff, and others described in the documentation) and it worked.

Thank you very much for the kind contribution
I'm using the same version as urs, i.e. 9.10 BUT not sure how to get the version of gfortran:confused:. This is the link I used to install Ubuntu 9.10: [http://www.ubuntu.com/getubuntu/download-wubi](http://www.ubuntu.com/getubuntu/download-wubi)
How did you install the other library? (motiff, and others described in the documentation)
Aren't they installed automatically when you install Ubuntu 9.10?
Regards

---

### Post by mionescu on 2009-12-16
I used Ubuntu since 6.04 and I only did ugrades on my computer. But it should not matter how you installed Ubuntu. I use Synaptic package manager (from the System menu) to install new software. It is more powerful than "Software Center". You just search for the library/program they suggest to install, mark it for installation and apply. You want to install the development packages as well (for example libmotif-dev) in order to compile the program (most of them have -dev attached to the name). Did you install the "build-essential" package? What version of gfortran do you have installed?

---

### Post by nabeels on 2009-12-16
> **mionescu said:**
> I used Ubuntu since 6.04 and I only did ugrades on my computer. But it should not matter how you installed Ubuntu. I use Synaptic package manager (from the System menu) to install new software. It is more powerful than "Software Center". You just search for the library/program they suggest to install, mark it for installation and apply. You want to install the development packages as well (for example libmotif-dev) in order to compile the program (most of them have -dev attached to the name). Did you install the "build-essential" package? What version of gfortran do you have installed?

Sorry for the silly questions, BUT how to install a new software from the Synaptic package.?
How can I know if the Fortran compiler is installed or not?:(
Are the development packages available in the Synaptic packages?
Thank you

---

### Post by mionescu on 2009-12-17
A good place to start is the Ubuntu help. You can find it also on the internet:
[https://help.ubuntu.com/9.10/add-applications/C/installing.html](https://help.ubuntu.com/9.10/add-applications/C/installing.html)
As I said, I use Synaptic which gives more flexibility. The installed packages are marked with green in Synaptic.

---

### Post by bfas on 2010-05-14
Hi mionescu,

(not 100% sure if my post fits the thread but here it goes)
I'm installing auto-07p (Ubuntu 10.04) and it seems that I didn't set my environment variables correctly, since when I type "auto" I get the "no command 'auto' found" message. Here is a copy of my .profile, could you give a look?

# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
	. "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

# 1st line introduced by ME: set environment variables to run AUTO
$HOME/auto/07p/cmds/auto.env.sh

Thanks,

---

### Post by mionescu on 2010-05-14
It seems fine to me. Try to add that line into .bash_profile as well.

---

### Post by bfas on 2010-05-17
Thanks for your reply.

I didn't find the file you mentioned still I figured out one solution (I post it for future occasions).

My home directory didn't have a bin subdirectory (I don't know if it's the Lucid's default structure, but it happened on both my laptop and my work desktop - both upgraded from 9.10). Because of that, and since the PATH definition was inside an If statement, it wasn't really defined. One possible solution (don't know if the best) is just to erase the if statement:

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

and define the path as follows:
PATH="$HOME/auto/07p/bin/:$PATH"

Probably one better solution would be to create a bin subdirectory in the home directory and add an additional line in the PATH's definition to include auto's binary (but still I have no experience on this stuff so...)

Rgrs

---

