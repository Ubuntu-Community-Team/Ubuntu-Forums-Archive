---
title: "Unable to locate package?"
date: 2011-06-25
forum: Installation &amp; Upgrades
---

### Post by 09061920 on 2011-06-25
I just reinstalled Xubuntu 11.04, and I'd like to install fluxbox:

```
09061920@system:~$ sudo apt-get install fluxbox
[sudo] password for 09061920: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package fluxbox
```I've already unhashed

deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

in /etc/apt/sources.list, but I'm on a very slow connection so I don't want to update 42 MB right now (trust me when I say I'm on a very slow connection :().

Can anyone tell me how to update *just* the updates necessary for apt-get without having to update the 42 MB of, for the moment, pointless updates?

Thanks, I appreciate it ;)

-09061920

---

### Post by Toz on 2011-06-25
The fluxbox package is in the **universe** repository - make sure it is enabled in your /etc/apt/sources.list file.```
$ apt-cache policy fluxbox
fluxbox:
  Installed: (none)
  Candidate: 1.3.1~dfsg1-1
  Version table:
     1.3.1~dfsg1-1 0
        500 http://ca.archive.ubuntu.com/ubuntu/ natty/**[COLOR="Red"]universe[/COLOR]** i386 Packages

```

As for installing only the "necessary" updates, you'll have to define what you mean by "necessary". You can always do an ```
apt-get --just-print upgrade
```to get the list of available updates and install them as required, one at a time, via: ```
sudo apt-get install <package>
```

---

### Post by 09061920 on 2011-06-25
Thanks. I just didn't know how the apt-get utility was called and what I had to install from the updates to get apt-get to work.

When I unhashed 

deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
 deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

in /etc/apt/sources.list, 

AptURL, apt-utils and apt appeared in update manager.

But thanks for your help, didn't know about

```
 apt-get --just-print upgrade 
``` 

before. :)

---

