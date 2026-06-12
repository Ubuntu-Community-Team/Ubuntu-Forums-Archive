---
title: "[ubuntu] Installing Lotus Notes 9.0.1 on 15.10 Wily"
date: 2016-03-30
forum: Installation &amp; Upgrades
---

### Post by havanahjoe on 2016-03-30
There are many blog posts and threads that talk about getting Lotus Notes to run on Ubuntu 64 bit (since IBM only builds 32 bit versions of the Linux versions). Most of those guides are for 12.04 or 14.04 so I wanted to write this up to show what I had to do to make it work on 15.10. Not a lot changed, but it wasn't very difficult.

First, you need the .deb package. You can get the .tar file from IBM or get it from your trusty IT department.

We need to add i386 architecture support
```

sudo dpkg --add-architecture i386
sudo apt-get update
```

Then we can install the 32 bit libraries that Notes requires:

```
sudo apt-get install gdb:i386 libart-2.0-2:i386 libasound2:i386 libatk1.0-0:i386 libbonobo2-0:i386 libbonoboui2-0:i386 libgconf2-4:i386 libgnome-desktop-2-17:i386 libgnomeui-0:i386 libjpeg62:i386 libpam0g:i386 libstdc++6:i386 libxkbfile1:i386 libxp6:i386 libxss1:i386 libxt6:i386 libxtst6:i386 liborbit2:i386 libpango1.0-0:i386
```

apt will take care of any other dependencies using the wily repositories.

After all it's done, you can use dpkg to install the Notes .deb package

```
sudo dpkg -i ibm-notes-9.0.1-1.i586.deb
```

To install sametime, you need to edit the .deb and remove an old dependency:

```
sudo dpkg -X ibm-sametime-9.0.1.i586.deb temp 
sudo dpkg -e ibm-sametime-9.0.1.i586.deb temp/DEBIAN 
vi temp/DEBIAN/control -- replace iproute with iproute2 or remote iproute
sudo dpkg -b st ibm-sametime-9.0.1.i586.deb 
```

I used 'temp' as a folder above but you can use whatever you want. The above instructions were taken from [here]("http://woonjas.linuxnerd.org/web/woonblog.nsf/d6plinks/NWEA-9QARJT")

Now you can install Sametime

```
sudo dpkg -i ibm-sametime-9.0.1.i586.deb

```

That's it. Now go bug your IT department to move away from Lotus Notes. I bitch at mine ALL the time.

---

