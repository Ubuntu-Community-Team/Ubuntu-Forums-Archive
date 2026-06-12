---
title: "updates way too infrequent?"
date: 2017-01-16
forum: Installation &amp; Upgrades
---

### Post by timonoj on 2017-01-16
Hi guys, 

Whenever I check for updates, I usually get 0 new updates:
```
~$ sudo apt update
Hit:1 http://hk.archive.ubuntu.com/ubuntu yakkety InRelease
Hit:2 http://hk.archive.ubuntu.com/ubuntu yakkety-updates InRelease
Hit:3 http://hk.archive.ubuntu.com/ubuntu yakkety-backports InRelease
Get:4 http://security.ubuntu.com/ubuntu yakkety-security InRelease [102 kB]
Fetched 102 kB in 1s (71.6 kB/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done
All packages are up to date.

```
...It stays like that for weeks. Once in a bluemoon it will detect one or two new packages. What's going on? From my experience ubuntu repositories release package updates almost daily...

---

### Post by howefield on 2017-01-17
Check your /var/log/apt/history log file for unattended upgrades being applied in the background.

Could be of course that there are genuinely no updates for your system ?

---

### Post by RobGoss on 2017-01-17
If he's using 16.04 you should be receiving updates daily. I'm also using Ubuntu 16.04 and I receive updates daily 

Try switching your download source list and see if that makes a difference 

What version of Ubuntu do you have installed?

---

### Post by howefield on 2017-01-17
> **RobGoss said:**
> If he's using 16.04 you should be receiving updates daily. I'm also using Ubuntu 16.04 and I cannot remember one day that when by I didn't have a update

Have a read at the original post.

---

### Post by RobGoss on 2017-01-17
>  
Whenever I check for updates, I usually get 0 new updates: 

I'm assuming this means he's not receiving  updates daily correct?

Maybe I'm missing something here

---

### Post by bearlake on 2017-01-17
Looks like there using 16.10.

Using 16.04 Server and not seeing very many updates.

16.10 with only a 9 month life would likely only see security updates.

Like posted above, check your /var/log/apt/history log file for unattended upgrades.

---

### Post by howefield on 2017-01-17
> **RobGoss said:**
> .....correct?

No, s/he would appear to be using the yakkety release - 16.10

---

### Post by deadflowr on 2017-01-17
Check another location/file
/var/log/unattended-upgrades/unattended-upgrades.log
on top of the suggested history.log

---

### Post by timonoj on 2017-01-17
Yeah I can see in the history.log some upgrades that I ran early last week. However before those ones, last upgrade time was somewhere beginning December. I'm kind of receiving updates ala MS style, every month...Is this normal?

---

### Post by deadflowr on 2017-01-17
A newer kernel was released for all versions on Jan 11. (Security related updates)
16.10 should currently be on 4.8.0-34
run 
```
uname -a
```
to see which kernel is in use now.
is it the same or different.

---

### Post by howefield on 2017-01-18
> **deadflowr said:**
> /var/log/unattended-upgrades/unattended-upgrades.log

Thanks, forgot about that more appropriate one :)

---

