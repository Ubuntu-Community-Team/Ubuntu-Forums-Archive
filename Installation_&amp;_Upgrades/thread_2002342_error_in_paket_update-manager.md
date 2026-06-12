---
title: "error in paket update-manager"
date: 2012-06-12
forum: Installation &amp; Upgrades
---

### Post by breithorn on 2012-06-12
E:Malformed line 5 in source list /etc/apt/sources.list (dist parse)

After I tried to install Adobe Reader in Ubuntu 12.04 sudo apt-get install acroread
:(

---

### Post by raja.genupula on 2012-06-12
Hi open your terminal and type this 
```
cat /etc/apt/sources.list
``` and post the output here .

---

### Post by breithorn on 2012-06-13
/home/martin/Pictures/Screenshot from 2012-06-13 15:45:48.png
# /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
deb [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner
deb-src [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse

---

### Post by raja.genupula on 2012-06-13
its looking fine , are you seeing anything odd 
```
gksu gedit /etc/apt/sources.list
```

---

### Post by breithorn on 2012-06-13
first thank you for your support, it's great!
gksu gedit /etc/apt/sources.list delivered 3 messages,
got 2 times this message:
Gtk-WARNING **: Locale not supported by C library. 
                            Using the fallback 'C' locale.
Then this message too:
GLib-GIO-WARNING **: Missing callback called fullpath = /root/.local/share/recently-used.xbel

---

### Post by raja.genupula on 2012-06-13
actually your terminal output of source.list seems to clear but apt saying there is a error in line number .

ok do one thing ..
open terminal and type as 
**sudo nautilus** then go to the sources.list by starting the navigation from the file system with the path as mentioned above . then open that file with gedit and look for any odd things

---

### Post by plucky on 2012-06-13
> deb [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner
deb-src [http://archive.canonical.com/precise](http://archive.canonical.com/precise) partner

Those two lines are incorrect.

Mine looks like

> deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

The /ubuntu are missing in your version.

Good Luck

---

### Post by breithorn on 2012-06-14
Wow, the error doesn't occur any more. I edited sources.list by modifying the two lines as mentioned above.  So far I'm happy now, thank you for your support):P

---

### Post by raja.genupula on 2012-06-14
Now please mark the thread as solved from thread tools . 

Thank you .

---

