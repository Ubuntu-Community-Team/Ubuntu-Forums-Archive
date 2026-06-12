---
title: "Root password not accepted"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by stratus75 on 2010-03-29
Trying to install a game and its asking for root password which i type in and it keeps coming back saying that its wrong but if i try and input the same password in when using package manager it works fine ?? and caps is off 

thanks

---

### Post by doas777 on 2010-03-29
there may be some confusion between a sudo password with teh password for the root account. 
does it actually use the word 'root' in either of the prompts?

in ubuntu, the root password is random, and the account is disabled so it cannot be used. some rather rare peices of software still assume you have a root account and will attempt to access it, but they are pretty rare.

---

### Post by stratus75 on 2010-03-29
had a look and software center is asking for an admin password and the game "Torcs" that im trying to install from the software center is asking for a root password !! is there a work around besides the terminal 

the same thing is happening with any programme i try to install from software centre it is asking for the root password specifically is there any way i could changed things ?

Thanks for the help!!

---

### Post by doas777 on 2010-03-29
just to clarify, you did try putting in your own password when it asked for root's, right?

I just installed it via the cli, and had no problems with a request for root; my sudo passwd was sufficient.

```
karmic:~$ sudo apt-get install torcs
[sudo] password for userperson: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  freeglut3 libalut0 libopenal1 libplib1 torcs-data torcs-data-cars
  torcs-data-tracks
The following NEW packages will be installed:
  freeglut3 libalut0 libopenal1 libplib1 torcs torcs-data torcs-data-cars
  torcs-data-tracks
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 173MB of archives.
After this operation, 338MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://us.archive.ubuntu.com karmic/main freeglut3 2.4.0-6.1ubuntu1 [86.9kB]
Get:2 http://us.archive.ubuntu.com karmic/universe libopenal1 1:1.8.466-2 [94.1kB]
Get:3 http://us.archive.ubuntu.com karmic/universe libalut0 1.1.0-2 [32.3kB]
Get:4 http://us.archive.ubuntu.com karmic/universe libplib1 1.8.5-4 [631kB]
Get:5 http://us.archive.ubuntu.com karmic/universe torcs-data-tracks 1.3.1-1 [129MB]
Get:6 http://us.archive.ubuntu.com karmic/universe torcs-data-cars 1.3.1-1 [2,761kB]
Get:7 http://us.archive.ubuntu.com karmic/universe torcs-data 1.3.1-1 [30.1MB] 
Get:8 http://us.archive.ubuntu.com karmic/universe torcs 1.3.1-2 [10.8MB]      
Fetched 173MB in 5min 0s (578kB/s)                                             
Selecting previously deselected package freeglut3.
(Reading database ... 271363 files and directories currently installed.)
Unpacking freeglut3 (from .../freeglut3_2.4.0-6.1ubuntu1_i386.deb) ...
Selecting previously deselected package libopenal1.
Unpacking libopenal1 (from .../libopenal1_1%3a1.8.466-2_i386.deb) ...
Selecting previously deselected package libalut0.
Unpacking libalut0 (from .../libalut0_1.1.0-2_i386.deb) ...
Selecting previously deselected package libplib1.
Unpacking libplib1 (from .../libplib1_1.8.5-4_i386.deb) ...
Selecting previously deselected package torcs-data-tracks.
Unpacking torcs-data-tracks (from .../torcs-data-tracks_1.3.1-1_all.deb) ...
Selecting previously deselected package torcs-data-cars.
Unpacking torcs-data-cars (from .../torcs-data-cars_1.3.1-1_all.deb) ...
Selecting previously deselected package torcs-data.
Unpacking torcs-data (from .../torcs-data_1.3.1-1_all.deb) ...
Selecting previously deselected package torcs.
Unpacking torcs (from .../torcs_1.3.1-2_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for desktop-file-utils ...
Setting up freeglut3 (2.4.0-6.1ubuntu1) ...

Setting up libopenal1 (1:1.8.466-2) ...

Setting up libalut0 (1.1.0-2) ...

Setting up libplib1 (1.8.5-4) ...

Setting up torcs-data-tracks (1.3.1-1) ...
Setting up torcs-data-cars (1.3.1-1) ...
Setting up torcs-data (1.3.1-1) ...
Setting up torcs (1.3.1-2) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
karmic:~$ 
```

---

### Post by sisco311 on 2010-03-29
> **stratus75 said:**
> had a look and software center is asking for an admin password and the game "Torcs" that im trying to install from the software center is asking for a root password !! is there a work around besides the terminal 

the same thing is happening with any programme i try to install from software centre it is asking for the root password specifically is there any way i could changed things ?

Thanks for the help!!

I think, that you have removed your user from the admin group.

Please post the output of:
```
id
```
and
```
cat /etc/group | grep $USER
```

then try to add your user to the admin group:
```
sudo gpasswd -a $USER admin
```

---

