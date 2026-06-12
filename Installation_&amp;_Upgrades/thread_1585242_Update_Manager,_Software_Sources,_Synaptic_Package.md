---
title: "Update Manager, Software Sources, Synaptic Package Manager not working"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by kermittoad on 2010-09-30
It started with Update Manager constantly recycling and not updating.  When it starts it shows 295 files and 308MB waiting to download.  When I click on 'Install Updates' it appears to go through the process, and then presents me with the same 'waiting to install' window again - and again, and again - in fact as many times as I care to click the 'Install Updates' button.  No error messages appear.  The 'Settings' button produces the same apparent process as the 'Install Updates' button, but doesn't present me with any other screen.
 
I've tried all the solutions I could find on these forums and nothing works.  The sudo suggestions for Terminal usually produce error codes.
 
One suggestion involved adjusting a line in the 'hosts' file.  When I tried this I was presented with the obstacle of not having access to the read-only file, and no matter how much I searched I couldn't find how to gain access - but that's another story.
 
While investigating all these possible solutions, I was directed in turn to the Software Sources and Synaptic Package Manager applications, but when I attempted to start them, 'Starting Administrative Application' appeared briefly on the taskbar - and then disappeared!  And nothing started.
 
I'm left wondering whether all these problems are connected, and whether this may give someone a clue to their cause.

---

### Post by oldos2er on 2010-09-30
Run ```
sudo apt-get update && sudo apt-get dist-upgrade
``` in a terminal, and post the output here.

---

### Post by kermittoad on 2010-09-30
Hello,
 
It produced the following -
 
> [FONT=Courier New][FONT=Courier New]gerald@gerald-Acer:~$[/FONT][FONT=Courier New] sudo apt-get update && sudo apt-get dist-upgrade[/FONT]
[FONT=Courier New]sudo: /etc/sudoers.d/README is mode 0460, should be 0440[/FONT]
[FONT=Courier New]>>> /etc/sudoers: /etc/sudoers.d/README near line 24 <<<[/FONT]
[FONT=Courier New]sudo: parse error in /etc/sudoers near line 24[/FONT]
[FONT=Courier New]sudo: no valid sudoers sources found, quitting[/FONT]
[FONT=Courier New]gerald@gerald-Acer:~$[/FONT]
[/FONT]

---

### Post by dino99 on 2010-09-30
> **kermittoad said:**
> Hello,
 
It produced the following -


check your sources.list: synaptic repo tab
be sure it only use genuine repo of the same distro (lucid or maverick or else)

copy/paste one by one these commands into a console:

sudo chown root:root /etc/sudoers.d/README
sudo chmod +x /etc/sudoers.d/README

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by kermittoad on 2010-09-30
> **dino99 said:**
> check your sources.list: synaptic repo tab
be sure it only use genuine repo of the same distro (lucid or maverick or else)
 
copy/paste one by one these commands into a console:
 
sudo chown root:root /etc/sudoers.d/README
sudo chmod +x /etc/sudoers.d/README
 
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
 
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
 
Sources.list shows that I have '[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]' installed.  I can't find any reference to 'synaptic repo'.
 
Running the above commands produced the following (I think unsatisfactory) output -
 
[HTML] 
gerald@gerald-Acer:~$ sudo chown root:root /etc/sudoers.d/README
sudo: /etc/sudoers.d/README is mode 0460, should be 0440
>>> /etc/sudoers: /etc/sudoers.d/README near line 24 <<<
sudo: parse error in /etc/sudoers near line 24
sudo: no valid sudoers sources found, quitting
gerald@gerald-Acer:~$ sudo chmod +x /etc/sudoers.d/README
sudo: /etc/sudoers.d/README is mode 0460, should be 0440
>>> /etc/sudoers: /etc/sudoers.d/README near line 24 <<<
sudo: parse error in /etc/sudoers near line 24
sudo: no valid sudoers sources found, quitting
gerald@gerald-Acer:~$ sudo apt-get clean
sudo: /etc/sudoers.d/README is mode 0460, should be 0440
>>> /etc/sudoers: /etc/sudoers.d/README near line 24 <<<
sudo: parse error in /etc/sudoers near line 24
sudo: no valid sudoers sources found, quitting
gerald@gerald-Acer:~$ sudo apt-get autoclean
sudo: /etc/sudoers.d/README is mode 0460, should be 0440
>>> /etc/sudoers: /etc/sudoers.d/README near line 24 <<<
sudo: parse error in /etc/sudoers near line 24
sudo: no valid sudoers sources found, quitting
gerald@gerald-Acer:~$ sudo apt-get autoremove
sudo: /etc/sudoers.d/README is mode 0460, should be 0440
>>> /etc/sudoers: /etc/sudoers.d/README near line 24 <<<
sudo: parse error in /etc/sudoers near line 24
sudo: no valid sudoers sources found, quitting
gerald@gerald-Acer:~$ sudo apt-get update
sudo: /etc/sudoers.d/README is mode 0460, should be 0440
>>> /etc/sudoers: /etc/sudoers.d/README near line 24 <<<
sudo: parse error in /etc/sudoers near line 24
sudo: no valid sudoers sources found, quitting
gerald@gerald-Acer:~$ sudo apt-get install -f
sudo: /etc/sudoers.d/README is mode 0460, should be 0440
>>> /etc/sudoers: /etc/sudoers.d/README near line 24 <<<
sudo: parse error in /etc/sudoers near line 24
sudo: no valid sudoers sources found, quitting
gerald@gerald-Acer:~$ sudo dpkg --configure -a
sudo: /etc/sudoers.d/README is mode 0460, should be 0440
>>> /etc/sudoers: /etc/sudoers.d/README near line 24 <<<
sudo: parse error in /etc/sudoers near line 24
sudo: no valid sudoers sources found, quitting
gerald@gerald-Acer:~$
[/HTML]

---

### Post by oldos2er on 2010-09-30
Have you edited /etc/sudoers?

---

### Post by kermittoad on 2010-09-30
> **oldos2er said:**
> Have you edited /etc/sudoers?
 
No, and when I just tried, I was told that I don't have permissions necessary to open the file.

---

### Post by kermittoad on 2010-10-03
It occurred to me that the reason I had not received any solutions to my problem with Update Manager was that I was perhaps asking the wrong question.
 
Since Update Manager would start but not function, and Software Sources and Synaptic Package Manager wouldn't even start, I reasoned that if I ignored the problem with Update Manager and targeted the other two applications, their solution might provide the answer to the third.
 
So I started another thread with this in mind and it provided the answer -
 
[http://ubuntuforums.org/showthread.php?t=1586269](http://ubuntuforums.org/showthread.php?t=1586269)
 
After resolving the issue with the other two programs, Update Manager now runs as it should.
 
Thank you to all those who offered help.

---

