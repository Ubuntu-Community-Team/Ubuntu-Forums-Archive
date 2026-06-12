---
title: "Lost /etc/syslog.conf Please help"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by manolo on 2007-12-10
I have just installed Ubuntu 7.1
Accidentally I have deleted file /etc/syslog.conf.
Would someone, please, post the file contents here?

Many thanks in advance,
Manolo.

---

### Post by ruibernardo on 2007-12-10
Hi manolo,

I changed mine, so I can't post the original one. 

If you used the Desktop CD to install, boot it and copy that one there to your hard disk.

After booting the Desktop CD, click on the main menu in Places > Computer and double click the root ubuntu partition. That partition should be mounted as /media/disk (confirm it). 

Open a terminal (Applications > Accessories > Terminal) and type:
```
sudo cp /etc/sysctl.conf /media/disk/etc/sysctl.conf
```Or maybe someone will post it.

---

### Post by Rocket2DMn on 2007-12-11
Here is mine, I haven't changed it.  There are no guarantees that it will work for you - use at your own risk.  Otherwise, do the LiveCD option that epimeteo suggested.

```
#  /etc/syslog.conf     Configuration file for syslogd.
#
#                       For more information see syslog.conf(5)
#                       manpage.

#
# First some standard logfiles.  Log by facility.
#

auth,authpriv.*                 /var/log/auth.log
*.*;auth,authpriv.none          -/var/log/syslog
#cron.*                         /var/log/cron.log
daemon.*                        -/var/log/daemon.log
kern.*                          -/var/log/kern.log
lpr.*                           -/var/log/lpr.log
mail.*                          -/var/log/mail.log
user.*                          -/var/log/user.log

#
# Logging for the mail system.  Split it up so that
# it is easy to write scripts to parse these files.
#
mail.info                       -/var/log/mail.info
mail.warn                       -/var/log/mail.warn
mail.err                        /var/log/mail.err

# Logging for INN news system
#
news.crit                       /var/log/news/news.crit
news.err                        /var/log/news/news.err
news.notice                     -/var/log/news/news.notice

#
# Some `catch-all' logfiles.
#
*.=debug;\
        auth,authpriv.none;\
        news.none;mail.none     -/var/log/debug
*.=info;*.=notice;*.=warn;\
        auth,authpriv.none;\
        cron,daemon.none;\
        mail,news.none          -/var/log/messages

#
# Emergencies are sent to everybody logged in.
#
*.emerg                         *

#
# I like to have messages displayed on the console, but only on a virtual
# console I usually leave idle.
#
#daemon,mail.*;\
#       news.=crit;news.=err;news.=notice;\
#       *.=debug;*.=info;\
#       *.=notice;*.=warn       /dev/tty8

# The named pipe /dev/xconsole is for the `xconsole' utility.  To use it,
# you must invoke `xconsole' with the `-file' option:
# 
#    $ xconsole -file /dev/xconsole [...]
#
# NOTE: adjust the list below, or you'll go crazy if you have a reasonably
#      busy site..
#
daemon.*;mail.*;\
        news.err;\
        *.=debug;*.=info;\
        *.=notice;*.=warn       |/dev/xconsole
```

---

### Post by manolo on 2007-12-11
I have used Rocket2DMn's copy and it seems to work all right.
Thank you very much epimeteo and Rocket2DMn!
Manolo.

---

