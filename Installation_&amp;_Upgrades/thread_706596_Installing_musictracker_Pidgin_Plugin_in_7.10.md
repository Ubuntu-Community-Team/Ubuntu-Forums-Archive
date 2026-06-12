---
title: "Installing musictracker Pidgin Plugin in 7.10"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by Ankhwatcher on 2008-02-24
Hello all, pleased to make your acquaintance! I'm Ankhwatcher, but you can call me ANkh.

I've been running Gutsy Gibbon on my retired dell 4600 desktop for a couple of weeks now.
I've managed through a method of copy/paste/pray to get by so far, and install and run an NX server (It works! I'm so proud).
But I've really been stumped trying to install something that will display my current song in rythmbox in pidgin.
A google search came up with [Music Tracker]("http://code.google.com/p/musictracker/") which sounds like just what I wanted. But sadly installing it involves a lot of prerequisites, and I'm running around the internet in circles trying to get it to work. Some guidance would be appreciated.

Thanks in advance,
-ANkh

---

### Post by rebegin on 2008-02-28
please post the last 10 lines of what you get in the terminal.
i had to install only 2 extra packages to compile it successfully but i might had some other packages already installed:

```
sudo apt-get install libpcre-ocaml-dev pidgin-dev
```

---

### Post by Ankhwatcher on 2008-02-28
Hey! Thanks for responding!
Okay here is the last ten lines:
```
Setting up ocaml-nox (3.09.2-9ubuntu1) ...

Setting up libpcre3-dev (7.4-0ubuntu0.7.10.2) ...
Setting up ocaml-findlib (1.1.2pl1-1build1) ...

Setting up libpcre-ocaml-dev (5.11.1-2) ...

Setting up libpurple-dev (1:2.2.1-1ubuntu4.1) ...
Setting up pidgin-dev (1:2.2.1-1ubuntu4.1) ...

Errors were encountered while processing:
 proftpd
 gproftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

p.s. as a side note, I'm enjoying a certain malicious glee from watching a "click here to see a picture of you" virus working its way through my msn contacts.

---

### Post by rebegin on 2008-02-28
it seems to have problems with the proftpd package which i think nothing to do with pidgin. try to reinstall it:

```
sudo apt-get install --reinstall proftpd gproftpd
```

if you still get error messages, you could also try this command:

```
sudo apt-get -f install
```

or you could also try to remove those packages:

```
sudo apt-get remove proftpd
```

i hope it helps.

---

### Post by Ankhwatcher on 2008-02-28
I ran option three, then the original code again. Result:
```

user@server:~$ sudo apt-get install libpcre-ocaml-dev pidgin-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libpcre-ocaml-dev is already the newest version.
pidgin-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
 No sign of the app in pidgin though.

---

### Post by rebegin on 2008-02-28
and did youtry to install the program again?

at the directory where you have extracted the sourcecode of musictracker:
```
./configure
```

```
make
```

```
sudo make install
```

---

### Post by Ankhwatcher on 2008-02-29
Yay! it worked! Thank you!

As I side note I got quite a laugh from the words already in the status filer!
I think I'll just set it to 'Billy Joel'... there are some things my friends just don't need to know about me!

I can delete the installer folder now, right?

---

### Post by rebegin on 2008-02-29
i think you can delete the installer folder but usually i keep it, in case i want to uninstall the program.
all the best.

---

### Post by gerxrdo on 2008-04-26
this is getting really annoying :/

when i try to install this i get this error

"*** 'pkg-config --modversion glib-2.0' returned 2.8.5, but GLIB (2.12.11)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error:
*** GLib 2.0 is required to build MusicTracker; please make sure you have the
*** GLib development headers installed. The latest version of GLib is always
*** available at [http://www.gtk.org/](http://www.gtk.org/).


i am pretty sure i have this install but i don't know why i am still getting it :|

help !

---

### Post by xMoDx on 2008-06-10
for Ubuntu Hardy users check this post for musictracker installation guide

[http://ubuntuforums.org/showthread.php?p=5160342](http://ubuntuforums.org/showthread.php?p=5160342)

---

### Post by Ankhwatcher on 2008-06-11
BTW I reinstalled to Kubuntu, where I was able to install pidgin-musictracker straight from Adept Manager; which has officially become my favourite thing ever!

---

