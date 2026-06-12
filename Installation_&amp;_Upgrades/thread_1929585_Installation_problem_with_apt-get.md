---
title: "Installation problem with apt-get"
date: 2012-02-22
forum: Installation &amp; Upgrades
---

### Post by viktorjano on 2012-02-22
Hi! I am new to ubuntu,so please help, but have that in mind! :D

I face a problem... I tried to install skype on ubuntu. I was working in terminal, so I used apt-get wrapper. So, usually I tried sudo apt-get install skype... and got this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
skype is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  skype: Depends: libasound2 (> 1.0.17) but 1.0.13-1ubuntu5 is to be installed
         Depends: libgcc1 (>= 1:4.3) but 1:4.1.2-0ubuntu4 is to be installed
         Depends: libqt4-dbus (>= 4.4.3) but it is not installable
         Depends: libqt4-network (>= 4.4.3) but it is not installable
         Depends: libqtcore4 (>= 4.4.3) but it is not installable
         Depends: libqtgui4 (>= 4.4.3) but it is not installable
         Depends: libstdc++6 (>= 4.3) but 4.1.2-0ubuntu4 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

So will someone help!
By the way, I have problems also with all the others packages, for example, this is what I get when try to install aptitude:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
aptitude is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  skype: Depends: libasound2 (> 1.0.17) but 1.0.13-1ubuntu5 is to be installed
         Depends: libgcc1 (>= 1:4.3) but 1:4.1.2-0ubuntu4 is to be installed
         Depends: libqt4-dbus (>= 4.4.3) but it is not installable
         Depends: libqt4-network (>= 4.4.3) but it is not installable
         Depends: libqtcore4 (>= 4.4.3) but it is not installable
         Depends: libqtgui4 (>= 4.4.3) but it is not installable
         Depends: libstdc++6 (>= 4.3) but 4.1.2-0ubuntu4 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


Since, as I know apt-get solves by its own dependencies issues, but still I get these massages!

---

### Post by roelforg on 2012-02-22
I'm gonna address the elephant in the room here...
Why not just do what apt-get suggests you do?
That is:
```

sudo apt-get install -f

```
Note: that is the whole command

---

### Post by viktorjano on 2012-02-23
Thanks Roelforg!

I did that... no results!!! I'll give another try, but I am skeptic about it!

---

