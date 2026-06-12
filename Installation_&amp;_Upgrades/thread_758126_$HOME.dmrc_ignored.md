---
title: "$HOME/.dmrc ignored"
date: 2008-04-17
forum: Installation &amp; Upgrades
---

### Post by free10 on 2008-04-17
I have a new system including new drive and loaded it with Ubuntu off CD and then started swapping out some home files and changed permissions on the home files to do so in properties using gksudo. Now I get the popup

"User $HOME/.dmrc file is being ignored. This prevent session and language from being saved. File should be owned by user and have 644 permissions. Users $HOME and not writable by other users."

at boot. Now I am dwight2 and the only user, but I have no idea what it telling me to do. Thanks --Dwight

---

### Post by Pumalite on 2008-04-17
You can safely ignore the message.

---

### Post by MiD-AwE on 2008-04-27
I have the same problem. Can anyone tell me how to fix it? I'm having problems with synaptic and I tried to upgrade but it seems to have failed now I can't run synaptic at all. I don't know if these things are related but I'm trying to eliminate possibilities. Please help.:confused:

---

### Post by savagenator on 2008-04-27
sudo chown jdoe:jdoe /home/jdoe
sudo chown jdoe:jdoe /home/jdoe/.dmrc
sudo chmod 750 /home/jdoe
sudo chmod 644 /home/jdoe/.dmrc

popped from 
[http://ph.ubuntuforums.com/showthread.php?t=435117&page=3](http://ph.ubuntuforums.com/showthread.php?t=435117&page=3)

Do a search :)

---

### Post by MiD-AwE on 2008-04-27
Thanks,

     I found an old post with similar response:

sudo chmod 644 .dmrc
sudo chown username .dmrc
sudo chmod 755 /home/username
sudo chown username /home/username

It works perfectly.:)

 Thanks again, although it seems to not have had any effect on recovering my upgrade and when I try to run synaptic or apt-get, I recieve a message telling me that "Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)". I have no idea where to go from here. Any advice is greatly appreciated.

---

### Post by MiD-AwE on 2008-04-27
Thanks,

     I found an old post with similar response:

sudo chmod 644 .dmrc
sudo chown username .dmrc
sudo chmod 755 /home/username
sudo chown username /home/username

It works perfectly.:)

 Thanks again, although it seems to not have had any effect on recovering my upgrade and when I try to run synaptic or apt-get, I recieve a message telling me that "Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)". I have no idea where to go from here.:confused:

Any advice is greatly appreciated.

---

### Post by danomatika on 2008-04-27
> **MiD-AwE said:**
> when I try to run synaptic or apt-get, I recieve a message telling me that "Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)". I have no idea where to go from here.:confused:

Any advice is greatly appreciated.

try
```
sudo apt-get clean
```
then apt-get/synaptic

---

### Post by MiD-AwE on 2008-04-27
Thank you. Installing upgrade as I type.:popcorn:

---

