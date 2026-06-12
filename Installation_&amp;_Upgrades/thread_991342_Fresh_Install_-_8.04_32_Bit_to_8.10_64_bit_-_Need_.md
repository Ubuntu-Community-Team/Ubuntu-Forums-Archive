---
title: "Fresh Install - 8.04 32 Bit to 8.10 64 bit - Need Help"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by fireboxtester on 2008-11-23
I want to be able to quickly get my installed packages back after the install.

Can  I do this deal to quickly get my installed apps back:
```

sudo dpkg --get-selections > /home/user/package.selections
```

and 
```
sudo dpkg --set-selections /home/package.selections && apt-get dselect-upgrade
```
on new system?

Or will that cause a lot of issues since I'm going from 32 bit to 64 bit?  Also package.selections seems to list everything installed such as firefox-3.0, but if 8.10 has a later version of firefox, will this cause it to be overwritten with this earlier version?

Is there a way I can just get a list of packages I've installed since I installed 8.04?  That way since there would be only 10 or 20, I could decide what to do with each one.

Please help.  Thanks.

---

### Post by Philio on 2008-11-23
Most packages use the same names for 32 and 64 bit so you should be ok for the most part. Not sure is a way you can see exactly which pakages were installed manually.

---

