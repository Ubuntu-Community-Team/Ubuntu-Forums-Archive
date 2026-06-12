---
title: "PPTP Install Problems due to JRE Java"
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by justinemtp22 on 2006-11-09
I'm using Ubuntu Edgy and I tried to install the PPTP client and it tells me that JRE plugin is not installed. I did have a problem installing JRE and the plugin. I tried to reinstall and I get the following message:


justin@Justin:~$ sudo apt-get install sun-java5-jre sun-java5-plugin
Reading package lists... Done
Building dependency tree... Done
sun-java5-plugin is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java5-jre: Depends: sun-java5-bin (= 1.5.0-06-1) but it is not going to be installed or
                          ia32-sun-java5-bin (= 1.5.0-06-1) but it is not installable
  sun-java5-plugin: Depends: sun-java5-bin (= 1.5.0-06-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I don't know how to unistall JRE and I'm not sure what to do at this point. Any help would be greatly appriciated.

Thanks,
Justin

---

