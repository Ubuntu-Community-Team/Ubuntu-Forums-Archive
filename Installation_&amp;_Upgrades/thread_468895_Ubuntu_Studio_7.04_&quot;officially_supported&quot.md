---
title: "Ubuntu Studio 7.04 &quot;officially supported&quot; install method for Cinelerra-CV"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by MetalMusicAddict on 2007-06-09
This repo is run buy a dev that has been working with us to try to free up the license issues surrounding Cinelerra-CV. This is the only install method Ubuntu Studio officially supports. It is a non-free [SIZE="2"][COLOR="DimGray"](Multiverse-like)[/COLOR][/SIZE] package for use with *buntu 7.04. More info [HERE]("http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu").

From a terminal run this command:
```
sudo su -c 'echo deb http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/ ./ >> /etc/apt/sources.list' && sudo apt-get update
```

Then:
```
sudo apt-get install cinelerra
```

"Cinelerra" will appear in your "Sound & Video" menu.

[LIST]
[*]**[COLOR="Red"]DO NOT[/COLOR]** report bugs on Launchpad about this package as it is not managed there nor officially part of Ubuntu.

[*]This thread is only for install support questions.

[*]A key for the repo will soon be added.
[/LIST]

---

### Post by Dread Knight on 2007-06-13
I tried and i tried and i couldn't get this work.
I'm damn frustrated.

---

### Post by polaren on 2007-06-16
The installing went fine, but it won't start. Nothing happens wen i try to run it.

---

### Post by kelvin spratt on 2007-06-16
that link is no good the package does not work properly i spent a lot of time getting Cinelerra to work in feisty this is how i got Cinelerra to work on fiesty
[http://ubuntuforums.org/showthread.php?t=464223](http://ubuntuforums.org/showthread.php?t=464223) this one after a clean install of fiesty
[http://ubuntuforums.org/showthread.php?t=463275](http://ubuntuforums.org/showthread.php?t=463275)  This one after i had tried unsuccessfully to install Cinelerra
both these work for me and these notes are how i install Cinelerra and it works perfect on my machine with no root messages and no file errors loading mov files

---

### Post by sirab on 2007-06-20
It worked perfectly for me.

Thanks!

---

### Post by danrael on 2008-07-21
Once you install Cinelerra: 

If Cinelerra shows a warning asking you to run 

 sudo echo "0x7fffffff" > /proc/sys/kernel/shmmax

after which you get a 'permission-denied' error, you can issue this command

 sudo su 

and then

 echo "0x7fffffff" > /proc/sys/kernel/shmmax

 After this, Cinelerra should stop giving a warning message at startup.

Just remember you are now in 'root', so log out before going back online.

---

