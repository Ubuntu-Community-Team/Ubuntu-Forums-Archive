---
title: "Error in compilation of drivers"
date: 2006-03-08
forum: Installation &amp; Upgrades
---

### Post by baggy on 2006-03-08
I try to install some modem's (Lucent Winmodem 56k) drivers.
I follow all the steps but when I try to use 'make' ( to compile the drivers ) I can see only this output :


************************************************
*******  make   ********************************
************************************************
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/miky/Desktop/driver/Driver_2.6_8alk/ltmodem-2.6-8alk modules
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'CC [M]  /home/miky/Desktop/driver/Driver_2.6_8alk/ltmodem-2.6-8alk/lt_modem.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/miky/Desktop/driver/Driver_2.6_8alk/ltmodem-2.6-8alk/lt_modem.o] Error 127
make[1]: *** [_module_/home/miky/Desktop/driver/Driver_2.6_8alk/ltmodem-2.6-8alk] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [module] Error 2


************************************************
*******  make -d    ****************************
************************************************
GNU Make 3.80
Copyright (C) 2002  Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.
Reading makefiles...
Reading makefile `Makefile'...
Updating makefiles....
 Considering target file `Makefile'.
  Looking for an implicit rule for `Makefile'.
  Trying pattern rule with stem `Makefile'.

... bla bla bla ...

   Trying implicit prerequisite `s.Makefile.sh'.
   Trying pattern rule with stem `Makefile.sh'.
   Trying implicit prerequisite `SCCS/s.Makefile.sh'.
  No implicit rule found for `Makefile'.
  Finished prerequisites of target file `Makefile'.
 No need to remake target `Makefile'.
Updating goal targets....
Considering target file `module'.
 File `module' does not exist.
 Finished prerequisites of target file `module'.
Must remake target `module'.
Putting child 0x0808abf0 (module) PID 9636 on the chain.
Live child 0x0808abf0 (module) PID 9636 
Got a SIGCHLD; 1 unreaped children.
Reaping winning child 0x0808abf0 PID 9636 
Removing child 0x0808abf0 PID 9636 from chain.
Successfully remade target file `module'.



I use Linux 2.6.12-9-386 and gcc-4.0 (NOT 3.4 !!!!)
What's the problem?!?!?

P.S.  I also try to modify gcc-version.sh in this way but nothing changed

#!/bin/sh
#
# gcc-version gcc-command
#
# Prints the gcc version of `gcc-command' in a canonical 4-digit form
# such as `0295' for gcc-2.95, `0303' for gcc-3.3, etc.
#compiler="$*"
#MAJOR=$(echo __GNUC__ | $compiler -E -xc - | tail -n 1)
#MINOR=$(echo __GNUC_MINOR__ | $compiler -E -xc - | tail -n 1)

MAJOR=00  # <--
MINOR=40  # <--

printf "%02d%02d\\n" $MAJOR $MINOR


Stupid solution?
Thanks...

---

### Post by Sutekh on 2006-03-08
Problem is the kernel was compiled with gcc-3.4.  If you want to compile these drivers and add them to the kernel you must compile them with gcc-3.4.  Did you install build-essential?  It installs gcc-4.0, which can't be used in this case.


Until you compile the drivers you don't have internet in Ubuntu right?

You will need the help of this thread to install gcc-3.4 without an internet connection

[Ubuntu Forums - HOWTO: Install gcc-3.4 via apt-get without an internet connection]("http://ubuntuforums.org/showthread.php?t=79896")

Once you have it, try ```
CC=gcc-3.4
export CC
``` before compiling the drivers.

---

### Post by baggy on 2006-03-09
Thank you very much.
I install gcc3.4 following the HOWTO. Then I try to compile typing 'make'; the output seems to be good but then I can't find the *.ok files...
What's the problem? ... 

(too much generic question!?!??!---> SORRY )

---

### Post by Sutekh on 2006-03-09
In general when you compile source you should follow these steps
```
./configure
make
sudo make install
```

I don't know about your modem drivers, could you paste the output of those commands (use CODE tags for easy reading) in a post, or provide the link to the drivers.

---

