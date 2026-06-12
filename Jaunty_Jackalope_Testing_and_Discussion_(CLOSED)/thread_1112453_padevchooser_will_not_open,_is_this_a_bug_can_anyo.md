---
title: "padevchooser will not open, is this a bug can anyone confirm"
date: 2009-03-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-03-31
Before I report the bug.

Tried running in a terminal and it just hangs no errors.

---

### Post by tghe-retford on 2009-03-31
Yep, hangs on my system from the command line as well.

---

### Post by philinux on 2009-03-31
Well I'm wrong. It puts an icon in the notification area. Totally missed that.

---

### Post by knarf on 2009-03-31
This most likely is caused by the absence of a running avahi daemon. Either try to run ```
sudo /etc/init.d/avahi-daemon restart
``` in a terminal and watch what happens. If it prints 
> * Restarting Avahi mDNS/DNS-SD Daemon avahi-daemon
* avahi-daemon disabled because there is a unicast .local domain something in your network, from your router to your ISP, responds to DNS requests for 'local' causing avahi to abort on startup. Another way of checking for this problem is by looking for the presence of a file named > /var/run/avahi-daemon/disabled-for-unicast-localIf either of these checks return a positive result you can switch off this check by editing avahi's default file using eg. ```
sudo $VISUAL /etc/default/avahi-daemon
``` and changing the default option of > AVAHI_DAEMON_DETECT_LOCAL=1 to > AVAHI_DAEMON_DETECT_LOCAL=0 Finally run ```
sudo rm /var/run/avahi-daemon/disabled-for-unicast-local
sudo /etc/init.d/avahi-daemon restart
``` to get avahi running again. If avahi was the cause of padevchooser not running it should now run again as it used to...

This is a known problem by the way, a simple $search_engine search would have pointed you in this direction... There is even a LP bug ([https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/327362](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/327362))

---

