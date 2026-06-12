---
title: "message on ubuntu 20.10 upgrade"
date: 2020-10-22
forum: Installation &amp; Upgrades
---

### Post by s9032g@comcast.net on 2020-10-22
Did upgrade from 20.04 to 20.10 and all seems well except this message:

All packages are up to date.
E: Could not open lock file /var/lib/dpkg/lock-frontend - open (13: Permission denied)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), are you root?

Anything that I need to do?

---

### Post by SeijiSensei on 2020-10-22
No, it's fine.  Try running "sudo apt update".  Did you get an error?

---

### Post by ActionParsnip on 2020-10-22
Key bit to read here is "are you root?" :cool:

---

### Post by s9032g@comcast.net on 2020-10-22
So far as I know I am root. That is why I am asking.

---

### Post by s9032g@comcast.net on 2020-10-22
Seiji

No error, looks fine

---

### Post by Impavidus on 2020-10-22
Without seeing the exact command you used, combined with the full output, there isn't much we can say.

Did you use a root shell or was the shell running under your normal user ID?

---

### Post by SeijiSensei on 2020-10-22
He was just subject to the locking issue that comes up with apt sometimes.

---

### Post by s9032g@comcast.net on 2020-10-23
command used was "sudo apt update && apt upgrade". The result posted in my thread starter were the last lines of the result.

This command was suggested in Foss instructions for upgrading to 20.10 from 20.04. This was the last step.

---

### Post by s9032g@comcast.net on 2020-10-23
I think that someone might ask me to see the entire result so here it is:

steven@steven-Latitude-E7240:~$ sudo apt update && apt upgrade
[sudo] password for steven:
Hit:1 [http://la-mirrors.evowise.com/ubuntu](http://la-mirrors.evowise.com/ubuntu) groovy InRelease
Hit:2 [http://la-mirrors.evowise.com/ubuntu](http://la-mirrors.evowise.com/ubuntu) groovy-updates InRelease
Hit:3 [http://la-mirrors.evowise.com/ubuntu](http://la-mirrors.evowise.com/ubuntu) groovy-security InRelease
Hit:4 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) groovy InRelease      
Reading package lists... Done
Building dependency tree      
Reading state information... Done
All packages are up to date.
E: Could not open lock file /var/lib/dpkg/lock-frontend - open (13: Permission denied)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), are you root?
steven@steven-Latitude-E7240:~$

---

### Post by ajgreeny on 2020-10-23
SeijiSensei was right when he said "He was just subject to the locking issue that comes up with apt sometimes."

If you've ever tried using synaptic, which I used to use but seldom do nowadays, that quite often seems to throw that error message when you click the Apply button; repeating the action seems to work the second time in my experience so try repeating the same command immediately and it may well work fine.

---

### Post by Impavidus on 2020-10-23
> **s9032g@comcast.net said:**
> command used was "sudo apt update && apt upgrade". The result posted in my thread starter were the last lines of the result.

This command was suggested in Foss instructions for upgrading to 20.10 from 20.04. This was the last step.

That will run "apt update" with sudo, but will run "apt upgrade" without.

---

### Post by garvinrick4 on 2020-10-23
Reboot should solve and easier code other than && is.
> sudo apt update; sudo apt upgrade

If you using terminal at time of reboot -r is reboot and -h shutdown
> sudo shutdown -r now
> sudo shutdown -h now

---

### Post by s9032g@comcast.net on 2020-10-24
I tried repeating 3 times with same results. Since everything is working fine I am going to write this off to some tech thing and mark it SOLVED

---

