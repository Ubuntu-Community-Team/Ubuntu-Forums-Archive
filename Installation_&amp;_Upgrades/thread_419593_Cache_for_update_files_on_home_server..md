---
title: "Cache for update files on home server."
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by MiKom on 2007-04-23
I have some cheap computer acting as home server and three desktops, all running ubuntu.
I would like to create some cache on the server for files needed for updates on these ubuntu machines. Now, every package is downloaded three times, once for every machine. Is it possible to make some file cache on the server so that everything would be downloaded once, and then sent through LAN.
Currently there is Gentoo system on the server, but I can install something else.
What programs should I use? Squid maybe?
Maybe there is already some howto for that?

---

### Post by ABCC on 2007-04-23
How about setting up your own local repo?

[http://people.connexer.com/~roberto/howtos/debrepository](http://people.connexer.com/~roberto/howtos/debrepository)

---

### Post by MiKom on 2007-04-23
But I need only files for updates, AFAIR full ubuntu packages repository is about 170GB, I just want update packages to be served locally. I don't even have that amount of storage space.

---

### Post by ABCC on 2007-04-24
I've never done this myself, so I can't talk from experience. There are plenty of custom/small repositories on the net, which does indicate a degree of configurability on the part of the repository setup.

Another option would be to share the package of the system you update first on the network, and have the others update with rsync.

hth

ABCC

---

### Post by mikesignguy on 2007-05-28
i would like to do the same thing... the best way would be if the repos on each computer saved  to the server then nomatter what computer you updated its files would be saved to a directory on the server... that would involve a script or moding the apt to save all downloaded files to the server instead of locally ... anyone know how this can be done?

---

### Post by MiKom on 2007-05-28
I've read on some blogs that during ubuntu install parties they were setting apt-cache on one computer so that everything was downloaded only once and then served from this computer. Has anyone have idea about that?

---

### Post by mikesignguy on 2007-05-28
that seems very simple to adding a line to your sources list to go to a computer and piont it to  /var/cache/apt/archives on the host computer 

simple but that computer has to be the most current and it doesn't take into account the different setups on different computers

  if you want the server  to have the files but typically your server has less packages than a desktop would make that scenario less than optitmum.. 


... the ideal and most efficient way is when the files are fetched that they save to the server...seen it done in gentoo ... 

even the apt man pages aren't much help ... seems like this would be very common i dunno

---

### Post by mikesignguy on 2007-05-28
i think i got it...

debmirror   or    apt-mirror

---

### Post by mikesignguy on 2007-05-28
[https://help.ubuntu.com/community/Debmirror](https://help.ubuntu.com/community/Debmirror)

how do u love me now?

---

### Post by MiKom on 2007-05-29
> **mikesignguy said:**
> ...seen it done in gentoo ... 


To be honest, my server runs Gentoo so Gentoo based solution would be optimal :)

---

### Post by mikesignguy on 2007-05-29
i don't know how to do it in gentoo but portage has a -f (fetch only option) that you can fetch it to a different directory.  Don't know the details, i didn't stay at a Holiday Inn last night.

which goes to my original solution ... fetch option for apt

---

### Post by mikesignguy on 2007-06-10
i have it all up and running if anyone is still interested in a little how-too:guitar:

---

### Post by ABCC on 2007-06-10
Did you use debmirror for your setup or have you found a way to only fetch the files your really need?

---

### Post by mikesignguy on 2007-06-17
the way i did it......
1. I   updated  all  packages on my "heavy" machine (the one with the most crap on it)

2. rysnc  the /var/cache/apt/archives to a remote location.   i.e. server
                                          or
      copy only the new files to the remote archive

3. Link the remote archives directory onto apache web server (  apt likes http and ftp  )

4. Edit the sourceslist file on all machines  to include the local repository  i.e. "deb [http://local](http://local) web address"  ( my server is 192.168.2.9)

4.5 optional :  cron the resyncs... i do it manual so it happens when i want

5. optional: rysnc after each update on each machine and you will have all the .deb files you have on all your systems.

6. optional: when you convert people to linux.. you invite them over ...install all the packages 

there are probably some disgusting errors and omissions in my  amateuristic  attempt at this..

really simple when you understand all the commands .... if i need to go into more detail and there is a call for it i will....my biggest challenge was apache.....i never used it before ... took a phone call to a friend to teach me about symbolic links

damon AIM : damonxb12s

---

### Post by ABCC on 2007-06-18
Hehehe,

Looks like you found a proper free software solution. I love solutions like this, they're the best way to learn about new programs.  Apache may be a bit of overkill, personally I would have started with mounted a network mounted directories/vpn solution. 

However, as you're running Apache anyway you may want to take a look at dwww [URL="http://www.penguin-soft.com/penguin/man/1/dwww.html"]http://www.penguin-soft.com/penguin/man/1/dwww.html[/UR]  with which you can make all your man pages accesible and browsable on your network.

Cheers for the mini howto, I'm currently looking at a pile of hardware that I'm thinking of reassembling. More than anything though I need a 'use' for it. Once I've found a good one I'll have the pleasure of setting up a similar setup. Glad to hear you've got it sorted out.

Regards,

ABCC

---

### Post by aboutblank on 2007-07-04
Check out [http://apt-proxy.sourceforge.net/](http://apt-proxy.sourceforge.net/)  (apt-proxy). It's a cache but only for requested files.

---

