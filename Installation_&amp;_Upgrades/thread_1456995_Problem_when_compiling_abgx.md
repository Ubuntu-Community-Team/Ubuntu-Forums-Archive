---
title: "Problem when compiling abgx"
date: 2010-04-18
forum: Installation &amp; Upgrades
---

### Post by frangoitia on 2010-04-18
Well, Im having problems when compiling abgx360gui. I compiled the abgx360 and it work but I want to compile the gui now, because otherwise it is very difficult to use it. 
And when I try to compile it, the following happens.

root@user-desktop:~/Descargas/abgxgui# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... 
configure: error: C++ compiler cannot create executables
See `config.log' for more details.

Any help with be apreciated.
Thanks in advance.

---

### Post by frangoitia on 2010-04-18
Well, Im having problems when compiling abgx360gui. I compiled the abgx360 and it work but I want to compile the gui now, because otherwise it is very difficult to use it.
And when I try to compile it, the following happens.

root@user-desktop:~/Descargas/abgxgui# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name...
configure: error: C++ compiler cannot create executables
See `config.log' for more details.

Any help with be apreciated.
Thanks in advance.

---

### Post by sisco311 on 2010-04-18
You have to install build-essential:
```
sudo apt-get install build-essential
```
and libwxgtk2.8-dev:
```
sudo apt-get install libwxgtk2.8-dev
```

EDIT: 

Don't compile it as root, only the installation needs root privileges:
```
./configure
make
sudo make install
```

---

### Post by Iowan on 2010-04-18
From Code of Conduct:> Please do not cross post, or post the same thing in multiple locations.Threads merged.

---

### Post by frangoitia on 2010-04-18
> **sisco311 said:**
> You have to install build-essential:
```
sudo apt-get install build-essential
```
and libwxgtk2.8-dev:
```
sudo apt-get install libwxgtk2.8-dev
```

EDIT: 

Don't compile it as root, only the installation needs root privileges:
```
./configure
make
sudo make install
```
Thank you very much. It worked.
Sorry for doing two threads. It s just that I realised that I had put the thread in the wrong area. It wont happen again.

---

### Post by sisco311 on 2010-04-18
> **frangoitia said:**
> Thank you very much. It worked.

You're welcome!


Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

> **frangoitia said:**
> 
Sorry for doing two threads. It s just that I realised that I had put the thread in the wrong area. It wont happen again.

You can use the [IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG] button to ask a moderator to move your thread in the appropriate sub-forum. In this case, I think, the general help forum is more appropriate, since installations & updates is for questions about upgrading and installation of Ubuntu.

---

