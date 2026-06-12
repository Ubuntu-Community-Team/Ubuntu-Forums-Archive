---
title: "[SOLVED] got disconnected while apt-get was downloading files"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by manishsk on 2008-04-02
Hi
I was doing 

```
sudo apt-get install kubuntu-desktop
```

It started downloading the files. The process was halfway completed. But some how I lost my internet connection and the download got halted.

I needed to reboot my machine to get connected again as I plog was showing some PAD0 timeout when I tried to connect again using pon [i did poff before doing pon again]. (well thats a different problem :mad: need to resolve that too)

Is there anyway I can resume the download or do I need to give the same command again and download everything else again?

Thanks,
Manish

---

### Post by Rocket2DMn on 2008-04-02
I don't know anything about using PPPOE/PPP in linux, but once you get back online you should be able to issue the command again and it will continue where it left off.  kubuntu-desktop is a metapackage that has a bunch of packages for KDE in it, some of which should already be downloaded.
You may get an error telling you to run this command, if so, do it, then proceed normally:
```
sudo dpkg --configure -a
```
That happens when apt-get is interrupted.

---

### Post by manishsk on 2008-04-02
Ran the same command again.

> sudo apt-get install kubuntu-desktop

And yes it started from where it left off! Also it did not gave any error. KDE is functional on my pc now. apt-get is pretty nice tool. :)

Thanks rocket2dmn...

Btw, what this command do exactly?
> sudo dpkg --configure -a

I am marking this tread as solved. I will open separate thread for the internet connection problem.

---

### Post by Rocket2DMn on 2008-04-03
That command just basically resets all packages to a normal state I think, it's a common solution to some problems, esp. when programs get interrupted during special execution sequences (like installing packages or using a lock file).
Good luck with your internet.

---

