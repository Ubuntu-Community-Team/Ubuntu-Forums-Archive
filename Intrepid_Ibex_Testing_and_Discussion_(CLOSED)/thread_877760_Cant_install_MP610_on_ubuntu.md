---
title: "Cant install MP610 on ubuntu"
date: 2008-08-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by eifel on 2008-08-02
Hi,
my name is eifel and im form germany.
I have a problem with Intrepid.
I cant install the Canon Mp610,
The ppd-File from Canon isnt usable at my Computer .
It says:
Zeile 173- Wert fehlt
in englisch:
Line 173- Value missed

I did the Installation as introduced by the Wiki. [http://wiki.ubuntuusers.de/Canon-Drucker?highlight=canon](http://wiki.ubuntuusers.de/Canon-Drucker?highlight=canon)
All dlls are linked right.

Has anybody got this Problem?

---

### Post by eifel on 2008-08-03
Anybody can give ma an advise?
If you are german,or can read it,please do it:
[http://forum.ubuntuusers.de/topic/mp-610-fehlerhaft-ppd/](http://forum.ubuntuusers.de/topic/mp-610-fehlerhaft-ppd/)

thanks in advance

---

### Post by ryo1127 on 2008-09-05
I am new to Linux, so for more information on what the following commands will do go to the following post:

[http://ubuntuforums.org/showpost.php?p=4096434&postcount=2]("http://ubuntuforums.org/showpost.php?p=4096434&postcount=2")

Pretty much **everything is based** on that post with minor modifications in order to install the MP610. I got it to work on for Ubuntu Hardy 8.04 64-Bit.

Get the drivers from: [http://software.canon-europe.com/software/0028478.asp?model=]("http://software.canon-europe.com/software/0028478.asp?model=")

You need:
[LIST]
[*]cnijfilter-common-2.80-1.i386.rpm
[*]cnijfilter-mp610series-2.80-1.i386.rpm
[/LIST]

Or from the terminal (easier):

```
wget http://software.canon-europe.com/files/soft28478/software/cnijfilter-common-2.80-1.i386.rpm

wget http://software.canon-europe.com/files/soft28478/software/cnijfilter-mp610series-2.80-1.i386.rpm
```

To extract the rpm files you need to install the rpm package if necessary ([more info]("http://packages.ubuntu.com/hardy/rpm")):

```
sudo apt-get install rpm
```

Extract the rpm files:

```
rpm2cpio cnijfilter-common-2.80-1.i386.rpm | cpio -ivd
rpm2cpio cnijfilter-mp610series-2.80-1.i386.rpm | cpio -ivd
```

Then copy the needed files to proper locations: First, the cups-Filter:

```
sudo cp usr/lib/cups/filter/pstocanonij /usr/lib/cups/filter/
```

Then the closed-source binary along with its shared librarys:

```
sudo cp usr/local/bin/cifmp610 /usr/local/bin/
sudo cp usr/lib/lib* /usr/lib32
```

And the configuration-files for the binary::

```
sudo cp -r usr/lib/bjlib /usr/lib
```

PPD-file modified by [daritter]("http://ubuntuforums.org/member.php?u=413154") according to [ubuntuusers.de]("http://wiki.ubuntuusers.de/Canon-Drucker#head-d442123c5638494a2189df5fc28f7759e5287de0"):

```
sudo cp usr/share/cups/model/canonmp610.ppd /usr/share/ppd/custom/
```

The driver needs the ia32-libs package and two symlinks to find libtiff and libpng (which one can see by running "ldd /usr/local/bin/cijmp610"):

```
sudo apt-get install ia32-libs
cd /usr/lib32
sudo ln -s libtiff.so.4 libtiff.so.3
sudo ln -s libpng12.so.0.15.0 libpng.so.3
sudo ldconfig
sudo /etc/init.d/cupsys restart
```

[SIZE="4"]**Thanks [daritter]("http://ubuntuforums.org/member.php?u=413154") for such a clear and easy to follow guide!**[/SIZE]

---

### Post by IanW on 2008-09-05
You might also find this blog useful:- [http://mp610.blogspot.com/](http://mp610.blogspot.com/)

---

