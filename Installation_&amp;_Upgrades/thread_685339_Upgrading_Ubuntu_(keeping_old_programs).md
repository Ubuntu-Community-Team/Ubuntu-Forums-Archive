---
title: "Upgrading Ubuntu (keeping old programs)"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by toyohta on 2008-02-02
I have currently installed Ubuntu 6.06, and I would like to upgrade it to a more recent version (I have a CD with 7.1).

However, I am worried that when I install the new version, old software may need to be re-instaled. Most importantly, I have a student license for Matlab, which will expire when I complete my degree, at which point my license will expire too, and I won't be able to re-install (and hence re-activate it), even on the same computers.

Is it possible to upgrade Ubuntu without affecting installed software?

BTW, the way the Matlab activation works on Linux is that it binds Matlab to eth0. If I knew that eth0 didn't change, then a work-around might be to just backup Matlab and copy it to the same location after re-installing the OS.

Any suggestions?

---

### Post by zvacet on 2008-02-02
First of all you can not upgrade from Dapper to Gutsy.You must do it this way 

**Dapper>Edgy>Feisty>Gutsy**

You can reinstall but backup your data,so you can use them again.if it is not some sort of urgent need for upgrade my advice is to wait until april when Hardy will be out.Because it will be LTS too you will be able to upgrade directly from Dapper to Hardy.

---

### Post by toyohta on 2008-02-02
This helped. I upgraded Ubuntu one version at a time, using:
  gksu "update-manager -c"

I now have Gutsy up and running.

Thanks.

---

### Post by erdomi on 2008-02-02
I would also like to upgrade, but when I check for updates using the command:

gksu "update-manager -c"

it tells me that my system is up to date.  I am definitely running Dapper now and would like to upgrade up to Gutsy.  I have also tried the command:

gksu "update-manager -c -d"

it gives me the option to upgrade to 8.04.  This is Beta, right?  I don't want 8.04 until it's officially released.  Any ideas?

Thanks!

---

### Post by zvacet on 2008-02-02
This method is described as **not recommended** but if you want you can try it 

```
sudo sed -e 's/\sdapper/ edgy/g' -i /etc/apt/sources.list
```

This will change your source list from Dapper to Edgy

```
  sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get dist-upgrade 
```


```
sudo apt-get update && sudo apt-get dist-upgrade
  sudo apt-get -f install
  sudo dpkg --configure -a 
```

---

