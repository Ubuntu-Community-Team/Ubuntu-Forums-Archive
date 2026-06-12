---
title: "Ubuntu Server question"
date: 2007-02-26
forum: Installation &amp; Upgrades
---

### Post by darkcyber on 2007-02-26
I have 2 pc's that I cannot even get the Ubuntu or Xbuntu live cd's to boot through, much less get them to install the OS.  Someone recommended using the server edition and install from it. And at the end I could do "apt-get install gnome-desktop-environment" and get the desktop  installed.

My question is how much of a different is there from the regular ubuntu version and the server version.  I really like the regular version and would like to have the same options on this pc, if I could get it to install.  So, if I install the server version and then add the desktop, am I pretty close to having regular ubuntu installed?

Thanks!

---

### Post by taurus on 2007-02-26
Actually, you want to run

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by darkcyber on 2007-02-26
Thanks for the reply.  So, by doing this...i.e. installing the server edition and then adding the desktop, will this be basically the same as if I installed regular ubuntu then? I don't know if there are drastic differences in server and regular ubuntu...thus the reason for the question.

---

### Post by taurus on 2007-02-26
That should give you the same Gnome as if you were installed it from the desktop CD/LiveCD.

---

### Post by ChrisN1313 on 2007-02-26
how do you get the desktop up when your in server mode.

---

### Post by taurus on 2007-02-26
```
sudo /etc/init.d/gdm start
```
or
```
startx
```

---

### Post by darkcyber on 2007-02-27
Thanks for the help...installing server right now!

---

### Post by darkcyber on 2007-02-27
> **taurus said:**
> Actually, you want to run

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```



Well, after I installed server and it rebooted it came back up to a DOS like screen, after I entered the login information.  I entered those 2 commands you listed and nothing happened.  It looked like ubuntu listed some errors and came right back to the DOS type prompt.  So, am I suppose to do something else to get the desktop to come up?  I also tried the command you listed at the bottom of the thread.

---

### Post by taurus on 2007-02-27
After you log in with your username and password, do

```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
```
And if there is an error, can you please post here?

---

