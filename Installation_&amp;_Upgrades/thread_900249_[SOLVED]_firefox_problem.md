---
title: "[SOLVED] firefox problem"
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by magnetism on 2008-08-25
After some effort, I managed to upgrade from dapper to hardy.
Everything is working excellent, expect, I can not install the latest firefox  (ver. 3).
Any advice on this please?

Thanks,
Mike

---

### Post by Dougie187 on 2008-08-25
What does your /etc/apt/sources.list file look like?

```
cat /etc/apt/sources.list
```

---

### Post by magnetism on 2008-08-25
these are the contents:

```

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu hardy-proposed main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse
deb http://ppa.launchpad.net/googlegadgets/ubuntu hardy main
# google gadgets
#deb-src http://ppa.launchpad.net/googlegadgets/ubuntu hardy main
# firefox 3
deb http://ppa.launchpad.net/fta/ubuntu hardy main


```

---

### Post by prshah on 2008-08-25
> **magnetism said:**
> After some effort, I managed to upgrade from dapper to hardy.
Everything is working excellent, expect, I can not install the latest firefox  (ver. 3).

Hardy comes with Firefox 3, so it's unlikely that it's not on your system. Most likely your menus are not updated. Press Alt+F2, and give the command```
/usr/bin/firefox-3.0
```; if that launches firefox, check the version in Help-About, then post back on how to edit your menus to make the change permanent.

---

### Post by magnetism on 2008-08-25
This command starts firefox 2.0
In /usr/bin I also have these files:
```

lrwxrwxrwx  1 root   root         20 2007-04-11 03:18 firefox -> /opt/firefox/firefox
lrwxrwxrwx  1 root   root         34 2008-08-25 13:31 firefox-3.0 -> ../lib/firefox-3.0.2pre/firefox.sh
lrwxrwxrwx  1 root   root         11 2008-08-25 13:31 firefox.ubuntu -> firefox-3.0
lrwxrwxrwx  1 root   root         20 2007-04-11 03:18 mozilla-firefox -> /opt/firefox/firefox

```

---

### Post by Crafty Kisses on 2008-08-25
Yeah Firefox 3 comes with Hardy and it's in the repos, try the following:
```
sudo apt-get install firefox
```

---

### Post by Dougie187 on 2008-08-25
You might have to remove firefox2 before you install firefox 3. I would suggest going through synaptic and making sure you have all the things you want for firefox. And removing the things you don't, like firefox-2.0

---

### Post by magnetism on 2008-08-25
I removed everything related to firefox from synaptic, removed the /opt/firefox directory and reinstalled firefox. This is working great.
The installed version is 

```
3.0.2pre
```

Is this the correct version?

---

### Post by Dougie187 on 2008-08-25
no, you should be at 3.0.1.
maybe go to your terminal and do a 
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by magnetism on 2008-08-25
I removed the last line from the repositeries list, removed firefox, reinstalled it and now have the 3.0.1 ver.

Thank you all!

---

### Post by magnetism on 2008-08-25
I now have a different problem related to the flash plugin.
The flash movies do not work the way they are supposed. I see a background color, even if the flash movie is supposed to be transparent. I use the 
flsahplugin-nonfree

Any ideas on this?

---

### Post by Dougie187 on 2008-08-25
No ideas. Maybe you should start a new thread with a descriptive name about the new issue. If you do, please mark this thread as solved. Thanks!

---

