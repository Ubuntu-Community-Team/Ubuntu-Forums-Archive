---
title: "newbie: make in a console gives errors ... (Solved)"
date: 2005-11-20
forum: Installation &amp; Upgrades
---

### Post by brannolte on 2005-11-20
Hi 
I try to a make for the first time and run into the error 
--------------------- 
pwc-10.0.9-rc1$ make 
make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/home/brannolte/temp/download/webcam/pwc-10.0.9-rc1 modules 
make: *** /lib/modules/2.6.10-5-386/build: Datei oder Verzeichnis nicht gefunden. Schluss. 
make: *** [default] Fehler 2 
--------------------- 
I installed "sudo apt-get install gcc" and run into an error that the system is unable to read some lists ... try "apt-get update" 

------------------
...
W: GPG error: [ftp://ftp.real-time.com](ftp://ftp.real-time.com) unstable Release: 
The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7CF1A7092CC1B288 W: Sie m&#246;chten vielleicht &#187;apt-get update&#171; aufrufen, um diese Probleme zu l&#246;sen 
------------------ 
I should try to run "apt-get update" :-((( I dont know what to do? 

Thanks matthias 

Linux lap-07 2.6.10-5-386 #1 Mon Oct 10 11:15:41 UTC 2005 i686 GNU/Linux KDE 3.4.2

---

### Post by Haegin on 2005-11-20
I think this is a public key problem that can be solved by importing the public keys into apt. To do this use the following commands:
[code]
$ gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
$ gpg --armor --export 1F41B907 | sudo apt-key add -
[/key]

This won't be the exact command for your problem as you need the key for another repo. To find this out you need to contact the repo owner (http://www.real-time.com/ i think) and they should be able to give you the key. Then replace the "1F41B907" with the similar code you have been given.

To find out more look here: https://wiki.ubuntu.com/AptAuthenticationInstructionsForHoary

Hope this helps

---

### Post by brannolte on 2005-11-20
Hi,

i solved the problem by
"http://www.psychocats.net/linux/sources.php"

but I have to build a new kernel for using my phillips webcam 
1. sudo apt-get install autoconf
2. sudo apt-get install build-essential
3. followed the instruction at [http://www.saillard.org/linux/pwc/](http://www.saillard.org/linux/pwc/) [install.en]
4. run every point till patching the kernel
5. patching the kernel I`ve got the error

make
  CHK     include/linux/version.h
  UPD     include/linux/version.h
  SPLIT   include/linux/autoconf.h -> include/config/*
make[1]: *** Keine Regel vorhanden, um das Target »init/main.o«,
  benötigt von »init/built-in.o«, zu erstellen.  Schluss.
make: *** [init] Fehler 2

Do you have a solution for that? What does that mean?

greets matthias

---

### Post by brannolte on 2005-11-20
Problem solved,

i missed to unpack the kernel sources, after that everything is fine

Thanks to all - not only "Human Prototype" 

greets matthias

For one little moment I was looking for windows again, but working there for half an hour brought me back :KS

---

