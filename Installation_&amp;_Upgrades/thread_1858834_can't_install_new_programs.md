---
title: "can't install new programs"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by d_stroyer on 2011-10-13
i recently installed ubuntu 11.04 on a dual-boot with win7. i had no problems at first, but now when i try to download a new app/prog i get the following errors. i downloaded and installed a few things before, but it doesn't work now? these are the error messages i've gotten:

  	 	 	 	 	 	  when i tried installing Chromium:
 Traceback (most recent call last):
   File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
     trans.unauthenticated = self._simulate_helper(trans)
   File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
     return depends, self._cache.required_download, \
   File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
     pm.get_archives(fetcher, self._list, self._records)
 SystemError: E:I wasn't able to locate file for the postfix package. This might mean you need to manually fix this package.

any info woulddef help me out. i'm a linux n00b fyi...so if you can dumb it down a little when explain a fix, it would be nice..thanks!!!

---

### Post by WasMeHere on 2011-10-13
Hello d_stroyer,

- How did you try to install it? From the repositories or from a deb file or ...  and which tool or command?

- Which version of Chromium did you want to install?

Have fun finding out :-)
Olle

---

### Post by d_stroyer on 2011-10-13
i tried to intall from the ubuntu software center thingy. but nothing will install from that. same thing happened when i tried to install flash plug-in to my firefox (i wanna get chromium cause i dont like ff) and mp3 software.

---

### Post by WasMeHere on 2011-10-13
Hmmm, the software center should work, but anyway, use **Synaptic** or a command line in the terminal```
sudo apt-get install chromium-browser
```

Have fun finding out :-)
Olle

---

### Post by d_stroyer on 2011-10-13
cool!! i tried it from the terminal and it worked. i was also able to get the flash plug i couldn't get earlier. it seems to have fixed what the problem was...but help me out if you see further replies ;). thanks again!!

---

### Post by WasMeHere on 2011-10-13
I'm glad that it worked for you. We are many people at the Ubuntu Forums to help you.

I suggest that you mark this thread SOLVED. Please come back with a new thread with a good description in the title if you have a new question, comment or problem!

Have fun
Olle

---

### Post by d_stroyer on 2011-10-13
will do.by the way, can you maybe explain to me a little more about what you told to do that may have fixed my problem? but be gentle..i'm new haha

---

### Post by WasMeHere on 2011-10-13
I think that there is nothing wrong with your system in general. There seems to be a problem with 'the ubuntu software center thingy' either at your end or at the ubuntu end.

Many programs are packed into packages and kept in repositories at ubuntu servers. These can be fetched using the terminal command *apt-get*, and you must run it with superuser privileges with *sudo*:
```
sudo apt-get install *program*
```There are also graphical user interfaces to apt-get. The general one is *Synaptic*, another one is 'the ubuntu software center thingy'. You can browse the internet and read about this method to install and update/upgrade programs. You can also get detailed information about *Synaptic* and *apt-get*.

---

