---
title: "Evolution setup assitant"
date: 2007-05-26
forum: Installation &amp; Upgrades
---

### Post by KingdomKid on 2007-05-26
I am attempting to setup my accounts in Evolution on my second laptop. 
(I run Kubuntu 7.04 and Evolution on all my computers). 
The Evolution Setup Assistant keeps running extremely slow until it all but freezes up. When I open Evolution it takes approx. 1min or so for it to open. Then I enter in my info and forward to next step. Evolution takes several minutes to advance to the next step. Way too long...like 4 to 5 mins from step to step, Yet, it is running. This is a fresh install of Kubuntu 7.04. I have uninstalled and reinstalled Evolution and this is not resolving the issue. I even reinstalled the OS (Kubuntu).
All other programs, etc. are running fine. No issues anywhere else that I can tell. It is just when I open Evolution and try to setup,](*,)

Thanks for the help.

Ok...so I finally made it all the way through the set up (3hrs). I rebooted, just to see if problem would go away after set up. Launched Evolution, it took 10 mins for it to completely load. Can not figure out why it is running so slow. All others are working fine.

---

### Post by bapoumba on 2007-05-27
Hum, and this doesnot happen on your other computers, right ?
Do you have any message when you launch evolution from a terminal ?

---

### Post by KingdomKid on 2007-05-27
> **bapoumba said:**
> Hum, and this doesnot happen on your other computers, right ?
Do you have any message when you launch evolution from a terminal ?


Right, this does not happen on any of my others.
Hey, thanks for reminding me...I'm kinda new at using linux, I didn't think to try and open in the terminal. Here is my out results when I did.

pamela@PamelasEvo:~$ evolution
CalDAV Eplugin starting up ...
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

Keep in mind, I uninstalled and reinstalled Evolution twice. 
Then I thought I broke something, because I had uninstalled Evolution from the terminal and removed all remaining "evolution" settings from the cache, etc.....That was a no no I think... I found out in my searching for a solution, that (K)unbuntu comes packaged with some Evolution necessities.
So to resolve anything I may have broke, I reinstalled the entire OS (Kubuntu) and started over on a fresh install.
Still, same issue. All other programs etc are working fine...I don't get it. In fact, I am using the computer now to write this. 
Thanks for any help bapoumba.

After I finshed this reply to you< I went back to my terminal and found this....in addition to what is above. Evolution did open, very slowly. I eventually shut it down.

/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
/bin/sh: /usr/bin/esd: not found
Killed
pamela@PamelasEvo:~$

---

### Post by KingdomKid on 2007-05-28
Bapoumba I installed esound in response to the results of my post above and help from an answer from launchpad. 

[https://answers.launchpad.net/ubuntu/+question/7191](https://answers.launchpad.net/ubuntu/+question/7191)

Evolution took approx 4mins or so to launch. Once launched it seemed to run ok. Checked mail, ran calendar, task ,etc. all seemed to run ok. I closed and launched again...still took 4 to 5 minutes to launch. Below is my terminal:

pamela@PamelasEvo:~$ evolution
CalDAV Eplugin starting up ...
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
(evolution-2.10:9428): e-data-server-DEBUG: Loading categories from "/home/pamel                                                              a/.evolution/categories.xml"
(evolution-2.10:9428): e-data-server-DEBUG: Loaded 29 categories

(evolution-2.10:9428): Gtk-CRITICAL **: gtk_widget_is_focus: assertion `GTK_IS_W                                                              IDGET (widget)' failed

(evolution-2.10:9428): Gtk-CRITICAL **: gtk_widget_is_focus: assertion `GTK_IS_W                                                              IDGET (widget)' failed

(evolution-2.10:9428): Gtk-CRITICAL **: gtk_widget_is_focus: assertion `GTK_IS_W                                                              IDGET (widget)' failed

(evolution-2.10:9428): Gtk-CRITICAL **: gtk_widget_is_focus: assertion `GTK_IS_WIDGET (widget)' failed

(evolution-2.10:9428): GLib-GObject-WARNING **: IA__g_object_set_valist: property `width' of object class `GtkTreeViewColumn' is not writable

(evolution-2.10:9428): libglade-WARNING **: unknown property `ellipsize' for class `GtkImage'

(evolution-2.10:9428): libglade-WARNING **: unknown property `width_chars' for class `GtkImage'

(evolution-2.10:9428): libglade-WARNING **: unknown property `single_line_mode' for class `GtkImage'

(evolution-2.10:9428): libglade-WARNING **: unknown property `angle' for class `GtkImage'

(evolution-2.10:9428): Gtk-CRITICAL **: gtk_widget_is_focus: assertion `GTK_IS_WIDGET (widget)' failed
process 9428: The last reference on a connection was dropped without closing the connection. This is a bug in an application. See dbus_connection_unref() documentation for details.
Most likely, the application was supposed to call dbus_connection_close(), since this is a private connection.
pamela@PamelasEvo:~$

Thanks for any help!

---

### Post by bapoumba on 2007-05-28
OK, yesterday I did look around about this error. There are bugs, looks like an X error to me (I am _not sure_ about this), at least an error from KDE, may be because of graphical libs (_not sure_ either). Evolution uses gtk libs and KDE qt. Are you using a cusom theme, icons for ex (once again, this is a _guess_)? If so, try to use the same as the ones on the other computers.

Your last post shows a dbus error. I'll dig into this. Anyone else as an idea ?

---

### Post by KingdomKid on 2007-05-29
Bapoumba, thanks for the input.
I am actually still running all default themes, etc. I haven't gotten to customizing anything yet, as I have been on this Evolution issue. 
It's kinda got me stumped here.

Thanks for anything you can come up with. I reseaching as well.
Thanks again :D
Hope to hear from you soon...and I'll post anything I come up with.

I got a response in launchpad ( link is in previous post )and he suggested:

"Cesare Tirabassi proposed the following answer:
There seems to be a serious bug with the CalDAV Eplugin.
For the time being the only way to solve it is by removing the plug-in.
You can also safely remove esound, I don't think it is needed on a Kubuntu desktop."

I gotta look in to this a little further???Not sure how to do that ( CalDAV Eplugin )

Thank You!

---

### Post by KingdomKid on 2007-05-29
I did a *sudo aptitude purge evolution*
Then I put it back in with *sudo aptitude install evolution*

Once I installed, I launched from terminal, here is my output:

```
pamela@PamelasEvo:~$ evolution
CalDAV Eplugin starting up ...
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

(evolution-2.10:6714): evolution-mail-WARNING **: ignored this junk plugin: not enabled or we have already loaded one

(evolution-2.10:6714): e-utils-WARNING **: Plugin 'Bogofilter junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'
** (evolution-2.10:6714): DEBUG: mailto URL command: evolution %s
** (evolution-2.10:6714): DEBUG: mailto URL program: evolution
```

You got me??? Get this, after about 4 to 5 mins....surprizingly..it launched....GO FIGURE?
Any suggestions?

---

### Post by KingdomKid on 2007-05-29
A little more info here:

I found something interesting.....
I was installing my hp printer. I downloaded HPLIP. After HPLIP and CUPS was downloaded and restarted..the hp-setup utility is suppose to be executed.

During the execution, I got this very same error message (see below ( X Error: )),
that I've been getting with Evolution. It is responding exactly as
evolution is responding. Any hints on what could be happening.
Apparently, it seems to be something besides just Evolution??????

Below is the BUILD and INSTALL commands up to the error message:

```
BUILD AND INSTALL
-----------------

Running './configure --enable-network-build --disable-pp-build --enable-fax-build --enable-gui-build --enable-scan-build --prefix=/usr'
Please wait, this may take several minutes...

Command completed successfully.

Running 'make clean'
Please wait, this may take several minutes...

Command completed successfully.

Running 'make'
Please wait, this may take several minutes...

Command completed successfully.

Running 'sudo make install'
Please wait, this may take several minutes...

Command completed successfully.

Running 'sudo /etc/init.d/hplip restart'
Please wait, this may take several minutes...

Command completed successfully.
Restarting CUPS...

Command completed successfully.
Please make sure your printer is connected and powered on at this time.
Password:

HP Linux Imaging and Printing System (ver. 1.7.4a)
Printer/Fax Setup Utility ver. 4.5

Copyright (c) 2001-7 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
error: Unable to connect to hpiod.
error: Unable to connect to HPLIP I/O. Please (re)start HPLIP and try again.
pamela@PamelasEvo:~$
```


As you can see....getting the same error when launching the printer utility as when launching Evolution. I tried to launch from the graphical side also....  menu->system settings->printers ....same response as I get from evolution

Could there be a connection with this?????

---

### Post by bapoumba on 2007-05-29
I had found a bug the other day. Did not know what to make of it, or if related to your problem:
[https://bugs.launchpad.net/ubuntu/+source/kde-guidance/+bug/104904]("https://bugs.launchpad.net/ubuntu/+source/kde-guidance/+bug/104904")

Looks related to the graphic card. Which card is on this computer, and which drivers are you using? (i'm not too familiar with video drivers, however). If related to hardware, that could explain why only one of your computers is affected. Does KDE-guidance package rings a bell ?

Anyone ?

---

### Post by KingdomKid on 2007-05-31
I did a comparison.

It seems the only difference in these units are the following:

```
< mavsevo
---
> pamelasevo
14c14

< product: Intel(R) Pentium(R) 4 Mobile CPU 1.80GHz
---
> product: Mobile Intel(R) Pentium(R) 4 - M CPU 1.80GHz
18c18
< version: 15.2.4
---
> version: 15.2.7

< product: HTS541040G9AT00
---
> product: IC25N030ATCS04-0
240c258
< capacity: 37GB
---
> capacity: 27GB
248c266
< product: Compaq DVD-ROM SD-C2512
---
> product: Compaq DVD-ROM DV28EB
```

Other than the above, these units are identical.
Any ideas???

---

### Post by bapoumba on 2007-05-31
Hmm. Not to me, but I'm not much into hardware things. Anyone ?

---

### Post by KingdomKid on 2007-06-04
Problem Solved!!

[https://answers.launchpad.net/ubuntu/+question/7191](https://answers.launchpad.net/ubuntu/+question/7191)

Just one of them things?????](*,)

Thanks AAAGAIN, Cesare!=D>

---

