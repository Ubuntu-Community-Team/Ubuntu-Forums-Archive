---
title: "Need knowhow: install/run mongodb from source???"
date: 2015-04-11
forum: Installation &amp; Upgrades
---

### Post by gregory10 on 2015-04-11
downloaded the latest version from the Mongodb site itself. Its labeled 'mongodb-linux-x86_64-ubuntu1404-3.0.2'
I got as far as unpacking it and copied it to  /usr/local/src
I was following the steps I took when doing the instalation of node.js from source yesterday.
Got this far using terminal and the next step was to command the configuration but there is no
configure file like there was within node.js. 

IN this there is only three files and the bin folder.
the three files are: 
GNU-APL-3.0 
README
THIRD-PARTY-NOTICES

the directory is like this:
mongodb-linux-x86_64-ubuntu1404-3.0.2 /
GNU-APL-3.0 
README
THIRD-PARTY-NOTICES
/bin
bsondump
mongo
mongod
mongodump
mongoexport
mongofiles
mongoimport
mongooplog
mongoperf
mongostore
mongos
mongostat
mongstop

these files in the /bin folder are all some sort of executable files.
looks like it operates from where ever you place the directory it came inside of.

If placing it is all I have to do before running it (with what eve command I need to run it). Where do I place it?
I like the idea of placing it in the /srv folder but don't really know what the protocol is.
thanks to anyone with the knowhow for your help.

---

### Post by Holger_Gehrke on 2015-04-11
Just above the link for the download there's another link to the installation instruction.They basically tell you to import their key into apt, include their repository in your sources and then to apt-get it. That way you get not only the naked binaries but also some start-stop scripts for init and some other goodies and everything is placed the way they think is good. And it's under control of tha package manager for updates or de-installation.

---

### Post by gregory10 on 2015-04-11
Holger_Gerhke
thanks for the reply. I did the instal by following the instructions just now.
I'm following what they say in the instal instructions mongodb has been loaded and installed.

it starts and stops but as yet have not found a way to open the 
/var/log/mongodb/mongod.log when I tried to open it the system said there is no program to open that file
I'm thinking it needs to be done through a terminal in some way.

Its all there as they say
I'm going to call this solved

---

