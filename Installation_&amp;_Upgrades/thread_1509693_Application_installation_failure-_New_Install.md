---
title: "Application installation failure- New Install"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by mkdw on 2010-06-14
I have installed Lucid 10.04 server on an IBM eserver 325 dual boot with 2003. 
The Issue:  the cd rom drive on the server is starting to go out and the install worked but failed to install key applications and files.  For examle- no VIM (just VI) and the apt sources.list file had one entry- the cd rom.  I need to update all the packages necessary for the system to operate fully. ( I have tons of broken dependencies when trying to install SSHserver, Samba and other apps)  I manually entered the muliverse and universe repositories in sources.list but this is not resolving the issues with the missing dependencies.

I can get a new cd-rom drive but it will certainly take a week or two to get and I need to get this project going.  I have some experience with Linux, but not enough to know if there is a magic command that I don't know.

Any assistance would be greatly appreciated.

Peace,

Mike

---

### Post by mkdw on 2010-06-14
I was hoping that someone could shed some light on possible ways to fix this by a command, but after no on replied I ended up pulling open the cover and running a standard PC CD drive with power from another box (the server has a slimline with a mini power connector).  This allowed me to reinstall from the good cd that the bad drive wasn't reading.

If anyone has any ideas about how to fix broken core applications without using a cd it still might be helpful to know.

- Mike

---

### Post by mkdw on 2010-06-15
Having a working CDRom drive did the trick. Everything is up and running.  I had another issue with not being able to login after a new installation.  It turned out that either the second drive I installed was bad or the disk was.  
Lesson here- having a verified install disk (like I have seen others write) and a working CD drive make for a good install.

---

