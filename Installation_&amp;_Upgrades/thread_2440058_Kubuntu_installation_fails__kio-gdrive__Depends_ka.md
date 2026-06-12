---
title: "Kubuntu installation fails | kio-gdrive : Depends: kaccounts-providers but it is not"
date: 2020-04-05
forum: Installation &amp; Upgrades
---

### Post by richucj on 2020-04-05
[FONT=arial]hi all,
I tried to install kde plasma after installing tasksel using this command in ubuntu 18.04[/FONT]
[COLOR=#000080]sudo tasksel install kubuntu-desktop[/COLOR]

but the installation fails and now when i try to upgrade using sudo apt-get upgrade it throws error.
```
richucj@richucj-Vostro-15-3568:~$ sudo apt-get upgrade
[sudo] password for richucj: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 kio-gdrive : Depends: kaccounts-providers but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).


```

[FONT=arial]please help[/FONT]..
regards,
richu

---

