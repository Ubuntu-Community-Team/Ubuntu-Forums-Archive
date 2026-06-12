---
title: "Minecraft overviewer gone :("
date: 2012-05-02
forum: Installation &amp; Upgrades
---

### Post by Fenlig on 2012-05-02
Hey guys,

So im running Ubuntu 64bit Server and after the upgrade from 11.04 to 12.04 my Minecraft-overviewer program is missing :(, but no biggy I just reinstall it with a good old sudo apt-get install minecraft-overviewer, but with I get a error.

```
skay@Servertron:~$ sudo apt-get install minecraft-overviewer
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 minecraft-overviewer : Depends: python2.6 but it is not installable
                        Depends: python2.6-imaging but it is not installable
                        Depends: python2.6-numpy but it is not installable
E: Unable to correct problems, you have held broken packages.
```

So when I try to install python im told

```
skay@Servertron:~$ sudo apt-get install python2.6
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package python2.6:i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  python2.6-minimal:i386 libpython2.6:i386 python-gdbm:i386 python-gdbm

E: Package 'python2.6:i386' has no installation candidate

```

And python2.6-minimal:i386 is already installed.

I presume Overviewer just needs to be updated or is there a way i can ignore dependencies?

Kind regards,
Fenlig

---

### Post by Keetveter on 2012-06-20
I would like to see a solution too. I'm experiencing the same problem :(.

---

### Post by Fenlig on 2012-06-21
I solved this ages ago but cannot fully remember how I did it, but I think I had to rebuild it from source rather than installing it through apt-get.

---

### Post by CounterPillow on 2012-06-24
Hi there!
We're currently working on the issue, the problem is that some distribution versions still use python 2.6, and some already python 2.7. This would normally be no problem, but since the install path has the version number in it and the extension has to be compiled for the right version, the developers are struggling to solve this issue with a clean and easy solution. :(

In the mean time, you can do the following:
```
# apt-get install python-numpy python-imaging git build-essential
```clone the git repo in the directory you wish:
```
~$ git clone https://github.com/overviewer/Minecraft-Overviewer.git
```cd into the directory and then build it!
```
~$ cd Minecraft-Overviewer/
:~/Minecraft-Overviewer$ python setup.py build
```You can then run it from source (which is the recommended way, until the package is fixed) by executing ./overviewer.py inside the directory you've cloned into.

You can update Overviewer from git by pulling and rebuilding (not always necessary):
```
:~/Minecraft-Overviewer$ git pull
:~/Minecraft-Overviewer$ python setup.py build
```

If you still have questions, feel free to ask on IRC (FreeNode, #overviewer, Webchat: [http://overviewer.org/irc/](http://overviewer.org/irc/)) or you can also [open an issue on github]("https://github.com/overviewer/Minecraft-Overviewer/issues?direction=desc&sort=created&state=open").

---

### Post by CounterPillow on 2012-09-19
I seem to be unable to edit my reply above, so I will just post this small correction here. As many people have pointed out on our IRC or ran into the problem, it may be helpful to mention that you'll also need to install the *python-dev* package in order to build the Overviewer.

I apologize for any unnecessary thread-bumping that my inability to find an option to edit a post has caused. :(

---

