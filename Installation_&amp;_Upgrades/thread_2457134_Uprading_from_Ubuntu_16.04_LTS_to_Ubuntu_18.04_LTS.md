---
title: "Uprading from Ubuntu 16.04 LTS to Ubuntu 18.04 LTS"
date: 2021-01-26
forum: Installation &amp; Upgrades
---

### Post by ahmed11ber on 2021-01-26
Hi,

I have upgraded my ubuntu 16.04 lts to ubuntu 18.04 lts, but when it startup and i logged-in, I have no lauch menu, no applications menu. In ubuntu 16.04 I have unity desktop, but in this version we don't  have unity desktop, it is now a gnome desktop. Please can you help me to solve this issue.

Thanks.

---

### Post by CelticWarrior on 2021-01-26
Sometimes the upgrade fails. Many reasons for that and really no point in troubleshooting.
Make your backups if you haven't done yet - you should always have backups and especially when doing such operations - and install fresh. And because you're now installing from scratch also no point in using the old LTS, install 20.04.

---

### Post by ahmed11ber on 2021-01-26
The reason I upgrade to 18.04 because I can't upgrade directly from 16.04 to 20.04.

---

### Post by deadflowr on 2021-01-26
Upgrades should still have unity installed.
Check in the login screen.
In 18.04 there should be an option to switch sessions.
After you click on your username, next to the password field should be a cog icon.
Click on the cog to see what sessions are available and try selecting one.
Then input your password and see if it logs in.

---

### Post by grahammechanical on 2021-01-26
Do you see in the top panel on the left the word Activities? Click on that. Do you now get access to application icons? Is the Dock set to autohide? I upgraded from 18.04 with Unity to 20.04 and I get a Dock/Launcher that is empty of icons until I use Activities to launch an application and then the Dock is populated with the icons of favourite apps.

I live with this situation. There are two solutions to my problem. Spend time and effort trying to identify which package needs re-installing or removal. Or, re-install Ubuntu. Eventually I shall re-install. It is the less stressful solution.

Regards

---

### Post by ahmed11ber on 2021-01-27
Thank you,
I have solved the problem by doing these commands.

sudo apt clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

---

### Post by rsteinmetz70112 on 2021-01-28
When you go to upgrade to 20.04 make sure you have fully updated and upgraded 18.04 

```
sudo apt update
sudo apt full-upgrade
sudo apt aotoremove
sudo apt autoclean
do-release-upgrade
```

Please mark this thread solved.

---

