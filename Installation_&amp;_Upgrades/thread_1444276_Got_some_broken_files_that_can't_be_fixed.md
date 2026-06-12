---
title: "Got some broken files that can't be fixed"
date: 2010-04-01
forum: Installation &amp; Upgrades
---

### Post by Parran on 2010-04-01
Hey you guys. first of i'm a total noob at Linux / Ubuntu but i still want to learn more about it and stop being a windfag :p.

Anyhow. i first of installed Ubuntu 9.10 and then updated to Ubuntu 10.(04?). and everything was running smooth and good. but when i started my com the next day i got some broken files that was broken. 

I thought "Okey.. I'll just go to the "Broken Fixer" and get it over with" and i went in to the broken fixer and like marked all and everything stared to update. i went of and got me some coffee and got back to my comp and got this error.

```
E: /var/cache/apt/archives/ia32-libs_2.7ubuntu21_amd64.deb: subprocess dpkg-deb --control returned error exit status 2
```If anyone could tell me what to do and how i can fix it i would mean alot to me.

and yea.. i'm still a winfag but i want to start being a "kewlFag"

EDiT: sorry if im not posting in the right forum btw. just want my question answered fast..

Sorry :(

---

### Post by Fafler on 2010-04-01
I'm not really sure what you are trying to say, but try opening a terminal and type
```
sudo apt-get update && sudo apt-get --fix-missing update
```
If it doesn't fix it, post the output here and try to explain you problem a bit better.

---

### Post by Parran on 2010-04-01
> **Fafler said:**
> I'm not really sure what you are trying to say, but try opening a terminal and type
```
sudo apt-get update && sudo apt-get --fix-missing update
```If it doesn't fix it, post the output here and try to explain you problem a bit better.

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```
sorry for being so bad at explaining. had to go to another class

---

### Post by Fafler on 2010-04-01
Reboot, try again.

---

### Post by Parran on 2010-04-01
Thanks. I found out what is was. 

I had to re-install the amd_64 thing and reboot and things work'd great. 

Now my problem is.. the damn flashplayer that i can't install coz, when i have installed it from ```
sudo apt-get install flashplugin-nonfree
``` and restart the comp i open up Mozilla and testing it (I just tested it on youtube.com) and it worked... Not so great. as i thought what the problem was i went in to the config (About:plugins) and it wasn't listened. 

anyway thanks for the help. and im sure of that you will see more of me in the future :D

---

