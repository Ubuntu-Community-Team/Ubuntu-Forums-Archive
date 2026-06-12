---
title: "xinetd problems after edgy upgrade"
date: 2007-02-07
forum: Installation &amp; Upgrades
---

### Post by DistantShadow on 2007-02-07
Just upgraded from dapper to edgy last night, and now xinetd is having problems.  It's complaining about all the settings in my /etc/xinet.d/Xvnc file...

> $ sudo /usr/sbin/xinetd -d
07/2/7@11:54:56: DEBUG: 6442 {handle_includedir} Reading included configuration file: /etc/xinetd.d/Xvnc [file=/etc/xinetd.conf] [line=15]
 [file=/etc/xinetd.d/Xvnc] [line=4]se_value_list} Bad service type: UNLISTED
07/2/7@11:54:56: ERROR: 6442 {identify_attribute} Error parsing attribute type - DISABLING SERVICE [file=/etc/xinetd.d/Xvnc] [line=4]
 [file=/etc/xinetd.d/Xvnc] [line=5]sable_parser} Bad value: no
07/2/7@11:54:56: ERROR: 6442 {identify_attribute} Error parsing attribute disable - DISABLING SERVICE [file=/etc/xinetd.d/Xvnc] [line=5]
 [file=/etc/xinetd.d/Xvnc] [line=6]t_type_parser} Bad socket type: stream
07/2/7@11:54:56: ERROR: 6442 {identify_attribute} Error parsing attribute socket_type - DISABLING SERVICE [file=/etc/xinetd.d/Xvnc] [line=6]
 not in /etc/protocols [file=/etc/xinetd.d/Xvnc] [line=7]cp
07/2/7@11:54:56: ERROR: 6442 {identify_attribute} Error parsing attribute protocol - DISABLING SERVICE [file=/etc/xinetd.d/Xvnc] [line=7]
 [file=/etc/xinetd.d/Xvnc] [line=8]parser} Bad value for wait: yes
07/2/7@11:54:56: ERROR: 6442 {identify_attribute} Error parsing attribute wait - DISABLING SERVICE [file=/etc/xinetd.d/Xvnc] [line=8]
 [file=/etc/xinetd.d/Xvnc] [line=9]parser} Unknown user: root
07/2/7@11:54:56: ERROR: 6442 {identify_attribute} Error parsing attribute user - DISABLING SERVICE [file=/etc/xinetd.d/Xvnc] [line=9]
 is not executable [file=/etc/xinetd.d/Xvnc] [line=10]sr/bin/Xvnc
07/2/7@11:54:56: ERROR: 6442 {identify_attribute} Error parsing attribute server - DISABLING SERVICE [file=/etc/xinetd.d/Xvnc] [line=10]
07/2/7@11:54:56: DEBUG: 6442 {remove_disabled_services} removing Xvnc
Service defaults
        Bind = All addresses.
        Only from: All sites
        No access: No blocked sites
        Logging to file: /tmp/xinetd.log (no limits)
        Log_on_success flags = HOST PID
        Log_on_failure flags = HOST

07/2/7@11:54:56: DEBUG: 6442 {cnf_start_services} mask_max = 0, services_started = 0
07/2/7@11:54:56: CRITICAL: 6442 {init_services} no services. Exiting...


I had this all working fine under dapper...  any ideas?

-ds

---

### Post by DistantShadow on 2007-02-07
I recreated my /etc/xinet.d/Xvnc file from scratch and it now works.  No idea why it had a problem to begin with, but I'm happy now.

-ds

---

