---
title: "Apache2 not working after upgrade"
date: 2017-12-10
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2017-12-10
Yesterday I ran an upgrade on a Ubuntu 16.04 server. There were some issues during the upgrade and although I thought I got everything working today I discovered that Egroupware was not working. When I log in to Egroupware the login times out no error messages.

Here are the most relevant error messages form the Apache2 logs.

```
[Sun Dec 10 13:39:28.420907 2017] [core:error] [pid 1548] [client 169.53.184.23:6666] AH00037: Symbolic link not allowed or link target not accessible: /var/www/sqwebmail/index.cgi

[Sun Dec 10 14:06:18.082495 2017] [:error] [pid 5211] [client 72.200.56.98:40807] script ‘/var/www/groupdav.php’ not found or unable to stat

[Sun Dec 10 13:21:20.912058 2017] [:error] [pid 1547] [client 72.200.56.98:2325] EGroupware\Api\Translation::load_app_files() lang file /usr/share/egroupware/api/lang/egw_en.lang contains invalid app ‘filemanager’ on line 801 --> ignored
```

**I COULD USE A FEW CLUES ON WHAT MIGHT HAVE GONE WRONG.**

---

### Post by SeijiSensei on 2017-12-11
> Symbolic link not allowed or link target not accessible: /var/www/sqwebmail/index.cgi
First, does that file exist?  If so, is it the target of a symbolic link in a directory visible over the web?  If so, does the relevant <Directory> section of the configuration file include an "Options All" or at least an "Options FollowSymLinks" directive?

---

### Post by rsteinmetz70112 on 2017-12-11
The file didn't exist but that not really relevant. I removed sqwebmail. I've now reinstalled it but the man problem persists. Egroupware will not start, it times out. Apparently it is a php problem, which didn't exist before the most recent upgrade.
I am getting this egroupware error:

```
error.log:[Mon Dec 11 10:54:38.168337 2017] [:error] [pid 15497] [client 192.168.1.68:2923] PHP Fatal error: Maximum execution time of 90 seconds exceeded in /usr/share/egroupware/api/src/Framework/IncludeMgr.php on line 89
```

This seem to be a php problem, but I’m having trouble figuring out where.

---

### Post by rsteinmetz70112 on 2017-12-12
I think the problem is in the php7 configuration. Looking into that.
Apache2 works when pointed at html files.

---

### Post by rsteinmetz70112 on 2017-12-12
Finally resolved the problem mostly. 

I had downloaded the upgrade for the wrong repository. Once I corrected that It mostly works now I have to restore some other stuff that was broken in the process.

Still can't figure out how the repository got broken.

---

