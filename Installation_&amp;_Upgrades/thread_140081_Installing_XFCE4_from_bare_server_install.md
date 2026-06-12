---
title: "Installing XFCE4 from bare server install"
date: 2006-03-05
forum: Installation &amp; Upgrades
---

### Post by Disorder on 2006-03-05
I'm installing Ubuntu on an old P2 333Mhz machine and need to install a basic windows mananger. I was told XFCE4 was great for older machines.

How do I go about installing it from the command line and then configuring it.

I've tried using 'apt-get install xfce4' to no avail.

---

### Post by taurus on 2006-03-05
At the prompt, type

```

sudo apt-get install xubuntu-desktop

```

---

### Post by Disorder on 2006-03-05
It's saying it could not find the package

---

### Post by aysiu on 2006-03-05
Follow this guide:
[http://www.psychocats.net/linux/xubuntu](http://www.psychocats.net/linux/xubuntu)

---

### Post by Disorder on 2006-03-07
That guide works fine up untill it says to "startx" 
I'm getting command not found

---

### Post by aysiu on 2006-03-07
That's weird.

Did you try 8b. (the thing about GDM)?

---

### Post by Disorder on 2006-03-07
no i did not, working with extremly limited HD space (6GB)

---

### Post by kaamos on 2006-03-07
Try startxfce4 instead of startx. You could also install wdm as a login manager, it should not pull any gnome libraries with it like gdm.

---

### Post by Disorder on 2006-03-07
startxfce4 does not work either

---

### Post by kaamos on 2006-03-07
are you sure you have xfce4-utils installed (should come with xubuntu-desktop) ?

[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=startxfce4&searchmode=searchfiles&case=insensitive&version=breezy&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=startxfce4&searchmode=searchfiles&case=insensitive&version=breezy&arch=i386)

---

### Post by Disorder on 2006-03-09
I installed xubuntu-desktop

---

### Post by bonzodog on 2006-03-09
Have you installed gdm/wdm/xdm? To start an Xsession you need the package xinit, which is a dependency of gdm/wdm/xdm. otherwise, install the xinit package seperately.

---

### Post by Disorder on 2006-03-10
I installed xdm and xinit via apt. 

I then typed sudo /etc/init.d/xdm stop and hit enter

It's said starting X display manager and nothing happened

I then typed sudo /etc/init.d/xdm stop and recieved the following
Stoping X display mananger: xdm not running (var/run/xdm.pid not found)

I then tryed "startx" and recieved

xauth: creating new authority file (home/username/ .serverauth.6106)
/etc/x11/xinit/xserverrc: line 2: usr/bin/x11/X: no such file or directory
/etc/x11/xinit/xserverrc: line 2: exec: usr/bin/x11/X: Cannot execute:no such file or directory
xinit: Server error

---

### Post by Disorder on 2006-03-11
^

---

### Post by Disorder on 2006-03-12
any idea's?

---

