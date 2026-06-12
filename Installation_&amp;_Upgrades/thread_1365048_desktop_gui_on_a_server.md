---
title: "desktop gui on a server"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by t00ls on 2009-12-26
I think this is my second post..... anyways

I searched and searched for a way to install the desktop gui on  ubuntu server without having to download it each time,without  any good results.

That being said...I did piece together some of my findings to come up with a solution ...I think.

after I installed ubuntu server off my cd, I logged in. After that I placed a ubuntu desktop cd in. typed in
```
sudo apt-cdrom add
```when that finished, I typed in
```
sudo tasksel
```that brought up a list of items to install as well as ones you had already installed for the server side of ubuntu, at any rate...I scrolled down and found ubuntu desktop,highlighted it,hit the space bar,hit enter, and waited.

I thought it was stuck or froze and was about to reset ... then it came up another screen

this screen says package configuration, and is currently retrieving files.

I thought this would take less time since it was coming off the cd....but right now it is connected to the internet downloading the package, instead of taking it from the cd

any ideas about what I missed :confused:

---

### Post by taurus on 2009-12-26
You forgot to run "sudo apt-get update" after you've added the CD as your source.  Therefore, it doesn't know it should install stuff from the CD.

---

### Post by t00ls on 2009-12-26
oops...that one slipped by me....thanks for a quick reply

I'll try it to see if that does it

---

### Post by t00ls on 2009-12-26
nah...still trying to retrieve it from the internet....I'll keep trying something different

anyone else have a solution?

---

### Post by taurus on 2009-12-26
Try the alternate CD instead of the desktop/LiveCD.

---

### Post by Dayofswords on 2009-12-26
not that i know anything but, wouldn't *sudo apt-get install ubuntu-desktop* work?

---

### Post by t00ls on 2009-12-26
yes the apt-get install ubuntu-desktop will work fine....over the internet

I want to be able to install without having to re-download the package each time

I am experimenting with a server install....but would like to have the gui

each time I decide to re-do everything, I dont want to have to re-download,consuming bandwidth

I think taurus has the solution....I will try the alternate cd...

thanks for the help... if I have to do this again and the alternate cd works ...I will post again

for now ...everything is up and running again

---

