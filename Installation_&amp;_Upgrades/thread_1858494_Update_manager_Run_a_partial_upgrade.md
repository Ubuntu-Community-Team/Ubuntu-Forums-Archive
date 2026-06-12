---
title: "Update manager: Run a partial upgrade"
date: 2011-10-12
forum: Installation &amp; Upgrades
---

### Post by createdcreature on 2011-10-12
What does the error message 'Run a partial upgrade' in update manager mean? How do I stop the problem? It won't let me install any updates, and occasionally says 'Software index is broken'.

---

### Post by Quackers on 2011-10-12
Running a partial upgrade will often break something.
Instead use Synaptic to update. That will tell you what is going to be removed if you update a given package. If you don't want the item(s) removed then don't run the update for that package.

---

### Post by Old_Grey_Wolf on 2011-10-12
You can fix the problem by running these commands:
```
sudo rm -vf /var/lib/apt/lists/*
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by raja.genupula on 2011-10-13
> **Quackers said:**
> Running a partial upgrade will often break something.
Instead use Synaptic to update. That will tell you what is going to be removed if you update a given package. If you don't want the item(s) removed then don't run the update for that package.

now i am on 11.10 started using it from Alpha version.It has asked me several times for partial upgrade and i have given yes.at that time i have enquired about this and got the answer as this is testing version and everytime we need some new updates with fixes and security updates...is that right for that? 
Thanks in advance,

---

### Post by Quackers on 2011-10-13
It is not normally a good idea to run Partial Upgrades.

[http://ubuntuforums.org/showthread.php?t=1751299](http://ubuntuforums.org/showthread.php?t=1751299)

---

### Post by raja.genupula on 2011-10-13
> **Quackers said:**
> It is not normally a good idea to run Partial Upgrades.

[http://ubuntuforums.org/showthread.php?t=1751299](http://ubuntuforums.org/showthread.php?t=1751299)


Thank you very much.In future i am not gonna touch them.
Thanks again.

---

### Post by notzippy on 2011-10-14
> **Old_Gray_Wolf said:**
> You can fix the problem by running these commands:
```
sudo rm -vf /var/lib/apt/lists/*
sudo apt-get update
sudo apt-get upgrade
```

I tried this and I still get the partial upgrade message, I  noticed that the remove failed to remove the folder  "/var/lib/apt/lists/partial" does it need to remove that folder also ?

thanks
nz

---

### Post by Old_Grey_Wolf on 2011-10-14
Yes, will need to remove "/var/lib/apt/lists/partial" as well.
```
sudo rm -rf /var/lib/apt/lists/partial
```
The previous command should have had -rf instead of -vf :oops:

---

### Post by Gremlyn1 on 2011-10-18
> **Old_Gray_Wolf said:**
> Yes, will need to remove "/var/lib/apt/lists/partial" as well.
```
sudo rm -rf /var/lib/apt/lists/partial
```
The previous command should have had -rf instead of -vf :oops:

So the actual command should be:
```
sudo rm -rf /var/lib/apt/lists/*
```
or
```
sudo rm -rf /var/lib/apt/lists/partial
```

??

I just want to make sure running with the wildcard won't actually remove sources for anything that I don't want to remove from my system or some similar undesired result

*********UPDATE*********
I made a backup of the lists/ dir and tried with the wildcard, and then ran the apt-get update command and received an error message that the partial/ dir was missing.

---

### Post by Old_Grey_Wolf on 2011-10-18
sudo rm -rf /var/lib/apt/lists/*

will get you what you want.

---

