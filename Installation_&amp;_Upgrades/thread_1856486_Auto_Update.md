---
title: "Auto Update"
date: 2011-10-08
forum: Installation &amp; Upgrades
---

### Post by avi9526 on 2011-10-08
Ubuntu 11.04, GNOME 2.32, KDE 4.6.5
How to make system update automatically without asking password and etc?
I try to use KDE and GNOME GUI to set autoupdate, but its doesn't work.
How to solve my problem? Thanks!

---

### Post by raja.genupula on 2011-10-08
[https://help.ubuntu.com/community/AutomaticSecurityUpdates](https://help.ubuntu.com/community/AutomaticSecurityUpdates)

---

### Post by Frogs Hair on 2011-10-08
In Gnome , (Update Manager > Settings) the only option for automatic installation of updates is for security updates . Other updates will require password conformation . What you are asking about may be possible , but I don't think it would be simple to accomplish .

---

### Post by avi9526 on 2011-10-08
I want ALL updates installed automatically without any pass (((
If I will add in
```
/etc/anacrontab
```
text
```
1    6    AutoUpdate    sh /home/avi9526/Scripts/AutoUpdate.sh
```
where AutoUpdate.sh have code
```
apt-get update
apt-get upgrade -y
```
does this will work ?

---

### Post by raja.genupula on 2011-10-08
> **avi9526 said:**
> I want ALL updates installed automatically without any pass (((
If I will add in
```
/etc/anacrontab
```
text
```
1    6    AutoUpdate    sh /home/avi9526/Scripts/AutoUpdate.sh
```
where AutoUpdate.sh have code
```
apt-get update
apt-get upgrade -y
```
does this will work ?


 yeah but small modification , i think ```
apt-get -y upgrade
```

---

### Post by avi9526 on 2011-10-08
I found similar way to solve my problem using unattended-upgrades package
[https://help.ubuntu.com/10.04/serverguide/C/automatic-updates.html](https://help.ubuntu.com/10.04/serverguide/C/automatic-updates.html)
And ... it works :) .. almost.
But this program not installing updates from ppa. Now I search way to solve that :-k
...
Found this article [http://blog.ezyang.com/2010/03/third-party-unattended-upgrade/](http://blog.ezyang.com/2010/03/third-party-unattended-upgrade/)
Now waiting for next autoupdate to see if all deb's from ppa's installed.

---

