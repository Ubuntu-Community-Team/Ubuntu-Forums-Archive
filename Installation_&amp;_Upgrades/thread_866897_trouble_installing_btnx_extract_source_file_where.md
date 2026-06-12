---
title: "trouble installing btnx extract source file where?"
date: 2008-07-22
forum: Installation &amp; Upgrades
---

### Post by coober85 on 2008-07-22
OK I installed the library thing "$ sudo apt-get install libdaemon0 libdaemon-dev" needed for btnx and btnx-config

and I downloaded the tar.gz file for btnx. I don't know what to do next (and I've been googling and fiddling and searching the forums for hours). the install guide says to <http://www.ollisalonen.com/btnx/man/btnx-manual.html#AEN102> extract the source file. A) where the hell is the source file and B) where do I extract it to? can someone explain to me (pretending I'm retarted) how to install btnx and btnx-config? I have Ubuntu 8.04 LTS 


 Linux is confusing the $%#^ out of me!

I want to love linux, I really do

I'm all for stuff that isn't completely user-friendly, thats why I like XP over mac OS X - you kind of have to conquer your windows system in order to get the best out of it... but this is ridiculous. I find solution after solution that doesn't seem to work for one reason or another, explanations that are always way over my head (and I'm no dumb-dumb). its so frustrating.

---

### Post by Pumalite on 2008-07-22
Are they in Synaptic?

---

### Post by coober85 on 2008-07-22
Solved it just mis-read instructions

written by a newbie for a newbie in 10 simple steps

answer for ubuntu version 8.04 lts
IN PLAIN ENGLISH

step 1: 
click on system in the top left corner, highlight administration, and move down to click on synaptic package manager (enter your password)

step 2:
in new window click on settings and then click on repositories from the drop down menu

step 3:
click the third-party Software tab

Step 4:
click on add+

Step 5:
type or copy and paste in
deb [http://ppa.launchpad.net/daou/ubuntu](http://ppa.launchpad.net/daou/ubuntu) hardy main

step 6:
Repeat steps 4 and 5 but instead of typing "deb http..." type this:

deb-src [http://ppa.launchpad.net/daou/ubuntu](http://ppa.launchpad.net/daou/ubuntu) hardy main

step 7:
close synaptic manager and open terminal by clicking on applications in the top left corner, then accessories, then scrolling down to terminal

step 8:
type or copy and paste in this:
sudo apt-get update && sudo apt-get install btnx

Step 9:
hit enter and then type your password

Step 10:
go to applications -> system tools -> and behold the glory that is an installed btnx!

---

