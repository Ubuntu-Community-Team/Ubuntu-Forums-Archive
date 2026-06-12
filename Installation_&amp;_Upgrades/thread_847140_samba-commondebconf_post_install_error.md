---
title: "samba-common/debconf post install error"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by bjolle on 2008-07-02
I'm running kubuntu 8.04. I recently had some file system errors, but I think fsck fixed most of them. But when upgrading today, the system failed upgrading samba-common:

```

$sudo apt-get install -f
Setting up samba-common (3.0.28a-1ubuntu4.4) ...
sed: -e expression #1, char 193: unknown option to `s'
dpkg: error processing samba-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 3.0.28a-1ubuntu4.4); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 samba-common
 smbclient
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I've inspected the post installation script (/var/lib/dpkg/info/samba-common.postinst), and have found out that the error happens here:

```

# Encrypt passwords?
db_get samba-common/encrypt_passwords || true
ENCRYPT_PASSWORDS="${RET}"

sed -i -e "s/^\([[:space:]]*\)\[global\]/\1\[global\]/i
                /^[[:space:]]*\[global\]/,/^[[:space:]]*\[/ \
                        s/^\([[:space:]]*\)encrypt passwords[[:space:]]*=.*/\1encrypt passwords = ${ENCRYPT_PASSWORDS}/i" \
                "$CONFIG"

```

More specifically, the return value from db_get is "10 samba-common/encrypt_passwords doesn't exist".

So this seems to be a debconf-issue. I tried reinstalling debconf but no change..

Is this likely to be related to the file system crash, or is it something else? (I don't think the lost+found directory  contained any related files). Where does debconf store this value?

Regards
B

---

### Post by cbahimsa on 2008-07-02
I've had something similar though on Hardy Ubuntu 64. It does not show up as broken. It first appeared on one of the early alpha releases. I'd like to fix it surgically rather then reinstall. Help please.

E: samba-common: subprocess post-installation script returned error exit status 1
E: smbclient: dependency problems - leaving unconfigured
E: ubuntu-desktop: dependency problems - leaving unconfigured

---

### Post by bjolle on 2008-07-03
Simply deleting all the files in the /var/cache/debconf/ directory fixed the problem. 

B

---

