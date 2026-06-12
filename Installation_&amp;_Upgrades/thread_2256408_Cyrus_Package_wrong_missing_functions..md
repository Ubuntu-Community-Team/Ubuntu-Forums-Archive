---
title: "Cyrus Package wrong? missing functions."
date: 2014-12-12
forum: Installation &amp; Upgrades
---

### Post by Wolfgang_Weinbrech on 2014-12-12
current package from cyrusimap.org - Ver. 
[cyrus-imapd-2.4.17.tar.gz]("ftp://ftp.cyrusimap.org/cyrus-imapd/cyrus-imapd-2.4.17.tar.gz")Dec 01 20122429k[[IMG]ftp://ftp.cyrusimap.org/squid-internal-static/icons/silk/package_go.png[/IMG]]("ftp://ftp.cyrusimap.org/cyrus-imapd/cyrus-imapd-2.4.17.tar.gz;type=i")[[IMG]ftp://ftp.cyrusimap.org/squid-internal-static/icons/silk/bullet_red.png[/IMG]]("ftp://ftp.cyrusimap.org/cyrus-imapd/cyrus-imapd-2.4.17.tar.gz.sig")[cyrus-imapd-2.4.17.tar.gz.sig]("ftp://ftp.cyrusimap.org/cyrus-imapd/cyrus-imapd-2.4.17.tar.gz.sig")Dec 01 20121k[[IMG]ftp://ftp.cyrusimap.org/squid-internal-static/icons/silk/page_white.png[/IMG]]("ftp://ftp.cyrusimap.org/cyrus-imapd/cyrus-imapd-2.4.17.tar.gz.sig;type=a")[[IMG]ftp://ftp.cyrusimap.org/squid-internal-static/icons/silk/package_go.png[/IMG]]("ftp://ftp.cyrusimap.org/cyrus-imapd/cyrus-imapd-2.4.17.tar.gz.sig;type=i")


allows this : 
[h=2]SYNOPSIS[/h][COLOR=#000000][FONT=Arial]**reconstruct** [ **&#8722;C** *config-file* ] [ **&#8722;p** *partition* ] [ **&#8722;x** ] [ **&#8722;r** ] [ **&#8722;f** ] 
[ **&#8722;k** ] [ **&#8722;s** ] [ **&#8722;g** ] [ **&#8722;G** ] [ **&#8722;R** ] [ **&#8722;o** ] [ **&#8722;O** ] *mailbox*... [B]
reconstruct[/B] [ **&#8722;C** *config-file* ] **&#8722;m**[/FONT][/COLOR]
[h=2]DESCRIPTION[/h]Ubuntu - Version: 14.04.1 LTS  Packages installed 
ii  cyrus-admin                      2.4.17+caldav~beta9-3         all          Cyrus mail system - administration tools (metapackage)
ii  cyrus-admin-2.4                  2.4.17+caldav~beta9-3         all          Cyrus mail system - administration tools
ii  cyrus-common                     2.4.17+caldav~beta9-3         all          Cyrus mail system - common files
ii  cyrus-common-2.4                 2.4.17+caldav~beta9-3         amd64        Cyrus mail system - common files



localhost.localdomain> reconstruct
usage: reconstruct [-r] mailbox

is the ubuntu package wrong?
sure, i can download and compile my own release. 

thanks for help.

---

### Post by steeldriver on 2014-12-12
Hello and welcome to the forums

I am not familiar with the cyrus software package, however based on the synopsis you need to give it the name of a mailbox to operate on - i.e.

```

reconstruct *some_mailbox*

```

instead of just
```

reconstruct

```

---

