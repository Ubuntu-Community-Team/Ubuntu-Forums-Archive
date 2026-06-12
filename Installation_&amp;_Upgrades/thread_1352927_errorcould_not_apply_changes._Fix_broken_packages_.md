---
title: "error:could not apply changes. Fix broken packages first"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by black&amp;blue on 2009-12-12
hello all. thank you very much for looking at my topic!
i have some trouble when try to install wine.
i did as [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) .after add the wineHQ APT repsitory and try to intall wine,i get a message "could not apply changes. Fix broken packages first".(my ubuntu is 9.10).
then i load up  synaptic,choose "custom filter"-->"broken",but no broken packages.
what should i do?

---

### Post by FrodeA on 2009-12-12
First off all: Any reason for choosing to download from winehq? Could you have chosen wrong distro?

I've used this link: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) to install what I need. Hope it helps.

---

### Post by black&amp;blue on 2009-12-12
just want to try some new,in fact i have two systems,xp and ubuntu.i'm sure no problem with distro.
the link is great but i can't find an anwser to solve my problem.
thank you for replying!

---

### Post by ibuclaw on 2009-12-12
Running in the terminal.

```
sudo apt-get install -f
```
or
```
sudo dpkg --configure -a
```
should resolve issues 90% of the time.

---

### Post by black&amp;blue on 2009-12-12
e.....i think i am the unlucky 10%.

---

### Post by ibuclaw on 2009-12-12
> **black&blue said:**
> e.....i think i am the unlucky 10%.

Well, are you going to post the output of those two commands then?

Saying that "it doesn't work" will not magically tell us what the problem is.

Regards
Iain

---

### Post by black&amp;blue on 2009-12-12
> **tinivole said:**
> Well, are you going to post the output of those two commands then?

Saying that "it doesn't work" will not magically tell us what the problem is.

Regards
Iain
output of 'sudo apt-get install -f'
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqca2 libwxgtk2.6-0 libqt4-test python-urwid libkonq5 libwxbase2.6-0
  libkonq5-templates libqca2-plugin-ossl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

```so i running 'sudo apt-get autoremove'
ouput
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libkonq5 libkonq5-templates libqca2 libqca2-plugin-ossl libqt4-test
  libwxbase2.6-0 libwxgtk2.6-0 python-urwid
0 upgraded, 0 newly installed, 8 to remove and 8 not upgraded.
After this operation, 12.8MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 154043 files and directories currently installed.)
Removing libkonq5 ...
Removing libkonq5-templates ...
Removing libqca2-plugin-ossl ...
Removing libqca2 ...
Removing libqt4-test ...
Removing libwxgtk2.6-0 ...
Removing libwxbase2.6-0 ...
Removing python-urwid ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
Processing triggers for python-support ...

```your second command noting to display on my terminal
after done those i reinstalled winehq,but the problem still exist.
Thanks for your help

---

### Post by Roblox on 2009-12-16
Mine sill didn't work

---

### Post by Scott O'Nanski on 2009-12-29
Bump, bumpipty bump bump, bumperoo...

---

### Post by mrgerlo on 2010-01-06
Same here.... the output of the commands given is the same, but the installation of wine doesn't start

---

### Post by bluelamp999 on 2010-01-07
This exact same thing is happening to me too.

Any more assistance?

Thanks

**Update!**

Went to Ubuntu Software Centre and installed it from there. Now have Wine 1.1.35

Go figure...

---

