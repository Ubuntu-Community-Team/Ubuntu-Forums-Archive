---
title: "dpkg errors after updgrade to maverick"
date: 2010-11-15
forum: Installation &amp; Upgrades
---

### Post by JaceMan on 2010-11-15
I am experiencing the same issue, with the same package, as the user from this "solved" thread.

[http://ubuntuforums.org/showthread.php?t=1545072&page=2]("http://ubuntuforums.org/showthread.php?t=1545072&page=2")

My question comes as this... the fix was to change the package name to one without underscores in it.  The underscores were changed to tildas.  What I don't understand is where I make those changes.

Crisnoh said that he tried commenting the package out of the 'file' but that didn't work.  However, changing the file name to tildas did... so which file am I supposed to be editing to change these underscores to tildas?

Thanks.

---

### Post by plucky on 2010-11-16
> so which file am I supposed to be editing to change these underscores to tildas?



The file is called status.
Open a terminal and ```
gksudo gedit /var/lib/dpkg/status
``` and search for 'virtualbox'.

Be careful with editing a system file,if you aren't sure what you are doing make a backup copy first.```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.backup
```
The version number should look like **Version: 3.2.10-66523~Ubuntu~karmic** with the tilda (~) instead of the underscore (_)


Good Luck

---

### Post by JaceMan on 2010-11-16
Thanks for the reply.  I actually wound up fixing the issue by other means.  I'd post what I did here to help others, unfortunately I have no idea what I did. :oops:

All I know, is that I tried a couple dozen things from various searches and only created new problems for myself.  I had to back track by way to get back to the lone issue, and from there I eventually stumbled upon a fix. :P

I will keep these instructions though in case I experience trouble with another package in the future.

---

### Post by dino99 on 2010-11-16
reboot

then:

sudo dpkg --configure -a
sudo apt-get install -f

---

### Post by JaceMan on 2010-11-16
As I was saying, it's fixed now.  I did try:

> sudo dpkg --configure -a
sudo apt-get install -f

that though.  That didn't bare any fruit for me.

---

