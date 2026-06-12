---
title: "lubuntu server vs ubuntu server for openbox desktop"
date: 2016-04-10
forum: Installation &amp; Upgrades
---

### Post by PeterTaps on 2016-04-10
I have build many Ubuntu machines. My standard configuration would be:

1. Install ubuntu-server and login
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get install xorg openbox
$ startx

This has always given me a very lean desktop environment and works amazingly well.

From what I have read, lubuntu server is ever leaner. I am thinking I will install lubuntu-server instead of ubuntu-server. Rest of the steps I guess can stay the same. 

Q1, Will my approach work? Is there anything I am missing?
Q2. Is lubuntu-server really leaner than ubuntu server?

Regards,
Peter

---

### Post by Ricardo_Parraga_Za on 2016-04-10
Hi Peter,

Good question. I believe they should be the same for server, but not for desktop. You can try your same drill and install the lubuntu server and then check:

How many packages are installed
```
dpkg -l | wc -l
```
How much hard drive space is being used
```
df
```
How are the processes running
```
top
```
How much memory is being used
```
free
```

Meybe you have an idea now and you can compare for yourself.

---

### Post by deadflowr on 2016-04-11
Lubuntu-server?

I'm pretty sure there is no such thing.

If there was, by definition it would have to be fatter, as it would contain the lxde desktop packages.
Ubuntu server does not contain any desktop packages, by default.

Where can you find Lubuntu server?

---

### Post by papibe on 2016-04-11
Hi PeterTaps.

AFAIN, there's no lubuntu-server. Lubuntu is desktop distribution. It is indeed lean, but compared to other desktop distributions.

Lubuntu includes lots of pre selected desktop applications, not necessarily thought for a server. Nevertheless, you may want to try LXDE, Lubuntu's desktop. So instead of installing openbox you could do:
```
sudo apt-get install lxde
```
Note that you can install both, and choose either openbox or lxde at log in.

More info [here]("http://askubuntu.com/questions/193861/what-is-the-difference-between-lubuntu-and-lxde"), [here]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu"), and [here]("http://askubuntu.com/questions/543829/how-to-disable-lxde-and-use-openbox").

Hope it helps. Let us know how it goes.
Regards.

---

### Post by PeterTaps on 2016-04-11
Thank you all for your help.

Looks like I was mistaken. There is no lubuntu server. There is only ubuntu server.

Looks like lxde is may be what I was looking for.

Previously, I used to install xorg and openbox. Just installing openbox with xorg would not work.

$ sudo apt-get install xorg openbox

If I have to install lxde on top of Ubuntu server, do I need to explicitly install xorg?

$ sudo apt-get install xorg lxde

Or, just installing lxde is good enough?

$ sudo apt-get install lxde

Also, if I install lxde, is it assumed that openbox is automatically getting installed?

Appreciate your help.

Regards,
Peter

---

### Post by papibe on 2016-04-11
Installing lxde should be enough, as it will pull all other dependencies.

Now, you could even try to go even leaner (haven't tried myself) and install this instead:
```
sudo apt-get install lxde-core
```
Regards.

---

### Post by The_Woodpecker on 2016-04-11
There is no such thing as Lubuntu-server although Lubuntu does make a good quick 'server' OS especially if you need a GUI for applications. Ubuntu is abit to heavy GUI-wise for a server unless you use the server version but then you need to install the GUI

---

### Post by PeterTaps on 2016-04-14
Thank you for your help. I will try this out.

---

