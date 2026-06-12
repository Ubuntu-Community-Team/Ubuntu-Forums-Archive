---
title: "Help, Gusty has stopped my Samba with AD"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by bgsneeze on 2007-10-30
I upgraded from 7.04 to 7.10. I had samba working with Active Directory before the upgrade. Has anything changed, I checked my config files an they appear to have been untouched by the upgrade. I can post the config files if needed. Please someone help!
Thanks
bgsneeze

---

### Post by bgsneeze on 2007-10-30
When I run "sudo net ads testjoin" the out put is:

[2007/10/30 10:55:25, 5] lib/debug.c:debug_dump_status(391)
  INFO: Current debug levels:
    all: True/10
    tdb: False/0
    printdrivers: False/0
    lanman: False/0
    smb: False/0
    rpc_parse: False/0
    rpc_srv: False/0
    rpc_cli: False/0
    passdb: False/0
    sam: False/0
    auth: False/0
    winbind: False/0
    vfs: False/0
    idmap: False/0
    quota: False/0
    acls: False/0
    locking: False/0
    msdfs: False/0
    dmapi: False/0
[2007/10/30 10:55:25, 3] param/loadparm.c:lp_load(5039)
  lp_load: refreshing parameters
[2007/10/30 10:55:25, 3] param/loadparm.c:init_globals(1438)
  Initialising global parameters
[2007/10/30 10:55:25, 3] param/params.c:pm_process(572)
  params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
[2007/10/30 10:55:25, 3] param/loadparm.c:do_section(3778)
  Processing section "[global]"
  doing parameter workgroup = NT
  doing parameter server string = %h Test server (Samba, Ubuntu, Storage)
  doing parameter dns proxy = no
  doing parameter log file = /var/log/samba/log.%m
  doing parameter max log size = 1000
  doing parameter syslog = 0
  doing parameter panic action = /usr/share/samba/panic-action %d
  doing parameter realm = NT.LOCAL
  doing parameter security = ADS
  doing parameter encrypt passwords = true
  doing parameter password server = 10.0.0.3
  doing parameter idmap uid = 10000-20000
  doing parameter idmap gid = 10000-20000
  doing parameter winbind enum users = yes
  doing parameter winbind enum groups = yes
  doing parameter winbind cache time = 10
  doing parameter winbind use default domain = yes
  doing parameter template shell = /bin/false
  doing parameter template homedir = /home/%U
  doing parameter client use spnego = yes
  doing parameter invalid users = root
  doing parameter domain master = no
  doing parameter local master = no
  doing parameter preferred master = no
  doing parameter os level = 0
  doing parameter socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
[2007/10/30 10:55:25, 4] param/loadparm.c:lp_load(5070)
  pm_process() returned Yes
[2007/10/30 10:55:25, 7] param/loadparm.c:lp_servicenumber(5208)
  lp_servicenumber: couldn't find homes
[2007/10/30 10:55:25, 10] param/loadparm.c:set_server_role(4314)
  set_server_role: role = ROLE_DOMAIN_MEMBER
[2007/10/30 10:55:25, 5] lib/iconv.c:smb_register_charset(105)
  Attempting to register new charset UCS-2LE
[2007/10/30 10:55:25, 5] lib/iconv.c:smb_register_charset(113)
  Registered charset UCS-2LE
[2007/10/30 10:55:25, 5] lib/iconv.c:smb_register_charset(105)
  Attempting to register new charset UTF-16LE
[2007/10/30 10:55:25, 5] lib/iconv.c:smb_register_charset(113)
  Registered charset UTF-16LE
[2007/10/30 10:55:25, 5] lib/iconv.c:smb_register_charset(105)
  Attempting to register new charset UCS-2BE
[2007/10/30 10:55:25, 5] lib/iconv.c:smb_register_charset(113)
  Registered charset UCS-2BE
[2007/10/30 10:55:25, 5] lib/iconv.c:smb_register_charset(105)
  Attempting to register new charset UTF-16BE
[2007/10/30 10:55:25, 5] lib/iconv.c:smb_register_charset(113)
  Registered charset UTF-16BE
[2007/10/30 10:55:25, 5] lib/iconv.c:smb_register_charset(105)
  Attempting to register new charset UTF8
[2007/10/30 10:55:25, 5] lib/iconv.c:smb_register_charset(113)
  Registered charset UTF8
[2007/10/30 10:55:25, 5] lib/iconv.c:smb_register_charset(105)
  Attempting to register new charset UTF-8
[2007/10/30 10:55:25, 5] lib/iconv.c:smb_register_charset(113)
  Registered charset UTF-8
[2007/10/30 10:55:25, 5] lib/iconv.c:smb_register_charset(105)
  Attempting to register new charset ASCII
[2007/10/30 10:55:25, 5] lib/iconv.c:smb_register_charset(113)
  Registered charset ASCII
[2007/10/30 10:55:25, 5] lib/iconv.c:smb_register_charset(105)
  Attempting to register new charset 646
[2007/10/30 10:55:25, 5] lib/iconv.c:smb_register_charset(113)
  Registered charset 646
[2007/10/30 10:55:25, 5] lib/iconv.c:smb_register_charset(105)
  Attempting to register new charset ISO-8859-1
[2007/10/30 10:55:25, 5] lib/iconv.c:smb_register_charset(113)
  Registered charset ISO-8859-1
[2007/10/30 10:55:25, 5] lib/iconv.c:smb_register_charset(105)
  Attempting to register new charset UCS2-HEX
[2007/10/30 10:55:25, 5] lib/iconv.c:smb_register_charset(113)
  Registered charset UCS2-HEX
[2007/10/30 10:55:25, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2007/10/30 10:55:25, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2007/10/30 10:55:25, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2007/10/30 10:55:25, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2007/10/30 10:55:25, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2007/10/30 10:55:25, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2007/10/30 10:55:25, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2007/10/30 10:55:25, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2007/10/30 10:55:25, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2007/10/30 10:55:25, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2007/10/30 10:55:25, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2007/10/30 10:55:25, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2007/10/30 10:55:25, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2007/10/30 10:55:25, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2007/10/30 10:55:25, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2007/10/30 10:55:25, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2007/10/30 10:55:25, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2007/10/30 10:55:25, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2007/10/30 10:55:25, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2007/10/30 10:55:25, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2007/10/30 10:55:25, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2007/10/30 10:55:25, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2007/10/30 10:55:25, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2007/10/30 10:55:25, 5] lib/charcnv.c:charset_name(82)
  Substituting charset 'UTF-8' for LOCALE
[2007/10/30 10:55:25, 5] lib/util.c:init_names(287)
  Netbios name list:-
  my_netbios_names[0]="LINUX-WEBSERVER"
[2007/10/30 10:55:25, 2] lib/interface.c:add_interface(81)
  added interface ip=192.168.168.154 bcast=192.168.168.255 nmask=255.255.255.0
[2007/10/30 10:55:25, 5] lib/gencache.c:gencache_init(61)
  Opening cache file at /var/run/samba/gencache.tdb
[2007/10/30 10:55:25, 10] lib/gencache.c:gencache_get(226)
  Returning valid cache entry: key = AD_SITENAME/DOMAIN/NT.LOCAL, value = Default-First-Site-Name, timeout = Mon Jan 18 22:14:07 2038
[2007/10/30 10:55:25, 5] libads/dns.c:sitename_fetch(677)
  sitename_fetch: Returning sitename for NT.LOCAL: "Default-First-Site-Name"
[2007/10/30 10:55:25, 6] libads/ldap.c:ads_find_dc(294)
  ads_find_dc: looking for realm 'NT.LOCAL'
[2007/10/30 10:55:25, 8] libsmb/namequery.c:get_sorted_dc_list(1626)
  get_sorted_dc_list: attempting lookup for name NT.LOCAL (sitename Default-First-Site-Name) using [ads]
[2007/10/30 10:55:25, 10] lib/gencache.c:gencache_get(212)
  Cache entry with key = SAF/DOMAIN/NT.LOCAL couldn't be found
[2007/10/30 10:55:25, 5] libsmb/namequery.c:saf_fetch(133)
  saf_fetch: failed to find server for "NT.LOCAL" domain
[2007/10/30 10:55:25, 3] libsmb/namequery.c:get_dc_list(1489)
  get_dc_list: preferred server list: ", 10.0.0.3"
[2007/10/30 10:55:25, 10] lib/gencache.c:gencache_get(226)
  Returning valid cache entry: key = AD_SITENAME/DOMAIN/NT.LOCAL, value = Default-First-Site-Name, timeout = Mon Jan 18 22:14:07 2038
[2007/10/30 10:55:25, 5] libads/dns.c:sitename_fetch(677)
  sitename_fetch: Returning sitename for NT.LOCAL: "Default-First-Site-Name"
[2007/10/30 10:55:25, 10] libsmb/namequery.c:remove_duplicate_addrs2(435)
  remove_duplicate_addrs2: looking for duplicate address/port pairs
[2007/10/30 10:55:25, 4] libsmb/namequery.c:get_dc_list(1599)
  get_dc_list: returning 1 ip addresses in an ordered list
[2007/10/30 10:55:25, 4] libsmb/namequery.c:get_dc_list(1600)
  get_dc_list: 10.0.0.3:389 
[2007/10/30 10:55:25, 5] libads/ldap.c:ads_try_connect(180)
  ads_try_connect: sending CLDAP request to 10.0.0.3 (realm: NT.LOCAL)
[2007/10/30 10:55:25, 10] libads/dns.c:sitename_store(638)
  sitename_store: realm = [NT.LOCAL], sitename = [Default-First-Site-Name], expire = [2147483647]
[2007/10/30 10:55:25, 10] lib/gencache.c:gencache_set(140)
  Adding cache entry with key = AD_SITENAME/DOMAIN/NT.LOCAL; value = Default-First-Site-Name and timeout = Mon Jan 18 22:14:07 2038
   (953727522 seconds ahead)
[2007/10/30 10:55:25, 3] libads/ldap.c:ads_connect(394)
  Connected to LDAP server 10.0.0.3
[2007/10/30 10:55:30, 2] libads/ldap.c:ldap_open_with_timeout(70)
  Could not open LDAP connection to data1.NT.local:389: Illegal seek
[2007/10/30 10:55:30, 10] lib/gencache.c:gencache_get(226)
  Returning valid cache entry: key = AD_SITENAME/DOMAIN/NT.LOCAL, value = Default-First-Site-Name, timeout = Mon Jan 18 22:14:07 2038
[2007/10/30 10:55:30, 5] libads/dns.c:sitename_fetch(677)
  sitename_fetch: Returning sitename for NT.LOCAL: "Default-First-Site-Name"
[2007/10/30 10:55:30, 6] libads/ldap.c:ads_find_dc(294)
  ads_find_dc: looking for realm 'NT.LOCAL'
[2007/10/30 10:55:30, 8] libsmb/namequery.c:get_sorted_dc_list(1626)
  get_sorted_dc_list: attempting lookup for name NT.LOCAL (sitename Default-First-Site-Name) using [ads]
[2007/10/30 10:55:30, 10] lib/gencache.c:gencache_get(212)
  Cache entry with key = SAF/DOMAIN/NT.LOCAL couldn't be found
[2007/10/30 10:55:30, 5] libsmb/namequery.c:saf_fetch(133)
  saf_fetch: failed to find server for "NT.LOCAL" domain
[2007/10/30 10:55:30, 3] libsmb/namequery.c:get_dc_list(1489)
  get_dc_list: preferred server list: ", 10.0.0.3"
[2007/10/30 10:55:30, 10] lib/gencache.c:gencache_get(226)
  Returning valid cache entry: key = AD_SITENAME/DOMAIN/NT.LOCAL, value = Default-First-Site-Name, timeout = Mon Jan 18 22:14:07 2038
[2007/10/30 10:55:30, 5] libads/dns.c:sitename_fetch(677)
  sitename_fetch: Returning sitename for NT.LOCAL: "Default-First-Site-Name"
[2007/10/30 10:55:30, 10] libsmb/namequery.c:remove_duplicate_addrs2(435)
  remove_duplicate_addrs2: looking for duplicate address/port pairs
[2007/10/30 10:55:30, 4] libsmb/namequery.c:get_dc_list(1599)
  get_dc_list: returning 1 ip addresses in an ordered list
[2007/10/30 10:55:30, 4] libsmb/namequery.c:get_dc_list(1600)
  get_dc_list: 10.0.0.3:389 
[2007/10/30 10:55:30, 5] libads/ldap.c:ads_try_connect(180)
  ads_try_connect: sending CLDAP request to 10.0.0.3 (realm: NT.LOCAL)
[2007/10/30 10:55:30, 10] libads/dns.c:sitename_store(638)
  sitename_store: realm = [NT.LOCAL], sitename = [Default-First-Site-Name], expire = [2147483647]
[2007/10/30 10:55:30, 10] lib/gencache.c:gencache_set(140)
  Adding cache entry with key = AD_SITENAME/DOMAIN/NT.LOCAL; value = Default-First-Site-Name and timeout = Mon Jan 18 22:14:07 2038
   (953727517 seconds ahead)
[2007/10/30 10:55:30, 3] libads/ldap.c:ads_connect(394)
  Connected to LDAP server 10.0.0.3
[2007/10/30 10:55:35, 2] libads/ldap.c:ldap_open_with_timeout(70)
  Could not open LDAP connection to data1.NT.local:389: Illegal seek
Join to domain is not valid: Operations error
[2007/10/30 10:55:35, 2] utils/net.c:main(1036)
  return code = -1

---

### Post by kah00na on 2007-10-30
I'd start by looking at these errors near the end.  Especially the "Join to domain is not valid".  You can also look in /var/log/samba/log.smbd and /var/log/log.nmbd for more information about what the error may be.

```
[2007/10/30 10:55:30, 3] libads/ldap.c:ads_connect(394)
Connected to LDAP server 10.0.0.3
[2007/10/30 10:55:35, 2] libads/ldap.c:ldap_open_with_timeout(70)
Could not open LDAP connection to data1.NT.local:389: Illegal seek
Join to domain is not valid: Operations error
[2007/10/30 10:55:35, 2] utils/net.c:main(1036)
return code = -1
```

---

### Post by bgsneeze on 2007-10-31
/var/log/samba/log.winbind is full of this:
[2007/10/28 07:37:38, 1] nsswitch/winbindd_util.c:trustdom_recv(235)
  Could not receive trustdoms

/var/log/samba/log.nmbd is full of this:
[2007/10/31 14:51:45, 0] nmbd/nmbd_namequery.c:query_name_response(109)
  query_name_response: Multiple (2) responses received for a query on subnet 1$
  This response was from IP 10.0.0.6, reporting an IP address of 10.0.0.6.

/var/log/samba/smbd is this:
[2007/10/30 10:15:12, 0] printing/nt_printing.c:nt_printing_init(650)
  nt_printing_init: error checking published printers: WERR_ACCESS_DENIED
[2007/10/30 10:15:25, 1] smbd/server.c:open_sockets_smbd(491)
  Reloading services after SIGHUP

Does this help anyone?

---

### Post by jonallport on 2008-02-05
May just be coincidence but I had the same issue after the Feisty-Gutsy server upgrade.

Turns out I had avahi installed (on a server ?!?) and mdns was refered before  dns in /etc/nsswitch.conf.  I removed the mdns entry and hey presto!

---

