---
title: "ubuntuguide : Protecting SSH from brute force attack"
date: 2007-10-05
forum: Installation &amp; Upgrades
---

### Post by bytemind on 2007-10-05
Hi,

I am trying to use the Protecting SSH from brute force attack guide on ubuntuguide.org ([http://ubuntuguide.org/wiki/Ubuntu:Feisty#Protecting_SSH_from_brute_force_attack](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Protecting_SSH_from_brute_force_attack))

I have added 

deb [http://ubuntu.tolero.org/](http://ubuntu.tolero.org/) feisty main

to my /etc/apt/sources.list

and done

sudo apt-get update

but gets an error on the update:

Err [http://ubuntu.tolero.org](http://ubuntu.tolero.org) feisty/main Packages
404 Not Found

---

### Post by bikeboy on 2007-10-05
It could either be that the tolero repository is down at the moment, or it doesn't exist anymore.

There's some great advice in the ubuntu wiki about ssh servers.
[SSH Howto](https://help.ubuntu.com/community/SSHHowto)
[Advanced OpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

---

### Post by bytemind on 2007-10-05
Thank you for the reply, but its not excatly what i am looking for - This advanced secutiry is about using keys, and i cant use that for this project.

---

### Post by hanserikbusk on 2007-10-05
You could use Fail2ban to lockout a specific IP address efter a certain number of logon attempts. Very easy to set up an configure.

---

