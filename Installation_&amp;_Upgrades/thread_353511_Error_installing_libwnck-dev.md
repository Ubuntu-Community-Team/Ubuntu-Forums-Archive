---
title: "Error installing libwnck-dev"
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by tyler9xp on 2007-02-04
I'm attempting to install avant-window-navigator ([http://code.google.com/p/avant-window-navigator]("http://code.google.com/p/avant-window-navigator"), [http://ubuntuforums.org/showthread.php?p=2093300]("http://ubuntuforums.org/showthread.php?p=2093300")). I'm doing "Option 2"--installing from SVN. When I try to install "libwnck-dev" to compile the code, it gives me the error:

> tyler@tyler-laptop:~/avant-window-navigator$ sudo apt-get install libgtk2.0-dev libwnck-dev libwnck-common libgconf2-dev libglib2.0-dev gnome-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtk2.0-dev is already the newest version.
libwnck-common is already the newest version.
libgconf2-dev is already the newest version.
libglib2.0-dev is already the newest version.
gnome-common is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libwnck-dev: Depends: libwnck18 (= 2.16.1-0ubuntu1) but 2.16.1-0ubuntu1.1 is to be installed
E: Broken packages


I'm using Ubuntu 6.10 Edgy Eft (with XGL and Beryl). Can someone please help me figure this out? Thanx.

---

### Post by chalewa on 2007-02-06
I am having the same issue...

---

### Post by tyler9xp on 2007-02-07
Cool.

I got it to work. First you need to install the correct version of libwnck18, which libwnck-dev needs to work. Type this into the terminal:

```
sudo apt-get install libwnck18=2.16.1-0ubuntu1
```

It will warn you that it needs to downgrade a couple packages ... say Y to let it continue (don't worry--I haven't noticed any problems because of downgrading). It installs and then you can do:

```
sudo apt-get install libwnck-dev
```

It should work. Say something and I'll try to help if it doesn't.

avant-window-navigator looks like it has a lot of potential, but it still has a little bit more to go before it can really be useful.

---

