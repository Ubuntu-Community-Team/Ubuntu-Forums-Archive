---
title: "Your Authentication Attempt Was Unsuccessful"
date: 2011-06-21
forum: Installation &amp; Upgrades
---

### Post by wishkah353 on 2011-06-21
Hello all,

Im having a problem whenever I try to authenticate the software manager.

I can log into synaptics fine. I open it, window pops up for authentication. I put in pw then it works.

but whenever I try to use the Ubuntu software center, I get this box that used to pop up and stay up long enough for you to enter your pw.

NOW it pops up for about a nano second and I had to try 5 times to screen cap it.

so whenever I try to install something, as soon as I hit install, the authenticate box pops up, looks like it does a little shaky shake back n forth then goes away and I cant install anything.

Anyone help me with this?

[http://imageshack.us/f/577/screenshot3v.png/](http://imageshack.us/f/577/screenshot3v.png/)

---

### Post by Beacon11 on 2011-06-22
There are a couple of things to try here: [http://ubuntuforums.org/archive/index.php/t-1404426.html](http://ubuntuforums.org/archive/index.php/t-1404426.html)

Most notably:

```
sudo apt-get update
sudo apt-get install -f
sudo apt-get upgrade
```

---

### Post by DarellCraighead on 2011-07-10
I am having the same problem - but it is worse than the original post.  It does not just affect the software updater - it affects ALL applications that cause the "click here to authenticate" popup to appear.  Problem is, that window disappears as fast as it appears and is followed by the "unsuccessful" window described (and captured) in the original post.

I believe the problem is permissions - most likely in the /usr/lib tree, and possibly others.  I believe this because it started happening to me shortly after I installed CUPS (which does not work by default) and I followed SEVERAL posts on changing permissions to make CUPS work.  After that I noticed this behavior.

I do *not* believe the *right* solution should be to put gksu in front of the command line - the authentication window is *supposed* to pop up and allow you to authenticate when needed.

Anyone?

---

### Post by masuch on 2011-08-09
Hi,

 I can confirm this behaviour as well. For the first time I reinstall update manager in synaptic package manager and error was gone. For the second time it did not help :-( 

Does anyone has reliable solution ?

---

### Post by steve11911 on 2011-08-10
There really doesn;t seem to be much out there on this,but I did find a page-somewhat related with a possible workaround:

[http://ubuntuforums.org/showthread.php?p=10271241#post10271241](http://ubuntuforums.org/showthread.php?p=10271241#post10271241)

Wish I had more...
[URL="http://ubuntuforums.org/archive/index.php/t-1404426.html"]
[/URL]

---

### Post by tumolo on 2011-09-07
I am having the same issue.  It definitely has something to do with the usr/* permission settings.  I was setting up a local dev environment and accidently chmod usr/*

I can't seem to figure out how to change everything back to system standard.  Any ideas?  

thanks for the help, can't save, install or change anything in my GUI.  Everything works great from terminal.

---

### Post by masuch on 2011-09-16
I still have this error.
It is wrongly affected many other application than update-manager.
In this bug report - it should be solved, but not for me:
[https://bugs.launchpad.net/ubuntu/+s...er/+bug/704667](https://bugs.launchpad.net/ubuntu/+s...er/+bug/704667)
Can anybody confirm does it work ?

---

### Post by wikes82 on 2011-09-21
It might be the policykit don't have setuid correctly

[http://ubuntuforums.org/showpost.php?p=11267228&postcount=10](http://ubuntuforums.org/showpost.php?p=11267228&postcount=10)

---

