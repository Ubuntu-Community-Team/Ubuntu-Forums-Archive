---
title: "Hplip broken in Jaunty"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by AndrewWalker on 2009-03-27
I've broken hplip in Jaunty upgrade. Has anyone else experienced this or know how to fix it? I've tried re-installing it but no change. Here's what I get on starting it

andrew@Dell:~$ hp-toolbox

HP Linux Imaging and Printing System (ver. 3.9.2)
HP Device Manager ver. 15.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Traceback (most recent call last):
  File "/usr/bin/hp-toolbox", line 246, in <module>
    from ui4.devmgr5 import DevMgr5
  File "/usr/share/hplip/ui4/devmgr5.py", line 45, in <module>
    from dbus.mainloop.qt import DBusQtMainLoop
ImportError: No module named qt
andrew@Dell:~$


Do I need to re-build a module or something?

---

### Post by macogw on 2009-03-27
Probably the Python bug.Please see the sticky.

---

### Post by binbash on 2009-03-27
today's update broke mine also :

hp-toolbox 
warning: CUPSEXT could not be loaded. Please check HPLIP installation.

---

### Post by kansasnoob on 2009-03-28
I had the same problem + printing stopped working properly.

Running sudo hp-setup produced error: CUPSEXT could not be loaded. Please check HPLIP installation.

So I was thinking about filing a bug report, but wondered if I should file in Ubuntu or upstream in HPLIP.

Since Intrepid had used an older version of HPLIP (8.7 maybe - I don't have Intrepid installed to check) I'd had to download the newer version of HPLIP and use the automatic installer previously.

I'd learned from that experience that you must begin by removing hplip and hplip-gui using synaptic, but to meet dependencies for HP Device Manager I'd have to manually install:

```
sudo apt-get install &#65279;libqt4-assistant libqt4-help libqt4-svg libqt4-test libqt4-webkit libqt4-xmlpatterns python-qt3 python-qt4 python-qt4-common python-reportlab python-sip4 ttf-dustin
```

Si I thought I'd check those dependencies first. This is what I get:

> E: Couldn't find package &#65279;libqt4-assistant

Yet I can go to synaptic and &#65279;libqt4-assistant is there - and installed! All other dependencies identified properly in apt.

So, as my next step I removed hplip and hplip-gui (using "remove completely" in synaptic - same as purge remove) and then dowloaded HPLIP and used the automatic installer:

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

All works properly now! (I should note that the gui now shows up in Accessories rather than Sys > Pref)

So I think I can assume that the problem is in Ubuntu and not upstream in HPLIP. I'd just like to see if others experience the same behavior before filing the bug report.

I've not found an existing bug report specific to Jaunty.

---

### Post by kansasnoob on 2009-03-28
I'm thinking about adding my findings here:

[https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/349781](https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/349781)

I'm still a dummy when it comes to reporting bugs, in spite of reading stickies and tutorials :)

Any feedback appreciated. I don't like wasting the devs time.

Edit:

I decided to do some further testing. Specifically this is an upgrade from Intrepid that I performed during Alpha 5, so I think I should check this out on a fresh install.

Time to pop in my testing drive and do some more studying!

---

### Post by kansasnoob on 2009-03-28
Glad I waited. I have much more info (still hoping someone else might participate), anyway I've previously listed the dependencies for hplip-gui in Intrepid.

It's way different in Jaunty (I haven't parsed this down to a command yet):

> libaudio2 (1.9.1-5)
libmysqlclient15off (5.1.30really5.0.75-0ubuntu9)
libphonon4 (4:4.3.1-0ubuntu1)
libqt4-assistant (4.5.0-0ubuntu2)
libqt4-dbus (4.5.0-0ubuntu2)
libqt4-designer (4.5.0-0ubuntu2)
libqt4-help (4.5.0-0ubuntu2)
libqt4-network (4.5.0-0ubuntu2)
libqt4-opengl (4.5.0-0ubuntu2)
libqt4-qt3support (4.5.0-0ubuntu2)
libqt4-script (4.5.0-0ubuntu2)
libqt4-sql (4.5.0-0ubuntu2)
libqt4-sql-mysql (4.5.0-0ubuntu2)
libqt4-svg (4.5.0-0ubuntu2)
libqt4-test (4.5.0-0ubuntu2)
libqt4-webkit (4.5.0-0ubuntu2)
libqt4-xml (4.5.0-0ubuntu2)
libqt4-xmlpatterns (4.5.0-0ubuntu2)
libqtcore4 (4.5.0-0ubuntu2)
libqtgui4 (4.5.0-0ubuntu2)
mysql-common (5.1.30really5.0.75-0ubuntu9)
phonon (4:4.3.1-0ubuntu1)
phonon-backend-gstreamer (4:4.3.1-0ubuntu1)
python-qt4 (4.4.4-2ubuntu5)
python-qt4-common (4.4.4-2ubuntu5)
python-qt4-dbus (4.4.4-2ubuntu5)
python-renderpm (2.3-0ubuntu1)
python-reportlab (2.3-0ubuntu1)
python-reportlab-accel (2.3-0ubuntu1)
python-sip4 (4.7.9-1ubuntu1)
python2.5 (2.5.4-1ubuntu3)
python2.5-minimal (2.5.4-1ubuntu3)

Once I've created a command and tested that I'll know more! It'll get there!

---

### Post by todak on 2009-03-28
Downloading the .run file from the [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html) site and executing it removes any other instance of hplip and automatically downloads and installs any needed dependencies. Then running the hp-setup utility helps install the proper drivers for the hplip-gui. Incidentally, I was able to print without the hp-toolbox, because jaunty installed the drivers via cups during the initial installation of the OS. I did this for both Ubuntu and Kubuntu that I have installed on separate drives. I only need use the systray indicator to check the ink levels in my printer as the cups module does not do so. In my case printing was not affected at all, only the appearance of the hp-systray indicator.

---

### Post by kansasnoob on 2009-03-28
> **todak said:**
> Downloading the .run file from the [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html) site and executing it removes any other instance of hplip and automatically downloads and installs any needed dependencies. Then running the hp-setup utility helps install the proper drivers for the hplip-gui. Incidentally, I was able to print without the hp-toolbox, because jaunty installed the drivers via cups during the initial installation of the OS. I did this for both Ubuntu and Kubuntu that I have installed on separate drives. I only need use the systray indicator to check the ink levels in my printer as the cups module does not do so. In my case printing was not affected at all, only the appearance of the hp-systray indicator.

Great info! Thank you!

My goal is to be sure that end users who upgrade from Intrepid to Jaunty don't lose the use of the hplip toolbox.

Why patch if we can fix?

---

### Post by andschuster on 2009-03-29
> **todak said:**
>  Incidentally, I was able to print without the hp-toolbox, because jaunty installed the drivers via cups during the initial installation of the OS. In my case printing was not affected at all, only the appearance of the hp-systray indicator.

That seems strange: If I tried to print nothing happened and I found the message that CUPSEXT could not be loaded in /var/log/syslog.

---

### Post by Cphood on 2009-03-29
After many attempts to use the synaptic packages to install an HP Laserjet 1018 I finally met with success using the following procedures:

Clean install of Jaunty 9.04 Beta

Select and install "Python-dev" and "Python2.6-dev" from the synaptic package

Download "hplip-3.9.2.run" from [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

Install "hplip-3.9.2.run" using the instructions from the download page.

The install program and Jaunty will clean up all previous installations and select/install the required dependencies.  The last phase of the hplip installation is a plug-in download and set-up.  The program crashed on two seperate computers with me.  I closed all windows and the terminal.

Reopened terminal and ran "sudo hp-setup" and Jaunty installed the required plug-in and completed the setup.  Printer worked normal afterwards.

Printer: HP Laserjet 1018
Comp#1 Biostar MB, Athlon 2500 Barton CPU, 750MB Mem
Comp#2 Biostar MB, AMD 5000 64 x 2 CPU, 3GB Mem

Hope this can help someone.

---

### Post by Till Kamppeter on 2009-03-30
Problem is solved now. The i386 version of HPLIP 3.9.2-3ubuntu2 was corrupted because the build server has used the broken Python packages. Now I have reuploaded HPLIP so that a working 3.9.2-3ubuntu3 gets built. So in a few hours you will get an update with a working HPLIP.

Users of amd64 systems should not suffer this problem at all. The amd64 package of HPLIP 3.9.2-3ubuntu2 is OK.

If you do not want to wait for the update you can quickly solve the problem by entering the following command in a terminal window:

sudo perl -p -i -e 's/PyUnicodeUCS2/PyUnicodeUCS4/g' /usr/lib/python2.6/dist-packages/cupsext.so

---

### Post by binbash on 2009-03-30
> **Till Kamppeter said:**
> Problem is solved now. The i386 version of HPLIP 3.9.2-3ubuntu2 was corrupted because the build server has used the broken Python packages. Now I have reuploaded HPLIP so that a working 3.9.2-3ubuntu3 gets built. So in a few hours you will get an update with a working HPLIP.

Users of amd64 systems should not suffer this problem at all. The amd64 package of HPLIP 3.9.2-3ubuntu2 is OK.

If you do not want to wait for the update you can quickly solve the problem by entering the following command in a terminal window:

sudo perl -p -i -e 's/PyUnicodeUCS2/PyUnicodeUCS4/g' /usr/lib/python2.6/dist-packages/cupsext.so

Thanks for the updated package + easy fix

---

### Post by chek2fire on 2009-03-30
The new update fix the problem but now the tabs in the programme have no names!! Anyone else notice this?

edit: mistake. i just open the programme for second time and now is work! :P

---

