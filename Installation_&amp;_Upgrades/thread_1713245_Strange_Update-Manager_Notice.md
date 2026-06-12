---
title: "Strange Update-Manager Notice"
date: 2011-03-23
forum: Installation &amp; Upgrades
---

### Post by defensorfedei on 2011-03-23
I recently had to restore my system via clonezilla due to hdd failure.  I frequently back up my /etc/apt folder as well as some other configuration files and settings that I use in my system to bring my restored image up to date with my ever changing preferences, etc...

I noticed the problem when I replaced the etc/apt folder with my backup version. After replacing the folder, I ran 'sudo apt-get update' and imported a list of all my previously installed software. Then I ran 'sudo apt-get upgrade'.  I didn't get any errors at all during any part of the update and upgrade process.

Then this popped up in my panel, and won't seem to go away.

 [IMG]http://dl.dropbox.com/u/21875930/ume.png[/IMG]

Anyone have any ideas?

---

### Post by Dutch70 on 2011-03-24
This is just a hunch, but try going to software sources & make sure the CD-ROM is not checked.

Also, you can try running...
```
sudo apt-get check 
```
to verify there are no broken dependencies.

---

### Post by sadiqdude on 2011-03-24
even i had the same roblem but later when i restarted my system every thing got right:P:P

---

### Post by defensorfedei on 2011-03-24
Hi Guys, thanks for the quick responses.  

I did in fact check to see if cd-rom was checked in my software sources list, which it was not.  Oddly enough, I had to do this through Synaptic Package Manager, as Software Center won't launch unless I launch it from the terminal (this may be part of the problem).

I also ran 'sudo apt-get check' and everything comes back clean.  I have rebooted the system several times since yesterday, but the problem still persists.  I am sure it must be something simple.

Thanks for helping.....perhaps someone else will have an idea of what is going on.  I am going to try and find out why Software Center won't start.

Thanks

---

### Post by plucky on 2011-03-24
> **defensorfedei said:**
> Hi Guys, thanks for the quick responses.  

I did in fact check to see if cd-rom was checked in my software sources list, which it was not.  Oddly enough, I had to do this through Synaptic Package Manager, as Software Center won't launch unless I launch it from the terminal (this may be part of the problem).

I also ran 'sudo apt-get check' and everything comes back clean.  I have rebooted the system several times since yesterday, but the problem still persists.  I am sure it must be something simple.

Thanks for helping.....perhaps someone else will have an idea of what is going on.  I am going to try and find out why Software Center won't start.

Thanks

From a terminal post output of ```
sudo apt-get update
``` and your sources.list ```
cat /etc/apt/sources.list
```

---

### Post by defensorfedei on 2011-03-24
Thanks Plucky,

I went ahead and did a complete reinstall, since I was itching to use the new script I made for the job, so I really can't post the output of those commands since I am no longer using that system.

The not being able to launch gdebi and software center was a deal breaker for me.  It seemed like it was going to take too much patch work to straighten everything out.

I assume the moderator will do whatever he/she wants to do with this thread.

Once again, thanks for the responses.

---

