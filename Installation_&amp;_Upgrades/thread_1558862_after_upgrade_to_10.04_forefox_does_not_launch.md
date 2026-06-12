---
title: "after upgrade to 10.04 forefox does not launch"
date: 2010-08-22
forum: Installation &amp; Upgrades
---

### Post by ericlb on 2010-08-22
Hi,

I just   upgraded from 8.04 to 10.04. All seemed to work well until I tried to launch Firefox.  It started (saw it in the task bar) but then a message ...  Firefox is already running. Close it or restart.  I rebooted and then tried Firefox... same issue.
 Firefox creates a .parentlock file just before it does not launch.  I delete the .parentlock and still no launch!
 Tried  firefox -safe-mode    no launch!!
 Tried firefox -P and created a new profile.  Same problem, could not launch the new profile!!!
 
 Messages reports  
 
 requested_mask="k::"  denied_mask="k::" and then creates the .parentlock file
 
I am a bit lost now. HOW can I get Firefox to launch?

[CENTER] Eric
[/CENTER]

---

### Post by lovinglinux on 2010-08-22
If it doesn't start with a new profile, then try to re-install firefox:

```
sudo apt-get install --reinstall firefox
```

Also check if you have Prism or Moonlight installed and remove them. They can cause such issues.

---

### Post by ericlb on 2010-08-22
> **lovinglinux said:**
> If it doesn't start with a new profile, then try to re-install firefox:

```
sudo apt-get install --reinstall firefox
```Also check if you have Prism or Moonlight installed and remove them. They can cause such issues.

Thanks for the suggestion. I already tried that - reinstalled Firefox - and checked for dependencies -- but problem continues.

If they are not in the 8.04 or 10.04 default installation, then I do not have them installed. I have not installed Prism or Moonlight but will check anyway to see if they are installed.  (I am accessing the Internet from a different (working) computer). 

Any other suggestions about what may be the cause?

---

### Post by lovinglinux on 2010-08-22
> **ericlb said:**
> Any other suggestions about what may be the cause?

I would say a bad upgrade or conflicting gnome settings.

You could try to re-install xulrunner too. Additionally, you could try to create a new Ubuntu user, just to verify if there isn't any old gnome settings messing with Firefox.

---

### Post by ericlb on 2010-08-22
> **lovinglinux said:**
> I would say a bad upgrade or conflicting gnome settings.

You could try to re-install xulrunner too. Additionally, you could try to create a new Ubuntu user, just to verify if there isn't any old gnome settings messing with Firefox.


Should have said that I found that suggestion too. I did reinstall xulrunner -- problem continued.

I had hoped not to have to do that... the user id number is sync'ed in home network.

---

### Post by lovinglinux on 2010-08-22
> **ericlb said:**
> Should have said that I found that suggestion too. I did reinstall xulrunner -- problem continued.

I had hoped not to have to do that... the user id number is sync'ed in home network.

Don't worry, is not to replace your user, but just to see if the problem persists.

---

