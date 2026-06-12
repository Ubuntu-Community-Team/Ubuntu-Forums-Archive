---
title: "M2400W - How to Configure &amp; Install in 6.0.6?"
date: 2006-10-14
forum: Installation &amp; Upgrades
---

### Post by trebor2510 on 2006-10-14
](*,) 

Hi there. 

I'm new to Ubunto and have just installed the latest version. Everything seems fine with the exception of adding the printer (a Magicolor 2400W).

I've attempted to install the driver by installing the RPM package from SourceForge and then adding the printer through the Admin option. I've now got the printer added to the printer list, but whenever I attempt to print a test page it just sits there and hangs with the message "Stopped: job-stopped" in the Status column of the printer window... :( 

Any ideas on what I'm doing wrong?

---

### Post by smileone on 2007-02-23
I have the same printer Konica Minolta Magicolor 2400:
(first install the build-essential for compile ```
sudo apt-get install build-essential
```)
1. download the latest version of CUPS from [http://www.cups.org/](http://www.cups.org/)
(ex. cups cups<version>.tar.gz)
2.extract the file that you just downloaded
3.you must modify the file contains in folder /backend/usb-unix.c
4.search the line usb_bc =... 
5.replace this line with usb_bc = 0;
6.now install the new version of cups that you have modify
```
./configure
make
sudo make install
```
7. restart cups system
```
sudo /etc/init.d/cupsys restart
sudo /etc/init.d/cupsd restart
```
Now download the driver for your printer from [http://sourceforge.net/projects/m2300w/]("http://sourceforge.net/projects/m2300w/")
1. extract the file you have downloaded
2. go to the folder that you have just create, and compile the driver
```
./configure
make
sudo make install
```
if you have any problem this is my e-mail [email]ely_on_msn@hotmail.it[/email]

---

### Post by CujoQuarrel on 2007-03-07
Was going down this path but I don't see the term **usb_bc** anywhere in the c code under the backend directory. 

And , not trying to complain, shouldn't there be an easier method than this?

---

### Post by fatpatns on 2007-03-13
5.replace this line with usb_bc = 0;



I think it's use_bc = 0;             not b!

---

### Post by zvacet on 2007-03-14
Install **alien** package with synaptic.Convert RPM to deb with
```
sudo alien file_name rpm
```
after that just install

---

### Post by taladon on 2007-04-17
Hello.

The alien install isn't going to help you.

There is a bug in the printing software (CUPS) that makes printing wtih the M2400w take a very long time.

Please see the following thread for instructions:

[http://ubuntuforums.org/showthread.php?t=206736&highlight=minolta+2400](http://ubuntuforums.org/showthread.php?t=206736&highlight=minolta+2400)

---

### Post by christhemonkey on 2007-04-30
Just to say that smileone's post is what enabled me to use this printer in feisty.

No need to compile the m2300w driver though, its in the repositories now! :D

Though i did need to upgrade cups from v1.2 to 1.3svn for it to print properly.

---

