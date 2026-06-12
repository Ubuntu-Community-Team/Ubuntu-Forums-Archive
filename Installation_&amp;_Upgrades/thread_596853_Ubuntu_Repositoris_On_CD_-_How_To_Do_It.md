---
title: "Ubuntu Repositoris On CD - How To Do It?"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by beebuntu on 2007-10-30
I have loaded Ubuntu 7.1 on a guys computer, and he has no internet connection as of yet.  Until he does have connectivity, how do I get Ubuntu repositories on CD so that he can add software to his system with Synaptic using the CD option?

Or, is this something I would not want to do?

Thanks.

bb

---

### Post by thelocust on 2007-10-30
The installation dvd has all the repo's on it.

---

### Post by mdebusk on 2007-10-30
> **beebuntu said:**
> I have loaded Ubuntu 7.1 on a guys computer

Careful. It's 7.10.

> how do I get Ubuntu repositories on CD so that he can add software to his system with Synaptic using the CD option?

You could do it [thread=352460]this way[/thread] as long as you [size=+1][color=red]mind the warning in the first post[/color][/size].

Better still would be to have him use Synaptic Package Manager to select everything he wants, write a download script (it's in the **File** menu), give the file to you on a flash drive, and have you run the script for him. He could then move everything to his /var/cache/apt/archives directory and it'll work with Synaptic as if he'd downloaded it all.

He'll need your sources lists. I can't recall what they're called or where they are on my system, but I imagine someone here knows.

---

### Post by mdebusk on 2007-10-30
> **thelocust said:**
> The installation dvd has all the repo's on it.

I wish it could be so. (I always get the DVD because I'm on dialup.) It has a LOT of stuff the CD doesn't have, but not all of every repo. That takes about **four** DVDs.

I never get all of the repos because I figure they'll be changed by the time I download all of the packages. If I have a huge download, I borrow bandwidth from my GF or from someone else with a broadband connection.

---

### Post by thelocust on 2007-10-30
> **mdebusk said:**
> I wish it could be so. (I always get the DVD because I'm on dialup.) It has a LOT of stuff the CD doesn't have, but not all of every repo. That takes about **four** DVDs. Thanks for the correction, guess I heard wrong.

---

### Post by beebuntu on 2007-10-30
Thanks for all the replies. I appreciate it.

Where can I find the DVD's to download?  All I have found is the live CD from the link on the Ubuntu home page. Does the live CD have extra stuff on it?

---

### Post by zvacet on 2007-10-30
[http://blog.mypapit.net/2006/08/get-ubuntu-repositories-on-dvd.html]("http://blog.mypapit.net/2006/08/get-ubuntu-repositories-on-dvd.html")

Please,read  Jigdo tutorial before you start.

---

### Post by beebuntu on 2007-11-01
jigdo doesn't install from synaptic. Tried it 3 times.  Here is the error message:

[B]E: xcwcp: subprocess post-installation script returned error exit status 10
[/B]

So, I went to the recommended Indonesian ftp site and am downloading over 4gb of dvd repository stuff.  Too bad the dl speed is only 67 kbps. In twenty four hours I should have the entire iso file if I don't get bumped off my connection.  Been downloading since 1:00 AM Eastern time, and at 10:45 AM, I am only 34% of the way there for the 4.3512 GB file.

Seems that this stuff might be available domestically in USA..  

I don't intend to start another thread on this, but, any suggestions on how to get jigdo installed would be appreciated.

bb

---

