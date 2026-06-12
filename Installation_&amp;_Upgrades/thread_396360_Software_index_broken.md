---
title: "Software index broken"
date: 2007-03-29
forum: Installation &amp; Upgrades
---

### Post by rpaco on 2007-03-29
Hi I seem to have broken it!
I was first trying to install  Skype using the deb file which did not work it said it needed q3lib  something (approx form memeory) So I then went to the Skype repository and did this :
1. As the root user, add this line to the end of your /etc/apt/sources.list file:

deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
This went ok, but then:

2. Then run apt-get update to sync to the latest repository and
apt-get install skype to install the latest version of Skype on your computer.
However on the execution of apt-get update the whole thing except the cursor froze.

I have rebooted and now on trying the software update manager via the menu I get the error:
**[CENTER]Software index is broken[/CENTER]**

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

So I do:
root@rpaco-pc:~# apt-get install -f
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Could this be from the earlier failed attempt to install Sykpe?

Any ideas how to recover please? Also later on instructions for installing skype which work. Many thanks

---

### Post by rpaco on 2007-03-30
Ok I have fixed it myself.

---

### Post by jeyno on 2007-04-05
How?

---

### Post by smackywentz on 2007-04-13
he had a syntax error is all, he needed to type

sudo apt-get install -f

instead of 

sudo apt-get -f install

---

### Post by vradovic on 2007-04-18
thanks works for me.

---

