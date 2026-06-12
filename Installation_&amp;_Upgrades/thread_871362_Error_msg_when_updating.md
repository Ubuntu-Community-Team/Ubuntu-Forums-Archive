---
title: "Error msg when updating"
date: 2008-07-26
forum: Installation &amp; Upgrades
---

### Post by cfishburn on 2008-07-26
I down loaded the latest version of Ubuntu about 30 days ago and now when ever I download new updates I get the following.

 E: flashplugin-nonfree:subprocess post-installation script returned error exit status 2.

 The just got this message when downloading updates to Firefox
Not a total newbee, but confused never the less. What's missing?
Thanks in advance

---

### Post by Partyboi2 on 2008-07-26
Can you post the more of the error message like the 5 or 10 lines before it?

---

### Post by cfishburn on 2008-07-27
Partyboi2,
Unfortunately, that's the only error message. The other item after downloading Hardy is that the default photo shop change to F-spot and now I can upload from my camera -
"Error writing to port" pops up, I wonder if I shouldn't try to download Hardy again.

---

### Post by zvacet on 2008-07-28
```
sudo apt-get update && sudo apt-get upgrade
```

Post output here.

---

### Post by cfishburn on 2008-07-28
Thanks zvacet. Ran your code suggestion and received following error message
  
Sorry the package"Flashplugin-nonfree 9.0.124.0 Ubuntu2" failed to install or upgrade.

I have reported the error any thoughts on what to do next.

Thanks
cfishburn

---

### Post by SkonesMickLoud on 2008-07-28
In a terminal copy/paste:

```
sudo aptitude update && sudo aptitude install flashplugin-nonfree
```

If it gives you the same error or tells you that it is already installed:

```
sudo aptitude remove flashplugin-nonfree && sudo aptitude install flashplugin-nonfree
```

---

### Post by cfishburn on 2008-07-28
SkonesMickLoud,
Thanks for the help.
The following appears after running your first suggestion:

Flash Plugin installed.
update-alternatives: unable to make /usr/lib/firefox/plugins/flashplugin-alternative.so.dpkg-tmp a symlink to /etc/alternatives/firefox-flashplugin: No such file or directory
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 flashplugin-nonfree
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             

Where to from here or do I ignore this
cfishburn

---

### Post by SkonesMickLoud on 2008-07-28
Odd, I have the same plugin installed, yet I don't have an "/etc/alternatives/firefox-flashplugin" directory either.  It seems that the installation is trying to find it.

You could try:

```
sudo mkdir /etc/alternatives/firefox-flashplugin
```

Then try again.  Can't guarantee that this'll work though.

---

### Post by iaculallad on 2008-07-28
I've had this kind of problem once, try doing this:

```
sudo apt-get install -f
```

---

### Post by cfishburn on 2008-07-28
StonesMickLoud,
And the result is:

cfishburn@ubuntu:~$ sudo mkdir /etc/alternatives/firefox-flashplugin
mkdir: cannot create directory `/etc/alternatives/firefox-flashplugin': File exists

Seems to me like end of road? I'll try iaculallad's suggestion.
cfishurn

---

### Post by cfishburn on 2008-07-28
Bingo. Thanks for your help.

Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
Installing from local file /var/cache/flashplugin-nonfree/install_flash_player_9_linux.tar.gz
Flash Plugin installed.

---

