---
title: "Networking Trouble"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by kid102 on 2010-01-01
I am a LAMP developer but mostly just the MP part, I'm trying to install Ubuntu Server 8.04 32-bit using VMare for my Windows 7 64-bit box and am having an extremely difficult time.  I am also using a verizon wireless broadband card for internet connectivity.

I got ubuntu to install and I am able to ping websites such as google.com but I can't get 'aptitude update' to work.  Also, I created another virtual machine using Ubuntu Desktop 9.04 and have the same problem, I can ping but I can't open sites in firefox or download packages with aptitude or synaptic

Here's what happens with aptitude:

After several minutes it finally outputs:

Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security release.gpg
  Could not connect to security.ubuntu.com:80 (91.189.88.37)

It does the same thing for several different connections hardy-security/main Translation-en_US unable to connect to security.ubunut.com http:, Err [http://security.ubunut.com](http://security.ubunut.com) hardy-security/restricted Translation-en_US Unable to connect to security.ubuntu.com http:  and on and on

then it pauses for several minutes and tries to connect to us.archive.ubuntu.com (91.189.88.46) and then outputs a similar string of error messages to that above.

After googling for a while many posts seem to suggest it could be an issue with the /etc/apt/sources.list which I would post here but I can't figure out how to copy and paste it outside of VMWare and it is really long, but it does include:

deb [http://security.ubuntu.com.ubuntu](http://security.ubuntu.com.ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted 

and same format for hardy-security main, universe and multiverse restricted

and also for [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy, hardy-updates multiverse, universe, etc.

I tried tweaking some of the domain names, remove us sub domain and a few other things I found in the posts to absolutely no affect.

I also tried disabling ipv6 as some posts suggested that route, it did nothing.

I've restarted, rebooted dozens of times.

Seems I've tried every option I've come across in google, anyone else have any suggestions?

Thanks in advance

---

### Post by kid102 on 2010-01-02
I had someone else look at my problem, here is the feedback:

I think VMware is having problems since the outbound interface is a PPP internface. Point to Point Protocol...  
 
I think its having problems routing certain traffic because of the fact that the default gateway is 0.0.0.0 in windows 
 
it has to be a problem with the aircard. I've never used an aircard with vmware.  
 
Try getting near a wifi point and trying then again. If it works then we know its an aircard problem. 
if it doesn't work then we know its a vmware problem.

---

