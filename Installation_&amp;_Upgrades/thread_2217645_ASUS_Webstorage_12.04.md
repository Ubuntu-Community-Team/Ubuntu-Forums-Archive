---
title: "ASUS Webstorage 12.04"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by Dave.YNA on 2014-04-18
Hello,
     Has anyone manage to get the ASUS Webstorage Sync agent to work on ubuntu 12.04? 

I downloaded and installed the Deb but nothing happens on launching. 

Any advice appreciated.

---

### Post by Dave.YNA on 2014-04-18
SOLVED IT..... after much searching around...

Here is what to do. 

First Install mono-complete
[COLOR="#008000"]apt-get install mono-complete[/COLOR]

Then change the icon executable
edit the following file

[COLOR="#008000"]/usr/share/applications/aws-autostart.desktop[/COLOR]

update the [COLOR="#008000"]"Exec=" [/COLOR]command to use the following command instead
[COLOR="#008000"]mono  --runtime=v4.0 /usr/lib/ASUSWebStorage/ASUSWebStorage.exe[/COLOR]

---

