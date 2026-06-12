---
title: "Copying my setup to another Laptop"
date: 2014-01-10
forum: Installation &amp; Upgrades
---

### Post by chrispepper1989 on 2014-01-10
Hi Everyone,

This may seem like a bit of a noobish question but whats the best way to replicate my set up on someone elses machine? 

I was thinking of just using clonezilla to create an img and then restore that on the other machine but I was wondering if that was the *best* way. My machine is an Asus ebook (netbook) and their machine is a Dell Laptop, so there are a lot of hardware differences. Will Xubuntu be able to work out the hardware differences at boot up and solve them? Or will this incur bloat and issues later? plus i would have to change the user name and home folder etc.

It seems that it would be *cleaner* to do a fresh install of Xubuntu and add all the packages and stuff again but it took me a good day to set up my netbook and the person I am setting it up for basically wants the exact same set up as mine. And its not a portable machine so I would have to set it up at their house...

Is there a better way that I can package up my desktop set up, the installed packages, the launcher configuration and create a live os that i can install that set up with? That would be the ideal situation as I envision repeating this install for other people. If I was to set up a persistent Xubuntu USB and set up the desktop etc in a certain way, is that how it would then be installed?

-Thanks, Chris

---

### Post by ibjsb4 on 2014-01-10
I am also thinking clonezilla :)

[http://ubuntuforums.org/showthread.php?t=2197659&highlight=](http://ubuntuforums.org/showthread.php?t=2197659&highlight=)

---

### Post by oldfred on 2014-01-10
Clonzilla should work. 
But a image copy will also make your user & password the default on new install, which you will have to reconfigure.

But how similar are systems?
Are both systems BIOS or both UEFI?
Did you have to install any proprietary drivers for video or Internet?
Are both Intel or AMD, still should work but better if similar.

But I install every new version, but keep 12.04 as my standard. And a full install after partitioning in advance takes 10 to 20 minutes, updates another 10 to 20 minutes depending on how old ISO is to current and usually another 20 minutes doing configuration. Or an hour. But then I am doing it more often and have fast Internet.
But if you copy your entire /home that copies all of the (hidden) user configuration & settings.

Many Dell XPS have sputnik updates for 12.04 or should have all those features installed in 13.10.

This covers some extra things like a complete list of installed apps and other settings to consider. My backup assumes I will just do a clean install and restore /home, installed packages and maybe some other settings from /etc.

       Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

