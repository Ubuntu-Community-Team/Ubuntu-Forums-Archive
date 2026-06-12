---
title: "LDAP and AD connection problem with 8.04"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by deadkey on 2008-04-28
Hello,

I have a strange problem after upgrading from gutsy to hardy. The user identification via LDAP Microsoft AD does not work anymore.

The /etc/ldap.conf and /etc/nsswitch.conf seems to be okay. "getent password" and "getent group" delivers the info from AD I expect. 

"ssh" and "id" hangs!

If I set "bind_policy soft" in /etc/ldap.conf, I get the following error:

#id  user
id: result.c:112: ldap_result: Assertion `ld != ((void *)0)' failed.
uid=10039(user) gid=10147(group)Aborted

and in /var/log/auth.log I found the following:
Apr 28 16:04:36 hostname id: nss_ldap: could not search LDAP server - Server is unavailable

If I delete the "ldap" in /etc/nsswitch.conf from "group", no hangers or errors anymore, but I can only see the local groups.

Exactly the same config under gutsy (7.10) works great. 

The problem occurs on a hardy upgrade and on a hardy fresh installation.

Any ideas?

---

### Post by deadkey on 2008-04-29
I compiled and installed openldap 2.4.8 and nss_ldap 260 on my own (with the default settings)

Now it works perfectly!

I try to contact the package maintainer and wait for an upgrade :-)

---

### Post by oxtub on 2008-04-30
I am having the exact same problem:

[http://ubuntuforums.org/showthread.php?t=775723](http://ubuntuforums.org/showthread.php?t=775723)

Thanks for the note on building it yourself.

---

### Post by deadkey on 2008-05-01
I noticed that you need the right configure parameter to get it working like the ubuntu packages.

Check the Ubuntu source diff packages for the correct parameter. 

For nss_ldap I used:
./configure --prefix=/usr/local/stow/nss_ldap-260 --enable-rfc2307bis --with
-ldap-dir=/usr/local/stow/openldap-2.4.8 --with-ldap-lib=openldap --enable-schem
a-mapping --enable-schema-mapping --enable-configurable-krb5-ccname-gssapi

For Openldap:
./configure --prefix=/usr/local/stow/openldap-2.4.8 --enable-overlays

With the "enable-overlays" I am not sure if it is correct. I will check the source diff.

---

### Post by oxtub on 2008-05-06
Did you ever hear back from the package maintainer on this? I have not seen any bug reports related to it.

---

### Post by deadkey on 2008-05-06
It is in the Ubuntu buglist:

[https://bugs.launchpad.net/ubuntu/+source/libnss-ldap/+bug/227229](https://bugs.launchpad.net/ubuntu/+source/libnss-ldap/+bug/227229)

---

### Post by songshu on 2008-05-08
i'm trying to se up hardy to authenticate to openldap en debian etch.

have been following the general and gutsy guides, unless i totally overlooked something (quit possible), its not working at all.

does anybody have a working set up?

---

### Post by markwolfe on 2008-05-08
I have also run into a similar issue with hardy and nss_ldap. 

It is quite disappointing that it was tested prior to release as it is quite a core requirement for most organizations to authenticate there machines from a central authentication system.

In my case I am seeing the same issues using a standard ldap server.

May  9 10:56:06 mark-wolfes-computer dbus-daemon: nss_ldap: could not search LDAP server - Server is unavailable

May  9 08:55:14 mark-wolfes-computer bash: nss_ldap: failed to bind to LDAP server ldap://XXXXX.com.au: Can't contact LDAP server

Would be nice to get this corrected soon.

Mark

---

### Post by gblfxt on 2008-05-16
i had the same issues initially, then i uninstalled libnss-ldap and backed up my old libnss-ldap.conf file.  i then deleted ALL other instances of LDAP confs (is /etc/ldap.conf, /etc/ldap.secret,/etc/libnss-ldap.conf,/etc/libpam-ldap.conf, etc.)

then i reinstalled libnss-ldap.  i copied my old libnss-ldap.conf file to /etc/ldap.conf and made a new /etc/ldap.secret

it seemed to finally work after all this.

---

### Post by songshu on 2008-05-17
> **gblfxt said:**
> i had the same issues initially, then i uninstalled libnss-ldap and backed up my old libnss-ldap.conf file.  i then deleted ALL other instances of LDAP confs (is /etc/ldap.conf, /etc/ldap.secret,/etc/libnss-ldap.conf,/etc/libpam-ldap.conf, etc.)

then i reinstalled libnss-ldap.  i copied my old libnss-ldap.conf file to /etc/ldap.conf and made a new /etc/ldap.secret

it seemed to finally work after all this.

can you post your config?

would be apreciated,

thanks

---

### Post by gblfxt on 2008-05-17
here you go, its setup with domain active.directory.com and ssl isn't setup on this sample.

###DEBCONF###
# the configuration of this file will be done by debconf as long as the # first line of the file says '###DEBCONF###'
#
# you should use dpkg-reconfigure libnss-ldap to configure this file.
#
 @(#)$Id: ldap.conf,v 2.47 2006/05/15 08:13:44 lukeh Exp $ 
# 
# This is the configuration file for the LDAP nameservice 
# switch library and the LDAP PAM module.
#
# PADL Software
# [http://www.padl.com](http://www.padl.com)
#

# Your LDAP server. Must be resolvable without using LDAP.
# Multiple hosts may be specified, each separated by a 
# space. How long nss_ldap takes to failover depends on 
# whether your LDAP client library supports configurable 
# network or connect timeouts (see bind_timelimit).
#host 127.0.0.1

# The distinguished name of the search base.
base dc=active,dc=directory,dc=com

# Another way to specify your LDAP server is to provide an uri 
ldap://192.168.100.50/ 
# Unix Domain Sockets to connect to a local LDAP Server.
#uri ldap://127.0.0.1/
#uri ldaps://127.0.0.1/   
#uri ldapi://%2fvar%2frun%2fldapi_sock/
# Note: %2f encodes the '/' used as directory separator

# The LDAP version to use (defaults to 3 # if supported by client library) ldap_version 3

# The distinguished name to bind to the server with.
# Optional: default is to bind anonymously.
# Please do not put double quotes around it as they # would be included literally.
#binddn cn=proxyuser,dc=padl,dc=com
binddn CN=guest user,OU=users,DC=active,DC=directory,DC=com

# The credentials to bind with. 
# Optional: default is no credential.
#bindpw secret
bindpw secret

# The distinguished name to bind to the server with 
# if the effective user ID is root. Password is 
# stored in /etc/libnss-ldap.secret (mode 600) 
# Use 'echo -n "mypassword" > /etc/libnss-ldap.secret' instead 
# of an editor to create the file.
rootbinddn cn=admin,ou=users,dc=active,dc=directory,dc=com

# The port.
# Optional: default is 389.
#port 389

# The search scope.
scope sub
#scope one
#scope base

# Search timelimit
#timelimit 30

# Bind/connect timelimit
#bind_timelimit 30

# Reconnect policy:
#  hard_open: reconnect to DSA with exponential backoff if
#             opening connection failed
#  hard_init: reconnect to DSA with exponential backoff if
#             initializing connection failed
#  hard:      alias for hard_open
#  soft:      return immediately on server failure
#bind_policy hard

# Connection policy:
#  persist:   DSA connections are kept open (default)
#  oneshot:   DSA connections destroyed after request
#nss_connect_policy persist

# Idle timelimit; client will close connections 
# (nss_ldap only) if the server has not been contacted 
# for the number of seconds specified below.
#idle_timelimit 3600

# Use paged rseults
#nss_paged_results yes

# Pagesize: when paged results enable, used to set the 
# pagesize to a custom value 
#pagesize 1000

# Filter to AND with uid=%s
#pam_filter objectclass=User

# The user ID attribute (defaults to uid) pam_login_attribute uidNumber

# Search the root DSE for the password policy (works # with Netscape Directory Server) pam_lookup_policy yes

# Check the 'host' attribute for access control 
# Default is no; if set to yes, and user has no 
# value for the host attribute, and pam_ldap is 
# configured for account management (authorization) 
# then the user will not be allowed to login.
#pam_check_host_attr yes

# Check the 'authorizedService' attribute for access 
# control 
# Default is no; if set to yes, and the user has no 
# value for the authorizedService attribute, and 
# pam_ldap is configured for account management 
# (authorization) then the user will not be allowed # to login.
#pam_check_service_attr yes

# Group to enforce membership of
#pam_groupdn cn=PAM,ou=Groups,dc=padl,dc=com

# Group member attribute
#pam_member_attribute uniquemember

# Specify a minium or maximum UID number allowed 
#pam_min_uid 0 
#pam_max_uid 0

# Template login attribute, default template user 
# (can be overriden by value of former attribute # in user's entry) 
#pam_login_attribute userPrincipalName 
#pam_template_login_attribute uid 
#pam_template_login nobody

# HEADS UP: the pam_crypt, pam_nds_passwd, 
# and pam_ad_passwd options are no 
# longer supported.
#
# Do not hash the password at all; presume 
# the directory server will do it, if 
# necessary. This is the default.
#pam_password clear

# Hash password locally; required for University of 
# Michigan LDAP server, and works with Netscape 
# Directory Server if you're using the UNIX-Crypt 
# hash mechanism and not using the NT Synchronization 
# service. 
#pam_password crypt

# Remove old password first, then update in 
# cleartext. Necessary for use with Novell 
# Directory Services (NDS) 
#pam_password nds

# RACF is an alias for the above. For use with 
# IBM RACF 
#pam_password racf

# Update Active Directory password, by
# creating Unicode password and updating 
# unicodePwd attribute.
#pam_password ad

# Use the OpenLDAP password change
# extended operation to update the password.
#pam_password exop

# Redirect users to a URL or somesuch on password 
# changes.
#pam_password_prohibit_message Please visit [http://internal](http://internal) to change your password.

# Use backlinks for answering initgroups() 
#nss_initgroups backlink

# Enable support for RFC2307bis (distinguished names in group # members) 
#nss_schema rfc2307bis

# RFC2307bis naming contexts
# Syntax:
# nss_base_XXX		base?scope?filter
# where scope is {base,one,sub}
# and filter is a filter to be &'d with the 
# default filter.
# You can omit the suffix eg:
# nss_base_passwd	ou=People,
# to append the default base DN but this 
# may incur a small performance impact.
nss_base_passwd		dc=active,dc=directory,dc=com?sub
nss_base_shadow		dc=active,dc=directory,dc=com?sub
nss_base_group		dc=active,dc=directory,dc=com?sub
#nss_base_hosts		ou=Hosts,dc=padl,dc=com?one
#nss_base_services	ou=Services,dc=padl,dc=com?one
#nss_base_networks	ou=Networks,dc=padl,dc=com?one
#nss_base_protocols	ou=Protocols,dc=padl,dc=com?one
#nss_base_rpc		ou=Rpc,dc=padl,dc=com?one
#nss_base_ethers	ou=Ethers,dc=padl,dc=com?one
#nss_base_netmasks	ou=Networks,dc=padl,dc=com?ne
#nss_base_bootparams	ou=Ethers,dc=padl,dc=com?one
#nss_base_aliases	ou=Aliases,dc=padl,dc=com?one
#nss_base_netgroup	ou=Netgroup,dc=padl,dc=com?one

# attribute/objectclass mapping
# Syntax:
#nss_map_attribute	rfc2307attribute	mapped_attribute
#nss_map_objectclass	rfc2307objectclass	mapped_objectclass

# configure --enable-nds is no longer supported.
# NDS mappings
#nss_map_attribute uniqueMember member

# Services for UNIX 3.5 mappings
#nss_map_objectclass posixAccount User
#nss_map_objectclass shadowAccount User
#nss_map_attribute uid msSFU30Name
#nss_map_attribute uniqueMember msSFU30PosixMember 
#nss_map_attribute userPassword msSFU30Password 
#nss_map_attribute homeDirectory msSFU30HomeDirectory 
#nss_map_attribute homeDirectory msSFUHomeDirectory 
#nss_map_objectclass posixGroup Group 
#pam_login_attribute msSFU30Name 
#pam_filter objectclass=User 
#pam_password ad

# configure --enable-mssfu-schema is no longer supported.
# Services for UNIX 2.0 mappings
#nss_map_objectclass posixAccount User
#nss_map_objectclass shadowAccount user
#nss_map_attribute uid msSFUName
#nss_map_attribute uniqueMember posixMember 
#nss_map_attribute userPassword msSFUPassword 
#nss_map_attribute homeDirectory msSFUHomeDirectory 
#nss_map_attribute shadowLastChange pwdLastSet 
#nss_map_objectclass posixGroup Group 
#nss_map_attribute cn msSFUName 
#pam_login_attribute msSFUName 
#pam_filter objectclass=User 
#pam_password ad

# RFC 2307 (AD) mappings
nss_map_objectclass posixAccount user
nss_map_objectclass shadowAccount user
nss_map_attribute uid sAMAccountName
nss_map_attribute uidNumber uidNumber
nss_map_attribute gidNumber gidNumber
nss_map_attribute loginShell loginShell
nss_map_attribute gecos name
nss_map_attribute homeDirectory unixHomeDirectory 
nss_map_attribute shadowLastChange pwdLastSet 
nss_map_objectclass posixGroup group 
nss_map_attribute uniqueMember member 
pam_login_attribute sAMAccountName 
pam_filter objectclass=User 
pam_password ad 
referrals no

# configure --enable-authpassword is no longer supported 
# AuthPassword mappings 
#nss_map_attribute userPassword authPassword

# AIX SecureWay mappings
#nss_map_objectclass posixAccount aixAccount 
#nss_base_passwd ou=aixaccount,?one 
#nss_map_attribute uid userName 
#nss_map_attribute gidNumber gid 
#nss_map_attribute uidNumber uid 
#nss_map_attribute userPassword passwordChar 
#nss_map_objectclass posixGroup aixAccessGroup 
#nss_base_group ou=aixgroup,?one 
#nss_map_attribute cn groupName 
#nss_map_attribute uniqueMember member 
#pam_login_attribute userName 
#pam_filter objectclass=aixAccount 
#pam_password clear

# For pre-RFC2307bis automount schema
#nss_map_objectclass automountMap nisMap 
#nss_map_attribute automountMapName nisMapName 
#nss_map_objectclass automount nisObject 
#nss_map_attribute automountKey cn 
#nss_map_attribute automountInformation nisMapEntry

# Netscape SDK LDAPS
#ssl on

# Netscape SDK SSL options
#sslpath /etc/ssl/certs

# OpenLDAP SSL mechanism
# start_tls mechanism uses the normal LDAP port, LDAPS typically 636 
#ssl start_tls 
#ssl on

# OpenLDAP SSL options
# Require and verify server certificate (yes/no) 
# Default is to use libldap's default behavior, which can be configured in 
# /etc/openldap/ldap.conf using the TLS_REQCERT setting.  The default for 
# OpenLDAP 2.0 and earlier is "no", for 2.1 and later is "yes".
#tls_checkpeer yes

# CA certificates for server certificate verification 
# At least one of these are required if tls_checkpeer is "yes"
#tls_cacertfile /etc/ssl/ca.cert
#tls_cacertdir /etc/ssl/certs

# Seed the PRNG if /dev/urandom is not provided 
#tls_randfile /var/run/egd-pool

# SSL cipher suite
# See man ciphers for syntax
#tls_ciphers TLSv1

# Client certificate and key
# Use these, if your server requires client authentication.
#tls_cert
#tls_key

# Disable SASL security layers. This is needed for AD.
#sasl_secprops maxssf=0

# Override the default Kerberos ticket cache location.
#krb5_ccname FILE:/etc/.ldapcache

---

### Post by songshu on 2008-05-18
> **gblfxt said:**
> here you go, its setup with domain active.directory.com and ssl isn't setup on this sample.



thanks dude

---

### Post by deadkey on 2008-07-30
There is a configuration which works around this issue. 

I have the SFU installed on my AD and this includes the attribute "msSFU30GidNumber", which I use for the UNIX GID. Now I set up a "nss_base_group" which filters out all groups without this attribute.

nss_base_group ou=OU_Groups,dc=my,dc=domain,dc=com?sub?&(msSFU30GidNumber=*)

---

### Post by sopsaare on 2008-08-18
Hey!

This problem is most probably caused by some invalid GID. That might be group without Unix attributes. 
I tried this one
```
nss_base_group dc=active,dc=directory,dc=com?sub
```
And gave all my groups in domain the Unix attributes and it worked. Then I commented the upper line out and the problem was there again. Then I hassled around with my Winbind test setup and found out that the problem was caused by one group from the trusted domain which was assigned to me (some permission to use some of their adminstrative shares).

But I didn't want to give all the group the Unix Attributes, so I just changed the upper line to be like this:
```
nss_base_group ou=linuxou,dc=active,dc=directory,dc=com?one
```

So the ldap searches only from the specified ou.

---

