---
title: "Ubuntu 11.04 (Could not calculate the upgrade)"
date: 2011-05-30
forum: Installation &amp; Upgrades
---

### Post by davoudi on 2011-05-30
I received the following error today and I did a search on the net. I tried sudo rm /var/cache/apt/archives/* but it didn't help. Any help is very appreciated.


Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the following error message:
'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'

---

### Post by mörgæs on 2011-05-31
If you boot the computer and run the commands 

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

what happens?

---

### Post by Bucky Ball on 2011-05-31
Is there enough room on the partition you are upgrading for the upgrade to have headroom to keep temp files and packages etc. In my experience you need more than just the size of the upgrade.

For instance, I have 8.04 on a nearly full partition (small one, 10Gb). When I try and upgrade it won't and tells me not enough room to upgrade, can't calculate.

---

### Post by mörgæs on 2011-05-31
Yes, that is why 'clean' is a good first step.

---

### Post by Bucky Ball on 2011-05-31
> **mörgæs said:**
> Yes, that is why 'clean' is a good first step.

I tried that. Didn't make any difference or anywhere near enough room. ;)

I am going to do a 'clean' 10.04 LTS install over the existing 8.04 LTS instead.

---

### Post by davoudi on 2011-05-31
> **mörgæs said:**
> If you boot the computer and run the commands 

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```what happens?

 Everything went fine. The problem appears when I use graphical update manager. Basically update manager does not behave as it use to. By the way, I did a clean install of Ubuntu 11.04.

---

### Post by linuxinstalledfromhdd on 2011-05-31
Did you try using Bleachbit before you did it to free up more space?

sudo apt-get install bleachbit
sudo bleachbit

---

### Post by davoudi on 2011-05-31
Here is a screenshot.

---

### Post by davoudi on 2011-06-01
> **linuxinstalledfromhdd said:**
> Did you try using Bleachbit before you did it to free up more space?

sudo apt-get install bleachbit
sudo bleachbit

I just installed a fresh Ubuntu 11.04 two weeks ago. Why should I have problem with space? Anyhow I am trying to clean things right now.

---

### Post by mörgæs on 2011-06-01
> **davoudi said:**
> Everything went fine. The problem appears when I use graphical update manager. Basically update manager does not behave as it use to. By the way, I did a clean install of Ubuntu 11.04.

There have been a number of reports on that. Best is just to forget about Update Manager and use the three commands in stead.

---

### Post by mas2265 on 2012-02-11
My experience:

I think I had the same or similar error message, trying to upgrade to 11.10.  I tried the

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

suggestion.  But, what I think did it (maybe in combination with the above) was:

I had noticed that there was a package, kdevelop, that wasn't upgrading for some reason, even though it appeared to be eligible for an update through the ui.  As I don't actively use kdevelop, I uninstalled it.  The next time I tried to upgrade to 11.10, I got past the problem spot.

---

