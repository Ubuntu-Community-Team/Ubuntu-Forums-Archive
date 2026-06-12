---
title: "apache sso &quot;failed to verify krb5 credentials: Bad encryption type&quot;"
date: 2011-02-14
forum: Installation &amp; Upgrades
---

### Post by dream4soul on 2011-02-14
Hi all,

I need preform apache auth using AD kerberos.

so my conf now ubuntu 10.10:
file /etc/krb5.conf

default = FILE:/var/log/krb5-lib.log
kdc = FILE:/var/log/krb5-kdc.log
admin_server = FILE:/var/log/kadmind.log

[login]
 krb4_convert = true
 krb4_get_tickets = false


[libdefaults]
	default_realm = MAIN.DOMAIN.MD
	default_tkt_enctypes = des-cbc-md5
	default_tgs_enctypes = des-cbc-md5
	allow_weak_crypto = true

# The following krb5.conf variables are only for MIT Kerberos.
	krb4_config = /etc/krb.conf
	krb4_realms = /etc/krb.realms
	kdc_timesync = 1
	ccache_type = 4
	forwardable = true
	proxiable = true
[realms]
	MAIN.DOMAIN.MD = {
		kdc = ODC1.MAIN.DOMAIN.MD
	}

[domain_realm]
	.main.DOMAIN.md = MAIN.DOMAIN.MD
	main.DOMAIN.md = MAIN.DOMAIN.MD
	dispute.DOMAIN.md = MAIN.DOMAIN.MD
	.dispute.DOMAIN.md = MAIN.DOMAIN.MD

file .htaccess 

AuthType Kerberos
AuthName "Kerberos Login"
KrbAuthRealms MAIN.DOMAIN.MD
KrbServiceName HTTP
Krb5Keytab /etc/krb5.keytab
KrbMethodNegotiate on
KrbMethodK5Passwd on
require valid-user


client auth works well

$ kinit username
Password for [email]username@MAIN.DOMAIN.MD[/email]:
klist -e
Ticket cache: FILE:/tmp/krb5cc_1000
Default principal: [email]username@MAIN.DOMAIN.MD[/email]

Valid starting     Expires            Service principal
02/14/11 14:29:45  02/15/11 00:29:51  krbtgt/MAIN.DOMAIN.MD@MAIN.DOMAIN.MD
	renew until 02/15/11 14:29:45, Etype (skey, tkt): DES cbc mode with RSA-MD5, ArcFour with HMAC/md5 


$kinit -k -t /etc/krb5.keytab HTTP/dispute.DOMAIN.md@MAIN.DOMAIN.MD
$ klist -ke
Keytab name: WRFILE:/etc/krb5.keytab
KVNO Principal
---- --------------------------------------------------------------------------
   4 HTTP/dispute.DOMAIN.md@MAIN.DOMAIN.MD (ArcFour with HMAC/md5) 
   4 HTTP/dispute.DOMAIN.md@MAIN.DOMAIN.MD (DES cbc mode with RSA-MD5) 
   4 HTTP/dispute.DOMAIN.md@MAIN.DOMAIN.MD (Triple DES cbc mode with HMAC/sha1) 
   4 HTTP/dispute.DOMAIN.md@MAIN.DOMAIN.MD (DES cbc mode with CRC-32) 
   4 HTTP/dispute.DOMAIN.md@MAIN.DOMAIN.MD (AES-256 CTS mode with 96-bit SHA-1 HMAC) 
   4 HTTP/dispute.DOMAIN.md@MAIN.DOMAIN.MD (AES-128 CTS mode with 96-bit SHA-1 HMAC) 
   4 HTTP/dispute.DOMAIN.md@MAIN.DOMAIN.MD (ArcFour with HMAC/md5) 
   4 HTTP/dispute.DOMAIN.md@MAIN.DOMAIN.MD (Exportable ArcFour with HMAC/md5) 


but apache !!! "failed to verify krb5 credentials: Bad encryption type" the url of http page dispute.domain.md

[Mon Feb 14 14:18:38 2011] [debug] src/mod_auth_kerb.c(1628): [client 192.168.53.143] kerb_authenticate_user entered with user (NULL) and auth_type Kerberos
[Mon Feb 14 14:18:38 2011] [debug] mod_deflate.c(615): [client 192.168.53.143] Zlib: Compressed 484 to 327 : URL /index.php
[Mon Feb 14 14:18:38 2011] [debug] src/mod_auth_kerb.c(1628): [client 192.168.53.143] kerb_authenticate_user entered with user (NULL) and auth_type Kerberos
[Mon Feb 14 14:18:38 2011] [debug] src/mod_auth_kerb.c(1240): [client 192.168.53.143] Acquiring creds for [email]HTTP@dispute.DOMAIN.md[/email]
[Mon Feb 14 14:18:38 2011] [debug] src/mod_auth_kerb.c(1385): [client 192.168.53.143] Verifying client data using KRB5 GSS-API 
[Mon Feb 14 14:18:38 2011] [debug] src/mod_auth_kerb.c(1401): [client 192.168.53.143] Client didn't delegate us their credential
[Mon Feb 14 14:18:38 2011] [debug] src/mod_auth_kerb.c(1101): [client 192.168.53.143] GSS-API major_status:000d0000, minor_status:000186a3
[Mon Feb 14 14:18:38 2011] [error] [client 192.168.53.143] gss_accept_sec_context() failed: Unspecified GSS failure.  Minor code may provide more information (, )
[Mon Feb 14 14:18:38 2011] [debug] mod_deflate.c(615): [client 192.168.53.143] Zlib: Compressed 484 to 327 : URL /index.php
[Mon Feb 14 14:18:38 2011] [debug] src/mod_auth_kerb.c(1628): [client 192.168.53.143] kerb_authenticate_user entered with user (NULL) and auth_type Kerberos
[Mon Feb 14 14:18:38 2011] [debug] src/mod_auth_kerb.c(994): [client 192.168.53.143] Using HTTP/dispute.DOMAIN.md@MAIN.DOMAIN.MD as server principal for password verification
[Mon Feb 14 14:18:38 2011] [debug] src/mod_auth_kerb.c(698): [client 192.168.53.143] Trying to get TGT for user [email]username@MAIN.DOMAIN.MD[/email]
[Mon Feb 14 14:18:38 2011] [debug] src/mod_auth_kerb.c(609): [client 192.168.53.143] Trying to verify authenticity of KDC using principal HTTP/dispute.DOMAIN.md@MAIN.DOMAIN.MD
[Mon Feb 14 14:18:38 2011] [debug] src/mod_auth_kerb.c(652): [client 192.168.53.143] krb5_rd_req() failed when verifying KDC
[Mon Feb 14 14:18:38 2011] [error] [client 192.168.53.143] failed to verify krb5 credentials: Bad encryption type
[Mon Feb 14 14:18:38 2011] [debug] src/mod_auth_kerb.c(1073): [client 192.168.53.143] kerb_authenticate_user_krb5pwd ret=401 user=(NULL) authtype=(NULL)
[Mon Feb 14 14:18:38 2011] [debug] mod_deflate.c(615): [client 192.168.53.143] Zlib: Compressed 484 to 327 : URL /index.php


I know that is encryption problem but where to fix ???

---

