---
title: "Upgrade problems"
date: 2019-08-27
forum: Installation &amp; Upgrades
---

### Post by hardcoretexan on 2019-08-27
I recently did an update(no problems) and then upgrade and got this error, Can anyone assist me as to what is the next step. 

```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

I then ran this in terminal and got this
```
apt --fix-broken install
E: Could not open lock file /var/lib/dpkg/lock-frontend - open (13: Permission denied)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), are you root?
```

---

### Post by cruzer001 on 2019-08-27
Usually a reboot will remove those locks.

Wait a minute!  Did you do "sudo apt"?

---

### Post by rsteinmetz70112 on 2019-08-27
Firsg did you run 

```
#sudo apt --fix-broken install
```

Are any other package management programs like synaptic or Software Updater open? they will prevent apt from running.

---

### Post by hardcoretexan on 2019-08-27
No I ran it just like I pasted it, as it was posted on terminal. Running now

---

