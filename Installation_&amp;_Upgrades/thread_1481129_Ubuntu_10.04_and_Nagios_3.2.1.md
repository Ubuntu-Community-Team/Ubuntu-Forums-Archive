---
title: "Ubuntu 10.04 and Nagios 3.2.1"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by mab1376 on 2010-05-12
The e-mail notifications don't seem to be working, I found a tutorial which said I should install the package "mailx" which has 3 candidates and I don't know which one to use.

[http://www.ubuntugeek.com/nagios-network-monitoring-system-setup-in-ubuntu.html](http://www.ubuntugeek.com/nagios-network-monitoring-system-setup-in-ubuntu.html) 

```
sudo apt-get install mailx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mailx is a virtual package provided by:
  mailutils 1:2.1+dfsg1-4ubuntu1
  heirloom-mailx 12.4-1.1
  bsd-mailx 8.1.2-0.20090911cvs-2ubuntu1
You should explicitly select one to install.
E: Package mailx has no installation candidate
```

I tried the first package, "mailutils" and still it's not working.

This is the command that is supposed to send out the email.

```
# 'host-notify-by-email' command definition
define command{
	command_name	host-notify-by-email
	command_line	/usr/bin/printf "%b" "***** Nagios  *****\n\nNotification Type: $NOTIFICATIONTYPE$\nHost: $HOSTNAME$\nState: $HOSTSTATE$\nAddress: $HOSTADDRESS$\nInfo: $HOSTOUTPUT$\n\nDate/Time: $LONGDATETIME$\n" | /usr/bin/mailx -s "Host $HOSTSTATE$ alert for $HOSTNAME$!" $CONTACTEMAIL$
	}
```

---

### Post by lemming465 on 2010-05-14
You probably need an MTA and an MUA.  Typical transmission agents are postfix, sendmail, or exim4.  Typical command line compatibility user agents would be something like bsd-mailx.

---

### Post by mab1376 on 2010-05-16
I have sendmail and heirloom-mailx installed but nagios does not send the notifications, even though I can send mail to myself from the command line.

---

### Post by lemming465 on 2010-05-16
If you have sendmail installed, is there any reason to not use *|sendmail -t* as your submission mechanism?  You just have to make the first few lines be To: Subject: and a blank line before the message body.

---

### Post by mab1376 on 2010-05-17
the message formatting is handled by nagios completely using variables which is gets from the application.

```

define command{
	command_name	host-notify-by-email
	command_line	/usr/bin/printf "%b" "***** Nagios  *****\n\nNotification Type: $NOTIFICATIONTYPE$\nHost: $HOSTNAME$\nState: $HOSTSTATE$\nAddress: $HOSTADDRESS$\nInfo: $HOSTOUTPUT$\n\nDate/Time: $LONGDATETIME$\n" | /usr/bin/mailx -s "Host $HOSTSTATE$ alert for $HOSTNAME$!" $CONTACTEMAIL$
	}

```

---

### Post by chubuntu on 2010-06-01
We had previously compiled nagios and ran it on 8.04 LTS.  After upgrading to 10.04 LTS, mail notifications stopped working.

Installed the bsd-mailx and everything is fine.

---

