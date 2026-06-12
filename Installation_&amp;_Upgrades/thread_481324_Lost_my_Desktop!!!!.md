---
title: "Lost my Desktop!!!!"
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by pebberbrown on 2007-06-22
Hello out there!
Boy these forums are a fantastic idea.
hey now
I was messing around late last night with the add/remove programs
and I somehow managed to delete something vital to my system

All I get now is a command line interface uponboot with
error message indicating I've lost my X windows.

Is there an easy way to repair this short of re-formatting and re-installing?
If not oh well - I only have 1.6GB of data to extract somehow....
My plan was to install Ubuntu on a NEW HD and then attache teh old HD as a second
drive and grab the data off of it once I was up.

feel free to email me directly

[email]pebberbrown@gmail.com[/email]

[www.pbguitarstudio.com](www.pbguitarstudio.com)

---

### Post by Claus7 on 2007-06-23
Hello,

may be it is because you seem to have done something to X-server. In order to (re)configure X-server you have to type the following command :

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

With this command I had reconfigured my X-server so as to have my desktop back (yet not because I was changing something in synaptic).

In case this doesn't work have a look also to /etc/X11/xorg.conf file.
In the above file you may find useful information on how to set up your X-server.
I hope this helps.

Regards!

---

### Post by Claus7 on 2007-11-26
Hello,

the other time I had to use this command was when I had to change my graphic card. I was able to do the configuration via the recovery mode though using the same command. Just FYI.

Regards!

---

