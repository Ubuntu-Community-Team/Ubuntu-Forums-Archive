---
title: "missing C headers when trying to install ndiswrapper from source code"
date: 2007-01-25
forum: Installation &amp; Upgrades
---

### Post by chalupa on 2007-01-25
Hello, sorry if this question has already been answered, but I have searched the forums and read through many threads unable to find the solution.

I am trying to install ndiswrapper 1.34 on Ubuntu desktop version 6.1. I download and tar'd the source code. First I manually deleted the ndiswrapper folder (i forget where it was) so that make uninstall would not produce errors.

Then, when i try sudo make install, i get many errors: (i am typing just a portion of what the computer without internet access is displaying, so please forgive typos)

[everything is good until it comes time to compile loadndiswrapper.c]
...
make -C utils
make[1]: Entering directory '/home/amp/ndiswrapper-1.34/utils'
gcc -g -Wall -I../driver -o loadndiswrapper loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:15:20: error: stdio.h: No such file or directory
loadndisdriver.c:15:20: error: errno.h: No such file or directory
loadndisdriver.c:15:20: error: string.h: No such file or directory
loadndisdriver.c:15:20: error: libgen.h: No such file or directory
loadndisdriver.c:15:20: error: sys/mman.h: No such file or directory
... [many more unfound .h files]
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits/h:7,
[tab]from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
[tab]from loadndiswrapper.c:28:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h No such file or directory
...
and unfound files
...
etc etc

I am guessing that, basically, the compiler cannot find all those essential C header files. I read someone saying in another thread that he or she had to run
sudo apt-get install linux-headers-2.6.17-10-386 linux-headers-2.6.17-10-generic
before sudo make would work.

When I do this, it says that my generic headers are already good, and it cannot find the package for the -386 headers. I tried looking for these on the ubuntu install cd, but to no success.

I find it hard to believe that files such as stdio.h, stlib,h, etc do not come installed with ubuntu, so what is the problem? I need ndiswrapper so that i can install old windows 98 driver to get my asus p5w dh deluxe on board-wireless to work.

If i need to download those .h files, i can easily boot to windows, download them, then restart, boot to ubuntu, and access them.

Thank you

---

### Post by chalupa on 2007-01-26
bump...please if you have any idea what to do please let me know.
thank you!

---

### Post by Sleepy_Sentry on 2007-01-27
I am having the same exact problem. Help would be appreciated.

---

### Post by Sleepy_Sentry on 2007-01-27
The solution was found here:
[http://ubuntuforums.org/showthread.php?p=2071292#post2071292](http://ubuntuforums.org/showthread.php?p=2071292#post2071292)

You can use the Ubuntu CD to install ndis wrapper.

---

