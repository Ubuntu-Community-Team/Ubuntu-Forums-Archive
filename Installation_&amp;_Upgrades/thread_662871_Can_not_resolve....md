---
title: "Can not resolve..."
date: 2008-01-09
forum: Installation &amp; Upgrades
---

### Post by rorsino on 2008-01-09
Hello
I have just installed 7.10 on a pc.During the install I got an error message about not being able to resolve security.ubuntu.com.  After the install finished and rebooted I got to the command prompt ok. When I run sudo apt-get install ubuntu-desktop or sudo apt-get update, all od the http references in the sources.list can not be resolved.  I have looked at every "solution" here and my source.list looks good.  I can ping my network computers, my routers etc.  Im not sure where to go from here.  Ant help would be greatly appreciated.
Robert

---

### Post by taurus on 2008-01-09
You now need to enable those repos in your /etc/apt/sources.list so you can install other stuff.

```
sudo nano -Bw /etc/apt/sources.list
```
Put a # in front of the first line to comment out the cdrom option and then remove the # in front of all the lines that start with **deb** & **deb-src**.  Save it with <Ctrl>o and exit with <Ctrl>x.  

Then run

```
sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

### Post by rorsino on 2008-01-09
I have commented out the CD-Rom statement and have removed all the # in front of those lines.

As soon as I run the sudo apt-get update I still get the 
can not resolve messages..

ugh...

---

### Post by taurus on 2008-01-09
Can you post your /etc/apt/sources.list and the output of this command from a terminal?

```
cat /etc/apt/sources.list
sudo apt-get update
```

---

### Post by rorsino on 2008-01-09
I will have to do it by hand since it is on another PC.  I will do it a bit later this afternoon :)

---

### Post by D1n0 on 2008-06-18
I'm having the same issue after a fresh install of 8.04 on a HP 2133 mini-note.  After running sudo apt-get update I get the following errors for each repository in my etc/apt/sources.list
.
.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-proposed/universe Translation-en_US
  Could not resolve 'http'
Reading package lists... Done
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'http'
.
.
I'd really appreciate help resolving this config issue.

---

### Post by Deanje on 2008-06-19
I've been having the same issues with 8.04 as well, I've spent hours on it. The repo's are pingable but apt-get update brings up a load of Cannot resolve messages. I'll be watching this thread!

---

