---
title: "can't load fglrx dirver"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by McTek on 2008-04-29
Have tried several threads but just can't get fglrx keeps loading Mesa.
Second how do you remove googleearth from your system.

---

### Post by ajmorris on 2008-04-29
hi there,
the following wiki article will teach you how to set up your ati drivers :) : [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

if they still do not working after following this wiki article, please post the output of:
sudo glxinfo
less /etc/X11/xorg.conf
sudo fglrxinfo


AJ

---

### Post by McTek on 2008-05-01
Can not get by step 2 of the Wiki, need more detail
"How do you set execute flag?"

---

### Post by ajmorris on 2008-05-03
the execute flag means that users can execute, ls -l <file> will tell you if it does.... the order is OWNER, GROUP, Other, and an 'x' says whether it has execute for each section, but, essentially, if you want it to have the execute flag set, then do sudo chmod a+x <file>.

AJ

---

### Post by McTek on 2008-05-03
Gotten by step #2. You forgot to place an sh in front of the run file.
Where do I find the files in step #3 @ #4?

---

### Post by ajmorris on 2008-05-06
if you are referring to where you create your own .deb file to install with dpkg, the files come from the ati site itself

In order to properly install the latest drivers from [[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] ati.amd.com]("http://ati.amd.com/support/driver.html"), their executable installer needs to be converted into a .deb package file that can then be installed using the package system. In order to perform this conversion, some basic developer tools need to be installed.

but the first method doesnt require installing from the ati site...

---

### Post by McTek on 2008-05-08
Don't understand what you mean by the first method?

---

