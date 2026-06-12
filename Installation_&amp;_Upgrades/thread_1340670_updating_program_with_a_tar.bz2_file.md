---
title: "updating program with a tar.bz2 file"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by tinytim174 on 2009-11-28
hi,

I'm trying to upgrade vuze, however its not available thru synaptic, and is only available as a tar.bz2.

I have DL'd to tmp, and extracted to tmp/vuze, but I don't know how to make the new version overwrite the old.

I've spent an hour trying to find a solution, now i feel like a numptey.

Any pointers appreciated

(I'm using 9.10)

---

### Post by tinytim174 on 2009-12-05
bump.  is this really that easy?  I spent hours still searching for an answer, and still drawing blanks.

any help appreciated

---

### Post by tommcd on 2009-12-05
Vuze is in the Ubuntu repos. It used to be called Azureus. 
It seems there is a newer version of Vuze available than the one in the Ubuntu repos:
[http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php)
So do you have the Vuze from the Ubuntu repos installed? And you are trying to upgrade to the current Vuze 4.3.0.4? Is that correct?
You really can't upgrade the version in the Ubuntu repos with the .tar.gz from the  Azueus site. It will break compatibility with the Ubuntu repos, and may break the program itself.
According to this page:
[http://azureus.sourceforge.net/howto_linux.php](http://azureus.sourceforge.net/howto_linux.php)
you should be able to download the .tar.gz file to your home directory, untar it, then cd into the azureus directory, then just run ./azureus from the terminal to launch it.
Running it from your home directory in this way will not break compatibility with the Ubuntu repos. I would use it that way. Then when the Ubuntu repos update Vuze you will get it with your regular updates.
I hope I made this clear. Write back if you need more help.

EDIT: I just tried downloading it and running it from my home directory like this and it works. I got an error about not having a .azureus/plugins directory in my home directory, but if you already have Vuze installed you should not bet that error. I do not have Vuze currently installed.

---

### Post by mbslrm on 2010-01-01
4.3.0.4 has been out for more than 40 days. How long does it take for it to hit the repos?

---

