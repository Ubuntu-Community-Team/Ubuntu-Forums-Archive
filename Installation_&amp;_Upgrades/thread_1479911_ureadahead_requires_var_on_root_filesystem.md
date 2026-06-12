---
title: "ureadahead requires /var on root filesystem"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by piedro on 2010-05-11
Hi! 

On Launchpad there is the following thread on ureadahead: 

[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/523484](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/523484) 

Is there any workaround yet? 
Is it sensible to remove "ureadahead" until this is fixed or is there no harm done? 

As a normal user ... 
(yes still I have /var in a separate partition, because I want to be on the safe side with my databases located in /var when reinstalling or upgrading the system ... - by the way: does this make sense or is it better to just have /home separate and use a backup of /var folders?) 

... as a normal user I feel a bit lost with bugs like this. It would be nice to get some information somewhere. 

Something like: 
"Don't worry, just wait for an update with a bugfix!" 
or 
"To avoid further problems just remove 'ureadahead' until it's fixed!" 
would be very much appreciated ... 

thx for reading, 
piedro

---

### Post by bigbaraboom on 2010-05-20
Hey piedro,

I have the same issue you're having. I made a thread somewhat similar to yours, take a look [http://ubuntuforums.org/showthread.php?t=1487981]("http://ubuntuforums.org/showthread.php?t=1487981").

So what I'm most concerned with here is what are the potential short/long term effects, of a setup that uses ureadahead as expected, while still maintaining a separate /var partition. I don't know about you, but I get "ureadahead terminated with status 5" on every boot. As some of the links we have found suggest, this is due to ureadahead not waiting for the /var partition's mount.

Following "...status 5" I experience a short but noticeable colorful blinks before my system lands on the login screen. Having said that, it would be ideal if a developer has a suggestion about having a /var partition at all. I personally like it, but if it's going to cause problems then I would have to remove it. I very carefully prepared my partitioning scheme before a clean install of Lynx, and my / partition does not have enough space to hold /var in the long run (as a directory). 

Why is it Ubuntu is trying new things that are largely unnecessary? Part of what makes Linux great is its distance from mainstream OS's, and it's skillful users. Going mainstream is not a good thing, if we'll suffer more bugs due to unnecessary additions. Who cares about saving a second or two during boot?!

---

### Post by piedro on 2010-06-04
Hi bigbaraboom! 

Though I feel the same way like you about establishing new features that mess up others we're already familiar with, - I think I found an easy workaround for the "should I still go with a seperate /var or better not"-question: 

On my home partition I create folders for all my databases (Mysql, postgresql, mpd e.g.), and now I symlink these into the respective /var locations ... simple & clean! 

I now have all(!) my individual system data on my seperate /home partition - no more need for searching update paths when doing a clean install ... 

/home looks like that now: 

/home/ > user1, user2, user3 ... , system 
/home/system/databases > mysql, postgres, mpd ... 
/home/system/settings > etc 

Just have to be careful with the file permissions to make them exactly like in their original locations ... 

Probably easy and obvious to the most users out there, I'm just glad you can do stuff like that with linux. 

thx for reading, 
piedro

---

### Post by kansasnoob on 2010-06-04
Eerrm, ureadahead is still quite a mystery to me but I don't believe it can be just removed. The lead ureadahead dev posted these notes during Lucid development:

[http://ubuntuforums.org/showthread.php?t=1434502](http://ubuntuforums.org/showthread.php?t=1434502)

I hope something there might be of value to you.

---

### Post by sblandford on 2012-02-04
I just faced the same problem with ureadahead throwing an error "5" on boot because I had set up var to be on a separate partition.

I resolved it by creating a skeleton /var directory tree on the root partition that keeps ureadahead happy until the real /var partition is mounted. I just copied what was on the /var partition to this directory and deleted all the log files, caches, databases and spools.

I was able to boot with no problem after that.

---

