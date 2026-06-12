---
title: "Ubuntu Software Center doesn't work"
date: 2012-09-30
forum: Installation &amp; Upgrades
---

### Post by david10p on 2012-09-30
Last time I tried downloading and installing updates to Ubuntu on my computer, the update failed randomly. I restarted the computer and tried running the updates again, and same error happened. I didn't have enough time to deal with it at the moment so I ignored it. Two days later I tried opening the Ubuntu Software Center and it starts loading and then it crashes on me, every time, before it even starts up. I tried reinstalling Software Center and this is what I get:

david10p@ubuntu:~$ sudo apt-get install --reinstall software-center
[sudo] password for david10p: 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
david10p@ubuntu:~$ 

..


Also, I can't update anything on the machine anymore. And this is the error I get:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'


Can any one please help me solve these two problems? Thanks.

---

### Post by deadflowr on 2012-09-30
I don't know if this would be helpful, but see if it helps:

[http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/]("http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/") 


Also, what happens when you try running the update through the terminal.
```
sudo apt-get update

  sudo apt-get upgrade
```

---

### Post by Old_Grey_Wolf on 2012-09-30
Thy this command```
sudo rm /var/lib/apt/lists/* -vf
```Then ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by david10p on 2012-09-30
Thanks for input guys.

I'm running the update && upgrade now and it seems to be working. It didn't work the first time, it gave me an error reading the package lists and then it stopped. Now I tried the sudo rm first and it seems to be working so far.

I will post an update soon.

---

### Post by david10p on 2012-09-30
SUCCESS! I got it to work with the help of a friend here. Thank you so much guys!

---

### Post by joshofalltrades on 2012-10-03
i'm having the exact same problem, just posted a new thread about it.  did your success come from the code posted above or from something else a friend of yours helped you with elsewhere?

---

### Post by david10p on 2012-10-03
> **joshofalltrades said:**
> i'm having the exact same problem, just posted a new thread about it.  did your success come from the code posted above or from something else a friend of yours helped you with elsewhere?
My success came entirely from the code posted above. More specifically, from these lines of code:

sudo rm /var/lib/apt/lists/* -vf

sudo apt-get update
sudo apt-get upgrade

Good luck!

---

