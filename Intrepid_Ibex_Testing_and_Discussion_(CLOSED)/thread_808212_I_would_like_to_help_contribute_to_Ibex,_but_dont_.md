---
title: "I would like to help contribute to Ibex, but dont know where to start."
date: 2008-05-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by toupeiro on 2008-05-26
I've gotten a lot out of ubuntu, and I would really like to help give back to it in this distro, but don't know where to start.  I have lots of windows packaging experience, so I understand the methodology, but I've never used the debian tools to do it.  I've participated in several beta tests for various applications and OSes, but I am not a "programmer".  I am good at troubleshooting hardware and software dependency problems, and fairly good at procedure documentation, but don't know if that is applicable to Ubuntu's development process.

My question is, where can I fit in and help?  I've 10 years system admin experience, covering several key area's of IT over that period of time.  

Many thanks!

-T

---

### Post by insane_alien on 2008-05-26
load up a spare computer/partition with intrepid and file good detailed bug reports. if possible, find a work around and post that to the bug report.

writing documentation for ubuntu is also a good thing.

you don't need to be a programmer to help. i'm not. i've filed a bunch of bug reports and on occasion submitted some documentation.

my programming abilites don't really apply to most of the applications on ubuntu.

---

### Post by ibizatunes on 2008-05-26
I too would like to help with the development of 8.10 but i cant program for sh**, i think im going to run my 8.10 alpha in a virtual machine
Is there a group or website that isn't really for programmer, more just application tester? So that application can be test throughly and systematically, when a update / application is upgrade programmers could tell testers to try this application as xyz patch / version has been applied? and give feedback on the update etc?
 
I know launchpad is where we report bugs, but is there a website out there for tester

---

### Post by ssam on 2008-05-26
How to contribute to ubuntu
[https://wiki.ubuntu.com/ContributeToUbuntu](https://wiki.ubuntu.com/ContributeToUbuntu)

[https://wiki.ubuntu.com/MOTU/School](https://wiki.ubuntu.com/MOTU/School) has some information and howtos for packaging.

---

### Post by 23meg on 2008-05-26
[http://ubuntuforums.org/showthread.php?t=603316](http://ubuntuforums.org/showthread.php?t=603316) can help (Intrepid version coming soon).

---

### Post by autocrosser on 2008-05-26
And I will say that the more of us there are, the faster the bugs will be found :)

Welcome to Ibex!!!!

---

### Post by danbuter on 2008-05-26
Just by doing bug reports will help. I tested beta for Hardy, and filed multiple bugs. At least one of them was fixed (still waiting for some of the others). Once I've actually become a better programmer, I intend on submitting actual patches (at this point in my programming capabilities, my patches would be more likely to create new bugs than fixing anything).

---

### Post by aikishugyo on 2008-05-27
I'm delighted that Intrepid Ibex is now running on my AMD64 machine---no more crashing Firefox, Seamonkey or Opera browsers (yes, eventually even that one crashed) every few monutes of browsing time. Obviously, some of the critical errors in the libraries shipped with Hardy have been fixed very well.

I added the intrepid, intrepid-backports, intrepid-updates, intrepid-security and intrepid-proposed repositories and did an upgrade grpahically (after installing findutils from the command line). Some 876 packages for 962.5 MiB were downloaded and installed successfully. Several dozen (or more than a hundred perhaps) other packages are not currently installable for whatever reasons, but I am not worried. I am happy that the combination of Hardy and Ibex is stable as a rock for me whereas Hardy was a royal pain these last months.

---

### Post by ibizatunes on 2008-05-27
"I added the intrepid, intrepid-backports, intrepid-updates, intrepid-security and intrepid-proposed repositories and did an upgrade graphically (after installing find utils from the command line)"

How did you do that?
Where  / what 
are the intrepid repo's, can someone post it for me

---

### Post by smartboyathome on 2008-05-27
Intrepid backports, updates, security, proposed etc are not online yet, and won't be until it is released.

---

### Post by aikishugyo on 2008-05-27
> **ibizatunes said:**
> "I added the intrepid, intrepid-backports, intrepid-updates, intrepid-security and intrepid-proposed repositories and did an upgrade graphically (after installing find utils from the command line)"

How did you do that?
Where  / what 
are the intrepid repo's, can someone post it for me

Hi, if you browse the below URL you can see the intrepid directories and the Releases files. Here is one example with just "intrepid":

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid multiverse universe main restricted

I don't know why smartboyathome thinks they are not available because the URLs certainly exist.

---

### Post by smartboyathome on 2008-05-27
No, I didn't say those ones, I said intrepid-backports, updates, security, and proposed don't exist until after the release, so they aren't very helpful. The deb line posted above DOES exist, though.

---

