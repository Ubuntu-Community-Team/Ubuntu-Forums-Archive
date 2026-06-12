---
title: "Ubuntu 9.04 don't want to upgrade"
date: 2011-11-30
forum: Installation &amp; Upgrades
---

### Post by roxy99 on 2011-11-30
Hi,

I like to dabble in linux but am by no means an expert.  What I have is a 9.04 server install acting as a media server to Windows PCs and an XBMC.  

Recently, I wanted to expand the file server into a LAMP server.  So I figured, no problem - sudo apt-get install apache2 , etc , etc.

[begin rant]The problem is, the sources.lst are no longer supported!!!  I don't care if Ubuntu doesn't want to keep patching and supporting the old 9.04 version but at least keep the bloody packages as they exist there for us slow adopters.  I don't want to upgrade and muck around if 9.04 is working fine.. [/end rant]

So I thought- Plan B:  I'll compile manually the MySQL etc.  Now, I get no valid C compiler?  Where can I get the deb package for gcc or whatever I need?

If its really going to be a nightmare, then I'll do a clean install to 12.04 although I really don't see why I should need to.  If I do need to upgrade though, how can I ensure my media drives are safe?  Should I unplug them while I install Ubuntu and then mount them later? 

It took me a while also to set up fstab, samba and everything else.  Can someone remind me of exacly all the config files I need to backup so that I can more easilly reconfigure the new install.

Thanks

---

### Post by roxy99 on 2011-11-30
sorry double post

---

### Post by Old_Grey_Wolf on 2011-11-30
> **roxy99 said:**
> 
[begin rant]The problem is, the sources.lst are no longer supported!!!  I don't care if Ubuntu doesn't want to keep patching and supporting the old 9.04 version but at least keep the bloody packages as they exist there for us slow adopters.  I don't want to upgrade and muck around if 9.04 is working fine.. [/end rant]

The old release repositories are stored at [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

You will have to manually edit your sources.list file to point to the "old-releases...." repository that you need.

---

### Post by roxy99 on 2011-11-30
Thanks I tried that and it just seems to be a list of complete install images (eg- [http://old-releases.ubuntu.com/releases/jaunty/](http://old-releases.ubuntu.com/releases/jaunty/)).

Can you be more specific because I am not that familiar with editing the sources.lst file?

---

### Post by dFlyer on 2011-11-30
As far as I know 9.04 is no longer supported and it may be time to upgrade. You may want to 12.04 comes out before you upgrade as it will be LTS as compared to everything else. Of course you can try 10.04 as that is LTS and has the longest support for servers.

---

### Post by funfrank on 2011-12-01
I also would like to continue using Jaunty 9.10, and cannot find the repos.  Anybody know where they are?

FunFrank

---

### Post by snowpine on 2011-12-01
> **funfrank said:**
> I also would like to continue using Jaunty 9.10, and cannot find the repos.  Anybody know where they are?

FunFrank

9.10 is also obsolete and unsupported, so the repositories moved to old-releases.ubuntu.com

---

### Post by roxy99 on 2011-12-01
> **snowpine said:**
> 9.10 is also obsolete and unsupported, so the repositories moved to old-releases.ubuntu.com


Please can someone just copy and paste a sample sources.list file for me?  I can see I am not the only one who doesn't feel the need to upgrade to 11.04 just because Ubuntu says they don't support 9.04 anymore.  I am only using this linux system as a file server so why should I make a major surgery on the system just to install Apache?  Now, I can't even run sudo apt-get update.  

I visited old-releases.ubuntu.com and its just a site with download mirrors.  How do I figure out what to download for 9.04?  How am I supposed to fix the broken packages on my system now?  I used to run sudo apt-get update and everything would fix itself.

There has to be an easier way to get Ubuntu 9.04 to install missing packages without having to upgrade to 11.04(or whatever)

What does it mean 'The old release repositories are stored at [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)'.  What do I do to get them to install? I am running a non-gui 9.04 server system.

Windows XP is not supported anymore either, but I can still run windows update and MS will still install missing security patches.  Granted, there will be no new patches released but to the extent that I haven't updated Windows XP for over a year and it may be missing some patches released a year ago, then it will update those old patches.  I have never heard of an operating system that just simply stops working after the end of its support cycle.  What is this ?? Some sort of planned obsolescence on Linux's part? If that were true then linux would'nt be so robust as it is today.

Please someone tell me there has to be an easier way to obtain Apache2 and MySql and PHP5 for my 9.04 Ubuntu server.

---

### Post by snowpine on 2011-12-01
Ubuntu 9.04 is completely unsupported. Any security vulnerabilities or bugs will **never** be patched. I cannot recommend 9.04 for your web server.

If you are interested in running a 9.04 server **for educational purposes only** then edit sources.list using your favorite text editor, for example:

```
sudo nano /etc/apt/sources.list
```

Change all URLs to old-releases.ubuntu.com, for example change this:

```
deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse
```

to this: 

```
deb http://old-releases.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse
```

Save the file and quit. Now you should be able to 

```
sudo apt-get update
```

and install unsupported, obsolete applications from the Jaunty 9.04 repos.

Most Ubuntu releases are supported 18 months, if you don't like that cycle then you should get on the LTS cycle; the LTS releases are supported 5 years. :)

---

### Post by roxy99 on 2011-12-02
> **snowpine said:**
> Ubuntu 9.04 is completely unsupported. Any security vulnerabilities or bugs will **never** be patched. I cannot recommend 9.04 for your web server.

If you are interested in running a 9.04 server **for educational purposes only** then edit sources.list using your favorite text editor, for example:

```
sudo nano /etc/apt/sources.list
```

Change all URLs to old-releases.ubuntu.com, for example change this:

```
deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse
```

to this: 

```
deb http://old-releases.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse
```

Save the file and quit. Now you should be able to 

```
sudo apt-get update
```

and install unsupported, obsolete applications from the Jaunty 9.04 repos.

Most Ubuntu releases are supported 18 months, if you don't like that cycle then you should get on the LTS cycle; the LTS releases are supported 5 years. :)

Thank you !  That worked like a charm.  I got all the LAMP components working.  I should have heeded snowpines advice and upgrade though.  Bad news:  Everything was working and then I installed a web based media server called Subsonic then all hell broke loose.  To make a long story short, I lost the root user and now I can't even login.  The server boots as normal but does not accept my user and password.

What is the best way now to backup my music and videos?  I hope that my data is still intact.  I imagine that the linux file system got corrupted and hopefully its not a hard drive failure.

---

### Post by snowpine on 2011-12-02
It is easy to reset your password if you're locked out:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

If you need an introduction to backups, this page should get you started: 

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by roxy99 on 2011-12-03
OK I  tried to drop to the promot from recover mode and the error given is:
Sulogin: cannot open password database

So the password database is corrupted.

---

### Post by snowpine on 2011-12-03
In that case you can boot with an Ubuntu Live CD and use that to copy your documents/data to an external hard drive or something.

---

