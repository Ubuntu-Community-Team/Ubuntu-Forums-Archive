---
title: "preventing kernel upgrade"
date: 2007-10-03
forum: Installation &amp; Upgrades
---

### Post by probalmitra on 2007-10-03
I am administering several (about ten) computers in a research lab environment. They currently use CentOS, and an RTAI (realtime application interface) patched vanilla kernel. I would like to switch them over to Ubuntu. I have the following questions:

Question 1:
Which is a good Ubuntu version to use? My guess is, the latest LTS version i.e. dapper

Question 2:
I will be downloading a vanilla kernel from kernels.org and patching with RTAI. I have done this on various other systems in the past (rh9, debian 3.1, centos4.5) and have read through the posts on this forum to make sure there weren't any surprises in Ubuntu. My question is: how do I prevent any further kernel updates from happening after I've set up our custom kernel?

I have found answers in the Ubuntu forum consisting of "just don't select updates starting with "linux-image". This would be my approach, if I were the only user. However, it won't work for the not-so-computer-savvy lab members who will be using these computers. Murphy's law: even if I disable the automatic update notification, at some point someone will run an update from the GUI menus and come complaining to me about RTAI errors  (e.g. "I'm sorry, I just wanted to upgrade Firefox, but now the RTAI modules refuse to load. Fix it please!"). I would like to make it so that kernel updates just aren't an option.

Any help is much appreciated! Also, if there are already good answers to these questions on the forum and I have simply failed to find them (trust me, I tried), then my apologies for the needless traffic, please just point me in the right direction.

---

### Post by Gremlinzzz on 2007-10-03
Talk to Walkerk knows allot about kernels.
[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

---

### Post by zvacet on 2007-10-04
1. Latest version is Feisty but in few weeks we will have new version named Gutsy.

2.find in synaptic linux -image you want to use>mark it>package>lock version

---

### Post by probalmitra on 2007-10-04
Thank you for your help. I have two further questions:

(1) Does anyone know if Gutsy is going to be a "Long-Term Support" release?

(2) I have considered using the version locking feature of apt, but there is one problem: I have to use a vanilla kernel downloaded from kernels.org and apply an RTAI patch to it -- so, my custom kernel will not be in the apt-cache and I cannot lock a version which isn't in the list. Does anyone know of another way? When I was using yum, I was abled to edit yum.conf with a line like "exclude=kernel*". Is there any equivalent for apt in Ubuntu?

Thanks again.

---

### Post by maybeway36 on 2007-10-04
Lock the linux-image-generic package, then tell it to boot your custom kernel instead (leaving Ubuntu's kernel under it on the GRUB list.)

---

