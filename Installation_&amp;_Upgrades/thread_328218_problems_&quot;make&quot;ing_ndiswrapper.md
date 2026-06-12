---
title: "problems &quot;make&quot;ing ndiswrapper"
date: 2006-12-30
forum: Installation &amp; Upgrades
---

### Post by alfiesty on 2006-12-30
I decided to try Ubuntu in a bookstore because I had an unused laptop (Compaq 1528). I bought "Beginning Ubuntu Linux" , which came with Ubuntu 5.10. The laptop had a Netgear MA111 wireless adapter, which connects by USB. I get no internet connection! After reading many forum posts, I found I needed "Ndiswrapper". I downloaded it, put on a USB drive and put on the laptop. The first attempt at make showed that make was not installed. I finally got it off the install disk, but the second try gives me this message:

jim@ubuntu:~/ndiswrapper-1.33$ make install
make -C driver install
make[1]: Entering directory `/home/jim/ndiswrapper-1.33/driver'
Can't find kernel build files in /lib/modules/2.6.12-9-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/jim/ndiswrapper-1.33/driver'
make: *** [install] Error 2

What do I need to load now? Am I doing this the right way? 

As soon as I get to the internet I'll download the latest version, but I need the internet to do that! I'm tired of MS/virii/etc and want Linux for my internet machine.

Jim

---

### Post by nyvalbanat on 2007-01-02
I'm no expert, but here are some thoughts. It seems like you have the ndiswrapper source (which needs compiling), and that needs to link with some kernel source code - which is seemingly not on your machine (see [http://www.linuxquestions.org/questions/showthread.php?t=214056)](http://www.linuxquestions.org/questions/showthread.php?t=214056)).

For an alternate approach, when I had this problem with Ubuntu6.0.6, I found the (pre-compiled) ndiswrapper package on the CD and installed it using dpkg. Also see [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu) if it's any help to you.

If you have the install CD, mount it and run  
   find . -name ndis\*
to see if it's there. Then you can run dpkg -i <filename> to install it. 

Regards,
Val

---

