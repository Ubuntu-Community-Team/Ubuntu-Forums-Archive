---
title: "'sudo dpkg --configure -a' freezes and does nothing for a long time"
date: 2010-09-21
forum: Installation &amp; Upgrades
---

### Post by svetiev on 2010-09-21
Hi,

I'm trying to fix a friends EeePC notebook (Asus) running a recently upgraded Ubuntu 10.04 from Karmic Koala. She used the update manager for the upgrade to 10.04 LTS and everything was fine until she had tried to install something from the Ubuntu Software Center (she doesn't remember what happened). After that, both Update manager and Synaptic stopped working.


Update manager gives the following error:

> Software index is broken. ... Try to use synaptic for something?!...Then Synaptic manager gives the following error:

> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.And when I try that command, the terminal just keeps blinking with the cursor and does nothing for more than an hour. This is the output of the comand:

> jasna@Jasna:~$ sudo dpkg --configure -a
[sudo] password for jasna:
Setting up moodle (1.9.4.dfsg-0ubuntu4) ...I'm not a noob, but I don't know to much either, I've been using ubuntu for more than a year now and learned a few things from reading the forums. I found several similar threads about this issue but wasn't able to fix this problem with the suggestions in those threads, so I hope someone can help me with this thing.

Boris

---

### Post by gnush on 2010-09-21
```

dpkg -D1 --configure -a

```What does that command say? You could try some of the options listed below.

> dpkg debugging option, --debug=<octal> or -D<octal>:

 number  ref. in source   description
      1   general           Generally helpful progress information
      2   scripts           Invocation and status of maintainer scripts
     10   eachfile          Output for each file processed
    100   eachfiledetail    Lots of output for each file processed
     20   conff             Output for each configuration file
    200   conffdetail       Lots of output for each configuration file
     40   depcon            Dependencies and conflicts
    400   depcondetail      Lots of dependencies/conflicts output
  10000   triggers          Trigger activation and processing
  20000   triggersdetail    Lots of output regarding triggers
  40000   triggersstupid    Silly amounts of output regarding triggers
   1000   veryverbose       Lots of drivel about eg the dpkg/info directory
   2000   stupidlyverbose   Insane amounts of drivel


---

### Post by svetiev on 2010-09-21
Hi Gnush thanks for aswering.

Here is the output from the last option:

> jasna@Jasna:~$ sudo dpkg -D2000 --configure -a
[sudo] password for jasna: 
Setting up moodle (1.9.4.dfsg-0ubuntu4) ...
^Cdpkg: error processing moodle (--configure):
 subprocess installed post-installation script killed by signal (Interrupt)
Setting up edubuntu-desktop-kde (1.80) ...
Setting up konqueror-nsplugins (4:4.4.2-0ubuntu2) ...
Setting up kubuntu-docs (10.04.3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Setting up kubuntu-firefox-installer (10.04ubuntu8) ...
Setting up libkipi7 (4:4.4.2-0ubuntu1) ...

Setting up ktimetracker (4:4.4.2-0ubuntu5) ...
Setting up gnugo (3.8-3) ...
Ignoring install-info called from maintainer script
The package gnugo should be rebuilt with new debhelper to get trigger support

Setting up k3b-data (1.91.0~rc2-0ubuntu3) ...

Setting up plymouth-theme-kubuntu-logo (1:10.04ubuntu23.2) ...
update-alternatives: using /lib/plymouth/themes/kubuntu-logo/kubuntu-logo.plymouth to provide /lib/plymouth/themes/default.plymouth (default.plymouth) in auto mode.
update-initramfs: deferring update (trigger activated)

Setting up kwalletmanager (4:4.4.2-0ubuntu1) ...
Setting up ldm (2:2.1.1-0ubuntu2) ...
update-alternatives: using /usr/share/ldm/themes/ltsp to provide /usr/share/ldm/themes/default (ldm-theme) in auto mode.

Setting up oxygen-cursor-theme (0.0.2008-07-07-svn824849-1ubuntu2) ...
update-alternatives: using /etc/X11/cursors/oxy-white.theme to provide /usr/share/icons/default/index.theme (x-cursor-theme) in auto mode.

Setting up openoffice.org-kde (1:3.2.0-7ubuntu4.1) ...

Setting up kubuntu-notification-helper (10.04ubuntu4) ...
Setting up php5-ldap (5.3.2-1ubuntu4.2) ...
Setting up quassel-data (0.6.1-0ubuntu1) ...
Setting up libksieve4 (4:4.4.2-0ubuntu5) ...

Setting up freespacenotifier (0.0svn1061317-0ubuntu1) ...
Setting up konqueror (4:4.4.2-0ubuntu2) ...

Setting up gnupg-agent (2.0.14-1ubuntu1) ...
Setting up k3b (1.91.0~rc2-0ubuntu3) ...

Setting up printer-applet (4:4.4.2-0ubuntu1) ...
Setting up libibus-qt1 (1.2.0.20091217-1) ...

Setting up ldm-edubuntu-theme (2:2.0.41) ...
update-alternatives: using /usr/share/ldm/themes/edubuntu to provide /usr/share/ldm/themes/default (ldm-theme) in auto mode.

Setting up gwenview (4:4.4.2-0ubuntu1) ...

dpkg: dependency problems prevent configuration of edubuntu-server:
 edubuntu-server depends on moodle; however:
  Package moodle is not configured yet.
dpkg: error processing edubuntu-server (--configure):
 dependency problems - leaving unconfigured
Setting up kmail (4:4.4.2-0ubuntu5) ...

Setting up ibus-qt4 (1.2.0.20091217-1) ...
Setting up kubuntu-konqueror-shortcuts (10.04ubuntu1) ...
Setting up quassel (0.6.1-0ubuntu1) ...
Setting up plasma-widget-kimpanel-backend-ibus (4:4.4.2-0ubuntu2) ...

Setting up plasma-widget-kimpanel (4:4.4.2-0ubuntu2) ...

Setting up libkopete4 (4:4.4.2-0ubuntu4.1) ...

Setting up kopete-message-indicator (0.2.0-0ubuntu1) ...
Setting up kopete (4:4.4.2-0ubuntu4.1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-23-generic
Errors were encountered while processing:
 moodle
 edubuntu-server

Any idea on how to fix this "moodle" thing? :D

---

### Post by gnush on 2010-09-21
```

moodle --configure
[I]If the above command doesn't work, is moodle installed?
[/I]
locate -i moodle

```

If that doesn't work, try to install moodle. It seems dpkg is trying to configure edubuntu-server which has a dependency (moodle) that doesn't exist.

---

### Post by svetiev on 2010-09-21
> jasna@Jasna:~$ moodle --configure
No command 'moodle' found, did you mean:
 Command 'doodle' from package 'doodle' (universe)
moodle: command not found

And the command 'locate -i moodle' spewed out a bunch of directories of which the last ones were:

> /var/lib/moodle
/var/lib/dpkg/info/moodle.conffiles
/var/lib/dpkg/info/moodle.config
/var/lib/dpkg/info/moodle.list
/var/lib/dpkg/info/moodle.md5sums
/var/lib/dpkg/info/moodle.postinst
/var/lib/dpkg/info/moodle.postrm
/var/lib/dpkg/info/moodle.templates


So do I or don't I have moodle installed?!

In the mean time I found this bug report:

[https://bugs.launchpad.net/ubuntu/+source/moodle/+bug/488591](https://bugs.launchpad.net/ubuntu/+source/moodle/+bug/488591)

Should I try what is suggested over there?

---

### Post by gnush on 2010-09-21
> **svetiev said:**
> So do I or don't I have moodle installed?!

In the mean time I found this bug report:

[https://bugs.launchpad.net/ubuntu/+source/moodle/+bug/488591](https://bugs.launchpad.net/ubuntu/+source/moodle/+bug/488591)

Should I try what is suggested over there?

I actually don't know, there seems to be traces of it at least.
Yeah, go ahead and try. It sounds like it'd be enough to install moodle though, but I don't know.
You choose. ^_^

---

### Post by gnush on 2010-09-21
By the way, how about trying the force option?

```
dpkg --force --configure -a
```

---

### Post by svetiev on 2010-09-21
Damn, it seems to be a catch 22 :D

What ever I try (install or reinstall moodle or that php5 something package from the bug report) it always hangs on configuring the moodle :(

This moodle is putting me in a bad mood :D

However something must have happened in the mean time cause now even 'sudo dpkg -D2000 --configure -a' doesn't return anything like it used to in one of my earlier replies. 

I have some things to do in the next two hours. When i come back I'll continue to work on this problem.

In the mean time any suggestions are wellcome :)

---

### Post by svetiev on 2010-09-21
This is the latest state of things:

> jasna@Jasna:~$ sudo apt-get install moodle
Reading package lists... Done
Building dependency tree       
Reading state information... Done
moodle is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-22 linux-headers-2.6.32-22-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 138 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up moodle (1.9.4.dfsg-0ubuntu4) ...



---

### Post by svetiev on 2010-09-21
Ok the problem seems to be i the instalation of this "moodle" package (Course management system for online learning) so it's Nothing Important. But, the installation was probably interrupted midway through and now DPKG can not finish without resolving this installation which seems to be broken.

Is there any way that I can reverse the damage done by this broken installation? 

Can I manually remove it from the system so it doesn't pose a problem?

---

### Post by svetiev on 2010-09-21
> **svetiev said:**
> Ok the problem seems to be i the instalation of this "moodle" package (Course management system for online learning) so it's Nothing Important. But, the installation was probably interrupted midway through and now DPKG can not finish without resolving this installation which seems to be broken.

Is there any way that I can reverse the damage done by this broken installation? 

Can I manually remove it from the system so it doesn't pose a problem?

When you ask the right question the answer is self evident: 

```
sudo apt-get --purge remove moodle
```

This command removed the broken package and all of it's corrupt files and everything is back to normal. 

I express a great THANK YOU to GNUSH for helping me and ultimately guiding me to the solution of this problem and I therefore pronounce this case SOLVED :)

---

### Post by girishlc on 2010-10-07
Hey guys,
 
For me this problem is still exists,
 
I wanted to enable the ssh in a newly installed Ubuntu m/c,
Here below are the steps and error which I got while installing,
 
1. sudo apt-get install openssh-server
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem
 
2. sudo dpkg --configure -a 
E: Runs for long time and does nothing
As gnush suggested I used command 
3. sudo dpkg -D2000 --configure -a
but same result  (hanging, does nothing for long time; I killed this process) :(
 
4. sudo apt-get install moodle
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem
 
*I'm not getting moodle error
Please suggest me some other solution,
 
 
-Thanks,
Girish.L.C

---

