---
title: "Not able to install new software"
date: 2012-01-22
forum: Installation &amp; Upgrades
---

### Post by kvalenza on 2012-01-22
I am no longer able to install software using Ubuntu Software Center. Here is the error message I get:

An unhandlable error occured

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate

What can I do to fix this problem

---

### Post by sanderd17 on 2012-01-22
First, try a reboot.

after that, try the following in a terminal and give us the output:

```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by kvalenza on 2012-01-22
> **sanderd17 said:**
> First, try a reboot.

after that, try the following in a terminal and give us the output:

```

sudo apt-get update
sudo apt-get upgrade

```

I got as far as the second command, but it wouldn't finish because I got this in the terminal:

TrueType core fonts for the Web EULA                                         
 &#9474;                                                                              
 &#9474; END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE                            
 &#9474;                                                                              
 &#9474; IMPORTANT-READ CAREFULLY: This Microsoft End-User License Agreement          
 &#9474; ("EULA") is a legal agreement between you (either an individual or a         
 &#9474; single entity) and Microsoft Corporation for the Microsoft software          
 &#9474; accompanying this EULA, which includes computer software and may include     
 &#9474; associated media, printed materials, and "on-line" or electronic             
 &#9474; documentation ("SOFTWARE PRODUCT" or "SOFTWARE"). By exercising your         
 &#9474; rights to make and use copies of the SOFTWARE PRODUCT, you agree to be       
 &#9474; bound by the terms of this EULA. If you do not agree to the terms of         
 &#9474;                                                                              
 &#9474;                                  <Ok>

---

### Post by sanderd17 on 2012-01-22
Are you able to answer that in any way? e.g. by typing 'y' or 'ok' and pressing enter.

If not, you might try to remove those microsoft fonts first:

```

sudo apt-get remove msttcorefonts

```

and execute the two commands I gave again.

---

### Post by kvalenza on 2012-01-22
> **sanderd17 said:**
> Are you able to answer that in any way? e.g. by typing 'y' or 'ok' and pressing enter.

If not, you might try to remove those microsoft fonts first:

```

sudo apt-get remove msttcorefonts

```

and execute the two commands I gave again.

I was not able to type 'y' or 'ok.' I opened up another terminal and I got this message when I tried to remove the microsof fonts:

keith@keith-Vostro-1720:~$ sudo apt-get remove msttcorefonts
[sudo] password for keith: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
keith@keith-Vostro-1720:~$

---

### Post by kvalenza on 2012-01-22
I rebooted the computer, entered sudo apt-get remove msttcorefonts and got this message:

keith@keith-Vostro-1720:~$ sudo apt-get remove msttcorefonts
[sudo] password for keith: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
keith@keith-Vostro-1720:~$ sudo dpkg --configure -a
keith@keith-Vostro-1720:~$ sudo apt-get remove msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'ttf-mscorefonts-installer' instead of 'msttcorefonts'
The following packages were automatically installed and are no longer required:
  browser-plugin-gnash menu-xdg ekiga gnuchess-book gnome-games-extra-data
  gtali glchess libclutter-gst-1.0-0 gnome-video-effects gnome-games cheese
  gdebi gnobots2 libfolks-eds25 liferea-data cheese-common libcheese1
  gdebi-core libcapi20-3 gnibbles gedit-plugins libboost-thread1.46.1 unixodbc
  libpt2.10.2 libboost-date-time1.46.1 gdm gnome-dictionary gnotski
  gnome-backgrounds libboost-signals1.46.1 libspandsp2
  libcluttergesture-0.0.2-0 iagno glines gnome-icon-theme-extras
  gir1.2-gucharmap-2.90 libmx-1.0-2 libopal3.10.2 liferea gnash gnotravex
  libcheese-gtk20 gnect python-evolution libgdict-1.0-6 gnome-contacts
  hamster-applet gnuchess gnash-common libclutter-imcontext-0.1-0 dconf-tools
  sound-juicer
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  ttf-mscorefonts-installer
0 upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing ttf-mscorefonts-installer (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
keith@keith-Vostro-1720:~$ sudo apt-get remove msttcorefonts

---

### Post by sanderd17 on 2012-01-22
great.

You can't remove it because it's corrupt, so you'll have to install it again first.

I hope you will be able to answer this time:

```

sudo apt-get install ttf-mscorefonts-installer

```

And don't forget to try apt-get update every now and then.

---

### Post by snowpine on 2012-01-22
You can press TAB to highlight the OK button, then press Enter to accept the Microsoft agreement.

[TAB is the standard keystroke to move between buttons/elements in a text interface.]

---

### Post by matt_symes on 2012-01-22
Hi

Use the tab key to move to the ok option on the EULA install page for mscorefonts and hit enter.

I would try to reinstall mscorefonts as suggested by the error message.

```
sudo apt-get install --reinstall ttf-mscorefonts-installer
```

Kind regards

---

### Post by kvalenza on 2012-01-22
> **snowpine said:**
> You can press TAB to highlight the OK button, then press Enter to accept the Microsoft agreement.

[TAB is the standard keystroke to move between buttons/elements in a text interface.]

This solved the problem! I couldn't figure out how to get the OK to work. Now I am able to install all software. Thanks.

---

