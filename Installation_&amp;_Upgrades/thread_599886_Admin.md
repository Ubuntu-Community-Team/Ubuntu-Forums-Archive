---
title: "Admin"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by Bobscrachy on 2007-11-01
How do I login as administrator. I installed xubuntu and i entered the terminal to install java for firefox. I have the package downloaded into the desktop, but the java instructions say login as "su." When i tried to do that in terminal it said i entered the wrong password. Do any of you have any suggestions?

---

### Post by Pumalite on 2007-11-01
sudo

---

### Post by taurus on 2007-11-01
Both Sun's java 6 and firefox 2.0.0.8 (Gutsy) are available in the repos so why not do it the easy way.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Bobscrachy on 2007-11-01
What is repos? I looked in add/remove and couldn't find it. Thats when I went to the java website and looked it their instructions.

---

### Post by taurus on 2007-11-01
Can you post your /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by Bobscrachy on 2007-11-01
Heres what it displayed when i typed in your command.

> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
bobscrachy@bobscrachy-laptop:~$ 


---

### Post by Bobscrachy on 2007-11-03
Please advise me a, complete linux newbie, on how to install java.

---

### Post by aysiu on 2007-11-03
**Method 1**
Go to Programs > Add/Remove

Show All Applications (top-right corner)

Then search for *Java*

**Method 2**
Paste this command into the terminal: ```
sudo apt-get update && sudo apt-get install sun-java6-plugin
```

Or, better yet, since you probably want more than just Java (Flash, MP3 playback, etc.)... ```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Bobscrachy on 2007-11-03
When i used the program manager it said 

> Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first.


When i used the terminal it gave me this error.

> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Pumalite on 2007-11-03
Close Synaptic while you use apt-get

---

### Post by Bobscrachy on 2007-11-03
[[IMG]http://img504.imageshack.us/img504/8121/24540488gs6.th.jpg[/IMG]](http://img504.imageshack.us/my.php?image=24540488gs6.jpg)
[[IMG]http://img504.imageshack.us/img504/7534/86132335xm9.th.jpg[/IMG]](http://img504.imageshack.us/my.php?image=86132335xm9.jpg)

I don't see Synaptic listed in the process manager. Synaptic does startup automatically when i turn on the laptop. I just close out of them. I didn't intentionally change any setting to make it do that. Gaim does the same thing. I don't know why they autostart.

---

### Post by Bobscrachy on 2007-11-03
I opened up synaptic and it told me i have a broken package. I searched for it and found it was java, but when i tried to uninstall it it said "E: sun-java5-bin: Package is in a very bad inconsistent state - you should." Ironically thats all it tells me. How do i remove this broken package?

---

### Post by Pumalite on 2007-11-03
sudo dpkg --remove --force-remove-reinstreq <packagename>

---

### Post by Bobscrachy on 2007-11-03
I reinstalled it through synaptic and it finished the install. The add and remove wizard works now and it looks like so does my java. Thank you so much for your help guys.

---

