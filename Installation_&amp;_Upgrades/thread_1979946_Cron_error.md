---
title: "Cron error"
date: 2012-05-14
forum: Installation &amp; Upgrades
---

### Post by taxidimu on 2012-05-14
In Ubuntu 10 + Postfix I get the following error message from CRON (extract from syslog):

[INDENT]May 14 14:40:01 www CRON[5226]: (sysman) CMD (php /var/www/crm/administrator/components/com_civicrm/civicrm/bin/civimail.cronjob.php)
May 14 14:40:01 www CRON[5223]: (CRON) error (grandchild #5226 failed with exit status 255)
May 14 14:40:01 www postfix/pickup[3529]: 7D6737E75: uid=1000 from=<sysman>
May 14 14:40:01 www postfix/cleanup[5231]: 7D6737E75: message-id=<20120514124001.7D6737E75@CHCServer>
May 14 14:40:01 www postfix/qmgr[1603]: 7D6737E75: from=<sysman@CHCServer>, size=982, nrcpt=1 (queue active)
May 14 14:40:01 www postfix/local[5234]: 7D6737E75: to=<sysman@CHCServer>, orig_to=<sysman>, relay=local, delay=0.2, delays=0.15/0/0/0.05, dsn=2.0.0, status=sent (delivered to mailbox)
May 14 14:40:01 www postfix/qmgr[1603]: 7D6737E75: removed
[/INDENT]Crontab file:
[INDENT]# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user    command
17 *    * * *    root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#

# for CIVICRM ...
CIVI_ROOT=/var/www/crm
PHP=nice -n19 /usr/bin/php
PARAMS= -j -sdefault -umailsender -pkar23fesk -e Job -a process_mailing

*/5 * * * * cd $CIVI_ROOT; $PHP bin/cli.php $PARAMS
# ... end for CIVICRM
[/INDENT]A "mailsender" user has been added, with group "www-data".
File  
/var/www/crm/administrator/components/com_civicrm/civicrm/bin/civimail.cronjob.php
exists, with ownwer/group www-data.

Thank you for help.

---

