---
title: "I couldn't upgrade from 20.04 to 22.04"
date: 2022-08-13
forum: Installation &amp; Upgrades
---

### Post by esso10 on 2022-08-13
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290862&stc=1[/IMG]

---

### Post by SeijiSensei on 2022-08-13
Make sure you've updated all your packages first. 

Open a terminal and type
```

sudo apt update
sudo apt dist-upgrade

```

Now try the migration again.

---

### Post by esso10 on 2022-08-14
[HTML]esso@lava:~$ sudo apt update
[sudo] password for esso: 
Reading package lists... Done
E: Could not get lock /var/lib/apt/lists/lock. It is held by process 2241 (packagekitd)
N: Be aware that removing the lock file is not a solution and may break your system.
E: Unable to lock directory /var/lib/apt/lists/
esso@lava:~$ sudo apt dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
esso@lava:~$ 


[/HTML]


then after that this message for more than one hour!!

---

### Post by SeijiSensei on 2022-08-14
You must close any application that deals with package management first. Otherwise you cannot run the update command from the terminal prompt.

If you've closed everything and still get the error above, you can fix this by brute force with:
```

sudo killall -9 packagekitd

```
Wait a few seconds, then try again.

---

### Post by esso10 on 2022-08-14
I did as you told me and killed all processes,then tried after seconds and started with [HTML]sudo apt update[/HTML]

[HTML] sudo apt update
Hit:1 http://archive.linux.duke.edu/ubuntu focal InRelease
Get:2 http://archive.linux.duke.edu/ubuntu focal-updates InRelease [114 kB]
Get:2 http://archive.linux.duke.edu/ubuntu focal-updates InRelease [114 kB]
Get:2 http://archive.linux.duke.edu/ubuntu focal-updates InRelease [114 kB]
Get:2 http://archive.linux.duke.edu/ubuntu focal-updates InRelease [114 kB]
Get:2 http://archive.linux.duke.edu/ubuntu focal-updates InRelease [114 kB]
Get:2 http://archive.linux.duke.edu/ubuntu focal-updates InRelease [114 kB]
Get:2 http://archive.linux.duke.edu/ubuntu focal-updates InRelease [114 kB]
Get:2 http://archive.linux.duke.edu/ubuntu focal-updates InRelease [114 kB]
Get:2 http://archive.linux.duke.edu/ubuntu focal-updates InRelease [114 kB]
Get:2 http://archive.linux.duke.edu/ubuntu focal-updates InRelease [114 kB]
Get:2 http://archive.linux.duke.edu/ubuntu focal-updates InRelease [114 kB]
Get:2 http://archive.linux.duke.edu/ubuntu focal-updates InRelease [114 kB]
0% [2 InRelease 0 B/114 kB 0%]




[/HTML]


It takes so long time and nothing happens, it seems it's not able to download those 114 KBs !

---

### Post by esso10 on 2022-08-14
It started to work now.

---

### Post by esso10 on 2022-08-14
AGAIN

Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade.

 If none of this applies, then please report this bug using the command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal. If you want to investigate this yourself the log files in '/var/log/dist-upgrade' will contain details about the upgrade. Specifically, look at 'main.log' and 'apt.log'.

---

### Post by esso10 on 2022-08-14
If none of this applies, then please report this bug using the 
command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal. If 
you want to investigate this yourself the log files in 
'/var/log/dist-upgrade' will contain details about the upgrade. 
Specifically, look at 'main.log' and 'apt.log'.

---

### Post by esso10 on 2022-08-14
Solved by[HTML]sudo apt purge -y python3.10

[/HTML] 

however, still stuck on some packages...

---

### Post by esso10 on 2022-08-15
Solved by changing the server to main server.

---

