---
title: "No NetworkManager after upgrade to 8.10"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by waylow on 2008-11-05
Hey There

I upgraded 8.04 to 8.10 - there are a few problems to sort out
the main one is that the networking is broken

I have been reading the forums and found other people are having the same problem

It seems in my circumstance - my system is now missing the Network Manager
does anybody know how to fix this


cheers

---

### Post by Vl@d on 2008-11-05
did you try sudo nm-applet?

Or take a look at this [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)

---

### Post by bscbrit on 2008-11-05
Yes, you're correct.  NetworkManager is causing some problems. After taking whatever advice you can find here - and there is a lot of good advice around - you might find that you simply cannot get NM to work for you.

Some of us have had to change to wicd until the bugs in NM get sorted out.  If you have no success with NM try this link:

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by waylow on 2008-11-05
Thanks for the quick response

it looks like it is missing

"The program nm-applet can be found in the following packages
network-manager-gnome
mythbuntu-diskless-client"

but obviously I can't download the packages

I will see if I have the packages on the old Ubuntu cd
(I upgraded to the new version - didn't DL the CD)

---

### Post by waylow on 2008-11-05
no good - can't get the package from the old 7.04 CD I have
(it still wants to connect to the internet to get the dependancies)


I guess I will have to DL the 8.10 CD 

(can't DL wicd either 'cos I got not internet....yet)

---

### Post by bscbrit on 2008-11-05
waylow - it might be missing but downloading won't necessarily solve your problem.  I've downloaded it but I cannot make it keep my settings over a reboot.

However, you are posting on this forum so you must have internet access.  Can you not download the package and move it across to the target machine using a removable drive or usb memory stick?

---

### Post by waylow on 2008-11-05
don't have a USB stick

downloaded the CD to see if I could get it off that

no love - it's not in the new release
(installed it as a virtual machine on my mac to see)

So the Question has changed - I obviously don't need Network manager for it work

How do I fix my networking?
I seem to be missing my eth0 interface
and the wlan0 can't connect

if I do iwlist scan - I can see my network and signal strength

I just need a way to configure the interface

---

### Post by bscbrit on 2008-11-05
Have you looked at

[http://ubuntuforums.org/showpost.php?p=3501096&postcount=1](http://ubuntuforums.org/showpost.php?p=3501096&postcount=1)

It's a howto for connecting a network manually :-)

---

### Post by waylow on 2008-11-05
OK so I have it working for now
but it is very temperamental 


(haven't looked at the link yet but I will check it out)

thanks for your help - it's fixed but not fully

---

