---
title: "apt-get error"
date: 2011-12-19
forum: Installation &amp; Upgrades
---

### Post by tbrminsanity on 2011-12-19
I'm getting the following error:

N: Ignoring file '50unattended-upgrades.distrib' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension

when I run the following command:

sudo apt-get -y update && sudo apt-get -y upgrade

It doesn't seem to be affecting my machine directly, but I would like to clear up the issue before it has a chance to develop into something worse.

---

### Post by Paddy Landau on 2011-12-19
I would recommend against using the option -y in your commands. Sometimes apt-get needs to ask questions.

Please run the following command by itself.```
sudo apt-get update
```If you get any errors, please paste the results here (between [noparse]```
[/noparse] and [noparse]
```[/noparse]).

If you do not get errors, do the same thing with the following command.```
sudo apt-get upgrade
```

---

### Post by tbrminsanity on 2011-12-19
```

... (All my repos listed above)
Fetched 7,257 B in 8s (848 B/s)                                                
Reading package lists... Done
N: Ignoring file '50unattended-upgrades.distrib' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension

```

---

### Post by Paddy Landau on 2011-12-19
That seems to be a first.

Please would you post the results of this command.
```
ls -l /etc/apt/apt.conf.d/
```

---

### Post by tbrminsanity on 2011-12-19
```

-rw-r--r-- 1 root root   40 2011-06-19 15:03 00trustcdrom
-rw-r--r-- 1 root root  430 2011-04-07 05:13 01autoremove
-rw-r--r-- 1 root root  153 2011-06-19 17:59 01<edited out>
-rw-r--r-- 1 root root   63 2011-09-21 07:23 01<edited out>
-rw-r--r-- 1 root root  127 2011-06-19 17:59 02<edited out>
-rw-r--r-- 1 root root  129 2008-11-11 05:19 10periodic
-rw-r--r-- 1 root root  108 2008-11-11 05:19 15update-stamp
-rw-r--r-- 1 root root   85 2008-11-11 05:19 20archive
-rw-r--r-- 1 root root  230 2011-11-01 13:02 20auto-upgrades
-rw-r--r-- 1 root root  123 2011-10-06 09:30 20changelog
-rw-r--r-- 1 root root  243 2009-12-16 02:02 20dbus
-rw-r--r-- 1 root root 1049 2011-04-04 01:42 20packagekit
-rw-r--r-- 1 root root 1166 2011-11-01 13:02 50unattended-upgrades
-rw-r--r-- 1 root root 1921 2011-04-12 03:22 50unattended-upgrades.distrib
-rw-r--r-- 1 root root  182 2011-02-20 04:25 70debconf
-rw-r--r-- 1 root root   32 2011-10-04 15:44 99synaptic
-rw-r--r-- 1 root root  231 2010-06-01 07:19 99update-notifier

```

---

### Post by dino99 on 2011-12-19
you seems to use some old config/settings mixed with recent ones :( (you should run gconf-cleaner & bleachbit to make some cleaning)

xxxxx.distrib should be removed (not a standard setting anyway) .

sudo rm /etc/apt/apt.conf.d/50unattended-upgrades.distrib

---

### Post by Paddy Landau on 2011-12-19
I agree with dino99 to remove the file 50unattended-upgrades.distrib using the command he gave you. Be careful to type it exactly as dino99 wrote (or copy-and-paste).

Once that is done, try again to update, either using Update Manager (if you prefer the GUI) or the following command (note the absence of the -y option).```
sudo apt-get update && sudo apt-get upgrade
```I'm not so sure about Bleachbit, as I have read some problems from using it. I do not know gconf-cleaner, so I cannot comment on it.

---

### Post by tbrminsanity on 2011-12-20
Thank you everyone, I backed up the offending folder and reran my update and upgrade.  It was clean this time.

---

