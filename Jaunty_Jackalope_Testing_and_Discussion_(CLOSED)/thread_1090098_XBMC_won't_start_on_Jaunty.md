---
title: "XBMC won't start on Jaunty"
date: 2009-03-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by fujikofujio on 2009-03-07
After installing XBMC on jaunty it works, but after restarting it keeps crashing with this error message:

X Error of failed request: BadMatch (invalid parameter attributes)
Major opcode of failed request: 1 (X_CreateWindow)
Serial number of failed request: 26
Current serial number in output stream: 27
CRITSEC[0x8b09ce4]: Trying to enter destroyed section.
CRITSEC[0x8b09ce4]: Trying to leave destroyed section.


I have an ATI video card.

lspci
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]

Using updated Jaunty

uname -a
Linux cinema 2.6.28-8-generic #28-Ubuntu SMP Thu Mar 5 21:49:36 UTC 2009 i686 GNU/Linux

---

### Post by anderston on 2009-03-13
I have the same problem. All the other programs work fine.

---

### Post by rburkartjo on 2009-03-13
i have the same problem

---

### Post by Nullack on 2009-03-13
Has anyone discussed it with upstream?

---

### Post by rburkartjo on 2009-03-13
okay ya'll  here is how to get it to work in 9,04 first install these sources
INTREPID PPA

Code:

deb [http://ppa.launchpad.net/team-xbmc-intrepid/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc-intrepid/ppa/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/team-xbmc-intrepid/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc-intrepid/ppa/ubuntu) intrepid main

update software sources note you will get that gpa error just ignore





the open terminal and enter
sudo apt-get update
sudo apt-get install xbmc


worked like a charm for me note xbmc installed under app/sound & video

i also deleted the two launchpad software sources after i installed.

enjoy

---

### Post by rburkartjo on 2009-03-13
let me know how this works. dont mind putting in the time to help others but like the feedback

---

### Post by fujikofujio on 2009-03-14
Thanks for the reply, but after putting those sources in my sources.list file and trying to install xbmc I get this error message:

> sudo apt-get install xbmc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xbmc: Depends: xbmc-common (= 8.10final1-intrepid5) but 8.10final1svn18432-jaunty1 is to be installed
        Depends: xbmc-skin-pm3-hd (= 8.10final1-intrepid5) but it is not going to be installed
        Depends: xbmc-web-pm3 (= 8.10final1-intrepid5) but it is not going to be installed
E: Broken packages

We do appreciate your reply and I hope someone finds a fix for this soon, I do have an ATI card and maybe its related to this, I was able to make XBMC work on my other pc with an NVIDIA card with no problem using the svn sources.

---

### Post by rburkartjo on 2009-03-14
fuj, sorry that didnt help i also have nvidia and i know when i did what i posted that it worked. it installed and works fine. kind of like that app. hey while talking about the program how does it play dvds i have a problem and it doesnt play nicely with dvd what do you have the working app set to watch dvd movies/tks

---

### Post by rburkartjo on 2009-03-14
fuj, unbelievable but now the program is playing dvds fine in 9.04 never worked worth a darn in 8.10 must be a driver thing

---

### Post by MaX on 2009-03-14
Has anyone checked on the official xbmc forums?
That would be the most logical place to ask the question

---

### Post by fujikofujio on 2009-03-14
It plays perfectly on my setup with Jaunty/Nvidia, I hate to ditch my ati card but it looks like I'm not gonna have any luck getting xbmc to work with Jaunty.

Browsed through the xbmc forums looking for a solution to this problem, no luck though, that's why I came and posted the question here (should have mentioned that in my 1st post)

I do hope they get fglrx working on Jaunty soon.

---

### Post by fujikofujio on 2009-03-18
Got me an Nvidia geforce 6200 and xbmc worked! Had to start from a fresh installation, installing the nvidia 180 driver gave me a bunch of errors.

My poor ati card, I do hope I can still use it when the final release of jaunty comes out.

---

