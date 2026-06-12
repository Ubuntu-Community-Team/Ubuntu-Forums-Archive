---
title: "Cannot use package managers"
date: 2012-01-20
forum: Installation &amp; Upgrades
---

### Post by Mr.Kuchinawa on 2012-01-20
Hi, recently I've had a problem: every time I try to e.g. run a software update, it says that another package manager is active. This happens every time, even if it is the first thing I do when I log on. So, what can I do about this? Hope I posted this in the right place.
Thanks in advance.

---

### Post by dino99 on 2012-01-20
try:

sudo dpkg-reconfigure -phigh -a

(can take a while, take a beer, and wait it end itself, dont stop it)

---

### Post by Mr.Kuchinawa on 2012-01-20
> **dino99 said:**
> try:

sudo dpkg-reconfigure -phigh -a

(can take a while, take a beer, and wait it end itself, dont stop it)

Thanks, but unfortunately it didn't solve the problem

---

### Post by Old_Grey_Wolf on 2012-01-20
There is a file called "lock" that can prevent the update manager from working. Try removing the lock file using this command ```
sudo rm /var/lib/apt/lists/lock
```

Then try to update.

---

### Post by Mr.Kuchinawa on 2012-01-20
> **Old_Gray_Wolf said:**
> There is a file called "lock" that can prevent the update manager from working. Try removing the lock file using this command ```
sudo rm /var/lib/apt/lists/lock
```

It says there's no such file or directory. It might be worth mentioning that the update manager itself works, it just won't update. Muon craches on startup.

---

### Post by Old_Grey_Wolf on 2012-01-20
I just noticed that your profile shows you are using Ubuntu 9.04. If that is true, that version is no longer supported and you can't get updates for it.

---

### Post by Mr.Kuchinawa on 2012-01-20
> **Old_Gray_Wolf said:**
> I just noticed that your profile shows you are using Ubuntu 9.04. If that is true, that version is no longer supported and you can't get updates for it.

I'm using the latest one, 11.10. Updated it now..

---

### Post by Old_Grey_Wolf on 2012-01-20
Now that you profile is updated...

I don't use the Muon graphical package manager for KDE; therefore, I will differ to someone else with KDE Muon experience.

---

### Post by cortman on 2012-01-20
Simple solution.
If you're sure you don't have another GUI package manager open (Synaptic, Ubuntu Software Center, Update Manager) you can open a terminal and run

```
ps -ef | grep apt
```

which will list all processes that are locking up Aptitude. You can kill these processes with the command

```
sudo kill-9 process_id
```

Substituting the process ID number (PID, which will be the four digit number in the column second from the left) for process_id.

For example, if I run ps-ef | grep apt on my VBox here, while running apt-get update, I get

```

root      1786  1654  2 16:07 pts/0    00:00:00 sudo apt-get update
root      1787  1786  4 16:07 pts/0    00:00:00 apt-get update
root      1791  1787  1 16:07 pts/0    00:00:00 /usr/lib/apt/methods/http
root      1792  1787  1 16:07 pts/0    00:00:00 /usr/lib/apt/methods/http
root      1793  1787  1 16:07 pts/0    00:00:00 /usr/lib/apt/methods/http
root      1794  1787  1 16:07 pts/0    00:00:00 /usr/lib/apt/methods/http
root      1795  1787  1 16:07 pts/0    00:00:00 /usr/lib/apt/methods/http
root      1797  1787  3 16:07 pts/0    00:00:00 /usr/lib/apt/methods/gpgv
root      1803  1787  0 16:08 pts/0    00:00:00 /usr/lib/apt/methods/bzip2
cortman   1809  1704  0 16:08 pts/1    00:00:00 grep --color=auto apt

```

To end these processes, I use the command

```
sudo kill -9 1786 1787 1791 1792 1793 1794 1795 1797 1803
```

The last process is your ps -ef |grep command. Don't kill it.

---

### Post by Mr.Kuchinawa on 2012-01-20
> **cortman said:**
> Simple solution.
If you're sure you don't have another GUI package manager open (Synaptic, Ubuntu Software Center, Update Manager) you can open a terminal and run

```
ps -ef | grep apt
```

which will list all processes that are locking up Aptitude. You can kill these processes with the command

```
sudo kill-9 process_id
```

Substituting the process ID number (PID, which will be the four digit number in the column second from the left) for process_id.

For example, if I run ps-ef | grep apt on my VBox here, while running apt-get update, I get

```

root      1786  1654  2 16:07 pts/0    00:00:00 sudo apt-get update
root      1787  1786  4 16:07 pts/0    00:00:00 apt-get update
root      1791  1787  1 16:07 pts/0    00:00:00 /usr/lib/apt/methods/http
root      1792  1787  1 16:07 pts/0    00:00:00 /usr/lib/apt/methods/http
root      1793  1787  1 16:07 pts/0    00:00:00 /usr/lib/apt/methods/http
root      1794  1787  1 16:07 pts/0    00:00:00 /usr/lib/apt/methods/http
root      1795  1787  1 16:07 pts/0    00:00:00 /usr/lib/apt/methods/http
root      1797  1787  3 16:07 pts/0    00:00:00 /usr/lib/apt/methods/gpgv
root      1803  1787  0 16:08 pts/0    00:00:00 /usr/lib/apt/methods/bzip2
cortman   1809  1704  0 16:08 pts/1    00:00:00 grep --color=auto apt

```

To end these processes, I use the command

```
sudo kill -9 1786 1787 1791 1792 1793 1794 1795 1797 1803
```

The last process is your ps -ef |grep command. Don't kill it.

I only get one...: 
```

simen    28046 27968  0 02:12 pts/1    00:00:00 grep --color=auto apt

```

---

### Post by Mr.Kuchinawa on 2012-01-20
Never mind, I'm just gonna do a fresh new installation. I appreciate the help, though.

---

### Post by cortman on 2012-01-20
Wow. If that was the only process, I'd say something was pretty wrong. Good luck with the reinstallation!

---

