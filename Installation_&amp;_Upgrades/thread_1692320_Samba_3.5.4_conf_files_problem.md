---
title: "Samba 3.5.4 conf files problem"
date: 2011-02-21
forum: Installation &amp; Upgrades
---

### Post by taxidimu on 2011-02-21
After reinstalling Samba 2:3.5.4 I have the following:

[LIST=1]
[*]smb.conf in /usr/share/samba
[*]locate smbpasswd finds 
/usr/bin/smbpasswd
/usr/sbin/mksmbpasswd
/usr/share/doc/samba-doc/htmldocs/manpages/smbpasswd.5.html
/usr/share/doc/samba-doc/htmldocs/manpages/smbpasswd.8.html
/usr/share/man/man5/smbpasswd.5.gz
/usr/share/man/man8/mksmbpasswd.8.gz
/usr/share/man/man8/smbpasswd.8.gz
/usr/share/pam-configs/smbpasswd-migrate
[*]testparm looks for smb.conf in /etc/samba
[/LIST]
I move /copy smb.conf and customize, and add users via
smbpasswd -a username

But I cannot locate a smbpasswd file, and cannot share dir /files.Thank you for answer.

---

