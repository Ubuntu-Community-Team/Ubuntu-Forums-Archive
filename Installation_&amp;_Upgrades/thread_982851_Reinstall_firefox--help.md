---
title: "Reinstall firefox--help"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2008-11-15
I have just installed ubuntu 8.10 but I have also install some add-ons I think have done some damages, I want to reinstall firefox  and need help if they are some command line commands one can use ?

---

### Post by Partyboi2 on 2008-11-16
Open a terminal and reinstall firefox
```
sudo apt-get --reinstall install firefox-3.0
```

---

### Post by linux_tech on 2008-11-16
First download Firefox .tar.bz2 file to your home directory, then run these commands: 
```
cp -R ~/.mozilla ~/.mozilla.backup
```
```
[code]sudo tar -jxvf firefox-3*.tar.bz2 -C /opt
rm firefox-3*.tar.bz2
```
```
sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup
```
```
sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins
```
```
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
```
```
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```

Installing Firefox from Mozilla-
[https://help.ubuntu.com/community/FirefoxNewVersion#Removing](https://help.ubuntu.com/community/FirefoxNewVersion#Removing)

---

