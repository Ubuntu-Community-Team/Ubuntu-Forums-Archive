---
title: "Update issues, I'm making it worse, HEEELP!!"
date: 2013-05-15
forum: Installation &amp; Upgrades
---

### Post by theonewhoshallnotbenamed on 2013-05-15
Hi everyone

I apologise in advance for my lack of technical knowledge with Linux.  

I have Ubuntu 12.04 and use it for browsing the web, office docs, music and video playing, and not much else really.  I like it and prefer it to Windows but I'll be honest, I'm not 100% sure what I'm doing with it sometimes :-/  I really need some step by step help, I'm actually thinking it would be best to use teamviewer remote access to see what's going on here rather than me trying to explain. 

Basically Firefox wasnt loading, I thought internet prob but after I forced updates, some FF ones were struggling.  I used the terminal to sudo apt-get purge, upgrade and update and uninstalled and reinstalled FF and the problem seems to have been resolved.  However, I went off some advice for a similar prob and the "other software" tab in update manager is confusing me to hell.  I don't understand what conflicting PPAs are which seem to be the problem.  

Can anyone please offer their assistance?  Please PM me on here and I'll respond.  Thanks so much 

Clare

---

### Post by ajgreeny on 2013-05-15
It would be interesting to see the output of```
cat /etc/apt/sources.list.d/*.list
```which will show us how many ppa repos you have enabled and then the contents of them.  We may be able to tell you which, if any, are perhaps causing your problem.

---

### Post by Bashing-om on 2013-05-15
theonewhoshallnotbenamed;

Hi ! ... 
Not knowing is nothing to be shamed about, none of us were born knowing. On this forum there is no such thing as a "dumb" question ! We exist here to guide and assist.

Bear in mind this is an open forum for the benefit of all. Thus all correspondence in respect to problem resolution is best conducted in the view of all, viewed by many and peer reviewed of all responses.
To address your present issue; Post back - copy and paste between code (#) tags at top of your post - the output of terminal commands:
```
sudo apt-get update
sudo apt-get upgrade
``` relates the state of your installation at large.

Package Management -> Applications and software::
Other Software tab: Standard install manages all installed applications with the database file /etc/apt/sources.list as the base (ubuntu Software Center is one front end for this utility) and when a Personal Package Archive for developed applications not in the standard files repository are made available to the public, that access is placed in the /etc/apt/sources.list.d directory (Other Software tab).

If you have a problem related to your sources list post back to us the out put of terminal commands:
```
cat /etc/apt/sources.list
#and
ls -la /etc/apt/sources.list.d
``` We will determine where the fault lies.[INDENT=2]
just try'n to help

[/INDENT]

---

