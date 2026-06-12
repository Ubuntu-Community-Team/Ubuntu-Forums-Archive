---
title: "Upgrade Failed, user closed durring installation"
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by 65 mustang on 2008-10-03
I was helping someone upgrade from 7.10 to 8.04 over the phone.  Somewhere in the installation stage they dident know an answer to a question that it asked them so they exited out of the upgrade all together.  Which was exactly what i instructed them not to do.  They have also rebooted the machine.

It booted up thank god.  But i have no way to know how far it got.  When they open the update manager it tells then to run a command to fix the package database.

How should i go about fixing this?  Can i start the upgrade again or do i have to work with what i have and manually fix it?

---

### Post by Sef on 2008-10-03
Do they have an alternate cd or can they download one?  If so, read this [thread]("http://ubuntuforums.org/showthread.php?t=937306").

---

### Post by 65 mustang on 2008-10-03
When i do a
```
sudo dpkg --configure -a
```
it gets them to the configure screen for the no-ip client.  When they enter the email account name it lock up the window.
When they try to close the window it does not continue with the dpkg.

Can i force it to remove no-ip while the package database is broken?

---

### Post by cariboo on 2008-10-03
Maybee get them to try:

```
sudo apt-get install -f
```

This may download some missing packages. THe packages are in an unstable state right now so it may take intervention in person to repair the problem.

Jim

---

### Post by Pumalite on 2008-10-03
And after both commands above:
sudo apt-get update
sudo apt-get dist-upgrade

---

