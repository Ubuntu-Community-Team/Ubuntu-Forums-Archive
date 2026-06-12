---
title: "/var/log/messages empty"
date: 2012-05-13
forum: Installation &amp; Upgrades
---

### Post by owise1 on 2012-05-13
Did a multiple upgrade 10.10 to 12.04 and PC runs well except for slow startup due to sda1 being checked at each boot.  On shutdown noticed a couple of messages fly past but too quick to read before the shutdown splash appears.

Looked in /var/log/messages but found it empty.  There is text in /var/log/messages.1 which looks to be pre update to 12.04.

Has the way messages are logged changed in 12.04?  I have looked in /var/log/kern.log but nothing in there either.

any suggestions

Dave

The log file must have been rotated as there was current data in kern.log.1 but there was nothing to help with the shutdown messages in there...damm

---

### Post by dino99 on 2012-05-13
sudo dpkg-reconfigure rsyslog

(need to be already installed of course)

sudo apt-get install -f

---

