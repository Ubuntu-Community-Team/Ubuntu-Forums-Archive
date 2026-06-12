---
title: "wineasio make error"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by secondsight on 2007-09-05
hi all :) have had a look around but i cant seem to find any threads with the info i want  (im new so its probably coz i dont know how to ask the right questions!) so here goes...

installed ubuntu studio and im trying to compile wineasio from the instructions here - [http://www.davehayes.org/2007/04/27/howto-reaper-on-ubuntu-linux-with-wineasio/](http://www.davehayes.org/2007/04/27/howto-reaper-on-ubuntu-linux-with-wineasio/)

but i get craploads of errors when trying to make from a terminal - the last little bit looks like this 

asio.c:899: error: ‘struct IWineASIOImpl’ has no member named ‘start_event’
asio.c:904: error: ‘struct IWineASIOImpl’ has no member named ‘semaphore1’
asio.c:907: error: ‘struct IWineASIOImpl’ has no member named ‘terminate’
asio.c:909: error: ‘struct IWineASIOImpl’ has no member named ‘stop_event’
asio.c:917: error: ‘struct IWineASIOImpl’ has no member named ‘state’
asio.c:919: error: ‘struct IWineASIOImpl’ has no member named ‘time_info_mode’
asio.c:922: error: ‘struct IWineASIOImpl’ has no member named ‘asio_time’
asio.c:922: error: ‘struct IWineASIOImpl’ has no member named ‘asio_time’
asio.c:923: error: ‘struct IWineASIOImpl’ has no member named ‘tc_read’
asio.c:925: error: ‘struct IWineASIOImpl’ has no member named ‘asio_time’
asio.c:925: error: ‘struct IWineASIOImpl’ has no member named ‘asio_time’
asio.c:926: error: ‘struct IWineASIOImpl’ has no member named ‘asio_time’
asio.c:928: error: ‘struct IWineASIOImpl’ has no member named ‘callbacks’
asio.c:928: error: ‘struct IWineASIOImpl’ has no member named ‘asio_time’
asio.c:928: error: ‘struct IWineASIOImpl’ has no member named ‘toggle’
asio.c:929: error: ‘struct IWineASIOImpl’ has no member named ‘asio_time’
asio.c:932: error: ‘struct IWineASIOImpl’ has no member named ‘callbacks’
asio.c:932: error: ‘struct IWineASIOImpl’ has no member named ‘toggle’
asio.c:936: error: ‘struct IWineASIOImpl’ has no member named ‘semaphore2’
make: *** [asio.o] Error 1

i have everything the guy says to get and im as up to date as i can be...
anybody know what i need to do?

---

### Post by knembo on 2007-09-11
Hi i have the same problem as you using gutsy. I found a solution, not very elegant and maybe dangerous, but i am newbie and  i wasn't able to  find a better one.
I downgraded (or removed) some library (g++(removed),cpp-2.95(downgraded),  build-essential(removed) and other library to feisty versions);then i followed the tutorial that you posted (make, sudo make install etc.) and all went fine. I am using wine version from Jacklab converted with alien to avoid midi freeze using reaper 2.0 beta.
At the and i reinstalled all gutsy version of the library downgraded or removed.


I like to try (no problem for me if i have to reinstall gutsy) so if you you have important data in your Pc consider not to try my solution and wait till someone will post a better and safer one.


Ciao Knembo

---

### Post by MobileDev on 2007-09-19
I have a solution! Chuck wineasio and get one of the cool Linux Live CDs with low latency kernels, lots of audio apps, and either dssi-vst or LMMS installed or available as add-on modules/extensions/plugins. I like dyne:bolic, but you can try Musix, Elive, or several others.

---

### Post by gorgon on 2008-03-26
I got the same error when I did 'make' with this in Makefile:

PREFIX                = /usr/local

..changed it to 

PREFIX                = /usr

**that is, I edited the file 'Makeflie' that came with wineasio.**
and then the errors disappeared. The readme file actually explains to do this too.

---

### Post by Sandsound on 2008-03-28
For those of you who dont want to bother compiling wineasio, I have a precompiled version 0.7.3 on my site :
[http://www.sandgreen.dk/index.php?side=linux_wineasio](http://www.sandgreen.dk/index.php?side=linux_wineasio)
I'll try to keep the site updated whenever the next version comes along.

I've also made a script that does a complete install of the latest winasio, wine, jack and so on. I have tried it on both 7.10 (Gutsy) and 8.04 (Hardy) and it seams to work. Just download the script, give it permission to be executed and then run it.

---

