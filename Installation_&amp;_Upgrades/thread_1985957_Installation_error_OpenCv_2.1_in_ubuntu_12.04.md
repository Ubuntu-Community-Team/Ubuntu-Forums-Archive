---
title: "Installation error OpenCv 2.1 in ubuntu 12.04"
date: 2012-05-24
forum: Installation &amp; Upgrades
---

### Post by stbb24 on 2012-05-24
I'm trying to install opencv 2.1 in ubuntu 12.04 using the instructions i found here [http://www.samontab.com/web/2010/04/installing-opencv-2-1-in-ubuntu/](http://www.samontab.com/web/2010/04/installing-opencv-2-1-in-ubuntu/) but i get this error 

```

sudo apt-get install build-essential libgtk2.0-dev libavcodec-dev libavformat-dev libjpeg62-dev libtiff4-dev cmake libswscale-dev libjasper-dev
[sudo] password for sandz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
cmake is already the newest version.
libavcodec-dev is already the newest version.
libavformat-dev is already the newest version.
libgtk2.0-dev is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libtiff4-dev : Depends: libjpeg-dev
E: Unable to correct problems, you have held broken packages.

```Also as my last resort i will just reinstall ubuntu and start from scratch. Can I uninstall ubuntu using the terminal??

Thanks in advance :)

---

### Post by stbb24 on 2012-05-24
by the way just to add i already tried sudo apt-get install libjpeg-dev but i just get the same error

---

### Post by sikander3786 on 2012-05-24
As you said you've already tried, but we want to see the exact error message from this command:

```
sudo apt-get install libjpeg-dev
```

Because, the package is available in the main Precise repositories:

[http://packages.ubuntu.com/search?keywords=libjpeg-dev&searchon=names&suite=precise&section=all](http://packages.ubuntu.com/search?keywords=libjpeg-dev&searchon=names&suite=precise&section=all)

---

### Post by stbb24 on 2012-05-24
So I've already tried installing all the packages needed using Ubuntu  Software Center one by one and I thought that should already work fine  but when I tried running the code in the terminal again just to make sure that there already installed I get a new error.

So this is the code and the error that i get
```

sudo apt-get install build-essential libgtk2.0-dev libavcodec-dev libavformat-dev libjpeg62-dev libtiff4-dev cmake libswscale-dev libjasper-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
cmake is already the newest version.
libavcodec-dev is already the newest version.
libavformat-dev is already the newest version.
libgtk2.0-dev is already the newest version.
libjasper-dev is already the newest version.
libswscale-dev is already the newest version.
libtiff4-dev is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libjpeg-turbo8-dev : Conflicts: libjpeg62-dev but 6b1-2ubuntu1 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```

---

### Post by sikander3786 on 2012-05-24
Try using 'aptitude' and keep a close eye on what it is going to install, and make sure it isn't going to remove any important packages:

```
sudo apt-get install aptitude
sudo aptitude install <packages>
```

---

### Post by raja.genupula on 2012-05-24
```
sudo apt-get install -f
```

```
sudo apt-get update
sudo apt-get dist-upgrade
```

do them one by one in your terminal .

---

### Post by stbb24 on 2012-05-24
I can't really use aptitude since it's going to uninstall important packages :(

---

### Post by sikander3786 on 2012-05-24
> **stbb24 said:**
> I can't really use aptitude since it's going to uninstall important packages :(
Can you post the outputs?

---

### Post by gutux on 2012-06-03
Hello all,

i get my self in pretty much the same trouble.
Since i want to try and use Sikuli-IDE, it seems,
OpenCV2.1 is needed. On my old BOX P4-2,66GHz CPU,
i did already use it, installed on Kubuntu 11.10,
and later ubgraded to 12.04.
Now setup 12.04 on my new BOX, i7 3770k CPU, with
12.04 straigt away, there is no way to get it go.
Reading on Projects Page, i get the feeling, that
OpenCV2.1 is mandatory.
Seeing the same instruction as the Thread-Starter, 
i can see, that there is NO WAY, to get the dependencies
right. Either can install libtiff4-dev OR libjpeg62-dev.
Because the moment libjpeg62 gets installed, libtiff4
will be removed. Pckage is "glued" to libjpeg8.
So i guess, i will have to wait, till there comes some
improvement for hyperhreading CPU's and those librarys
before i can continue exploring Sikuli.

best regards
gutux

---

