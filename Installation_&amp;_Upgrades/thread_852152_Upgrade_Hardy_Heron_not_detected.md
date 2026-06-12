---
title: "Upgrade Hardy Heron not detected"
date: 2008-07-07
forum: Installation &amp; Upgrades
---

### Post by Frog in the fog on 2008-07-07
I am currently using the Gutsy Gibbon distribution on my laptop, and I would like to upgrade to Hardy Heron. I have tried to do it through the update manager, but I am told that my system is "up to date".

I have also tried by entering sudo apt-get update / sudo apt-get upgrade in a terminal but again, nothing is detected.

I connect to the internet through my university's wireless network. I can install softwares with synaptic, so it does not seem to be a connection problem. 

Thanks in advance

---

### Post by rogier.de.groot on 2008-07-07
You have to do something special for a distribution upgrade; consult the docs - I think you have to replace your repos in /etc/apt/sources.list and then do "update-manager -d" or something, it'll be in the help pages somewhere.

---

### Post by avtolle on 2008-07-07
Have you seen [http://www.ubuntu.com/getubuntu/upgrading#head-a0ae29eade9bae9df2a7e2eb9f3594b4e7b6f50d](http://www.ubuntu.com/getubuntu/upgrading#head-a0ae29eade9bae9df2a7e2eb9f3594b4e7b6f50d) and followed the directions?

---

### Post by flostre on 2008-09-03
I have the same problem.

> **avtolle said:**
> Have you seen [http://www.ubuntu.com/getubuntu/upgrading#head-a0ae29eade9bae9df2a7e2eb9f3594b4e7b6f50d](http://www.ubuntu.com/getubuntu/upgrading#head-a0ae29eade9bae9df2a7e2eb9f3594b4e7b6f50d) and followed the directions?

I read them. The problem is that the upgrade to the new distribution is not offered. I tried starting upgrade-manager -d and even upgrade-manager --dist-upgrade, but it didn't work. I'm still on Gutsy.

IIRC the button was there earlier, but I decided to wait a while to do the upgrade.

flostre

---

### Post by Kevbert on 2008-09-03
You can perform this via terminal with
```

sudo apt-get update
sudo apt-get upgrade 
sudo apt-get dist-upgrade
```
Please make sure you've backed everything up first as not all upgrades (Gutsy to Hardy) work.

---

### Post by flostre on 2008-09-03
> **Kevbert said:**
> You can perform this via terminal with

Don't you think it is a bug that I have to?

Edit: I had the same problem when updating to Feisty: [http://ubuntuforums.org/showthread.php?t=505713](http://ubuntuforums.org/showthread.php?t=505713)

---

### Post by Amarsingh0793 on 2008-09-03
Maybe Update Manager has not been set to tell you to install a Distro Upgrade. Check in Software Sources (System > Administration > Software Sources) and check your Update and Upgrade Settings.

---

### Post by Kevbert on 2008-09-03
What you should get is the attached screen/window.  If you don't get this you have a bug.

---

### Post by flostre on 2008-09-03
Okay, then I have a bug.

---

### Post by Andre-D on 2008-10-31
same here, and the termanial-commands does not find any updates - nor does the GUI

---

### Post by GooglieS on 2008-10-31
I have the same problem on my 2nd computer! Trying to do something with that.

---

### Post by GooglieS on 2008-10-31
sudo do-release-upgrade
Checking for a new ubuntu release
No new release found

:(

---

### Post by Amarsingh0793 on 2008-10-31
Run this following command (press Alt + F2):

```
update-manager -d
```

This will allow you to install the latest version.

Hope this Helps :)

---

