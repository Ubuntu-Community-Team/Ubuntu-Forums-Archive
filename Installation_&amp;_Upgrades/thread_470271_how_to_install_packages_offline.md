---
title: "how to install packages offline"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by cbweixin on 2007-06-10
hi buddies,

I use vmware to install ubuntu 7.04 on my company's pc, my system right now is windows. but because the company's policy, I can not get valid IP to surf on the internet on my linux. That's really anoying because I can not use apt-get or aptitude or synaptic. I wondering if I could download packages onto my windows system(my windows can access to the internet) and then I install those packages offline.

I have another question is that how I can share the windows partition to my ubuntu inside vmware. 

thanks for prompt help. best wishes to all.

---

### Post by mitch.c on 2007-06-12
I've never tried it, but take a look at the package aptoncd. It let's you create a cd based repository. From the website:
> 
APTonCD is a tool with a graphical interface which allows you to create one or more CDs or DVDs (you choose the type of media) with all of the packages you've downloaded via APT-GET or APTITUDE, creating a removable repository that you can use on other computers.
APTonCD will also allow you to automatically create media with all of your .deb packages located in one especific repository, so that you can install them into your computers without the need for an internet conection.
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)
```
$ sudo apt-get install aptoncd
```
[[COLOR="Red"]UAResolved[/COLOR]]("http://ubuntuforums.org/showthread.php?t=377083")

---

