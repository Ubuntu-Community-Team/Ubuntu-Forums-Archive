---
title: "APT - how to install copied apps only"
date: 2008-09-03
forum: Installation &amp; Upgrades
---

### Post by tommaso.ferigo on 2008-09-03
Hi guys, 

I'm quite new to Ubuntu and to any forum, so please don't blame me (or give link for other similar threads in case) if I did not manage to find a reply to this question yet.
I have burned a DVD with APTonCD to back up some apps I am trying to install on a second PC. 
I have restored the apps, and I read that I have now to install them manually from synaptic, from the terminal or via add/remove.
As far as I understood, so far I have copied the apps somewhere (but where?) and they are ready to be installed.
I opened synaptic package manager and I can see the list of all available packages. By the way I am using a virtual machine on a XP OS now with only 1Gb RAM, so it is not that quick.
MY QUESTION
How can I install ONLY the applications copied from a APT DVD and spread among all the available apps in the synaptic area?
Can I install them all at once and not by double checking the names of what was on APT DVD (I had 1Gb apps on the DVD, it would take me forever)? How can I filter the apps copied from APT DVD and ask to install them all at once?

Thank you in advance for yr kind answers. T.

---

### Post by Partyboi2 on 2008-09-03
Open a terminal (Applications>Accessories>Terminal)
and 
```
sudo apt-cdrom add
```
then open up synaptic package manager
```
gksudo synaptic
```
click on the reload button then select "orgin" from the menu on the left. You should see the aptoncd listed. Highlight it and on the right side should be a list of all the packages on the dvd. Then mark them all for install and press "Apply"

---

