---
title: "Disable login screen on intrepid"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by depping on 2008-10-14
Hi,

I'm new to this stuff, I searched the forums but couldn't find an answer and hope that any of you can help me out...

I've been trying to auto login into intrepid. I've done the obvious:
system - administration - security - enable...

but still it doesn't work. I checked gdm.conf:
AutomaticLoginEnable=true
AutomaticLogin=<username>

Anyone with an idea where to look?

---

### Post by gjoellee on 2008-10-14
in the menu go to System->Administration->Loogin Windows go to the security tab. Not click on "Enable Automatic Login" and choose your user. Then click close.

---

### Post by depping on 2008-10-14
that's what I already did, but it doesn't automatically login. I selected the correct user...

---

### Post by depping on 2008-10-15
> **depping said:**
> that's what I already did, but it doesn't automatically login. I selected the correct user...

I must have been sleeping, the topic should say, enable automatic login...

---

### Post by depping on 2008-10-16
I found two related messages in /var/log:
daemon: gdm[5481]: WARNING: Couldn't authenticate user 
syslog: gdm[5481]: WARNING: Unable to establish service gdm-autologin: Critical error - immediate abort  

anyone?

---

