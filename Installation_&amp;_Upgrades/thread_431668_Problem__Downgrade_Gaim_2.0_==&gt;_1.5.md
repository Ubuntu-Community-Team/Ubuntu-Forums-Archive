---
title: "Problem:  Downgrade Gaim 2.0 ==&gt; 1.5"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by casperlingus on 2007-05-03
Gaim, Pidgin, whatever you want to call it is extremely "buggy" on my fresh feisty install (maybe they're actually features, but I hate it).  I want to downgrade to 1.5, and am surprised at the difficulty in doing so.   Is it possible someone could add 1.5 to the feisty repos?  I'm having a hell of a time pulling this off. 

I've found two posts on the forums about doing so, and I've tried both.  The first one was simply downloading a package and running it:

```
wget http://optusnet.dl.sourceforge.net/sourceforge/gaim/gaim-1.5.0.x86.package
sudo sh gaim-1.5.0.x86.package
```

The wget command didn't work, so I went and found the package on the Pidgin website.  I downloaded it and got:

```
desktop:~/download$ sudo sh gaim-1.5.0.x86.package
gaim-1.5.0.x86.package: 19: Syntax error: "(" unexpected
```


Next I tried to install from source.  Again, the wget didn't work, so I had to go find the tar.bz2 elsewhere:

```
wget http://optusnet.dl.sourceforge.net/sourceforge/gaim/gaim-1.5.0.tar.bz2
tar jxvf gaim -1.5.0.tar.bz2
cd gaim
sudo aptitude install build-essential checkinstall
sudo apt-get build-dep gaim
./autogen.sh #or ./configure if that doesn't work
gmake
sudo checkinstall gmake install
```

I got 98% of the way there then got an error running the .deb file:

```
Selecting previously deselected package gaim.
(Reading database ... 133861 files and directories currently installed.)
Unpacking gaim (from .../gaim_1.5.0-1_i386.deb) ...
dpkg: error processing /home/username/download/gaim-1.5.0/gaim_1.5.0-1_i386.deb (
--install):
 trying to overwrite `/usr/lib/gcc/i486-linux-gnu/4.1.2/collect2', which is also
 in package gcc-4.1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/username/download/gaim-1.5.0/gaim_1.5.0-1_i386.deb
```

There must be an easier way to do this...  Help??
-Casper

---

### Post by casperlingus on 2007-05-03
**Solved:  **

```
sudo apt-get remove gaim gaim-data
sudo cp /etc/apt/sources.list /etc/apt/sources.list~
sudo vim /etc/apt/sources.list
:%s/feisty/dapper/g
:wq
sudo apt-get update
sudo apt-get install gaim gaim-data
sudo cp /etc/apt/sources.list~ /etc/apt/sources.list
sudo apt-get update

```

If you're not famliar with vim, the :%s command is a find&replace command in vim, and :wq writes&quits.  Simply put, you're changing your repos to the dapper repos which used v1.5, then changing back once you've reinstalled gaim.  You'll probably get some errors when you update with the dapper repos, but the errors happen after it's updated the gaim version.

I just got it working, so it's difficult to tell if this is a stable solution (for gaim *and* apt-get), but so far all is well.  I'm getting a bzip2 error on one of my repos when I update, but it hasn't seemed to affected anything.

Cheers,
-Casper

---

### Post by Mr.NiceGuy on 2007-05-05
this works all the way to the last two command and then i get an error:
 Failed to fetch 
[http://ubuntusoftware.info/dists/dapper/all/binary-i386/Packages.gz](http://ubuntusoftware.info/dists/dapper/all/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

what do i do?

---

### Post by casperlingus on 2007-05-07
I actually have no idea.  I assume you got that error when you ran 

```
sudo apt-get install gaim gaim-data
```
...?

Do you have any unusual repos in your sources.list that may not have a dapper-version? 

I'm going to have to ask for backup on this, b/c I'm not good at troubeshooting these things.  In what repo is dapper-gaim ?  Perhaps this solution should be modified so that only the correct dapper repo is in the temporary sources.list...

---

### Post by Mr.NiceGuy on 2007-05-30
i had my gaim 1.5 working but then there were updates and when i updated i didnt see the gaim update so now my gaim-xfire dont work and this solution isnt working anymore... i get this message when i type  in this command in vim          :%s/feisty/dapper/g                              

E486: Pattern not found: feisty 

what can i do?

---

