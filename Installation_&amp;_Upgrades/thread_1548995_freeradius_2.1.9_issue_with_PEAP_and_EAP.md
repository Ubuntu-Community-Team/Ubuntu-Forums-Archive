---
title: "freeradius 2.1.9 issue with PEAP and EAP"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by krushnaec on 2010-08-09
Hi ...
 
I have setup the freeradius 2.1.9 with ubuntu 10.04.
After that i have change the "default_eap_type = peap" in eap.conf and facing the Below issue..
 
any one have any idea about this error...wht is missing in configuration.
 
thanks in Advance for reply... 
 
kumar@kumar-desktop:~$ sudo -i
[sudo] password for kumar: 
root@kumar-desktop:~# 
root@kumar-desktop:~# 
root@kumar-desktop:~# 
root@kumar-desktop:~# cd /usr/local/etc/raddb/
root@kumar-desktop:/usr/local/etc/raddb# gedit eap.conf 
root@kumar-desktop:/usr/local/etc/raddb# radiusd -X
FreeRADIUS Version 2.1.9, for host i686-pc-linux-gnu, built on Aug 6 2010 at 11:09:06
Copyright (C) 1999-2009 The FreeRADIUS server project and contributors. 
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A 
PARTICULAR PURPOSE. 
You may redistribute copies of FreeRADIUS under the terms of the 
GNU General Public License v2. 
Starting - reading configuration files ...
including configuration file /usr/local/etc/raddb/radiusd.conf
including configuration file /usr/local/etc/raddb/proxy.conf
including configuration file /usr/local/etc/raddb/clients.conf
including files in directory /usr/local/etc/raddb/modules/
including configuration file /usr/local/etc/raddb/modules/mschap
including configuration file /usr/local/etc/raddb/modules/pam
including configuration file /usr/local/etc/raddb/modules/ldap
including configuration file /usr/local/etc/raddb/modules/counter
including configuration file /usr/local/etc/raddb/modules/mac2vlan
including configuration file /usr/local/etc/raddb/modules/wimax
including configuration file /usr/local/etc/raddb/modules/mac2ip
including configuration file /usr/local/etc/raddb/modules/detail.log
including configuration file /usr/local/etc/raddb/modules/smsotp
including configuration file /usr/local/etc/raddb/modules/preprocess
including configuration file /usr/local/etc/raddb/modules/linelog
including configuration file /usr/local/etc/raddb/modules/attr_filter
including configuration file /usr/local/etc/raddb/modules/checkval
including configuration file /usr/local/etc/raddb/modules/ippool
including configuration file /usr/local/etc/raddb/modules/detail.example.com
including configuration file /usr/local/etc/raddb/modules/unix
including configuration file /usr/local/etc/raddb/modules/acct_unique
including configuration file /usr/local/etc/raddb/modules/chap
including configuration file /usr/local/etc/raddb/modules/policy
including configuration file /usr/local/etc/raddb/modules/otp
including configuration file /usr/local/etc/raddb/modules/exec
including configuration file /usr/local/etc/raddb/modules/pap
including configuration file /usr/local/etc/raddb/modules/ntlm_auth
including configuration file /usr/local/etc/raddb/modules/sql_log
including configuration file /usr/local/etc/raddb/modules/smbpasswd
including configuration file /usr/local/etc/raddb/modules/expr
including configuration file /usr/local/etc/raddb/modules/expiration
including configuration file /usr/local/etc/raddb/modules/passwd
including configuration file /usr/local/etc/raddb/modules/detail
including configuration file /usr/local/etc/raddb/modules/always
including configuration file /usr/local/etc/raddb/modules/sqlcounter_expire_on_login
including configuration file /usr/local/etc/raddb/modules/attr_rewrite
including configuration file /usr/local/etc/raddb/modules/files
including configuration file /usr/local/etc/raddb/modules/digest
including configuration file /usr/local/etc/raddb/modules/sradutmp
including configuration file /usr/local/etc/raddb/modules/echo
including configuration file /usr/local/etc/raddb/modules/perl
including configuration file /usr/local/etc/raddb/modules/krb5
including configuration file /usr/local/etc/raddb/modules/etc_group
including configuration file /usr/local/etc/raddb/modules/realm
including configuration file /usr/local/etc/raddb/modules/inner-eap
including configuration file /usr/local/etc/raddb/modules/radutmp
including configuration file /usr/local/etc/raddb/modules/logintime
including configuration file /usr/local/etc/raddb/modules/cui
including configuration file /usr/local/etc/raddb/eap.conf
including configuration file /usr/local/etc/raddb/policy.conf
including files in directory /usr/local/etc/raddb/sites-enabled/
including configuration file /usr/local/etc/raddb/sites-enabled/default
including configuration file /usr/local/etc/raddb/sites-enabled/control-socket
including configuration file /usr/local/etc/raddb/sites-enabled/inner-tunnel
main {
allow_core_dumps = no
}
including dictionary file /usr/local/etc/raddb/dictionary
main {
prefix = "/usr/local"
localstatedir = "/usr/local/var"
logdir = "/usr/local/var/log/radius"
libdir = "/usr/local/lib"
radacctdir = "/usr/local/var/log/radius/radacct"
hostname_lookups = no
max_request_time = 30
cleanup_delay = 5
max_requests = 1024
pidfile = "/usr/local/var/run/radiusd/radiusd.pid"
checkrad = "/usr/local/sbin/checkrad"
debug_level = 0
proxy_requests = yes
log {
stripped_names = no
auth = no
auth_badpass = no
auth_goodpass = no
}
security {
max_attributes = 200
reject_delay = 1
status_server = yes
}
}
radiusd: #### Loading Realms and Home Servers ####
proxy server {
retry_delay = 5
retry_count = 3
default_fallback = no
dead_time = 120
wake_all_if_all_dead = no
}
home_server localhost {
ipaddr = 127.0.0.1
port = 1812
type = "auth"
secret = "testing123"
response_window = 20
max_outstanding = 65536
require_message_authenticator = no
zombie_period = 40
status_check = "status-server"
ping_interval = 30
check_interval = 30
num_answers_to_alive = 3
num_pings_to_alive = 3
revive_interval = 120
status_check_timeout = 4
irt = 2
mrt = 16
mrc = 5
mrd = 30
}
home_server_pool my_auth_failover {
type = fail-over
home_server = localhost
}
realm example.com {
auth_pool = my_auth_failover
}
realm LOCAL {
}
radiusd: #### Loading Clients ####
client 192.168.1.1 {
require_message_authenticator = no
secret = "Test"
shortname = "192.168.1.1"
nastype = "cisco"
}
client 192.168.1.100 {
require_message_authenticator = no
secret = "Test"
shortname = "192.168.1.1"
nastype = "cisco"
}
radiusd: #### Instantiating modules ####
instantiate {
Module: Linked to module rlm_exec
Module: Instantiating exec
exec {
wait = no
input_pairs = "request"
shell_escape = yes
}
Module: Linked to module rlm_expr
Module: Instantiating expr
Module: Linked to module rlm_expiration
Module: Instantiating expiration
expiration {
reply-message = "Password Has Expired "
}
Module: Linked to module rlm_logintime
Module: Instantiating logintime
logintime {
reply-message = "You are calling outside your allowed timespan "
minimum-timeout = 60
}
}
radiusd: #### Loading Virtual Servers ####
server inner-tunnel {
modules {
Module: Checking authenticate {...} for more modules to load
Module: Linked to module rlm_pap
Module: Instantiating pap
pap {
encryption_scheme = "auto"
auto_header = no
}
Module: Linked to module rlm_chap
Module: Instantiating chap
Module: Linked to module rlm_mschap
Module: Instantiating mschap
mschap {
use_mppe = yes
require_encryption = no
require_strong = no
with_ntdomain_hack = no
}
Module: Linked to module rlm_unix
Module: Instantiating unix
unix {
radwtmp = "/usr/local/var/log/radius/radwtmp"
}
Module: Linked to module rlm_eap
Module: Instantiating eap
eap {
default_eap_type = "peap"
timer_expire = 60
ignore_unknown_eap_types = no
cisco_accounting_username_bug = no
max_sessions = 4096
}
Module: Linked to sub-module rlm_eap_md5
Module: Instantiating eap-md5
Module: Linked to sub-module rlm_eap_leap
Module: Instantiating eap-leap
Module: Linked to sub-module rlm_eap_gtc
Module: Instantiating eap-gtc
gtc {
challenge = "Password: "
auth_type = "PAP"
}
Ignoring EAP-Type/tls because we do not have OpenSSL support.
Ignoring EAP-Type/ttls because we do not have OpenSSL support.
Ignoring EAP-Type/peap because we do not have OpenSSL support.
Module: Linked to sub-module rlm_eap_mschapv2
Module: Instantiating eap-mschapv2
mschapv2 {
with_ntdomain_hack = no
}
rlm_eap: No such sub-type for default EAP type peap
/usr/local/etc/raddb/eap.conf[17]: Instantiation failed for module "eap"
/usr/local/etc/raddb/sites-enabled/inner-tunnel[223]: Failed to load module "eap".
/usr/local/etc/raddb/sites-enabled/inner-tunnel[176]: Errors parsing authenticate section. 
root@kumar-desktop:/usr/local/etc/raddb#
 
Best Regards,
Krushna

---

