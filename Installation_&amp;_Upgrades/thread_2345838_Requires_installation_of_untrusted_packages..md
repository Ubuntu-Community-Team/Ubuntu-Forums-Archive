---
title: "Requires installation of untrusted packages."
date: 2016-12-08
forum: Installation &amp; Upgrades
---

### Post by boatcat on 2016-12-08
Hi, 

I'm very new to linux and have just installed Gnome 16.04 on my laptop. 

I'm trying to install some updates through the software updater and get this error:

'Requires installation of untrusted packages. This requires installing packages from unauthenticated sources.'

sudo apt-get update  output is 

> 
Hit:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease
Hit:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease              
Hit:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial InRelease                     
Ign:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease             
Hit:5 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates InRelease       
Hit:6 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release               
Hit:7 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports InRelease    
Get:8 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial/main Translation-en_GB [426 kB]
Get:10 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial/restricted Translation-en_GB [2,556 B]
Get:11 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial/universe Translation-en_GB [3,040 kB]
Get:12 [https://download.01.org/gfx/ubuntu/16.04/main](https://download.01.org/gfx/ubuntu/16.04/main) xenial InRelease [3,651 B]
Ign:12 [https://download.01.org/gfx/ubuntu/16.04/main](https://download.01.org/gfx/ubuntu/16.04/main) xenial InRelease          
Get:13 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial/multiverse Translation-en_GB [88.1 kB]
Fetched 3,560 kB in 1s (1,829 kB/s)                                            
Reading package lists... Done
W: GPG error: [https://download.01.org/gfx/ubuntu/16.04/main](https://download.01.org/gfx/ubuntu/16.04/main)  xenial InRelease: The following signatures couldn't be verified because  the public key is not available: NO_PUBKEY 56A3DEF863961D39
W: The repository 'https://download.01.org/gfx/ubuntu/16.04/main xenial InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.


Thanks for any help!

---

### Post by #&amp;thj^% on 2016-12-08
Try this:
Open terminal and paste this in there
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 56A3DEF863961D39 
```
And then recheck by way of:
```
sudo apt update
```
And if all goes well then enter this:
```
sudo apt upgrade
sudo apt full-upgrade
```
Report back any errors.

---

### Post by boatcat on 2016-12-08
> **1fallen said:**
> Try this:
Open terminal and paste this in there
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 56A3DEF863961D39 
```
And then recheck by way of:
```
sudo apt update
```
And if all goes well then enter this:
```
sudo apt upgrade
sudo apt full-upgrade
```
Report back any errors.

Worked perfectly. Thank you :D

---

### Post by #&amp;thj^% on 2016-12-08
Cool...Your Welcome :grin:
And don't forget to run autoremove  to keep your /boot nice and tidy.
```
sudo apt autoremove
```
Kind Regards

---

### Post by boatcat on 2016-12-08
That's a new one - so much to learn!

---

### Post by #&amp;thj^% on 2016-12-08
> **boatcat said:**
> That's a new one - so much to learn!

Hehe I have been here for 11 years now and still learning new things.
Welcome to the Forums BTW

---

### Post by boatcat on 2016-12-08
Thanks, the forum is so useful. I can tell I'll be posting here quite a bit as I have a couple of other things to sort out already.

Not sure sure if there's anyway to give you 'rep' on here....

---

