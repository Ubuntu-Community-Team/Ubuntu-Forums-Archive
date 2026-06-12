---
title: "Administrator login?"
date: 2005-09-17
forum: Installation &amp; Upgrades
---

### Post by dustyjay on 2005-09-17
I am not very versedin linux.  I just installed Ubuntu 5.04.  I am trying to learn my way around.  I was able to get my email set up and can surf the web.  I am noticing that a lot of things that I do dont work.  Like trying to open update manager.  It fails no motter what I do.  It asks me for my password which I type.  then when I go to launch it it fails.  every thing tells me that I do not own or do not have permission to do something.  

Question is how do I get this done.  Or did I make some errors while installing it.  Also how does one log in as administrator? ](*,)

---

### Post by John.Michael.Kane on 2005-09-17
[QUOTE=dustyjay]I am not very versedin linux.  I just installed Ubuntu 5.04.  I am trying to learn my way around.  I was able to get my email set up and can surf the web.  I am noticing that a lot of things that I do dont work.  Like trying to open update manager.  It fails no motter what I do.  It asks me for my password which I type.  then when I go to launch it it fails.  every thing tells me that I do not own or do not have permission to do something.  

Question is how do I get this done.  Or did I make some errors while installing it.  Also how does one log in as administrator? ](*,)[/QUOTE]
 Use of sudo= root=Administrator..

When you use update manager or synaptic make sure you have the repo's set 

1) open synaptic or update manager click on settings click repositories. remove the cd repo if it's listed. click settings at the bottom. click show disabled software resources.
update manager click prefances.. that will allow you to checkyour repo's.. 

if you want to add repos.. 
Type this in termanial sudo gedit /etc/apt/sources.list
add these lines 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

Hope this helps, and welcome to gnu/linux/Ubuntu..

you can also try here [http://ubuntuguide.org/](http://ubuntuguide.org/), and some of the sites in my sig..

---

### Post by ree on 2005-09-17
[QUOTE=dustyjay]I am not very versedin linux.  I just installed Ubuntu 5.04.  I am trying to learn my way around.  I was able to get my email set up and can surf the web.  I am noticing that a lot of things that I do dont work.  Like trying to open update manager.  It fails no motter what I do.  It asks me for my password which I type.  then when I go to launch it it fails.  every thing tells me that I do not own or do not have permission to do something.  

Question is how do I get this done.  Or did I make some errors while installing it.  Also how does one log in as administrator? ](*,)[/QUOTE]
 I had a similar issue because I wasn't in the sudoers (admins) group and therefore couldn't change practically anything on my computer at all.  The thread that contained the solution is located [here](http://ubuntuforums.org/showthread.php?t=58919)

---

