---
title: "Weird Karmic apt problem"
date: 2009-09-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kozimodo on 2009-09-03
When I "apt-get upgrade" I always get "and 1 not upgraded" but it does not tell me what is not being upgraded.  Is my apt database corrupted?  How can I fix this?

---

### Post by MacUntu on 2009-09-03
Does update-manager show you a grayed out package?

---

### Post by taavikko on 2009-09-03
```
sudo aptitude update && sudo aptitude full-upgrade
```
Should show needed info.

If it fails, then
```
aptitude search ~U
```

---

### Post by kozimodo on 2009-09-03
@MacUntu: update-manager doesn't show anything.

@taavikko: "aptitude search ~U" doesn't turn up anything.

Some additional information that might be useful is that I dist-upgraded from a Jaunty install.

---

### Post by taavikko on 2009-09-03
> **kozimodo said:**
> @MacUntu: update-manager doesn't show anything.

@taavikko: "aptitude search ~U" doesn't turn up anything.

Some additional information that might be useful is that I dist-upgraded from a Jaunty install.

Paste output of the aptitude update command i gave earlier.

---

### Post by WaterKip on 2009-09-03
Could be the cups package, that package cannot be upgraded for over a week now.

---

### Post by ilna on 2009-09-03
```
sudo aptitude -P -V -v -W safe-upgrade
```
shows me everything I need, and more :-)

---

### Post by kozimodo on 2009-09-03
```
sudo aptitude -P -V -v -W safe-upgrade
[sudo] password for tct: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

Current status: 0 broken [+0], 0 updates [+0], 3303 new [+0].
```
Unfortunately this doesn't show anything more than the unadorned upgrade command...:(

---

### Post by ilna on 2009-09-03
'sudo apt-get check' ?

---

### Post by kozimodo on 2009-09-03
```
sudo apt-get check
[sudo] password for tct: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
```
Not looking good...

---

### Post by VMC on 2009-09-03
> **taavikko said:**
> ```
sudo aptitude update && sudo aptitude full-upgrade
```
Should show needed info.

If it fails, then
```
aptitude search ~U
```

I've notice you use Aptitude over apt-get. I couldn't understand how to navigate though the curses menu(I ended up cursing.) Didn't realize I could just call the needed function instead of going to the menu. As you just gave an example. 

Then again, using aptitude by itself and looking around can give a great deal of information. I'm starting to like it better then apt-get. A lot went into making that program. I know Debian recommends Aptitude over Apt-get.

---

### Post by gwenn on 2009-09-04
I had these kind of things , so i made a fresh install of karmic4.
I upgraded from jaunty and some times I had to tweak a lot. No more problems now.

---

### Post by kozimodo on 2009-09-04
Yea, I posted as a curiosity more than anything else as the system works just fine. I will eventually do a clean install.

---

### Post by taavikko on 2009-09-04
> **VMC said:**
> I've notice you use Aptitude over apt-get. I couldn't understand how to navigate though the curses menu(I ended up cursing.) Didn't realize I could just call the needed function instead of going to the menu. As you just gave an example. 

Then again, using aptitude by itself and looking around can give a great deal of information. I'm starting to like it better then apt-get. A lot went into making that program. I know Debian recommends Aptitude over Apt-get.

I indeed prefer aptitude over apt-get.
"man aptitude" gives great information and links to files with more information.

aptitude makes apt-get/apt-cache obsolete .)
too bad that "aptitude search ~o" doesn't print apt-get as obsolete.

---

