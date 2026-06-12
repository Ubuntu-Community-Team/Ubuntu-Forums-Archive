---
title: "Install PC without internet"
date: 2005-02-18
forum: Installation &amp; Upgrades
---

### Post by milou on 2005-02-18
Hello. I am searching a way to install universe/multiverse etc...  on a PC without internet connection.
I don't know how to do, I already have the ISO install CD (warty and hoary) but I will want to add other packages, and I don't know how to do.
On the other hand I do have an internet connection at work, so I should be able to download packages if necessary.
Is there a way for such problem ?
For ex. is it possible to make a selection with synaptic, and get a file which could be used to download the selected stuff ?
Any ideas will be nice for me.

PS : I have windows at work ... no linux station

---

### Post by CyrilleMortreux on 2005-02-18
[QUOTE=milou]Hello. I am searching a way to install universe/multiverse etc...  on a PC without internet connection.
I don't know how to do, I already have the ISO install CD (warty and hoary) but I will want to add other packages, and I don't know how to do.
On the other hand I do have an internet connection at work, so I should be able to download packages if necessary.
Is there a way for such problem ?
For ex. is it possible to make a selection with synaptic, and get a file which could be used to download the selected stuff ?
Any ideas will be nice for me.

PS : I have windows at work ... no linux station[/QUOTE]


Input your CDROM in your drive and as root "apt-cdrom" toadd it at your sources.list.

But You will not have all packages availables on one CD, maybe on 1 or 2 DVD ;)

---

### Post by Ste on 2005-02-18
I've been meaning to try this...

Download the packages, will be hard to calculate the dependencies tho. Burn them to disc in windows then copy to /var/apt/cache/arcives/

Then try update that way.

Best of luck.

---

### Post by CyrilleMortreux on 2005-02-18
[QUOTE=Ste]I've been meaning to try this...

Download the packages, will be hard to calculate the dependencies tho. Burn them to disc in windows then copy to /var/apt/cache/arcives/
[/QUOTE]

Well, dependecies are going to be very hard to setlle and why can't you connect to the net from your linux box if you do so under MS ???

---

### Post by milou on 2005-02-18
As I said before, I have no linux at work. I want to use linux at home, but I have no internet at home (at  present and maybe for some weeks or months that will be the same).

---

### Post by Juergen on 2005-02-18
I don't know if this works, but maybe you could try to fetch
dists/warty/*/binary-i386/Packages.gz, same for warty-security and so on,
put them in different dirs at home and add these to your sources.lst.

If that works, you could look what Synaptic wants to get, and fetch the packages the next day at work. 
This could resolve the dependency-problems.

I can run Ubuntu in a Virtual PC at work and just carry around a copy of the download-cache.
Much easier, but probably not an option for you.

---

### Post by CyrilleMortreux on 2005-02-18
[QUOTE=Juergen]

If that works, you could look what Synaptic wants to get, and fetch the packages the next day at work. 
This could resolve the dependency-problems.
.[/QUOTE]

That's right, but what a job !!!  :-k 

Do you have a laptop ? You may find usefull to set up an Ubuntu mirror on and to add it at your linux box (at home) sources.list

First time is long to prepare, then, just have to rsync, or use apt-proxy or something else : 

Package debmirror

    * unstable (net): Debian partial mirror script, with ftp and package pool support
      20050207: all


Package apt-zip

    * unstable (admin): Update a non-networked computer using apt and removable media
      0.13.2: all

---

