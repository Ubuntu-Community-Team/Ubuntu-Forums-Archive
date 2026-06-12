---
title: "Firefox 3 not loading"
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by rootk1t on 2008-06-22
I don't know why, but this version:

firefox_3.0+nobinonly-0ubuntu0.8.04.1_all.deb

Is not loading, I mean the GUI it's not loading. I can see it's icon moving along my mouse, but can't use it.

The only window I see is that where I am asked to restore the previous session or to start a new session.

But actually it's not loading any of it. 

:confused:

---

### Post by rootk1t on 2008-06-22
I'm the only one with this problem?

---

### Post by rootk1t on 2008-06-22
Hello?

---

### Post by perlluver on 2008-06-22
Type firefox in the terminal, and post what it gives you here.

---

### Post by rootk1t on 2008-06-22
> **perlluver said:**
> Type firefox in the terminal, and post what it gives you here.
johny@johny:~$ firefox



That is a blank new row.

As root:

root@johny:/home/john# firefox
No protocol specified
Error: cannot open display: :0.0

---

### Post by perlluver on 2008-06-22
Ok, go to your home folder, and click view hidden files, go to the .mozilla folder, and open up the profiles.ini and change the line startwithlastprofile=1 to a 0.  Then try to open it again.

---

### Post by rootk1t on 2008-06-22
> **perlluver said:**
> Ok, go to your home folder, and click view hidden files, go to the .mozilla folder, and open up the profiles.ini and change the line startwithlastprofile=1 to a 0.  Then try to open it again.

Absolute same thing, same outputs.

edit: It started after a few minutes, but crashed, I mean I can't access it. I have to kill it.

---

### Post by dakal on 2008-06-22
If it takes a few minutes to start Firefox, either your system is seriously underpowered, or there is something very wrong. What kind of CPU, graphics card and how much RAM does it have? What version of Kubuntu is this, I assume Hardy (8.04)?

Try renaming the .mozilla directory to something else, and let Firefox create a completely new profile. See if that helps.

If you don't have any bookmarks or such that you care about you can delete .mozilla, too. I just prefer to rename to move things out of the way when experimenting, myself. :)

---

### Post by murjam on 2008-06-24
> **rootk1t said:**
> I'm the only one with this problem?
You're not alone. I'm having the same issue. Clean firefox installation and removing ~/.mozilla directory do not help. Everything worked fine with beta 5, but after the firefox 3 (not beta) came from ubuntu repos, it got broken. I'm using firefox 2 until i find a solution.
```
sudo apt-get install firefox-2
```

---

### Post by jonez176 on 2008-06-27
My FireFox was doing this until I realized I was very low on disk space.

You probably have sufficient space but I'm just letting everyone know because FireFox did not make it obvious that it was having a memory-related issue.

---

### Post by murjam on 2008-06-29
I've got over 4GB free space on my root partition - should not be an issue :roll:

Somehow i now managed to get this output when trying to run firefox as root (usually there is still no output to command line):

> Obtaining the module object from Python failed.

Traceback (most recent call last):
cant import cStringIO
<type 'exceptions.ImportError'>: /usr/lib/python2.5/lib-dynload/time.so: undefined symbol: PyExc_ValueError
Segmentation fault

---

### Post by murjam on 2008-07-02
I occasionally waited for minutes and my firefox showed up, but just loads and runs extremely slow, following this thread now: [http://ubuntuforums.org/showthread.php?t=824754](http://ubuntuforums.org/showthread.php?t=824754)

---

### Post by robertchahine on 2008-07-02
how did you run it as root? 
you should type
```
gksudo firefox
```.
because the sudo firefox, may cause that slow and other graphical problems

---

### Post by murjam on 2008-07-02
```
gksudo firefox-3.0
```
produces the same output and takes minutes to load.

EDIT: it's not using CPU power when "loading" and hangs very, very easily when finally started.

---

### Post by rootk1t on 2009-01-04
Problem continues with firefox 3.0.5 after an upgrade to this version.

I am using Kubuntu 8.04 i386.

---

