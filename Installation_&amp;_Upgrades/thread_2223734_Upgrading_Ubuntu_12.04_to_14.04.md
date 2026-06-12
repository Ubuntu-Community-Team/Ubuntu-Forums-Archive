---
title: "Upgrading Ubuntu 12.04 to 14.04"
date: 2014-05-12
forum: Installation &amp; Upgrades
---

### Post by harshall2 on 2014-05-12
Hi,

I was in the process of upgrading ubuntu 12.04 to 14.04 & my battery died... :(. I restarted the laptop and I am able to get to the login but then my screen freezes. 

I can move my cursor but I do not have any icons only a purple screen with Ubuntu 14.04 LTS on the bottom left.

I can get access to the shell using Ctrl+all+f1, I have tried couple of things mentioned on Google but no luck, I am hoping someone can help me sort this, don't really want to remove my hardrive backup & do a fresh install unless I am totally screwed.

Any help /suggestions will be appreciated, is there a way to do a system restore like in windows?

Thanks,

Harsh

---

### Post by deadflowr on 2014-05-12
Please give a list of the things you tried, as mentioned, from google.
That way, we don't give advice you know doesn't work.

---

### Post by harshall2 on 2014-05-12
Thanks, for the quick reply.

I tried the following commands:

apt-get -f install
dpkg --configure -a
apt-get update

I have tried all the solutions on the website below, except the sudo mount commands.

[http://www.justanswer.com/software/89keh-upgrade-14-04-system-system-hangs-login.html](http://www.justanswer.com/software/89keh-upgrade-14-04-system-system-hangs-login.html)

I have also tried the following:

sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install unity
sudo reboot

.….....…..............................................................

They are all the commands I tried, sorry for the delay I am currently using a tablet.

Hopefully this information will help & save time.

---

### Post by harshall2 on 2014-05-12
Just a quick update I tried the following commands listed below:

sudo su
apt-get install –reinstall ubuntu-desktop
apt-get install unity
apt-get purge nvidia* bumblebee*
apt-get install nvidia-prime
shutdown -r now

This worked a treat, sorry for wasting your time, hopefully this solution will help someone.

Thanks.

---

### Post by deadflowr on 2014-05-12
> **harshall2 said:**
> Just a quick update I tried the following commands listed below:

sudo su
apt-get install –reinstall ubuntu-desktop
apt-get install unity
apt-get purge nvidia* bumblebee*
apt-get install nvidia-prime
shutdown -r now

This worked a treat, sorry for wasting your time, hopefully this solution will help someone.

Thanks.


No time wasted if the solution you found can also help others along the way.
You can mark this thread as solved, if it is indeed solved, by going to Thread Tools.
Thread Tools is right above the first post on the right side.

---

