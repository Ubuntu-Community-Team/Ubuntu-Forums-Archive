---
title: "Ubuntu Edgy to Kubuntu Edgy from cd doesn't work"
date: 2006-11-18
forum: Installation &amp; Upgrades
---

### Post by dir3wolf on 2006-11-18
Hi,

I'm trying to add KDE (Kubuntu) to my Ubuntu installation. I allready have Kubuntu Edgy CD and would like to add Kubuntu without downloading it. 
I added Kubuntu to my sources list
```
sudo apt-cdrom add
```
and update gives me
```
sudo apt-get update

Ign cdrom://Kubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-hr

Ign cdrom://Kubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-hr
```
but when I try
```
sudo apt-get install kubuntu-desktop
```
it still downloads from the Internet. 
I commented all other sources in the /etc/apt/sources.list but now I get 
```
d3vetka@lapi:~$ sudo aptitude install kubuntu-desktop

Reading package lists... Done

Building dependency tree       

Reading state information... Done

Reading extended state information      

Initialising package states... Done

Writing extended state information... Done

Building tag database... Done             

Couldn't find any package whose name or description matched "kubuntu-desktop"
```

Any ideas? I have no idea what to try next. I searched the forums but all I could get was to add CD. I did, and I know CD is working 'cause I used it to install kubuntu on my other machine.

---

### Post by mips on 2006-11-18
Weird one, hopefully someone has a solution.

---

### Post by outofnicks on 2006-11-18
I am hoping so also, wanting to install kde in Ubuntu Dapper with a dialup connection. The base install of kubuntu-desktop would take about 3 hours--not too bad, but I have a friend a block away with a DSL connection to haul my computer to although I'd like to see if the CD works first.
So, BUMP :)

---

### Post by outofnicks on 2006-11-18
Browsing the Kubuntu 6.06 CD, I found nothing of kubuntu, kde, or kubuntu-desktop. I added the CD to my sources list and also commented out the URLs just as dir3wolf did, tried the apt-get in the terminal and got this:
. 
```
ken@ubuntu:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kubuntu-desktop
```

Apparently, kubuntu-desktop is not on the Dapper CD, at least not in the package form found online.

Or, was apt-get still trying to read the online package lists, instead of the CD? I don't know.

---

### Post by unisol on 2006-11-19
you should be able to find it on the ubuntu dvd

---

### Post by dir3wolf on 2006-11-20
I've been browsing through various instructions and I think I found a refference that you can upgrade from Dapper to Edgy without internet only if you have Alternative version of the Ubuntu CD.
Can anybody confirm that?
Because if that is so, I assume the same would aply for adding Kubuntu to Ubuntu or vice versa.:neutral:

---

