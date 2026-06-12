---
title: "Syanptic and apt-get updates not working"
date: 2005-03-16
forum: Installation &amp; Upgrades
---

### Post by andyman on 2005-03-16
Hello,

Very much a newbie here, so I'd appreciate any help available.

Decided after years of Windows as a user and an engineer, I'd try out and force myself to use Linux as my main PC.  IN order to help me do this, I wanted to try and run Ubunto through a Vmware session at work.

All seemed to be going great, got Hoary installed without a problem, up and running without problem, except one….  Whereas I can access the net through Firefox without a problem (through a proxy), the same cannot be said for synaptic or apt-get.  I've configured the proxy in these applications (excuse the wrong terminology!), but they don’t error, they just never download any updates or say 0 updates to download.  Firefox continues to work as expected.

If this is a common question, apologies, but any help greatly appreciated.

Andy.

________________________

EDIT
Doh, I hadnt added the online repositories in.....
I'll get my coat.

---

### Post by Seer on 2005-09-07
I'll revive this unanswered thread...

with a  simple me too!

Using VMWare 5 and hoary - configured every proxy setting found and nada for synaptic.

Firefox and other working apps prompt me for user/pass to auth against the proxy - but synaptic doesnt and I guess thats where the problems lie?

---

### Post by sideshowrob on 2005-09-23
Alright, can I say me three?  

Using Ubuntu Hoary Hedgehog release on a desktop at my office, and am at the mercy of the company proxy.  I have added in the proxy settings every place I have found them, I have no trouble browsing the internet and have pulled things down via FTP with no issues.  

I can even resolve both the URL's and by IP from the Sources.list file using Firefox.  But am unable to ping and get a response.  DNS is working correctly, if I ping by name I get the IP.

Here is my output when issuing a sudo apt-get update:

Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release.gpg
  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204), connec tion timed out
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release.gpg
  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204), connec tion timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (82.211.81.151), connection time d out [IP: 82.211.81.151 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg
  Could not connect to security.ubuntu.com:80 (82.211.81.151), connection timed out [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg
  Could not connect to archive.ubuntu.com:80 (82.211.81.151), connection timed o ut [IP: 82.211.81.151 80]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (82.211.81.151), connection time d out [IP: 82.211.81.151 80]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
  Could not connect to archive.ubuntu.com:80 (82.211.81.151), connection timed o ut [IP: 82.211.81.151 80]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
  Could not connect to archive.ubuntu.com:80 (82.211.81.151), connection timed o ut [IP: 82.211.81.151 80]
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204), connec tion timed out
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204), connec tion timed out
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204), connec tion timed out
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
  Could not connect to ubuntu-backports.mirrormax.net:80 (66.90.101.204), connec tion timed out
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
22% [Connecting to us.archive.ubuntu.com (82.211.81.182)] [Connecting to security.ubuntu.com (82.211.81.182)]

and well, you get the idea.  It times out.  (I also realize I have some screwed up URL entries in the Sources.list, I copied and pasted from a bad example it seems) I would imagine this has to do with the proxy.  Should I submit a bug report, or is there a Proxy setting for apt-get somewhere?

Thanks in advance.

---

### Post by gpredrag on 2005-09-23
Try /etc/apt/apt.conf.d/30proxy, something like:
```
Acquire{
http::Proxy "http://your.proxy.dns.name:port_no";
};
``` 
That is if your proxy doesn't require authentication.
And why dont you just use update manager, if it is a desktop machine and you have X?

---

### Post by mlomker on 2005-09-23
[Look here.](http://ubuntuforums.org/showpost.php?p=364026&postcount=2) 

This one comes up if you search for **apt-get proxy**.

---

### Post by sideshowrob on 2005-09-23
[QUOTE=gpredrag]Try /etc/apt/apt.conf.d/30proxy, something like:
```
Acquire{
http::Proxy "http://your.proxy.dns.name:port_no";
};
``` 
That is if your proxy doesn't require authentication.
And why dont you just use update manager, if it is a desktop machine and you have X?[/QUOTE]
 Thanks, your idea worked.  Some of the URL's came back with 404's, but the URL's that were correct actually pulled down updates.  I can't thank you enough.

I tried Update Manager and did not receive any results either.  I felt more comfortable troubleshooting apt-get since I was getting actual output back.  With Update Manager it just sat in a hung state.

---

### Post by kingshaun on 2005-10-11
Synaptic still does not seem to support authenticated proxies as of 5.10. The easiest way to get around this is to go to the proxy setting inside synaptic:

Settings -> Preferences -> Network -> 

and put the following lines in the proxy server:
```
username:password@your.proxy.com 
```
instead of just the server address. 

it sits there in plain text which sucks though.


Hope that helps.

---

### Post by 76thParadox on 2006-08-01
That solution used to work for me but in 6.06 (64bit) it looks like Synaptic won't recognise an authenticated proxy in that way.  Does anyone have another means of using Synaptic or the Ubuntu software updater through an authenticated proxy?

I know that apt-get with work with the right environment variables but I'm looking for a solution for less savy end users.

---

