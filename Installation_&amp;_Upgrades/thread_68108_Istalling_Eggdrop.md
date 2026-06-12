---
title: "Istalling Eggdrop"
date: 2005-09-22
forum: Installation &amp; Upgrades
---

### Post by xl8r on 2005-09-22
Hi!

Sorry being so n00b, I've got a problem installing Eggdrop.

I installed eggdrop with 

sudo apt-get install eggdrop 

...and it went fine. But what should I do next? I've tried to run eggdrop with

eggdrop

..but all I get is this:

Eggdrop v1.6.17 (C) 1997 Robey Pointer (C) 2004 Eggheads
[12:05] --- Loading eggdrop v1.6.17 (Thu Sep 22 2005)
[12:05] * CONFIG FILE NOT LOADED (NOT FOUND, OR ERROR)

Where I can find this config file? Or how can I make one and where will I put it?

---

### Post by luckyaba on 2005-10-04
extract /usr/share/doc/eggdrop-data/examples/eggdrop.conf.gz

there is a conf file for you

---

### Post by veehell on 2005-12-21
Check [this]("http://www.ubuntuforums.org/showpost.php?p=393763&postcount=5") thread's post.
or [EggHELP]("http://www.egghelp.org/") or [EggFAQ]("http://www.eggfaq.com/cgi-bin/display.cgi?main.html") and finaly [EggHEADS]("http://www.eggheads.org/") 

I used EggConfMk (Win32 mini tool) to genereta own "starting.conf" afterward i edited few lines directly in VI (it is better to avoid bad EOL/EOF signs). Some sort of config generator is on EggFaq(it use the example.tar.gz) with some basic inputs and generete for you.

---

### Post by CoLt-[45] on 2005-12-22
I dunno what's went wrong but when i type

sudo apt-get install eggdrop

I get this error

colt45@217:~$ sudo apt-get install eggdrop
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package eggdrop
colt45@217:~$

What i've done wrong here? :???:

even if I use root

root@217:~# apt-get install eggdrop
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package eggdrop
root@217:~#

Same thing :???:

Any chance of help here? TIA

---

### Post by veehell on 2006-01-26
Dude there is better way to download and compile from tarball. There should be some *.DEB packages also, but i advice you to compile (more stable, more faster and it is not so hard) 
Check the links above (in my previews post and it might help you really) :)
Cheers.

---

### Post by frodon on 2006-01-26
[QUOTE='CoLt-[45]']Ieven if I use root

root@217:~# apt-get install eggdrop
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package eggdrop
root@217:~#

Same thing :???:

Any chance of help here? TIA[/QUOTE]You shouldn't have enabled all the repositories, i installed eggdrop without any problems.
See this link for repositories informations : [http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

---

### Post by veehell on 2006-01-26
[http://www.geteggdrop.com](http://www.geteggdrop.com) or [http://www.eggheads.org/downloads/](http://www.eggheads.org/downloads/) to get the official tarballs.

---

