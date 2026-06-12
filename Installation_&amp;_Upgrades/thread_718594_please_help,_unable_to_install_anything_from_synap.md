---
title: "please help, unable to install anything from synaptic"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by whathappened on 2008-03-08
Hi there, 

I am hoping someone can help me. truth be told im still a bit new to ubuntu, (although i did have 7.04 and am currently using 7.10)

I really like it but it has had some teething problems, which i've got round one way or the other. now though I really need a hand.

when ever I try to get a Codec to play my music (which mostly is WMA/MP3) and I go to install the codec (when prompted to in totem) I get the following error

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

then when i try and get it using synaptic i get the same error :confused:

what do I do? 

thanks

daniel

---

### Post by Pumalite on 2008-03-08
This involves a series of steps: first post the output of:
sudo dpkg --configure -a
sudo apt-get update

---

### Post by whathappened on 2008-03-08
daniel@dan:~$ sudo dpkg --confiure -a
[sudo] password for daniel:
dpkg: unknown option --confiure

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
daniel@dan:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_GB
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_GB
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B] 
Get: 2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_GB [21.3kB]
Get: 3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_GB [4405B]
Get: 4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_GB [2395B]
Get: 5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_GB [8133B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Fetched 36.4kB in 0s (67.0kB/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
daniel@dan:~$

---

### Post by Pumalite on 2008-03-08
Typo: 'sudo dpkg --configure -a'

---

### Post by whathappened on 2008-03-08
oh sorry, my bad.

I did that and this is what I got


daniel@dan:~$ sudo dpkg --configure -a
Setting up java-common (0.26ubuntu1) ...

Setting up odbcinst1debian1 (2.2.11-16) ...

Setting up unixodbc (2.2.11-16) ...

Setting up gcc-3.3-base (1:3.3.6-15ubuntu2) ...
Setting up libstdc++5 (1:3.3.6-15ubuntu2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
daniel@dan:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_GB
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_GB
Get: 1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B] 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Fetched 1B in 0s (1B/s)  
Reading package lists... Done
daniel@dan:~$ 


then I tried to install the packages again and it worked, so presumably what is above is good? anyway, thank you for your help.

---

### Post by Pumalite on 2008-03-08
You are welcome. Good luck.

---

