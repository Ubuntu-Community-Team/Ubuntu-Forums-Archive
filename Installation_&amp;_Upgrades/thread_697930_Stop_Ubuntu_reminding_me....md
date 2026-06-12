---
title: "Stop Ubuntu reminding me..."
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by tom66 on 2008-02-15
I had a problem with Ubuntu. I solved the problem with some help, by forcing the version one version lower. Now Ubuntu keeps prompting me to upgrade the packages - I've tried this, but this triggers the problem once again. 

How do I stop it bugging me? Thanks.

---

### Post by dje on 2008-02-15
To stop update manager from checking for updates go to:

System >> Administration >> Software Sources
Then go to the Updates tab and uncheck 'Check for updates'

This will stop the orange icon from appearing in the notification area. You can manually check for updates by going to:
System >> Administration >> Update Manager

Bear in mind that this will stop reminders of all system updates, including security updates

Hope that helps you
dje

---

### Post by tom66 on 2008-02-15
I still want security updates. I just want it to not remind me about these particular packages...

Thanks anyway,
Tom

---

### Post by dje on 2008-02-15
Sorry I don't know how to stop reminders of particular packages but I do know how to stop updates to particular packages. Is that helpful?

Open up synaptic
Highlight a package you don't want updates for
Go to Package >> Lock Version

And its done, that package won't receive updates
If you want updates again just repeat the procedure

dje

---

### Post by tom66 on 2008-02-15
Thank you! It solved the problem.

Thanks again,
Tom

---

### Post by dje on 2008-02-15
You're very welcome

dje

---

