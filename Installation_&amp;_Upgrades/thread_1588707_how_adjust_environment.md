---
title: "how adjust environment"
date: 2010-10-05
forum: Installation &amp; Upgrades
---

### Post by ahmedo047 on 2010-10-05
I want to install gromacs-4.5.1 on ubuntu 9.04.

**1. I installed fftw-3.2.2 as following**
ab@ab-desktop:~/Masaüstü/ cd fftw-3.2.2
ab@ab-desktop:~/Masaüstü/fftw-3.2.2
ab@ab-desktop:~/Masaüstü/fftw-3.2.2 ./configure --enable-threads --enable-float
ab@ab-desktop:~/Masaüstü/fftw-3.2.2 sudo make
ab@ab-desktop:~/Masaüstü/fftw-3.2.2 sudo make install


**In this way, FFTW-3.2.2 installed /usr/local/include ****and  ****/usr/local/bin ****directories**-**-(I have root permissions to write there)**


**2. I installed gromacs-4.5.1 as following**                         
ab@ab-desktop:~/Masaüstü/gromacs-4.5.1 ./configure 
ab@ab-desktop:~/Masaüstü/gromacs-4.5.1 sudo make
ab@ab-desktop:~/Masaüstü/gromacs-4.5.1 sudo make install


**In this way, Gromacs-4.5.1 installed /usr/local/gromacs directory-(I have root permissions to write there)**


 I try running the following command,
$luck
there is error.
ab@ab-desktop:~/Masaüstü/gromacs-4.5.1 pdb2gmx -h

I've written the Gromacs Mail list before, but I get the answers as following:

**1**.In a normal Unix/Linux/Cygwin/MacOS environment you will need to know the location where GROMACS is installed, e.g. /usr/local/gromacs. In your shell configuration file (e.g. .bashrc for bash, or .cshrc / .tcshrc for tcsh) you should use a command analogous to:
 source /usr/local/gromacs/bin/GMXRC near the end of that file.
([http://www.gromacs.org/Downloads/Installation_Instructions](http://www.gromacs.org/Downloads/Installation_Instructions))
**2**."You need to either add the location  of your Gromacs installation to your PATH (in whatever shell  configuration file, likely .bashrc) or source GMXRC every time you log  in to a new terminal.  Once your Gromacs installation is recognized by  your shell environment you can run all the commands."
**3**.You a suitably configured environment.
**4**.This is a fairly basic UNIX issue, and has nothing specific to do with  GROMACS. You need to have an appreciation of what the UNIX environment  is, and how you can "source" a file to adjust that environment.  Once  you understand the need to adjust the environment, you can see how  "sourcing" GMXRC will solve some of your problems.

What should I do? how can I adjust the Environment?

Thanks in advance

---

### Post by mörgæs on 2010-10-05
Since you are running Ubuntu 9.04, which is unsupported by the end of the month, I guess it is best first to get the system running with a fresh install of 10.04.

After that we can focus on getting applications to work.

---

