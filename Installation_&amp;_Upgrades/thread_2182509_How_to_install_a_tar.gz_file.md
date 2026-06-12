---
title: "How to install a tar.gz file?"
date: 2013-10-21
forum: Installation &amp; Upgrades
---

### Post by blake4 on 2013-10-21
The tar.gz file is pcmonitor.tar.gz 

I'd like to install the software through Terminal.

---

### Post by Lars Noodén on 2013-10-21
I would first check the repositories for the program.  Look in the Software Center or the Synaptic to see if the program is there.  If it is, you'll save tons of work and worry by using that one.  

Otherwise, make a directory and open the tarball there.  Then look for the files README or INSTALL and follow the instructions there.

```

mkdir X
cd X
tar zxf ../pcmonitor.tar.gz 
less README
less INSTALL

```

But really that is last resort.  Doing it through the package manager will take care of dependencies as well as automatically notify you of updates and security patches.

---

### Post by slickymaster on 2013-10-21
After downloading and placing it in your home directory, open a terminal and run the following command  to unpack it```
tar xzvf pcmonitor.tar.gz
```This will create a directory named pcmonitor. After that to run install do this```
sudo ./install
```The use of **sudo** is because the installation needs root privileges. From here on the installation should take over.

Please note that this install is not the usual```
tar xvzf *.tar.gz
cd *
./configure [options]
make
sudo make install
```

---

### Post by heir4c on 2013-10-21
I think, this is what you want to install?:
[http://www.mobilepcmonitor.com/](http://www.mobilepcmonitor.com/)

You must have installed java on your system.

You must first unpack the tar.gz file to your home folder or to what folder you want. It will create a folder with the name: pcmonitor.
Than you must open a terminal and change to the directory where you unpack the file. If there NOT in your home folder you need first to change to that directory and the pcmonitor folder, so if it is in the Downloads folder, type:
```
cd Downloads/pcmonitor
```
Then you must run the install script as root:
```
sudo ./install
```

Then you get (with your username of course):

> gerolf@GerolfE350M1M:~/Downloads/pcmonitor$ sudo ./install

Welcome to PC Monitor version 3.1.1 (build 20830)
For support please visit www. mobilepcmonitor.com or send an email to support@ mobilepcmonitor.com

java version "1.7.0_25"
OpenJDK Runtime Environment (IcedTea 2.3.12) (7u25-2.3.12-4ubuntu3)
OpenJDK 64-Bit Server VM (build 23.7-b01, mixed mode)
Enter the installation path [/opt/pcmonitor]:
 
Click Enter.
Then answer the questions there will be ask.

For further information look at this tutorial:
Look out! it is a tutorial for on CentOS (used rpm and yumi instead of deb and apt-get) But when you read all the stuff you can use something in this tutorial:
[http://forum.mobilepcmonitor.com/topic/354-installation-tutorial/](http://forum.mobilepcmonitor.com/topic/354-installation-tutorial/)

---

### Post by blake4 on 2013-10-21
I'm still not getting it installed. This is a bit wierd. I've had no problems installing other tar.gz files. Interesting. I'll get back here in a bit.

---

### Post by heir4c on 2013-10-22
Where you download the packages? In your home folder or downlaods folder or...?
And you right click on it and unpack it?

---

