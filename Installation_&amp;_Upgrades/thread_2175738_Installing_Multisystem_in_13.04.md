---
title: "Installing Multisystem in 13.04"
date: 2013-09-20
forum: Installation &amp; Upgrades
---

### Post by andytlong on 2013-09-20
Hello all,

I'm really not sure if this post is in the right area, as I seldom post on Ubuntu Forums. I'm more of a lurker, and nearly always find a solution in this wonderful resource we have.

Anyways, to the meat of my post. I was attempting to install Multisystem on my 13.04 system, but was running into a few issues. First of all, the website is in French, which really isn't a problem except that Google translate isn't the best tool in the world to use. Following the installation instructions, I downloaded the bash script, but whenever I attempted to install it using that method, I was constantly met with:```
install-depot-multisystem.sh: 2: install-depot-multisystem.sh: Syntax error: redirection unexpected
```. 
So, I continued researching how to go about such an installation and was met with instructions on how to do it via apt, which I tried and was met with more subsequent failures such as:```
W: Failed to fetch http://liveusb.info/multisystem/depot/dists/all/hand/binary-i386/Packages  404  Not Found
```. 
[SIZE=5]**My Workaround:**[/SIZE]

      1. I tweaked the installation instructions a bit, and this is what worked for me:```
sudo nano /etc/apt/sourcesl.list
``` 
       2. and then I added```
deb http://liveusb.info/multisystem/depot all main
``` to the end of the file. 

       3. Next, I updated my repositories:```
sudo apt-get update
``` 
       4. and then installed Multisystem:```
sudo apt-get install multisystem
```. 

Everything seems to be working thus far. For those who have also been having problems installing Multisystem, you may try this method and see if it works for you.

---

### Post by on32 on 2014-02-20
Thank you. Very simple and working. The guide at multisystem's website is kinda old and having issue with the script.

---

### Post by guitarafro on 2014-06-24
I don't mean to necropost, but the command should be```
sudo nano /etc/apt/sources.list
```

Just fixing for people after me that can't figure out why it's not working.

---

