---
title: "Several problems after upgrade to 10.4"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by the52poet on 2010-06-25
I am using Linux Mint at the moment because the Ubuntu upgrade caused several problems. (Some of which are also present in Linux Mint 9 - Isadora)

First problem was being automatically logged out continually and having to log back in. Thunderbird E-Mail worked fine, but the messages would not show in the view panel, as well as menu pull downs working, but also blank.

My sound no longer works, my 500 gig Seagate hard drive is history, and Firefox will instantly terminate at any given moment.

My 3.2 gig CPU stays at 90+% and my 1gig memory and 1 gig swap file are also close to peak at most times.

The system takes about twice as long to boot up, and runs much slower than it once did. (Like the day before I upgraded).

I would love to be able to correct most of these problems and get back to some form of reasonable usability once again. (The hard drive is beyond hope).

Since Linux Mint seems to have most of these same problems after they upgraded, I am thinking it is a 'core' problem and another update of some sort will be needed to correct it. (The problems and complaints on this forum almost made me think I had logged into Redmond somehow).

I hope everything works out fine in the end, in the meantime I do have work to do, so I am using something else until then.

---

### Post by kooia on 2010-06-25
Well, there's always the tiny chance that there's a virus.  Look at the system monitor and send post all the things running.  A high CPU usage is normal on Ubuntu I think, sometimes I just look at the System monitor without anything running (things open but I'm not calculating Pi or anything similar), and sometimes the usage spikes (on one processor) up to 90%.  But since it's constantly 90%, something is probably running, and Ubuntu doesn't normally use almost any RAM (I have 2GB, and right now, with 16 windows open in 3 windows, it's at 28.8%, which is pretty high for my standards).  If you can't find the problem, maybe you should just reinstall.

The reason it's more likely that there's a virus is because you upgraded, from the Ubuntu website.  Someone could have planted a virus there, and would have been sure it would run because only people using Ubuntu would install the stuff.

Also... when I upgraded, my bios stopped working.  It went straight to Ubuntu.  Here's what I fixed it with... in case you have troubles with the bios.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by the52poet on 2010-06-25
kooia, 
Thanks for the input, but I did a fresh install. (My original hard drive got crippled - 100mb unreadable at the beginning of the drive, but I'll work on that later). When I first encountered the problems, I did run Avira Linux Bootable Virus CD and nothing found - then the hard drive went down after I did a reboot to check out the new upgrade. 

After the fresh install, the problems persisted, so I tried going with Linux Mint 9 and the problems (most) are still there. (It doesn't keep logging me out).

I can run other Operating Systems without the problems showing up, so I think I can safely rule out a virus or hardware problem. Debian works fine, Puppy, DSL, TinyCore and others - I have no problems with them.

---

### Post by Don Barzini on 2010-06-25
> **the52poet said:**
> First problem was being automatically logged out continually and having to log back in.

You may have multiple problems..... but if you have the constant logout problem..... which seems to be a common problem and bug with the latest version of Ubuntu..... you might be able to fix it with the solution I and many other people have employed.

An Xorg developer for Ubuntu put up his own PPA to fix this problem. Not sure if Ubuntu incorporated the fix in it's updates just yet.. they might have, but I'm not completely sure. Have you updated the system since install? (You can do it from a root shell in Recovery Mode).

If you did update, and the problem wasn't fixed... you can start by adding the following repository. In a terminal window do the following...

```
sudo add-apt-repository ppa:bryceharrington/purple
```

Then run ...

```
sudo apt-get update
```

Then run...

```
sudo -apt-get upgrade
```

Reboot the machine afterwards and see if that helps with the constant logout problem.

More info on that bug....

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/539772](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/539772)

---

### Post by the52poet on 2010-06-29
I'm on Linux Mint for the time being, so I may try your advice when I get my other problems and system back to reasonable usability.

My hard drive primary superblock was corrupted, I repartitioned the drive and it works. Since I could not access the drive (even with my Easyrecovery program) I lost about 450 gigs of songs, movies and pictures. Most I can restore, but much is gone for good.

From this point forward, I will use an old 12 gig hard drive to try my upgrades on. This has NOT been fun.

---

