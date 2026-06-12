---
title: "Gnutella update giving troubles"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by layers on 2010-11-09
My gtk-gnutella 0.96.6 apparently has become "ancient" but I don't know how to fix it, and I cannot seem to find anything relevant inline. Would there be one line terminal command to update it? (I've never build something from files only)

```
ibo@ibo-laptop:~$ sudo apt-get update gtk-gnutella
[sudo] password for ibo: 
E: The update command takes no arguments
ibo@ibo-laptop:~$ sudo apt-get gtk-gnutella
E: Invalid operation gtk-gnutella
ibo@ibo-laptop:~$ 

```

---

### Post by sanderj on 2010-11-10
```

sudo apt-get install gtk-gnutella
```

---

### Post by layers on 2010-11-10
```
ibo@ibo-laptop:~$ sudo apt-get install gtk-gnutella
[sudo] password for ibo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gtk-gnutella is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ibo@ibo-laptop:~$ 
```

I still get the "Ancient" warning upon opening Gnutella.

---

### Post by sanderj on 2010-11-10
0.96.6 = "ancient"
0.96.8 = current

Aha ... I wouldn't bother.

*If* you want to make ... get the source, bunzip2 it, untar it, read README.Debian for the dependencies, then readme README for the easy build method, and it should work.

However, as said: I wouldn't bother.

---

### Post by layers on 2010-11-10
But it doesn't work otherwise. No connections. Is there anywhere some kind of an option?

---

### Post by ram4 on 2010-11-11
> **layers said:**
> But it doesn't work otherwise. No connections. Is there anywhere some kind of an option?

There's no option to connect.  You just need to get the latest SVN version:

svn co [https://gtk-gnutella.svn.sourceforge.net/svnroot/gtk-gnutella/trunk/gtk-gnutella/](https://gtk-gnutella.svn.sourceforge.net/svnroot/gtk-gnutella/trunk/gtk-gnutella/)

Then look at the README.Debian file which will give you all the instructions you need.
Unfortunately, even 0.96.8 may not connect correctly to Gnutella currently.  However the latest SVN version should correctly bootstrap you.

Don't blame gtk-gnutella for this.  This is not something it can do anything about as bootstrapping into the network is an operation requiring external resources that can change over time.

Once you have bootstrapped, leave the program running 24x7 and you'll never need to bootstrap again even if you have to stop for a few days.  In any case, NEVER NEVER delete your ~/.gtk-gnutella directory or you will have to bootstrap again.

Good luck.

---

### Post by layers on 2010-11-11
OK, then is this going to happen every single time they come up with a new minor revision of the program? If yes, are there any other non-complicated-GUI peer-to-peer programs, like gnutella?

---

### Post by ram4 on 2010-11-12
> **layers said:**
> OK, then is this going to happen every single time they come up with a new minor revision of the program? If yes, are there any other non-complicated-GUI peer-to-peer programs, like gnutella?

You misunderstood: it has nothing to do with gtk-gnutella itself or which version number it has.  It has to do with the Gnutella global bootstrapping environment which changes and for which older versions of the program are not (and cannot be) aware of.

Gnutella is one of the best networks because it's completely open and decentralized. And gtk-gnutella is the best program to use Gnutella on Ubuntu or other UNIX machines.

Did you try to grab the latest SVN version and build it like I recommended?  Did it work (i.e. did you now manage to bootstrap to the network)?

---

### Post by layers on 2010-11-12
> **ram4 said:**
> You misunderstood: it has nothing to do with gtk-gnutella itself or which version number it has.  It has to do with the Gnutella global bootstrapping environment which changes and for which older versions of the program are not (and cannot be) aware of.

Gnutella is one of the best networks because it's completely open and decentralized. And gtk-gnutella is the best program to use Gnutella on Ubuntu or other UNIX machines.

Did you try to grab the latest SVN version and build it like I recommended?  Did it work (i.e. did you now manage to bootstrap to the network)?

No I haven't done anything yet.

I just installed all those libraries and packages via terminal. Now I'm stuck, at part 2: I think I'm supposed to have some files and then run a command to build something.

---

### Post by ram4 on 2010-11-12
> **layers said:**
> No I haven't done anything yet.

I just installed all those libraries and packages via terminal. Now I'm stuck, at part 2: I think I'm supposed to have some files and then run a command to build something.

Step 2 is to run:

$ fakeroot debian/rules binary

at the shell prompt ("$").  That should build the .deb file for you, and then you can install it using:

# dpkg --install FILE.deb

Where FILE.deb is the name of the generated file. Works for me.

---

### Post by layers on 2010-11-12
> **ram4 said:**
> Step 2 is to run:

$ fakeroot debian/rules binary

at the shell prompt ("$").  That should build the .deb file for you, and then you can install it using:

# dpkg --install FILE.deb

Where FILE.deb is the name of the generated file. Works for me.

```
ibo@ibo-laptop:~$ fakeroot debian/rules binary
/usr/bin/fakeroot: line 176: debian/rules: No such file or directory
ibo@ibo-laptop:~$
```

---

### Post by ram4 on 2010-11-14
> **layers said:**
> ```
ibo@ibo-laptop:~$ fakeroot debian/rules binary
/usr/bin/fakeroot: line 176: debian/rules: No such file or directory
ibo@ibo-laptop:~$
```

In which directory are you?  What is the content of that directory?

---

### Post by layers on 2010-11-14
> **ram4 said:**
> In which directory are you?  What is the content of that directory?

```
ibo@ibo-laptop:~$ pwd
/home/ibo
ibo@ibo-laptop:~$ ls
Desktop    electronicver.cpp       hs_err_pid4526.log  Pictures   Videos
Documents  examples.desktop        Library             Public
Downloads  gtk-gnutella-downloads  Music               Templates
ibo@ibo-laptop:~$ fakeroot debian/rules binary
/usr/bin/fakeroot: line 176: debian/rules: No such file or directory
ibo@ibo-laptop:~$ 


```

I really have no idea which the files are, and where there are.

---

### Post by ram4 on 2010-11-15
> **layers said:**
> ```
ibo@ibo-laptop:~$ pwd
/home/ibo
ibo@ibo-laptop:~$ ls
Desktop    electronicver.cpp       hs_err_pid4526.log  Pictures   Videos
Documents  examples.desktop        Library             Public
Downloads  gtk-gnutella-downloads  Music               Templates
ibo@ibo-laptop:~$ fakeroot debian/rules binary
/usr/bin/fakeroot: line 176: debian/rules: No such file or directory
ibo@ibo-laptop:~$ 


```I really have no idea which the files are, and where there are.

You have to run this command first:

svn co  [https://gtk-gnutella.svn.sourceforge.net/svnroot/gtk-gnutella/trunk/gtk-gnutella/](https://gtk-gnutella.svn.sourceforge.net/svnroot/gtk-gnutella/trunk/gtk-gnutella/)

This will create a gtk-gnutella directory.  You can then cd to it and run the fakeroot command I told you about.

You may need to

# apt-get install subversion

to be able to access the "svn" command.

---

### Post by layers on 2010-11-15
> **ram4 said:**
> You have to run this command first:

svn co  [https://gtk-gnutella.svn.sourceforge.net/svnroot/gtk-gnutella/trunk/gtk-gnutella/](https://gtk-gnutella.svn.sourceforge.net/svnroot/gtk-gnutella/trunk/gtk-gnutella/)

This will create a gtk-gnutella directory.  You can then cd to it and run the fakeroot command I told you about.

You may need to

# apt-get install subversion

to be able to access the "svn" command.

Alright! So all I those instruction on their package is missing is the ```
svn co
``` command. Thanks!

---

### Post by sanderj on 2010-11-15
You can try the easy way:

First:
sudo apt-get install gtk-gnutella

then go to [http://stinker.serveftp.net:8000/gtkgnutella/](http://stinker.serveftp.net:8000/gtkgnutella/) and download the *correct* version depending on your Ubuntu version and "bitness", in my case gtk-gnutella_0.96.8u~svn17408~lucid_amd64.deb . 
After downloading, open the file by double clicking it, and install it with Package Installer.

That will give you gtk-gnutella 0.96.8 stable installed on your system

HTH

---

### Post by ram4 on 2010-11-15
> **sanderj said:**
> 
That will give you gtk-gnutella 0.96.8 stable installed on your system


The problem is: 0.96.8 is no longer capable of easily bootstrapping to Gnutella. This is due to the fact that when LimeWire went down, they took with them all the UDP Host Caches which were hardwired in the program and which are necessary for joining the network initially.

This is why I was suggesting that the original poster download and compile the latest (unstable, sure, but functional) version on his system.  That version will correctly bootstrap.

---

### Post by sanderj on 2010-11-15
> **ram4 said:**
> The problem is: 0.96.8 is no longer capable of easily bootstrapping to Gnutella. This is due to the fact that when LimeWire went down, they took with them all the UDP Host Caches which were hardwired in the program and which are necessary for joining the network initially.

This is why I was suggesting that the original poster download and compile the latest (unstable, sure, but functional) version on his system.  That version will correctly bootstrap.

I see. [http://stinker.serveftp.net:8000/gtkgnutella/gtkgnutella.html](http://stinker.serveftp.net:8000/gtkgnutella/gtkgnutella.html) has the newest version (and a better overview of versions): "Currently 0.96.9u is available.  Page last updated 11-10-2010"

So the OP can download the relevant .DEB.

HTH

---

### Post by ram4 on 2010-11-15
> **sanderj said:**
> I see. [http://stinker.serveftp.net:8000/gtkgnutella/gtkgnutella.html](http://stinker.serveftp.net:8000/gtkgnutella/gtkgnutella.html) has the newest version.

So the OP can download the relevant .DEB.


Right, good pointer.

Only the most temerarious should run the latest SVN and compile it themselves. Although SVN is usually fairly usable (but still experimental).  You just need to be willing to report bugs on the #gtk-gnutella channel (irc.freenode.net) when the SVN version crashes :)

---

