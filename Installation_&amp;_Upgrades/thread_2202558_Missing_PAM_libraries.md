---
title: "Missing PAM libraries"
date: 2014-01-29
forum: Installation &amp; Upgrades
---

### Post by spiros88 on 2014-01-29
A few days I messed up something with a strange at-get operation (I was testing an unofficial package). Since then I cannot log in animore in the CUPS webinterface, i.e., if I try to do an operation that requires authentication both my normal user and root fail to authenticate.

I had a look into /var/log/auth.log and:

```

Jan 29 23:41:06 bertie cupsd: PAM unable to dlopen(pam_unix.so): /lib/security/pam_unix.so: cannot open shared object file: No such file or directory
Jan 29 23:41:06 bertie cupsd: PAM adding faulty module: pam_unix.so
Jan 29 23:41:06 bertie cupsd: PAM unable to dlopen(pam_deny.so): /lib/security/pam_deny.so: cannot open shared object file: No such file or directory
Jan 29 23:41:06 bertie cupsd: PAM adding faulty module: pam_deny.so
Jan 29 23:41:06 bertie cupsd: PAM unable to dlopen(pam_permit.so): /lib/security/pam_permit.so: cannot open shared object file: No such file or directory
Jan 29 23:41:06 bertie cupsd: PAM adding faulty module: pam_permit.so
Jan 29 23:41:06 bertie cupsd: PAM unable to dlopen(pam_ecryptfs.so): /lib/security/pam_ecryptfs.so: wrong ELF class: ELFCLASS64
Jan 29 23:41:06 bertie cupsd: PAM adding faulty module: pam_ecryptfs.so
Jan 29 23:41:06 bertie cupsd: PAM unable to dlopen(pam_umask.so): /lib/security/pam_umask.so: cannot open shared object file: No such file or directory
Jan 29 23:41:06 bertie cupsd: PAM adding faulty module: pam_umask.so
Jan 29 23:41:06 bertie cupsd: PAM unable to dlopen(pam_systemd.so): /lib/security/pam_systemd.so: cannot open shared object file: No such file or directory
Jan 29 23:41:06 bertie cupsd: PAM adding faulty module: pam_systemd.so
Jan 29 23:41:06 bertie cupsd: PAM unable to dlopen(pam_ck_connector.so): /lib/security/pam_ck_connector.so: cannot open shared object file: No such file or directory
Jan 29 23:41:06 bertie cupsd: PAM adding faulty module: pam_ck_connector.so
Jan 29 23:41:10 bertie cupsd: PAM unable to dlopen(pam_unix.so): /lib/security/pam_unix.so: cannot open shared object file: No such file or directory
Jan 29 23:41:10 bertie cupsd: PAM adding faulty module: pam_unix.so
Jan 29 23:41:10 bertie cupsd: PAM unable to dlopen(pam_deny.so): /lib/security/pam_deny.so: cannot open shared object file: No such file or directory
Jan 29 23:41:10 bertie cupsd: PAM adding faulty module: pam_deny.so
Jan 29 23:41:10 bertie cupsd: PAM unable to dlopen(pam_permit.so): /lib/security/pam_permit.so: cannot open shared object file: No such file or directory
Jan 29 23:41:10 bertie cupsd: PAM adding faulty module: pam_permit.so
Jan 29 23:41:10 bertie cupsd: PAM unable to dlopen(pam_ecryptfs.so): /lib/security/pam_ecryptfs.so: wrong ELF class: ELFCLASS64
Jan 29 23:41:10 bertie cupsd: PAM adding faulty module: pam_ecryptfs.so
Jan 29 23:41:10 bertie cupsd: PAM unable to dlopen(pam_umask.so): /lib/security/pam_umask.so: cannot open shared object file: No such file or directory
Jan 29 23:41:10 bertie cupsd: PAM adding faulty module: pam_umask.so
Jan 29 23:41:10 bertie cupsd: PAM unable to dlopen(pam_systemd.so): /lib/security/pam_systemd.so: cannot open shared object file: No such file or directory
Jan 29 23:41:10 bertie cupsd: PAM adding faulty module: pam_systemd.so
Jan 29 23:41:10 bertie cupsd: PAM unable to dlopen(pam_ck_connector.so): /lib/security/pam_ck_connector.so: cannot open shared object file: No such file or directory
Jan 29 23:41:10 bertie cupsd: PAM adding faulty module: pam_ck_connector.so

```

(bertie is my laptop's name)

/lib/security contains just the two files pam_ecryptfs.so and pam_vbox.so.  How can I solve the issue?  It is probably enough to find the right package to install, but I don't know which one.  I find a lot of libpam-* packages.

By the way, when I messed up my system, it installed some 32-bit libraries, while my system is amd64.  I don't know if this helps.

Thanks in advance.

---

