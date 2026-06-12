---
title: "synaptic / ubuntu software centre"
date: 2013-06-13
forum: Installation &amp; Upgrades
---

### Post by christon74 on 2013-06-13
Hello everybody

synaptic simply does not launch any longer. I have not got any idea why. And it has now become impossible to remove any software I no longer need (like audacity)
Normally, after clicking on 'remove' ubuntu would ask for my password.... Well not anymore....

what the hell is going on?

---

### Post by matt_symes on 2013-06-13
Hi

Open a terminal and type
```

software-center
```

You should then get some debugging output to the terminal window.

Copy and paste the output from the terminal window into your next post between code tags.

Kind regards

---

### Post by christon74 on 2013-06-13
```
christophe@christophe-TPS01:~$ software-center
2013-06-13 18:16:52,341 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-06-13 18:16:52,462 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2013-06-13 18:16:55,851 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-06-13 18:16:57,166 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2013-06-13 18:16:57,190 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2013-06-13 18:17:32,988 - softwarecenter.db.update - INFO - skipping region restricted app: 'Bulleti d'esquerra de Calonge i Sant Antoni ' (not whitelisted)
2013-06-13 18:17:34,591 - softwarecenter.db.update - INFO - skipping region restricted app: 'Comentarios Web' (not whitelisted)
2013-06-13 18:17:56,964 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 0
2013-06-13 18:17:57,009 - softwarecenter.db.database - INFO - reopen() database
2013-06-13 18:17:57,019 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
```

---

### Post by christon74 on 2013-06-13
Ha! I have just successfully removed audacity and wine using 'apt-get remove'

---

### Post by matt_symes on 2013-06-13
Hi

No traceback reported from running software-center.

```
sudo apt-get install --reinstall software-center
```

Try reinstalling it from the command line and if that does not fix it, try renaming your cache to a different name.

```
mv ~/.cache/software-center{,.old}
```

After both the above commands, restart software-center and see if it works.

Kind regards

---

### Post by christon74 on 2013-06-13
Daesnae work at all.
sudo apt-get install --reinstall software-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of software-center is not possible, it cannot be downloaded.
The following packages were automatically installed and are no longer required:
  ttf-umefont libcapi20-3 libgettextpo0 unixodbc gettext ufraw-batch
  wine-gecko1.4 libunistring0 libmpg123-0 libodbc1 fonts-droid ttf-droid
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

root@christophe-TPS01:/home/christophe# mv ~/.cache/software-center{,.old}
mv: cannot stat `/root/.cache/software-center': No such file or directory
root@christophe-TPS01:/home/christophe#

---

### Post by matt_symes on 2013-06-13
Hi

> **christon74 said:**
> ```
Daesnae work at all.
sudo apt-get install --reinstall software-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of software-center is not possible, it cannot be downloaded.
The following packages were automatically installed and are no longer required:
  ttf-umefont libcapi20-3 libgettextpo0 unixodbc gettext ufraw-batch
  wine-gecko1.4 libunistring0 libmpg123-0 libodbc1 fonts-droid ttf-droid
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Are you connected to the Internet on that machine ?

> ```

root@christophe-TPS01:/home/christophe# mv ~/.cache/software-center{,.old}
mv: cannot stat `/root/.cache/software-center': No such file or directory
root@christophe-TPS01:/home/christophe#
```

You're running under root ? I wanted you to run that command under you own user.

```
matthew-S206:/home/matthew % ls -ld ~/.cache/software-center && echo $USER
drwxrwxr-x 8 matthew matthew 4096 Jun 13 18:20 /home/matthew/.cache/software-center/
matthew
matthew-S206:/home/matthew %
```

Kind regards

---

### Post by christon74 on 2013-06-13
Hello Matt :)

Well yes I am connected to the internet!!!! how else could I post the results of the terminal??? uh?

---

### Post by christon74 on 2013-06-13
This very moment I am listening to BBC Radio scotland (Get it on with Bryan Burnett)
Vic GALLOWAY is standing in for him til the end of the week and the theme is 'strings'
:D
christophe@christophe-TPS01:~$ sudo apt-get install --reinstall software-center
[sudo] password for christophe: 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of software-center is not possible, it cannot be downloaded.
The following packages were automatically installed and are no longer required:
  ttf-umefont libcapi20-3 libgettextpo0 unixodbc gettext ufraw-batch
  wine-gecko1.4 libunistring0 libmpg123-0 libodbc1 fonts-droid ttf-droid
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by matt_symes on 2013-06-13
Hi

I thought i'd better ask about the Internet connection; you never know. :)

Can you post the output of these commands...

```

cat /etc/lsb-release
echo $DESKTOP_SESSION
grep "^[^#]" /etc/apt/sources.list{,.d/*} 
dpkg -l software-center
```

Linux is case sensitive so uppercase where i have written it above.

Kind regards

---

### Post by christon74 on 2013-06-14
Hello again Matt:D

Here is the result:
christophe@christophe-TPS01:~$ sudo su
[sudo] password for christophe: 
root@christophe-TPS01:/home/christophe# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
root@christophe-TPS01:/home/christophe# echo $DESKTOP_SESSION

root@christophe-TPS01:/home/christophe# grep "^[^#]" /etc/apt/sources.list{,.d/*} 
/etc/apt/sources.list:deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) precise main restricted
/etc/apt/sources.list:deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) precise main restricted
/etc/apt/sources.list:deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) precise universe
/etc/apt/sources.list:deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) precise universe
/etc/apt/sources.list:deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) precise multiverse
/etc/apt/sources.list:deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) precise multiverse
/etc/apt/sources.list:deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
/etc/apt/sources.list:deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
/etc/apt/sources.list:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
/etc/apt/sources.list:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
/etc/apt/sources.list:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
/etc/apt/sources.list:deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
/etc/apt/sources.list:deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
/etc/apt/sources.list.d/precise-partner.list:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner #Added by software-center
/etc/apt/sources.list.d/precise-partner.list.save:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner #Added by software-center
/etc/apt/sources.list.d/webupd8team-java-precise.list:deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) precise main
/etc/apt/sources.list.d/webupd8team-java-precise.list:deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) precise main
/etc/apt/sources.list.d/webupd8team-java-precise.list.save:deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) precise main
/etc/apt/sources.list.d/webupd8team-java-precise.list.save:deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) precise main
root@christophe-TPS01:/home/christophe# dpkg -l software-center

Many thanks for your help and patience;-)

---

### Post by christon74 on 2013-06-14
uh oh; here is something even worse! updates no longer install. I can click 'install updates' til I am blue in the face.... nothing happens

---

### Post by christon74 on 2013-06-14
uh oh, problems with update/upgrade

Task cannot be monitored or controlled

The connection to the daemon was lost. The background daemon probably crashed.

---

### Post by matt_symes on 2013-06-14
Hi

Not only do you have those problems, but you have no desktop session environmental variable set and software-center is not installed according to dpkg.

I would start with hardware checks from a LiveCD/USB.

Run a long SMART test and a memory test to start with.

How old is the machine/ the parts inside the machine ?

KInd regards

---

### Post by christon74 on 2013-06-14
christophe@christophe-TPS01:~$ sudo su
[sudo] password for christophe: 
root@christophe-TPS01:/home/christophe# 
root@christophe-TPS01:/home/christophe# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
root@christophe-TPS01:/home/christophe# echo $DESKTOP_SESSION

root@christophe-TPS01:/home/christophe# grep "^[^#]" /etc/apt/sources.list{,.d/*} 
/etc/apt/sources.list:deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) precise main restricted
/etc/apt/sources.list:deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) precise main restricted
/etc/apt/sources.list:deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) precise universe
/etc/apt/sources.list:deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) precise universe
/etc/apt/sources.list:deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) precise multiverse
/etc/apt/sources.list:deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) precise multiverse
/etc/apt/sources.list:deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
/etc/apt/sources.list:deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
/etc/apt/sources.list:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
/etc/apt/sources.list:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
/etc/apt/sources.list:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
/etc/apt/sources.list:deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
/etc/apt/sources.list:deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
/etc/apt/sources.list.d/precise-partner.list:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner #Added by software-center
/etc/apt/sources.list.d/precise-partner.list.save:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner #Added by software-center
/etc/apt/sources.list.d/webupd8team-java-precise.list:deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) precise main
/etc/apt/sources.list.d/webupd8team-java-precise.list:deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) precise main
/etc/apt/sources.list.d/webupd8team-java-precise.list.save:deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) precise main
/etc/apt/sources.list.d/webupd8team-java-precise.list.save:deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) precise main
root@christophe-TPS01:/home/christophe# dpkg -l software-center

---

### Post by christon74 on 2013-06-14
Hello again Matt. The machine I bought from Amazon approximately a year ago. Processor intel_ Motherboard Foxconn (Yes, I know.... )
What I have just done is updating the kernel from the terminal.
Could you please explain what exactly is a LiveCD ? Is it the Ubuntu install CD? 
Thanks ;)

---

### Post by matt_symes on 2013-06-14
Hi

Yes, A ubuntu LiveCD is a Ubuntu install CD, but you don't select the install option (select the try Ubuntu option).

From there you can run various tests on the machine.

However, that is new to be suffering from hardware faults, although this is not impossible.

Whst do these two commands return ?
```

dpkg -C
```
Capitals where i use them as Linux is case sensitive.

```
dpkg -S * 
```

No need to post the output of the second command. I'm just interested in if you get a lot of scrolling text.

KInd regards

---

### Post by christon74 on 2013-06-14
Ouch! I thought it would never end LOL :lolflag: I am not sure you will read this in its entirety, but if you do, then 'bon courage' as we say in French

linux-headers-3.2.0-26: /usr/src/linux-headers-3.2.0-26/include/linux/unaligned/be_struct.h
linux-headers-3.2.0-44-generic-pae: /usr/src/linux-headers-3.2.0-44-generic-pae/include/config/snd/hda/hwdep.h
linux-headers-3.2.0-36: /usr/src/linux-headers-3.2.0-36/arch/mips/include/asm/dec/ioasic_addrs.h
linux-headers-3.2.0-43: /usr/src/linux-headers-3.2.0-43/arch/um/include/asm/fixmap.h
libgarcon-common: /usr/share/locale/ku/LC_MESSAGES/garcon.mo
linux-headers-3.2.0-20-generic-pae: /usr/src/linux-headers-3.2.0-20-generic-pae/include/linux/llc.h
linux-headers-3.2.0-40: /usr/src/linux-headers-3.2.0-40/drivers/net/ethernet/neterion/vxge/Makefile
linux-headers-3.2.0-41: /usr/src/linux-headers-3.2.0-41/include/linux/ip_vs.h
linux-headers-3.2.0-39: /usr/src/linux-headers-3.2.0-39/arch/ia64/include/asm/sn/pda.h
brltty: /usr/share/doc/brltty/French/BRLTTY-7.html
libbonobo2-0: /usr/lib/i386-linux-gnu/bonobo-activation/bonobo-activation-server
linux-headers-3.2.0-48-generic-pae: /usr/src/linux-headers-3.2.0-48-generic-pae/include/config/ad7291.h
linux-headers-3.2.0-40-generic-pae: /usr/src/linux-headers-3.2.0-40-generic-pae/include/config/ir/rc5/sz
linux-headers-3.2.0-29: /usr/src/linux-headers-3.2.0-29/include/sound/wm8904.h
linux-headers-3.2.0-31: /usr/src/linux-headers-3.2.0-31/include/net/netfilter/nf_queue.h
humanity-icon-theme: /usr/share/icons/Humanity-Dark/status/16/gpm-battery-000-charging.svg
linux-headers-3.2.0-41: /usr/src/linux-headers-3.2.0-41/arch/m32r/include/asm/termbits.h
linux-headers-3.2.0-31: /usr/src/linux-headers-3.2.0-31/arch/arm/mach-iop32x/include/mach/iop32x.h
linux-headers-3.2.0-31: /usr/src/linux-headers-3.2.0-31/arch/m68k/include/asm/spinlock.h
libgtk2.0-common: /usr/share/doc/libgtk2.0-common
python2.7: /usr/lib/python2.7/xml/dom/NodeFilter.py
linux-headers-3.2.0-48: /usr/src/linux-headers-3.2.0-48/arch/arm/mach-sa1100/include/mach/debug-macro.S
linux-headers-3.2.0-32-generic-pae: /usr/src/linux-headers-3.2.0-32-generic-pae/include/config/pata/efar.h
linux-headers-3.2.0-40: /usr/src/linux-headers-3.2.0-40/sound/isa/cs423x
linux-headers-3.2.0-27: /usr/src/linux-headers-3.2.0-27/arch/arm/mach-s3c2410/include (....)

Yes yes yes, I get a whole pack of lines......

---

### Post by christon74 on 2013-06-14
christophe@christophe-TPS01:~$ sudo su
[sudo] password for christophe: 
root@christophe-TPS01:/home/christophe# dpkg -C
root@christophe-TPS01:/home/christophe#

---

### Post by christon74 on 2013-06-14
Hey Matt, I have a silly question:D How safe is it to use a LiveCD?  what if I insert the CD and it does not let me chose any option but immediately starts running the install? :eek:

---

### Post by christon74 on 2013-06-14
Hello again Matt :) 
If I open a terminal and type 'sudo synaptic' or 'gksu /usr/sbin/synaptic' then it launches the synaptic.But if I click the icon on the left panel, nothing happens.

---

### Post by christon74 on 2013-06-14
Hello again Matt :) 
If I open a terminal and type 'sudo synaptic' or 'gksu /usr/sbin/synaptic' then it launches the synaptic.But if I click the icon on the left panel, nothing happens.

---

### Post by christon74 on 2013-06-14
I have found this somewhere on the ubuntu forums:
Try resetting the Synaptic command in your system menu by going to  System > Preferences > Main Menu > Administration, right-click  on Synaptic Package Manager and click Revert to Original.

---

### Post by matt_symes on 2013-06-15
Hi

> **christon74 said:**
> I have found this somewhere on the ubuntu forums:
Try resetting the Synaptic command in your system menu by going to  System > Preferences > Main Menu > Administration, right-click  on Synaptic Package Manager and click Revert to Original.

Did this work ?

Kind regards

---

### Post by christon74 on 2013-06-15
Hello again Matt:D
No, it does not work for me. I have tried up to 7 times but then it opens back-up and you have to chose a restore date _ which I have tried, obviously_ then after a while I get the message that 'backup' cannot find the file to restore.:frown:
Anyway, I can still launch synaptic from the terminal ;)

---

### Post by matt_symes on 2013-06-15
Hi

> **christon74 said:**
> I have found this somewhere on the ubuntu forums:
Try resetting the Synaptic command in your system menu by going to  System > Preferences > Main Menu > Administration, right-click  on Synaptic Package Manager and click Revert to Original.

It may just be the .desktop shortcut is broken then.

What do  these two commands return ?

```
cat /usr/share/applications/synaptic.desktop
```

```
which synaptic
```

Kind regards

---

