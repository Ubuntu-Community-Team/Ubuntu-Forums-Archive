---
title: "Gutsy Installation Hung At Configuring xvnc4viewer stage"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by harshad on 2007-10-20
Hi,

My upgrade to Gutsy from Feisty AMD64 was progressing well. After many hours of downloads and installation work however the process has hung up, the message showing for over an hour is

Configuring xvnc4viewer 
About 27 minutes remaining

I  don't wish to restart as I don't want to risk a partial and unstable upgrade

Any suggestions?

Attached is a screen capture of the hung up installation screen.

Thanks,
harshad

---

### Post by harshad on 2007-10-20
I did restart as I did not see any other solution.
Ubuntu did restart but it only got to a blank yellow screen with a mouse pointer over it. 

Can't do anything here. 

Please help.

thanks,
harshad

---

### Post by harshad on 2007-10-20
With reference to this post
[http://ohioloco.ubuntuforums.org/showthread.php?t=418138](http://ohioloco.ubuntuforums.org/showthread.php?t=418138)

I tried using
1. Exit my session with ctrl-alt-backspace
2. Go to command line with ctrl-alt-f1 

Created a new user but that didn't do the trick.

However using ctrl-alt-f1 can now get to the command line. Did not know about this earlier.

Here tried running sudo apt-get dist-upgrade but got a message saying that I first need to run dpkg --configure -a

So tried
sudo dpkg --configure -a

Things are moving again. Lots appearing in the command prompt and it looks like the incomplete part of the installation is being completed.

I hope this will fix my problems. Have my fingers crossed.

---

### Post by harshad on 2007-10-20
Eureka...looks like the installation has now been completed. Restarted and got good old ubuntu in a new look. 

gutsy doesn't seem to have broken anything. 

although it does seem very slow to start up.

---

