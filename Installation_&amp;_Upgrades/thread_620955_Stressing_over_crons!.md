---
title: "Stressing over crons!"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by twill30 on 2007-11-23
I've just set up and configured a remote server running 6.06 LTS and now am establishing a daily/weekly workflow to stay on top of security checks etc.

I haven't used Ubuntu before so would appreciate some advice on running cron scripts.

The things I would like to have emailed to me daily are:

Log watch report
Tripwire report
RKHunter report

Nothing else.

At the moment, after a default install, I have (excuse long list):

cron.daily:

.placeholder
00logwatch
apt
apt-clean
aptitude
bsdmainutils
chrootkit
dlocate
exim
find
logcheck
logrotate
man-db
modutils
netkit-inetd
ntp-server
rkhunter
standard
syshlogd
tripwire

cron.weekly:

man-db
ntp-server
rkhunter
syshlogd

cron.monthly:

standard

With the following in crontab file:

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
47 6	* * 7	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
52 6	1 * *	root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly
#

Could someone please explain the steps to take in removing what I don't want/need (without breaking anything) and configuring what I do. I only want standard reports from the aforementioned 3 packages and don't want other log files getting clogged up etc...

---

