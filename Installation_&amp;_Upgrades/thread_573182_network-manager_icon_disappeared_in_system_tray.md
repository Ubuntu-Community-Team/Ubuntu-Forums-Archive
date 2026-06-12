---
title: "network-manager icon disappeared in system tray"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by davidyu on 2007-10-11
For unknown reason,  my network-manager icon was disappeared from the system tray.
I go to \system\preference\session try to take it back to the system tray, but not working.
How can I put network-manager icon back to the system tray.

---

### Post by cmnorton on 2007-10-11
Check your logs

sudo tail /var/log/syslog
sudo tail /var/log/messages

Which version of Ubuntu?

---

### Post by davidyu on 2007-10-11
My version is Ubuntu 7.10 Beta

---

### Post by cmnorton on 2007-10-12
Today the release candidate was announced. I'd upgrade to the officially released Gutsy, when it is announced.

---

### Post by fuhrysteve on 2007-10-15
Looks like something weird in one of the later updates for Gutsy. Anyways, I fixed it on a friend's IBM Thinkpad T41 Laptop running 7.10.

Go to System => Preferences => Sessions

Look under the Startup Programs tab.  If "Network Manager" is not already there, click Add and put this stuff in:

Name: Network Manager
Command: nm-applet --sm-disable
Comment: Network Manager applet

Then press Alt-F2 and run 
nm-applet --sm-disable
to get it running in this session.

Hopefully the next update for the Network Manager will check to see that someone added that manually before adding another Startup entry, because if they don't, you might end up with two Network Managers running in your System Tray. If that happens, just delete one of them from the Startup menu under Sessions.

---

