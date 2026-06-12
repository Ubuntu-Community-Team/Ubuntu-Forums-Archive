---
title: "gvfs + auditd = d?????? ? ? ? ? ? .gvfs"
date: 2010-04-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by biovore on 2010-04-26
I am working on trying to make a CIS test case for my ubuntu 10.04 boxes. I am applying auditing to the system. 

After I setup some audit rules, I noticed that I couldn't do a ls -al in my home directory.  ls -al would just hang, But ls works just fine.

After some futzing with it, I did get it to give me a ls -al
I noticed the in-venerable "d????????? ? ? ? ? ? ? .gvfs" bug.
I believes this is still unresolved over with the redhat folks.

I disabled auditing and restarted the computer.
problem goes away.  Re-enable auditing, problem comes back. 

Just wondering if this is replicate-able by anyone else?
Any ideas what rules here might cause the problem?

Audit rules I am using atm:
```

# e - audit enable
# 0 - no enabled, 1 - enable, changes allows, 2 - enabled, no changes allowed
-e 1

# f - failure handling
# 0 - silent, 1 - printk, 2 - panic
-f 1

# b - buffers
# number of event buffers
# if buffer overflow occurs, does the failure action above
-b 320

-r 0

# Flush rule table to fresh state
-D

# System calls to log
# List of system calls we want to log (32 bit system)
# Note: on 64bit systems these are the 64 bit calls.. you need to also cover the 32bit comatiblity calls like chmod32
# see: man syscalls
-a entry,always -S chmod -S fchmod -S chown -S fchown -S lchown

# SUID files to watch
-w /usr/sbin/pppd -p rwxa
-w /usr/lib/pt_chown -p rwxa
-w /usr/lib/openssh/ssh-keysign -p rwxa
-w /usr/lib/eject/dmcrypt-get-device -p rwxa
-w /usr/lib/policykit-1/polkit-agent-helper-1 -p rwxa
-w /usr/bin/arping -p rwxa
-w /usr/bin/pkexec -p rwxa
-w /usr/bin/sudoedit -p rwxa
-w /usr/bin/X -p rwxa
-w /usr/bin/newgrp -p rwxa
-w /usr/bin/traceroute6.iputils -p rwxa
-w /usr/bin/sudo -p rwxa
-w /usr/bin/mtr -p rwxa
-w /usr/bin/chsh -p rwxa
-w /usr/bin/lppasswd -p rwxa
-w /usr/bin/chfn -p rwxa
-w /usr/bin/gpasswd -p rwxa
-w /usr/bin/passwd -p rwxa
-w /lib/dbus-1.0/dbus-daemon-launch-helper -p rwxa
-w /bin/umount -p rwxa
-w /bin/mount -p rwxa
-w /bin/ping6 -p rwxa
-w /bin/su -p rwxa
-w /bin/ping -p rwxa
-w /bin/fusermount -p rwxa

```

Auditd.conf file:
```

log_file = /var/log/audit/audit.log
log_format = RAW
log_group = root
priority_boost = 4
flush = INCREMENTAL
freq = 20
num_logs = 4
disp_qos = lossy
dispatcher = /sbin/audispd
name_format = NONE
##name = mydomain
max_log_file = 5 
max_log_file_action = ROTATE
space_left = 4096
space_left_action = SYSLOG
action_mail_acct = <user>
admin_space_left = 50
admin_space_left_action = SUSPEND
disk_full_action = SUSPEND
disk_error_action = SUSPEND
##tcp_listen_port = 
tcp_listen_queue = 5
##tcp_client_ports = 1024-65535
tcp_client_max_idle = 0
enable_krb5 = no
krb5_principal = auditd
##krb5_key_file = /etc/audit/audit.key

```

---

### Post by biovore on 2010-04-26
After some more messing with it, I have come to the conclusion that:
```

-w /bin/fusermount -p rwxa

```
makes gvfs unhappy and unable to set permissions correctly.

---

