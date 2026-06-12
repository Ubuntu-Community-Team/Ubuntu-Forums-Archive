---
title: "Problem with Ubuntu - After Installation"
date: 2011-04-09
forum: Installation &amp; Upgrades
---

### Post by Zimbu on 2011-04-09
Hi Everyone,
I'm new with LINUX Platform.
I have Windows XP installed in my desktop PC and i have insatllled UBUNTU 10.10 downloaded from ubuntu webiste in VMWARE.

I wanted to install Oracle in linux, So i downloaded oracle10g from oracle website for linux and when i double clicked the downloaded file. It gives me the following error



[IMG]http://www.imgupload.org/images/219_archieve_not_found.jpg[/IMG]


I was advised by 1 forum to "The list of available applications is out of date. So try to update & try again !" and this is the error i get.

[IMG]http://www.imgupload.org/images/329_download_repos_failed.jpg[/IMG]

[COLOR=Black]
[/COLOR] [COLOR=Red][COLOR=Black]My internet connection are all fine ![/COLOR][B]

Kindly get me out of this. I'm struck up.
Is it a problem caused by UBUNTU or ORACLE SETUP FILE or AM I MISSING SOMETHING ![/B][/COLOR]

Should i re install Ubuntu or
Should i re download Oracle ?

I'm not able to move forward or backward !
Not sure what is the problem !

---

### Post by coffeecat on 2011-04-09
You are trying to install a RPM package in Ubuntu. That won't work. You need a deb package for Ubuntu.

But you were told this a week ago in your other thread:

[http://ubuntuforums.org/showthread.php?t=1716856](http://ubuntuforums.org/showthread.php?t=1716856)

---

### Post by Zimbu on 2011-04-09
Yes. Sorry i almost forgot whether i have posted it before.
You are right that i posted few weeks back & i turned busy with my office stuffs....
Anyways thanks a lot for the reply.
I'll check with that solution & if that does'nt work, Then i'll come back !

---

### Post by Zimbu on 2011-04-10
I downloaded the Debian Oracle setup & now when i double click it gives me this error !
**[COLOR=Red]Error: Dependency is not satisfiable: libaio|libaio 1[/COLOR]**

---

### Post by coffeecat on 2011-04-10
Those are called dependencies. You need to read the documentation provided by Oracle. The link posted in your other thread > Installation guide > Requirements leads to this:

[http://www.oracle.com/technetwork/database/express-edition/downloads/toc-090217.html#CIHFEBGE](http://www.oracle.com/technetwork/database/express-edition/downloads/toc-090217.html#CIHFEBGE)

However, those pages date from 2006. You may or may not be able to get Oracle to work in recent version of Ubuntu.

The two dependencies you need are libaio which is in the repository - simply install it with Synaptic. And glibc which isn't called glibc in Ubuntu. Install the package build-essential and you'll get libc6-dev and libc-dev which will probably do the trick.

---

