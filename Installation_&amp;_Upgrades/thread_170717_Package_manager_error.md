---
title: "Package manager error"
date: 2006-05-05
forum: Installation &amp; Upgrades
---

### Post by theaffman on 2006-05-05
Today I tried to install kubuntu-desktop, but foolishly ran out of disk space.  Anarky ensued and after learning to delete from command line and clearing some space got things working again. However when running the Package manager i get this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

 So I run that command, and it hangs on the following:

bryan@ubuntu:~$ sudo dpkg --configure -a
Password:
dpkg: dependency problems prevent configuration of python-kde3:
 python-kde3 depends on python2.4-kde3; however:
  Package python2.4-kde3 is not installed.
dpkg: error processing python-kde3 (--configure):
 dependency problems - leaving unconfigured
Setting up debtags (1.4+svn20050912-0ubuntu1) ...
Get:1 [http://people.debian.org/~enrico/tags/tags-current.gz](http://people.debian.org/~enrico/tags/tags-current.gz) [215kB]
Get:2 [http://people.debian.org/~enrico/tags/vocabulary.gz](http://people.debian.org/~enrico/tags/vocabulary.gz) [14.5kB]
Fetched 230kB in 8s (26.3kB/s)
Reading tag data and vocabulary for [http://people.debian.org/~enrico/tags/](http://people.debian.org/~enrico/tags/)...
Writing system vocabulary...
Writing merged tag database...


Help, i just want to fix the package manager so that i can try again.

---

### Post by Sef on 2006-05-05
Try this from the Terminal:

sudo apt-get install python2.4-kde3

then 

sudo apt-get install python-kde3

or you might be able to do this

sudo apt-get install python2.4-kde3 python-kde3

---

### Post by theaffman on 2006-05-05
Thank You i tried that but it didn't work, it just came up with the same error.

Any body else with any ideas?

---

### Post by Sef on 2006-05-05
how many times did you do try    dpkg --configure -a

Sometimes if you do it a few times it will take care of the problem.

---

### Post by theaffman on 2006-05-06
About six so far.  It seems to be the Python package that is the problem. Is there not some way to clear the cache, or do something to reset to whole package manager, and then just start again?

---

### Post by Sef on 2006-05-06
Since you are running Kubuntu was told to use this command instead of sudo.

Kdesu apt-get install python2.4-kde3

then

kdesu apt-get install python-kde3

---

### Post by theaffman on 2006-05-07
ahh you see now, i'm still using gnome because of the lack of disk space i'll try that though.

motoring news rss

---

### Post by Sef on 2006-05-10
> ahh you see now, i'm still using gnome

Then try this:

sudo apt-get install python2.4-kde3

---

