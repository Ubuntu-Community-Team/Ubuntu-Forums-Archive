---
title: "squid3 guides + AD Authentication"
date: 2014-07-29
forum: Installation &amp; Upgrades
---

### Post by mark_graham on 2014-07-29
i'm at a standstill with this right now and its bugging me :mad:

Ubuntu 14.04, squid3 is installed, Kerberos and winbind is working (i can kinit users and i see users and groups if i use wbinfo -u and wbinfo -g wbinfo -t show's success )  


having an issue with testing and getting users to authenticate with squid. 


i dont have any of the files alot of the guides "say"  you should use or have, however, i do see things like basic_ldap_auth  and the likes, however, i dont see anything like squid_ldap_auth 


all the authentication files are in /usr/lib/squid3 too btw.  


is there anything anyone can point me in the direction to?  

directory listing of /usr/lib/squid3

-rwxr-xr-x  1 root root  4144 Feb 17 22:21 **basic_db_auth**
-rwxr-xr-x  1 root root 10208 Feb 17 22:21 **basic_fake_auth**
-rwxr-xr-x  1 root root 10208 Feb 17 22:21 **basic_getpwnam_auth**
-rwxr-xr-x  1 root root 22512 Feb 17 22:21 **basic_ldap_auth**
-rwxr-xr-x  1 root root 43552 Feb 17 22:21 **basic_msnt_auth**
-rwxr-xr-x  1 root root  3954 Feb 17 22:21 **basic_msnt_multi_domain_auth**
-rwxr-xr-x  1 root root 22496 Feb 17 22:21 **basic_ncsa_auth**
-rwxr-xr-x  1 root root 14304 Feb 17 22:21 **basic_nis_auth**
-rwxr-xr-x  1 root root 14320 Feb 17 22:21 **basic_pam_auth**
-rwxr-xr-x  1 root root  1460 Feb 17 22:21 **basic_pop3_auth**
-rwxr-xr-x  1 root root 18816 Feb 17 22:21 **basic_radius_auth**
-rwxr-xr-x  1 root root 14304 Feb 17 22:21 **basic_sasl_auth**
-rwxr-xr-x  1 root root 14304 Feb 17 22:21 **basic_smb_auth**
-rwxr-xr-x  1 root root  2229 Feb 17 22:21 **basic_smb_auth.sh**
-rwxr-xr-x  1 root root 22496 Feb 17 22:21 **digest_file_auth**
-rwxr-xr-x  1 root root 26616 Feb 17 22:21 **digest_ldap_auth**
-rwxr-xr-x  1 root root 18464 Feb 17 22:21 **diskd**
-rwxr-xr-x  1 root root 26600 Feb 17 22:21 **ext_ldap_group_acl**
-rwxr-xr-x  1 root root 10208 Feb 17 22:21 **ext_session_acl**
-rwxr-xr-x  1 root root  3935 Feb 17 22:21 **ext_sql_session_acl**
-rwxr-xr-x  1 root root 14304 Feb 17 22:21 **ext_unix_group_acl**
-rwxr-xr-x  1 root root  4999 Feb 17 22:21 **ext_wbinfo_group_acl**
-rwxr-xr-x  1 root root  5499 Feb 17 22:21 **helper-mux.pl**
-rwxr-xr-x  1 root root 12179 Feb 17 22:21 **log_db_daemon**
-rwxr-xr-x  1 root root 10208 Feb 17 22:21 **log_file_daemon**
-rwxr-xr-x  1 root root 26600 Feb 17 22:21 **negotiate_kerberos_auth**
-rwxr-xr-x  1 root root 14352 Feb 17 22:21 **negotiate_kerberos_auth_test**
-rwxr-xr-x  1 root root 18408 Feb 17 22:21 **negotiate_wrapper_auth**
-rwxr-xr-x  1 root root 18408 Feb 17 22:21 **ntlm_fake_auth**
-rwxr-xr-x  1 root root 61064 Feb 17 22:21 **ntlm_smb_lm_auth**
-rwsr-xr-x  1 root root 72472 Feb 17 22:21 pinger
-rwxr-xr-x  1 root root 10200 Feb 17 22:21 **unlinkd**
-rwxr-xr-x  1 root root 10208 Feb 17 22:21 **url_fake_rewrite**
-rwxr-xr-x  1 root root  1126 Feb 17 22:21 [B]url_fake_rewrite.sh


squid.conf  in /etc/squid3/squid.conf 


[/B]



### negotiate kerberos and ntlm authentication
auth_param negotiate program /usr/local/bin/negotiate_wrapper -d --ntlm /usr/bin/ntlm_auth --diagnostics --helper-protocol=squid-2.5-ntlmssp --domain=domain --kerberos /usr/lib/squid3/negotiate_kerberos_auth -d -s GSS_C_NO_NAME
auth_param negotiate children 10
auth_param negotiate keep_alive off

### pure ntlm authentication
auth_param ntlm children 10
auth_param ntlm keep_alive off
auth_param basic children 10

### provide basic authentication via ldap for clients not authenticated via kerberos/ntlm
auth_param basic realm Internet Proxy
auth_param basic credentialsttl 1 minute
auth_param basic program /usr/lib/squid3/basic_ldap_auth -R -b "dc=domain,dc=org" -D [email]user@domain.org[/email] -W /etc/squid3/ldappass.txt -f sAMAccountName=%s -h dc1.domain.org

### acl for proxy auth and ldap authorizations
 acl auth proxy_auth REQUIRED

### enforce authentication
 http_access deny !auth
 http_access allow auth
 http_access deny all






i *think*  those are all the lines you need right?

---

