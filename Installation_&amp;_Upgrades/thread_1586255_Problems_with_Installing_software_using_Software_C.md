---
title: "Problems with Installing software using Software Center"
date: 2010-10-01
forum: Installation &amp; Upgrades
---

### Post by vanchope on 2010-10-01
Hello!

I use Ubuntu already a quite long time, more than 1 year probably. At the moment I have installed Ubuntu 10.04 on  VirtualBox 3.2.8 (Windows 7 is host OS).

Everything works fine for me, but now I have strange problem with installing soft using Software Center. 

When I click some software to be installed, nothing happens...

I checked /var/log/syslog file and found following lines:


> Oct  2 00:00:10 ivan-laptop-ub AptDaemon: INFO: InstallPackages() was called: dbus.Array([dbus.String(u'texworks')], signature=dbus.Signature('s'))
Oct  2 00:01:30 ivan-laptop-ub AptDaemon: INFO: Quiting due to inactivity
Oct  2 00:01:30 ivan-laptop-ub AptDaemon: INFO: Shutdown was requested
Oct  2 00:01:30 ivan-laptop-ub AptDaemon: INFO: Initializing daemon


I searched a bit, but didn't find relevant links. Maybe I missed it... If someone has any idea about what's this issue, please share your opinion. Thanks in advance.

Ivan.

P.S. Btw, sudo apt-get install xxx works fine for me.

---

### Post by mörgæs on 2010-10-02
I have never understood the idea behind Software Centre, and there are quite a few bugs in it. Just stick to Synaptic.

---

### Post by vanchope on 2010-10-13
Today I upgraded my ubuntu to the lastest 10.10 version.
Last release looks very nice, especially new fonts :popcorn:

And now I checked Update Manager... Some updates can not be inslatted... When I click "Install Updates", button becomes disabled, and after few seconds of "thinking" becomes again enabled. Nothing installed.. :confused:

/var/log/syslog

> Oct 13 18:31:05 ivan-laptop-ub AptDaemon: INFO: Initializing daemon
Oct 13 18:31:05 ivan-laptop-ub AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String(u'libboost-program-options1.42.0')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s'))


---

### Post by vanchope on 2010-10-15
It seems, I fixed currently the issue, by using 

> sudo apt-get dist-upgrade

and then I installed package, which was marked as 'being kept', even after dist-upgrade.

Let's wait for other updates...

---

### Post by vanchope on 2010-10-18
Well, new updates cannot be installed using Update Manager (!).
It's possible only using command line. 
> sudo apt-get update
sudo apt-get upgrade

Does anyone has similar problems?

---

