---
title: "Skype tell me Dependency is not satisfiable..."
date: 2007-08-09
forum: Installation &amp; Upgrades
---

### Post by hsalgado on 2007-08-09
Hello Ubuntu friends, I need your help.  I installed my bluetooth headset in ubuntu, but when I wanted to install new software it tell me that Dependency is not satisfied: libasound2.  This package is already installed.  I tried uninstalling it to install it again, but it start uninstalling the desktop, so I had to install the desktop again... It also uninstalled me skype.  When I tried to reinstall skype it keep saying the same... dependency is not satisfiable: libasound2.

Is there anyway I can reinstall that package without remove it?

Thanks a lot for any help!!!!!!!!

---

### Post by hsalgado on 2007-08-09
I tried sudo apt-get install --reinstall libasound2 and it reinstalled it, but skype keep telling me the same...  Please help!!!!!

---

### Post by hsalgado on 2007-08-09
OK, It looks like the version that I need for skype is libasound2 1.0.12, but I have installed libasound2 1.0.11... is there any way I can update to the newest version in Ubuntu Edgy?  Or do I need to install Feisty?  Thanks for any help!

---

### Post by maclenin on 2007-08-09
I think you need to install feisty! I ran into a similar problem when I tried to upgrade to the latest version of skype - certain dependencies could not be met - and the only way to resolve the dependency (I discovered) was to upgrade to fiesty - which I will try in the near future. Good luck!

---

### Post by hsalgado on 2007-08-12
Thanks a lot for your reply... It looks like that is the only solution.  Too bad I didn't have the old version of skype installation files.  I have tried to update to Fiesty but the process can not finish for some weird reason.  It looks like it can not find the repositories of some packages I have installed...

I will post I have find any solution.

---

### Post by hsalgado on 2007-08-14
Solution found.  I updated to fesity and everything works now.  Thanks for your help.

---

### Post by maclenin on 2007-08-15
Glad to hear you got it working!

---

