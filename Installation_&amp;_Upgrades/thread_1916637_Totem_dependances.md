---
title: "Totem dependances"
date: 2012-01-28
forum: Installation &amp; Upgrades
---

### Post by silmaa on 2012-01-28
Hi all,

I have just installed ubuntu 11.10, but I cannot intall any paquet or upgrade my system due to a problem with totem... Here is the message :

```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 totem : Depends: totem-common (= 3.0.1-0ubuntu7.1) but 3.0.1-0ubuntu5 is installed
 totem-plugins : Depends: gir1.2-totem-1.0 (= 3.0.1-0ubuntu7.1) but 3.0.1-0ubuntu5 is installed
E: Unmet dependencies. Try using -f.

```

As a consequence, I use the -f option, but I guess it is not good to use it all the time...

What can I do ?

Thank you in advance,

Silmaa

---

### Post by jerrrys on 2012-01-30
that is "**sudo** apt-get -f install" also did you "sudo apt-get update" first?

---

### Post by skyiscrying on 2012-04-10
I've very recently installed 12.04LTS Beta2  and Totem would not work. However some updates came through today - I used Update Manager -  and now it's working.

---

