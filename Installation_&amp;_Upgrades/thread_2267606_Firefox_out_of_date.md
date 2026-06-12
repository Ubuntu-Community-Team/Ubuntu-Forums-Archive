---
title: "Firefox out of date?"
date: 2015-03-02
forum: Installation &amp; Upgrades
---

### Post by renee4 on 2015-03-02
I have upgraded to 14.04. Lately when I go to Gmail I get notification -
 This version of Firefox is no longer supported. Please upgrade to asupported browser

In terminal pasteds udo apt-get update, sudo apt-get upgrade, sudo apt-get update
and supo apt-get dist-upgrade

Still getting the message in Gmail. What else do I do?

---

### Post by sammiev on 2015-03-02
What version of FF do you have? It should FF36 as I have that in my 14.04 OS.

---

### Post by pfeiffep on 2015-03-02
I just tested this for myself using web access to gmail and I got no such warning. (I normally use Thunderbird)

My FireFox version is 36.0
Ubuntu 14.04.2 - you may verify yours by executing in a terminal.
```
lsb_release -a
```
results should be similar to ...> No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trustyAfter your upgrade did you perform an immediate "Software Updater" or execute these commands in a terminal?
```
sudo apt-get update
sudo apt-get upgrade
```

---

