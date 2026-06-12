---
title: "upgrade error"
date: 2006-08-03
forum: Installation &amp; Upgrades
---

### Post by petervdv on 2006-08-03
I am getting this error when I try to sudo apt-get upgrade:
```
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  totem-gstreamer-firefox-plugin
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up ssh-krb5 (3.8.1p1-10) ...
/etc/ssh/sshd_config: line 73: Bad configuration option: AcceptEnv
/etc/ssh/sshd_config: terminating, 1 bad configuration options
invoke-rc.d: initscript ssh-krb5, action "restart" failed.
dpkg: error processing ssh-krb5 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 ssh-krb5
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

How do I solve the ssh-krb5 error?
Please because he won't go on now, cannot install ,remove or update anything anymore at the moment.

---

### Post by hw-tph on 2006-08-04
Try just commenting out line #73 in /etc/ssh/sshd_config. AcceptEnv should be supported by ssh-krb5 but it seems it is not.


Håkan

---

### Post by petervdv on 2006-08-04
Thank you hw-tph !

---

