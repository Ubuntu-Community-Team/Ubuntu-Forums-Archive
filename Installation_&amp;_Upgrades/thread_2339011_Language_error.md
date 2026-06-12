---
title: "Language error"
date: 2016-10-03
forum: Installation &amp; Upgrades
---

### Post by alfirdaous on 2016-10-03
Hi everyone,

While updating and upgrading, I've got these errors regarding the language:

```

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LC_CTYPE = "UTF-8",
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Setting up iptables-persistent (0.5.3ubuntu2) ...
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
FATAL: Could not load /lib/modules/3.8.13-xxxx-std-ipv6-64/modules.dep: No such file or directory
dpkg: error processing iptables-persistent (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 iptables-persistent
[ Rootkit Hunter version 1.3.8 ]
File updated: searched for 165 files, found 135
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

System information:

```

# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:        12.04
Codename:       precise

```

Thanks in advance

---

