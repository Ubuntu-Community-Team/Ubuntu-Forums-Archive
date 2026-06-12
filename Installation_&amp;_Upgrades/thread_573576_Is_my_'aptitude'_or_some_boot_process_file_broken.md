---
title: "Is my 'aptitude' or some boot process file broken?"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by dryder on 2007-10-11
Hi,
Feisty - latest updates installed.

In the last few days, each time I reboot the process stalls and goes into shell mode, telling me that 'apt-get' is not installed and to install it by typing 'apt-get install aptitude'. I can continue the remaining boot process successfully.

If I reboot again, the same thing happens.

However, if I re-install aptitude via Synaptic (which asks for the install disc even though I have the latest kernel ... .16) then my next reboot works successfully.

But the reboot after that ... tells me again to install 'aptitude'.

Any help please on how I can resolve what the issue is?

Many thanks,
David

---

### Post by paxmark1 on 2007-10-12
No great ideas come to mind.  Funny that it says that apt-get is not installed, but that it then asks you to utilize aptitude (a higher level function) to install apt-get.  And if apt-get is not installed - my assumption is that synaptic should not work.  

from man apt-get 
apt-get is the command-line tool for handling packages, and may be considered the user&#8217;s "back-end" to other  tools using the APT library. Several "front-end" interfaces exist, such as dselect(8), aptitude, synaptic,  gnome-apt and wajig.

also
   try apt-get -v     or apt-get --version
          Show the program version.

Have you tried using dpkg?  That is a more basic level function.  

[http://www.debian.org/doc/manuals/debian-tutorial/ch-dpkg.html](http://www.debian.org/doc/manuals/debian-tutorial/ch-dpkg.html)

If apt-get --version yields no version of apt-get  installed  maybe try to get the
proper apt-get-version.deb to your system, and then
sudo dpkg -i apt-get-blah-blah of version.deb

would work.  

The only times I use dpkg is when a new Adobe acroread or Opera comes out and I download and then install with dpkg.

Hopefully a wiser person will reply.  I will watch this thread to learn more.
Peace,  Mark

---

### Post by dryder on 2007-10-12
Hi,

apt-get -v gave me:
apt 0.6.46.4ubuntu10 for linux i386 compiled on Mar 14 2007 17:43:24
Supported modules:
*Ver: Standard .deb
*Pkg:  Debian dpkg interface (Priority 30)
 S.L: 'deb' Standard Debian binary tree
 S.L: 'deb-src' Standard Debian source tree
 Idx: Debian Source Index
 Idx: Debian Package Index
 Idx: Debian Translation Index
 Idx: Debian dpkg status file

which looks OK to me - a non-expert - does it to you? :-)

---

### Post by paxmark1 on 2007-10-13
I get the same output from apt-get -v on my 7.04 edgy.    

That means it is installed on your system.   I know nothing about aptconf and aptconf.d - the configurartion files for apt.  Possibly try a search on "apt-get aptitude conflicts"  If no one answers you here,  you might have better luck in the Debian forums.  

Me, I 'm just waiting for people to start posting how it goes with updating via aptitude on the command line for 7.10  If I don't see it, I will just keep 7.04 for awhile.  

apt 0.6.46.4ubuntu10 for linux i386 compiled on Mar 14 2007 17:43:24
Supported modules:
*Ver: Standard .deb
*Pkg:  Debian dpkg interface (Priority 30)
 S.L: 'deb' Standard Debian binary tree
 S.L: 'deb-src' Standard Debian source tree
 Idx: Debian Source Index
 Idx: Debian Package Index
 Idx: Debian Translation Index
 Idx: Debian dpkg status file

and my version of aptitude

paxmark@raunes:/etc/apt$ aptitude --version
aptitude 0.4.4 compiled at Feb 26 2007 15:45:48
Compiler: g++ 4.1.2 (Ubuntu 4.1.2-0ubuntu3)

NCurses version: 5.5
libsigc++ version: 2.0.17

---

