---
title: "install gnome for ubuntu server 10.10"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by cyl3032 on 2010-10-18
I know this question has been asked many times. However I just cannot make it done following all those descriptions. What I want to do is install minimal gnome from ubuntu CD on my server. First I run the command "**apt-cdrom add**". Then I start running **apt-get install xxx** where xxx includes gnome, gnome-core, xorg, gdm, gnome-applets and everything I saw from the search result but nothing works. I always see errors about package not found. I thought maybe server CD doesn't include gnome package so I use desktop CD to try again but still got failed. I really have no idea what's wrong here.

---

### Post by lechien73 on 2010-10-18
Have you read this "howto": [https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

---

### Post by cyl3032 on 2010-10-18
> **lechien73 said:**
> Have you read this "howto": [https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

No, I don't. I found the big problem to me is why I cannot find desktop packages in setup CD, both server and desktop editions. After connecting my computer to Internet, I finished my desktop installation with a simple apt-get command. I don't believe setup CD not including desktop packages but I just cannot find them.

---

### Post by souptafied on 2011-01-10
The name of the package for the default ubuntu desktop has changed.
Try typing:

sudo apt-get install ubuntu-desktop

If you're having trouble installing certain packages, you can edit your repositories to allow more apps.
Type:

sudo nano /etc/apt/sources.list

Notice that some of the lines start with "# deb..."
One of the first lines is the CDROM repository.
Uncomment it by removing the "#" from the begining of "deb" line.
If you scroll down, there are more repositories that can be uncommented (you must have an internet connection to activate these repositories). 
When you are done editing the file press "cntrl+X" then "Y" then "Enter" to save.
Now type:

sudo apt-get update

Now you should be able to get more packages.

WARNING: 
If using ubuntu as a server, there are security risks when using a GUI (e.g. ubuntu-desktop)

---

