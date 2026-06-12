---
title: "Ubuntu Packages Not Found on Server"
date: 2006-08-17
forum: Installation &amp; Upgrades
---

### Post by nudnik on 2006-08-17
libvte4_0.12.2-0ubuntu2_i386.deb
libvte-common_0.12.2-0ubuntu2_all.deb
python-vte_0.12.2-0ubuntu2_i386.deb

The packages listed above will not install on my system because they are not found on the server the system attempts to download from. 

I've updated and installed many times without ever encountering this problem. To make matters worse, the terminal is unavailable because my upgrade is incomplete. 

I assume I will have to go to comand line and manually edit the sources list, but I am hoping there is a less time consuming alternative. 

This is the problem source address: [www.beerorkid.com](www.beerorkid.com)

---

### Post by Adler on 2006-08-17
nudnik,

I've run into the same problem, and suddenly can not launch Terminal.

Adler

---

### Post by reacocard on 2006-08-17
same here. i just went and manually downloaded them from the compiz repos (the packages enable true transparent terminal backgrounds under compiz). I've attached the files so you don't have to go hunting for them.

---

### Post by ajgreeny on 2006-08-17
I'm sure you will have done so, but have you tried the versions of libvte4, libvte-common and python-vte available in the repos, which are slightly different to those you show above?  I looked at the beerorkid site but didn't see any reference to the deb packages you mention.  Did I just overlook something?

---

### Post by reacocard on 2006-08-17
beerorkid won't let you manually download the packages. i had to use ubuntu.compiz.info to get them. and they're the same packages. gdebi recognized they were the same as the ones in the repos when i installed them. Unless you're referring to the official ubuntu versions? those aren't compiz-enabled, and use 'fake' transparency in their terminal background. if you don't care about true terminal transparency, there is no reason to use these packages over the official ubuntu ones.

---

### Post by Adler on 2006-08-17
Hi Guys,

I might have run into something else. I keep seeing that I need to do the compiz up-date, but can't launch a Terminal window. Can everybody launch Terminal?

I'm backing up everything that I can, just to be sure that things haven't changed too much and might do a fresh install.

---

### Post by reacocard on 2006-08-17
try using xterm or one of the virtual console instead of the default terminal. for xterm, alt+f2, command is xterm. vc's are ctrl+alt+F1 through +F6, GUI is on +F7. i used xterm to install the new vte packages. after i installed, gnome-terminal works perfectly again.

---

### Post by Adler on 2006-08-17
reacocard,

**Thanks.** I'll give that a try. I **hate** when something like this happens -- but backing up things is a good thing. I do torture my Linux Box.

BTW -- any thing that you want to see added to my Site? It is pretty much OpenSource dedicated.

Adler

---

### Post by Adler on 2006-08-17
Hi,

I'm an ex-KDE SuSE (9.1 through SLED), guy and don't think that I can recover from this. 

Hey, I've backed everything up and will just do a re-install.

**But.** What happened here?

Adler

---

### Post by reacocard on 2006-08-17
apparently, the beeorkid repo got an updated packages.gz file, without getting the actual .deb files. so, apt thinks the .debs are there, tries to get them, gets a 404 not found error, and stops.

i wonder if this is happening with the other compiz mirrors. you could try editing your /etc/apt/sources.list, replacing
```
deb http://www.beerorkid.com/compiz dapper main
```
with
```
deb http://ubuntu.compiz.net/ dapper main
```
or
```
deb http://media.blutkind.org/xgl/ dapper main
```
then 
```
sudo apt-get update && sudo apt-get dist-upgrade
```
and see if it works.

There are other errors if you actually get the update. apparently it screws up your fonts somehow. the compiz people have noticed, and hopefully someone will come out with an update to the fonts problem. but idk if anyone has noticed beerorkid needs to be fixed too.

---

### Post by daveisadork on 2006-08-17
Seems like it's working now.

---

### Post by reacocard on 2006-08-17
daveisadork, are you sure you're using the beerorkid repos? i am, and they're still not working. i just checked.

---

### Post by reacocard on 2006-08-17
the ```
deb http://ubuntu.compiz.net/ dapper main
``` repo works perrfectly. use this one instead of beerorkid.

---

### Post by nudnik on 2006-08-17
Thanks to all that responded. I'll give the new source a try. 

I hate this sort of thing too, it does indeed bite.

](*,)

---

### Post by Adler on 2006-08-17
After a Complete install I still have lost Terminal.

Is this becuse of AUTOMATIX? 

Adler

---

### Post by reacocard on 2006-08-17
> After a Complete install I still have lost Terminal.

are you still using the beerorkid repo? try the repo i suggested a couple posts up. it should actually work, so you'll have the terminal again.

---

### Post by Adler on 2006-08-17
reacocard,

I'm a very experienced Linux User. I've nevr seen this before. I can not get "Terminal" to launch before, and after a frsh install.

I've run AUTOMATIX and the that put the repos that I wanted into my box. But, since this morning my Box has been trashed.

Adler

---

