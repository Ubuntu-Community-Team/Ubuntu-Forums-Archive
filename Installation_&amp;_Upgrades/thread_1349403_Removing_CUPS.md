---
title: "Removing CUPS"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by paulocr on 2009-12-08
Hello,

I have removed cups from my system as I will not be using a printer with it however the update manager keeps telling me to upgrade libraries related to cups and to install cups (new install it says).

How can I purge this package from my system and stop it from being offered as an installation/upgrade candidate?

Thanks,

Paulo

---

### Post by MelDJ on 2009-12-08
go to system-admin-synaptic and find for the cups package then mark it for complete removal

---

### Post by paulocr on 2009-12-08
Thanks but I had already removed it by doing 

aptitude remove cups

Should I reinstall and them do the Complete Removal through Synaptic?

---

### Post by Zoot7 on 2009-12-08
```
sudo apt-get clean && sudo apt-get autoremove
```
That'll get rid of any packages that aren't needed any more.

---

