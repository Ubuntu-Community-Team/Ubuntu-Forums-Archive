---
title: "linux video studio install problems"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by juantovarm on 2006-11-05
Hello, I've been trying to install linux video studio from code, i ran into problems because i am a newbie and i do not know what this means, if anyone could help...

checking for X... no
checking for XvQueryExtension in -lXv... no
configure: error: Could not find Xv libraries


Thanx
Juan

---

### Post by taurus on 2006-11-05
Do you even have X running???

---

### Post by juantovarm on 2006-11-05
> **taurus said:**
> Do you even have X running???

What is X? how do i install X?

---

### Post by taurus on 2006-11-05
> **juantovarm said:**
> What is X? how do i install X?
Oh dear...

Did you do a server install or how did you install it on your machine?  What happens when you type this from a terminal?

```
startx
```
If you get an error message saying that the command not found, then you need to install a window manager first...

```

sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start

```

---

### Post by juantovarm on 2006-11-05
> **taurus said:**
> Oh dear...

Did you do a server install or how did you install it on your machine?  What happens when you type this from a terminal?

```
startx
```
If you get an error message saying that the command not found, then you need to install a window manager first...

```

sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start

```

I went to the ubuntu's website, downloaded an iso image from one of the links, burnt it and installed it from there

I get this message

xauth:  creating new authority file /home/juan/.serverauth.12984


Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

---

### Post by taurus on 2006-11-05
When you boot up Ubuntu, do you see a splash screen and after a few second, see a login screen with music or do you only a prompt asking you for a login name?

---

### Post by juantovarm on 2006-11-05
> **taurus said:**
> When you boot up Ubuntu, do you see a splash screen and after a few second, see a login screen with music or do you only a prompt asking you for a login name?

splash scree, after a few seconds, login screen and music

---

### Post by taurus on 2006-11-05
So did you log in from that GUI screen with your username and password?

---

### Post by juantovarm on 2006-11-06
> **taurus said:**
> So did you log in from that GUI screen with your username and password?

yes, i did and i always log in that way

---

