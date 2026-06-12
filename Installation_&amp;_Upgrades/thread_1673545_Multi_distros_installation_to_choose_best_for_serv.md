---
title: "Multi distros installation to choose best for server: what partitions?"
date: 2011-01-22
forum: Installation &amp; Upgrades
---

### Post by RonGraham on 2011-01-22
Hi everybody,

I'm quite new to Linux world, but I'm learning each day more and i think my conversion from win to linux has been done!

Well, i decided to build a home server on an AMD64 (buyed some years ago) for file storage, printer sharing and something else...
I've searched a lot for "the best distros for server" and discarding extreme solution (like command line only) what remains is: Ubuntu, Fedora and Debian

Now the problem: how to install more than one distros on the same hdd? what i know is that i need a bootloader (grub/lilo) and partitions for boot,swap, and remaining space will be split for the distro itself. 

I think is a good idea to have a partition only for files (/data) that all distros can access, but for sure i'd like to have one /root and one /home partitions each distro!


I can't understand if the correct way is first of all to install a distro (let's say ubuntu), then set up everything such as partitions and bootloader and then install other distros. 
I'd like to know if it is possible to manage dinamycally the space reserved for distros, so i'll be able to install 2,3,4,5...distros with no problems.

I need your help!
Thank you everybody for the attention!

---

### Post by mikewhatever on 2011-01-22
Wait, so you want a file sharing and printing server, right? Where do multiple OSs come in?

PS: Just thought I'd mention that Ubuntu server doesn't have a gui either.

---

### Post by RonGraham on 2011-01-22
Yeah you're right...everyway i don't need only printer and file storage, i need the server, to monitor some sensors and control actuators for a smart control system. The server will also provides services available through a web page (or an application i don't know yet...). Then i'd like the server to do compilation / building operations while i'm doing other things with my laptop... 

Everyway I know that for my needs, every distro is ok, but i'd like to explore different distro so i can really check what change from one distro to another


i already installed ubuntu server, but i was going crazy setting wifi connection...everyway i'd like to use it...but i'm not able at the moment!

---

