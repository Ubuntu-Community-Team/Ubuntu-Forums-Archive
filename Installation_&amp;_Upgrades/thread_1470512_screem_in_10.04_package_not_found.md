---
title: "screem in 10.04: package not found?"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by bohemier on 2010-05-02
Hello everyone,

I'm trying to install screem in 10.04. I can't find the package... where did it go?

```

sudo apt-get install screem
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package screem

```

Thanks!

---

### Post by tbrminsanity on 2010-05-04
Yeah I noticed this as well.  I tried to install Screem from source but it won't recognize my GLib :-x .  If Canonical isn't going to include Screem in the Repos I want to know a Repo that does include it, and if none exits then I want to know a good replacement for Screem.

---

### Post by bohemier on 2010-05-04
> **tbrminsanity said:**
> Yeah I noticed this as well.  I tried to install Screem from source but it won't recognize my GLib :-x .  If Canonical isn't going to include Screem in the Repos I want to know a Repo that does include it, and if none exits then I want to know a good replacement for Screem.

There's Bluefish and Quanta, which I was testing and wanted to compare with Screem.

I tried to compile screem but wasn't able to. I finally got all dependencies, but make fails...

If anyone knows a repo that would be nice.

TIA

---

### Post by markrawcliffe on 2010-05-05
Hello all, I got make failed too after installing all the dependencies.I gave up and installed Bluefish from the repos. Is it as full-featured though? Does it have FTP capabilities etc?I found a post somewhere asking why you would try and build manually when it's in the repos. Must just be this version of Ubuntu that can't see it?

---

### Post by bohemier on 2010-05-05
> **markrawcliffe said:**
> Hello all, I got make failed too after installing all the dependencies.I gave up and installed Bluefish from the repos. Is it as full-featured though? Does it have FTP capabilities etc?I found a post somewhere asking why you would try and build manually when it's in the repos. Must just be this version of Ubuntu that can't see it?

I know it was in 9.10 repos because I installed it once when I had 9.10. But it isn't there in 10.04.

As for FTP support, I don't remember if it had any. But everyone will tell you that you can mount ftp locations directly into your system (Connect to server)... This is true but sometimes the file-open dialog will not show remote locations. To bypass this problem, I simply look for my mounted ftp locations in ~/.gvfs

HTH

---

### Post by FastRPN on 2010-05-07
This is my first upgrade; from 9.10 to 10.04. Is this a common thing? Screem was easy to configure and to use.

 Re-installing or adding 2 or 3 ftp accounts to new applications is no  big deal, but I wouldn't look forward to upgrades if I have to do it  every time. Firefox routinely drops extensions and themes due to incompatibility, which frankly I have never understood.

Do Ubuntu upgrades typically remove or delete applications  and is the list of viable applications pretty stable?

---

### Post by Mr Nemo on 2010-05-14
I know this thread is a bit old, but since I miss screem too...: Screem seems to be discontinued in lucid ATM due to its reliance on deprecated/removed libraries from within lucid. Or so I hear. It would be nice if someone knew of a way to fix this.

---

### Post by Mr_CHISOL on 2010-06-01
Found this thread when I searched for a solution to get Screem working in Ubuntu 10.04 and just wanted to share my (easy?) solution..

Just make a search for "Screem deb" (without qouts..) (or just go here: [http://packages.debian.org/lenny/i386/screem/download](http://packages.debian.org/lenny/i386/screem/download) ) and download and install that deb.. Worked fine for me.. :?)

---

### Post by Mr Nemo on 2010-06-07
You can load an older version of screem into lucid, but it will be unstable because of missing dependencies in 10.04. Screem will probably crash a lot if you load the older version. I found a good alternative to screem though. 

[http://www.activestate.com/komodo-edit](http://www.activestate.com/komodo-edit)

This is a very nice html editor, and it seems powerful. It has a nice autofill feature that screem had, and it is free/opensource for linux. Seems to be a very cool program. I like it better than bluefish and komposer so far.

---

### Post by benneh on 2011-06-24
Try:
[http://launchpadlibrarian.net/18505135/screem_0.16.1-4.2ubuntu1_i386.deb](http://launchpadlibrarian.net/18505135/screem_0.16.1-4.2ubuntu1_i386.deb)

It works for me!

---

