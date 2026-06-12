---
title: "vsftpd Setup Problems"
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by weswitt on 2010-01-21
I would like some help getting vsftpd working with virtual users.  I have followed the readme and some corresponding posts that explain how to make this work, but I still cannot get it working.

Any help would be greatly appreciated.

The problem is that the virtual users cannot login.

After attempting to login I see in the auth.log file the following line:

Jan 21 15:25:34 rainier pam_pwdfile[1]: password file name not specified


My /etc/pam.d/vsftpd file is as follows:

auth    required        pam_listfile.so item=user sense=deny file=/etc/ftpusers onerr=succeed

@include common-session

auth    required        /lib/security/pam_pwdfile.so    db=/etc/vsftpd_login.db debug
account required        /lib/security/pam_permit.so     db=/etc/vsftpd_login.db debug


My vsftpd.conf file is as follows:

anonymous_enable=NO
chroot_local_user=YES
connect_from_port_20=YES
dirmessage_enable=YES
guest_enable=YES
guest_username=virtual
hide_ids=YES
listen=YES
local_enable=YES
local_root=/var/www/sites/$USER
pam_service_name=vsftpd
secure_chroot_dir=/var/run/vsftpd
use_localtime=YES
user_sub_token=$USER
virtual_use_local_privs=YES
write_enable=YES

---

### Post by suseendran.rengabashyam on 2010-01-22
Hi,

I guess that you haven't mentioned the path of your password file in /etc/pam.d/vsftpd.

Comment out the existing lines in your /etc/pam.d/vsftpd and make the following changes:

```
auth required pam_pwdfile.so pwdfile /pathof/your/passwdfile
account required pam_permit.so
```

Hope this helps.

---

