---
title: "Black Screen trying to instill 7.10 with 8800GT"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by Volume on 2008-04-30
Hello all,

Pretty new  to Ubuntu, I just popped in my install disk, and X is not starting. I have read that there are several issues with the 8800 GT card.  All that I have seen involve installing new drivers or updating or something.  However, when I attempt to install the OS from the boot menu, it loads some files, for a couple of minutes, and then I either get a black screen, or the blue screen which says unable to start X.

Please Help!!!

---

### Post by Wazoot on 2008-04-30
Are you installing using the live cd?
Or Wubi?

---

### Post by Volume on 2008-04-30
Not sure what Wubi is, but I bought a book that had the CD in the back, and it said that it is both the live and install version (just one CD).

Does that help?

Also, there are options on the boot menu to "start/install linux" or to do some other things (pretty much all of which I have tried).  I have tried removing the "quiet" and "splash" commands from the command line too.

---

### Post by bulldog on 2008-04-30
Maybe you can download the 'alternate cd' ?
I have a 8800GT and installed Gutsy and Hardy without any problem.

---

### Post by Volume on 2008-04-30
Interesting idea.  Where can I find that file... Sorry major noob.

---

### Post by Rocky37 on 2008-04-30
> **Volume said:**
> Interesting idea.  Where can I find that file... Sorry major noob.


[http://releases.ubuntu.com/8.04/](http://releases.ubuntu.com/8.04/)

Not quite half way down the page

---

### Post by Volume on 2008-04-30
Thank you for your help.  I'll let you know how it goes.  Not that I was too lazy to find the file, I just wanted to make sure I got the same one you were talking about. :)
V

---

### Post by Volume on 2008-05-03
Still no luck after doing the alternate install.  I have tried 7.04, 7.10, and 8.04, and run the cdcheck on all 3, I continue to get a black screen on trying to install.  It doesn't seem to matter if I do the live, or install option.  Every time it tries to start X, I get an error saying X has been shut down 6 times in 90 seconds, and then black screen of death... Any suggestions?

---

### Post by jlandaw on 2008-05-03
when you start the install, click advanced options (not sure on the wording) i think its f6 and add the following to the end of the line, after spalsh. (just type this... dont delete anything.)


noapic irqpoll noirqdebug

Edit: there is a space between each command

---

### Post by Volume on 2008-05-04
Ok.  I was finally able to install 7.10.  However, my graphics card still does not seem to be working.  When I boot GRUB loads and I can choose 7.10, but then some things load and then the screen goes black, I am assuming when X tries to start.  I have no idea what to do... any suggestions?

---

