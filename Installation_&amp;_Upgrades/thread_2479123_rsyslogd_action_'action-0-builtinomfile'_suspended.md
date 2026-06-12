---
title: "rsyslogd: action 'action-0-builtin:omfile' suspended after upgrading from 22.04.1 LTS"
date: 2022-09-15
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2022-09-15
After upgrading from 20.04.5 LTS server to 22.04.1 LTS server I'm getting hundreds of the following warnings in syslog


```
Sep 15 06:36:09 mail2 rsyslogd: action 'action-0-builtin:omfile' suspended (module 'builtin:omfile'), retry 0. There should be messages before this one giving the reason for suspension. [v8.2112.0 try https://www.rsyslog.com/e/2007 ]
Sep 15 06:36:09 mail2 rsyslogd: action 'action-0-builtin:omfile' resumed (module 'builtin:omfile') [v8.2112.0 try https://www.rsyslog.com/e/2359 ]
Sep 15 06:36:09 mail2 rsyslogd: action 'action-0-builtin:omfile' suspended (module 'builtin:omfile'), retry 0. There should be messages before this one giving the reason for suspension. [v8.2112.0 try https://www.rsyslog.com/e/2007 ]
Sep 15 06:36:09 mail2 rsyslogd: action 'action-0-builtin:omfile' resumed (module 'builtin:omfile') [v8.2112.0 try https://www.rsyslog.com/e/2359 ]
Sep 15 06:36:09 mail2 rsyslogd: action 'action-0-builtin:omfile' suspended (module 'builtin:omfile'), retry 0. There should be messages before this one giving the reason for suspension. [v8.2112.0 try https://www.rsyslog.com/e/2007 ]
Sep 15 06:36:09 mail2 rsyslogd: action 'action-0-builtin:omfile' resumed (module 'builtin:omfile') [v8.2112.0 try https://www.rsyslog.com/e/2359 ]
Sep 15 06:36:09 mail2 rsyslogd: action 'action-0-builtin:omfile' suspended (module 'builtin:omfile'), retry 0. There should be messages before this one giving the reason for suspension. [v8.2112.0 try https://www.rsyslog.com/e/2007 ]
Sep 15 06:36:09 mail2 rsyslogd: action 'action-0-builtin:omfile' resumed (module 'builtin:omfile') [v8.2112.0 try https://www.rsyslog.com/e/2359 ]
Sep 15 06:36:09 mail2 rsyslogd: action 'action-0-builtin:omfile' suspended (module 'builtin:omfile'), retry 0. There should be messages before this one giving the reason for suspension. [v8.2112.0 try https://www.rsyslog.com/e/2007 ]
Sep 15 06:36:09 mail2 rsyslogd: action 'action-0-builtin:omfile' suspended (module 'builtin:omfile'), next retry is Thu Sep 15 06:36:39 2022, retry nbr 0. There should be messages before this one giving the reason for suspension. [v8.2112.0 try https://www.rsyslog.com/e/2007 ]

```

Not sure what the issue is

---

### Post by lister171254 on 2022-09-15
Fixed as per the doc rsyslog V8 [https://www.rsyslog.com/doc/v8-stable/configuration/modules/omfile.html]("https://www.rsyslog.com/doc/v8-stable/configuration/modules/omfile.html")

Interesting thing is that the rsyslog version for 20.04.5 LTS (swVersion="8.2001.0") has no problem with the obsolete/changed parameters, while the version for 22.04.1 LTS (swVersion="8.2112.0") does.

I have made the following changes to /etc/rsyslog.conf
[LIST]
[*]Changed the first letter from uppercase for the legacy parameters
[*]Commented out the obsolete parameters
[*]
[/LIST]


```

$fileOwner syslog
$fileGroup adm
$fileCreateMode 0640
$dirCreateMode 0755
$umask 0022
#$PrivDropToUser syslog
#$PrivDropToGroup syslog

```

---

