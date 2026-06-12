---
title: "no graphical boot screen after upgrading to Feisty"
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by alexheizer on 2007-01-26
Hi. First, let me start off by saying everything works after upgrading -- video, gdm, kde, etc. Except when it boots, it flashes my grub splash screen then goes into a text-based boot instead of the graphical boot screen that I had in breezy, dapper and edgy. I used the default for that, so I think it used usplash for the graphical boot screen.

Does anyone know how to switch this back?

As I said, it boots fine, I just would rather have the graphical boot screen back, since it's much more skinable than the ascii text version... :)

-Alex

---

### Post by teaker1s on 2007-01-26
install
[COLOR="Red"]usplash
usplash-theme-ubuntu[/COLOR]

---

### Post by alexheizer on 2007-01-27
> **teaker1s said:**
> install
[COLOR="Red"]usplash
usplash-theme-ubuntu[/COLOR]

Hi,

Sorry, usplash and usplash-theme-ubuntu were both already installed, but I reinstalled them through Synaptic just to make sure (which didn't fix it). 

Is there a program to load at boot time that might have gotten taken out of an RC file somewhere?

thx

---

### Post by Rui Pais on 2007-01-27
hi, have you tried:

```
sudo dpkg-reconfigure linux-image-$(uname -r)
```?

---

### Post by alexheizer on 2007-01-27
> **Rui Pais said:**
> hi, have you tried:

```
sudo dpkg-reconfigure linux-image-$(uname -r)
```?

I just did that. Didn't work.

I did get the error message that mdadm wasn't working. When I upgraded, it asked me if I would like to use that. Since I don't have any software raid I turned that off.
a) Could that be the problem, and
b) how would I turn it back on?

---

### Post by PapaWiskas on 2007-02-15
I have now done three formats and 3 cleand Edgy installs and have this problem, and none of those suggestions worked.

When i was running Dappy on it it was fine.  It all started when I did an upgrade from Dapper to Edgy, that is when Usplash stopped working.

I thought formatting and reinstalling would fix it, but it hasnt.  And I cant find any answers anywhere.....:( :confused:

---

### Post by kinemagician on 2007-02-15
I have the same problem.  The usual screen requesting username never appears.  Pleas help!!!

---

