---
title: "Help Installing Byond"
date: 2008-09-17
forum: Installation &amp; Upgrades
---

### Post by Dlanir on 2008-09-17
I made it this far then puzzled from here where to find it is the installation complete what do I do next?:

rinald@rinald-desktop:~$ cd /home/rinald/Desktop/byond
rinald@rinald-desktop:~/Desktop/byond$ make
There are two options for installing BYOND.  You can install
it for all users or you can install it for your own personal
use.  To install for all users, you must run this makefile
as root.  In that case, edit this makefile, configure the
installation parameters to your liking, and run 'make install'.

To install for your personal use, simply put the 'byond'
directory where you want to keep it and type 'make here'.

rinald@rinald-desktop:~/Desktop/byond$ sudo make install
[sudo] password for rinald: 
if [ ! -d /usr/local/byond ]; then mkdir /usr/local/byond; fi
cp -R cfg bin /usr/local/byond
if [ "" = "yes" ]; then \
		chown root /usr/local/byond/bin/DreamDaemon; \
		chmod a+xs /usr/local/byond/bin/DreamDaemon; \
		if [ "" = "yes" ]; then \
			chown root host/host.dmb; \
			chmod a+xs host/host.dmb; \
		fi \
	fi
ln -f -s /usr/local/byond/bin/DreamDaemon /usr/local/bin/DreamDaemon
ln -f -s /usr/local/byond/bin/DreamSeeker /usr/local/bin/DreamSeeker
ln -f -s /usr/local/byond/bin/DreamMaker /usr/local/bin/DreamMaker
ln -f -s /usr/local/byond/man/man6/DreamDaemon.6 /usr/share/man/man6/DreamDaemon.6
ln -f -s /usr/local/byond/man/man6/DreamMaker.6 /usr/share/man/man6/DreamMaker.6
ln -f -s /usr/local/byond/man/man6/DreamSeeker.6 /usr/share/man/man6/DreamSeeker.6

*****************
You can find out more about the software by doing 'man DreamDaemon'.
A host server has also been included so edit host/hostconf.txt and
boot up your world server!
*****************

Please I really love this program can some one guide me through step by step?I'm a beginner ubuntu user I have the latest version.

---

### Post by Dlanir on 2008-09-17
I might be asking for too much but can someone sort've like send me step by step instructions for the ENTIRE PROCESS pretty please i really wish to install BYOND and I'm begging you..........and e-mail or anything please I'm very desperate.

---

