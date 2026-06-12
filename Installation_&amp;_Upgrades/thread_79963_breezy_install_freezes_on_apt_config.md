---
title: "breezy install freezes on apt config"
date: 2005-10-21
forum: Installation &amp; Upgrades
---

### Post by flower on 2005-10-21
breezy install freezes on the screen saying : 
=================================
Configuring apt-get 

25% progress

Setting primary repository
=================================

I tried several times, trying different stuff ... but nothing ... 
I used hoary for so long ... I didn't expect I will have trouble with breezy .. :confused:

---

### Post by suchyxxx on 2005-10-21
Have this same problem.How to solve it? Pls help apt configuration primary repository freezes in 25% and ...nothing.

---

### Post by suchyxxx on 2005-10-21
I installed ubuntu 5.10 5 times and always this same.It's no matter what type of partition i make (ext3,reiserfs) always this same.I tried expert mode but it is still this same.

---

### Post by flower on 2005-10-23
yes I also tried several times , even tought it might be from my network card, so I took it out of the pc case, but still no luck ... :( 

anyone .. idea ?

---

### Post by drew_t on 2005-10-23
[http://ubuntuforums.org/showthread.php?t=76631](http://ubuntuforums.org/showthread.php?t=76631)

---

### Post by flower on 2005-10-24
gosh ... in the cited thread there was the answer : 

when install is stuck on apt conf, I killed the 2 last created processes and it continued (almost happily)

then ... after rebooting ... the configuration of the installation got stuck again !!!
I again killed the stucked processes and now I'm posting from my new ubuntu :)

anyway ... I love ubuntu ... but ... breezy install sucks :(
========================================================
right ... after I run around repositories are missing (since I killed the apt conf) ...

can somebody post here his breezy sources.list  ?
I would appreaciate very much ...

---

### Post by flower on 2005-10-25
I continue to post things I discover on my new breezy install - maybe I will be hopeful to somebody :) 

Killing the stuck processes during the installation and configuration is great idea,
and it worked fine.

BUT : it seems that the stucked process during install was generating error log. I discovered 8Gigabytes file in /var/log/ folder. So if somebody uses this solution better check out this folder ;)

---

### Post by towsonu2003 on 2005-10-26
I'm not sure whether this is gonna be helpful for you but, tell ubuntu not to configure the network when it asks permission to do that during install.

---

### Post by webnar on 2005-11-02
Doesn someone kow what to do when breezy freezes at the end of stage 1 when he's making the log. it always get stuck at 83%?

greatings
webnar

---

### Post by flower on 2005-11-02
well when I switched to the output console it was installing some package and was asking for input (Yes/No) but it seems the install was giving some wrong input and it was stuck like : 

Enter choice (Yes/No) ... wrong input enter yes or no
Enter choice (Yes/No) ... wrong input enter yes or no
Enter choice (Yes/No) ... wrong input enter yes or no
Enter choice (Yes/No) ... wrong input enter yes or no ...

---

### Post by BrokenBrick on 2005-12-05
What always has worked for me is to exit out once the install gets to setting up users.  Either ESC or hit the "Go Back" button.  Once you do it will return you to the menu of install steps.  Skip the user config and apt config steps, and jump straihg to installing grub/lilo.  The install will then write your boot loader's code and reboot.  Once it does the user config step will come back up (don't boot off the CD) and then it should move along to configuring apt with no problems :)

---

### Post by Darius-Sylar on 2007-10-01
Hi! I had the same problem during "configuring apt" because it got freeze. I did this:
Go to other console, (ALT + CTRL + F2) for example and write
# ps -ef

Find the process with:
#wget [http://ubuntu.org/dist](http://ubuntu.org/dist)... etc

And then kill this process.
#kill -9 18964 (for example)

Go back to the installation screen  (ALT + CTRL + F1) and you will see that the installation continues.
This action worked pretty well, so I hope it works with you.

Good luck!

PD: Thanks Chuche!!

---

