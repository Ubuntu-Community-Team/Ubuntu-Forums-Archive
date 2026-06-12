---
title: "Squid3-3.1.19 on Ubuntu 12.04 - https ssl shebang"
date: 2012-08-28
forum: Installation &amp; Upgrades
---

### Post by mentalcic on 2012-08-28
Hi,

I am a total beginner in Linux server administration and I appreciate all your help you are willing to provide. Sorry for the long post and my not-so-great English.

I am having a bit of a problem understanding what is going on here and where did I do something wrong. Here are the steps I took.
I installed Ubuntu 12.04 server from a CD and updated.
```
sudo apt-get update
sudo apt-get upgrade
```

```
uname -a

Linux MyHostname.MyDomain.local 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

I have installed various software (apache2, php, mysql etc.), configured and confirmed that it works.

A requirement for this setup is for all users on my network to manually setup proxy settings in their browser to myproxyhost on port 3128 as they do not have any access to the internet and this server should be their "window to the world" when it comes to browsing the web.

And next in line of services was installation of some proxy. I wanted to try out squid3 so I did

```
sudo apt-get install squid3
```

I created some custom squid.conf which I took from the web
```

# ACCESS CONTROLS OPTIONS
# ====================
#
acl QUERY urlpath_regex -i cgi-bin ? .php$ .asp$ .shtml$ .cfm$ .cfml$ .phtml$ .php3$ localhost
acl all src
acl localnet src 10.0.0.0/8
acl localnet src 192.168.1.0/24 # Your network here
acl localhost src 127.0.0.1/32
acl safeports port 21 70 80 210 280 443 488 563 591 631 777 901 81 3128 1025-65535
acl sslports port 443 563 81 2087 10000
acl manager proto cache_object
acl purge method PURGE
acl connect method CONNECT
acl ym dstdomain .messenger.yahoo.com .psq.yahoo.com
acl ym dstdomain .us.il.yimg.com .msg.yahoo.com .pager.yahoo.com
acl ym dstdomain .rareedge.com .ytunnelpro.com .chat.yahoo.com
acl ym dstdomain .voice.yahoo.com
acl ymregex url_regex yupdater.yim ymsgr myspaceim
#
http_access deny ym
http_access deny ymregex
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !safeports
http_access deny CONNECT !sslports
http_access allow localhost
http_access allow localnet
http_access deny all
#
# NETWORK OPTIONS
# .....
#
http_port 3128
#
# OPTIONS WHICH AFFECT THE CACHE SIZE
# ==============================
#
cache_mem 64 MB
maximum_object_size_in_memory 1024 KB
memory_replacement_policy heap GDSF
cache_replacement_policy heap LFUDA
cache_dir aufs /home/precise/cache 10000 14 256
maximum_object_size 128000 KB
cache_swap_low 95
cache_swap_high 99
#
# LOGFILE PATHNAMES AND CACHE DIRECTORIES
# ==================================
#
access_log /var/log/squid3/access.log
cache_log /var/log/squid3/cache.log
#cache_log /dev/null
cache_store_log none
logfile_rotate 5
log_icp_queries off
#
# OPTIONS FOR TUNING THE CACHE
# ========================
#
cache deny QUERY
refresh_pattern ^ftp: 1440 20% 10080 reload-into-ims
refresh_pattern ^gopher: 1440 0% 1440
refresh_pattern -i .(gif|png|jp?g|ico|bmp|tiff?)$ 10080 95% 43200 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-private
refresh_pattern -i .(rpm|cab|deb|exe|msi|msu|zip|tar|xz|bz|bz2|lzma|gz|tgz|rar|bin|7z|doc?|xls?|ppt?|pdf|nth|psd|sis)$ 10080 90% 43200 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-private
refresh_pattern -i .(avi|iso|wav|mid|mp?|mpeg|mov|3gp|wm?|swf|flv|x-flv|axd)$ 43200 95% 432000 override-expire override-lastmod reload-into-ims ignore-no-cache ignore-private
refresh_pattern -i .(html|htm|css|js)$ 1440 75% 40320
refresh_pattern -i .index.(html|htm)$ 0 75% 10080
refresh_pattern -i (/cgi-bin/|?) 0 0% 0
refresh_pattern . 1440 90% 10080
#
quick_abort_min 0 KB
quick_abort_max 0 KB
quick_abort_pct 100
store_avg_object_size 13 KB
#
# HTTP OPTIONS
# ===========
vary_ignore_expire on
#
# ANONIMITY OPTIONS
# ===============
#
request_header_access From deny all
request_header_access Server deny all
request_header_access Link deny all
request_header_access Via deny all
request_header_access X-Forwarded-For deny all
#
# TIMEOUTS
# =======
#
forward_timeout 240 second
connect_timeout 30 second
peer_connect_timeout 5 second
read_timeout 600 second
request_timeout 60 second
shutdown_lifetime 10 second
half_closed_clients off
#
# ADMINISTRATIVE PARAMETERS
# =====================
#
cache_mgr ninja
cache_effective_user proxy
cache_effective_group proxy
httpd_suppress_version_string on
visible_hostname ninja
#
ftp_list_width 32
ftp_passive on
ftp_sanitycheck on
#
# DNS OPTIONS
# ==========
#
dns_timeout 10 seconds
dns_nameservers 8.8.8.8 8.8.4.4 # DNS Server
#
# MISCELLANEOUS
# ===========
#
memory_pools off
client_db off
reload_into_ims on
coredump_dir /cache
pipeline_prefetch on
offline_mode off
#
#Marking ZPH
#==========
zph_mode tos
zph_local 0x04
zph_parent 0
zph_option 136
### END CONFIGURATION ###

```

Everything works like a charm but the funny thing I've noticed is that I am able to browse the following websites (note the https):
[https://mail.yahoo.com](https://mail.yahoo.com)
[https://accounts.google.com](https://accounts.google.com)
[https://login.live.com](https://login.live.com)
[https://twitter.com](https://twitter.com)
BUT unable to browse following websites 
[https://help.ubuntu.com/](https://help.ubuntu.com/)
[https://www.facebook.com/](https://www.facebook.com/)
due to error
```
The proxy server is refusing connections
          Firefox is configured to use a proxy server that is refusing connections.
  Check the proxy settings to make sure that they are correct.
  Contact your network administrator to make sure the proxy server is
    working.
```

I did some research and found out that support for ssl is not built by default and that I should download source and rebuild it myself with --enable-ssl option. I did this by following a merge of information found on this forum and on other webpages:
```
apt-get install devscripts build-essential
apt-get source squid3
apt-get build-dep squid3
cd squid3-3.1.19
nano debian/rules # or whatever editor you use

```
add the --enable-ssl line among the other --enable-blah- lines
```
debuild -us -uc
cd ..
dpkg -i squid3_3.1.19-1ubuntu3.12.04.1_amd64.deb squid3-common_3.1.19-1ubuntu3.12.04.1_all.deb squid3-dbg_3.1.19-1ubuntu3.12.04.1_amd64.deb

```

Now I have:
```
$ squid3 -v
Squid Cache: Version 3.1.19
configure options:  '--build=x86_64-linux-gnu' '--prefix=/usr' '--includedir=${prefix}/include' '--mandir=${prefix}/share/man' '--infodir=${prefix}/share/info' '--sysconfdir=/etc' '--localstatedir=/var' '--libexecdir=${prefix}/lib/squid3' '--srcdir=.' '--disable-maintainer-mode' '--disable-dependency-tracking' '--disable-silent-rules' '--datadir=/usr/share/squid3' '--sysconfdir=/etc/squid3' '--mandir=/usr/share/man' '--with-cppunit-basedir=/usr' '--enable-inline' '--enable-async-io=8' '--enable-storeio=ufs,aufs,diskd' '--enable-removal-policies=lru,heap' '--enable-delay-pools' '--enable-cache-digests' '--enable-underscores' '--enable-icap-client' '--enable-ssl' '--enable-follow-x-forwarded-for' '--enable-auth=basic,digest,ntlm,negotiate' '--enable-basic-auth-helpers=LDAP,MSNT,NCSA,PAM,SASL,SMB,YP,DB,POP3,getpwnam,squid_radius_auth,multi-domain-NTLM' '--enable-ntlm-auth-helpers=smb_lm,' '--enable-digest-auth-helpers=ldap,password' '--enable-negotiate-auth-helpers=squid_kerb_auth' '--enable-external-acl-helpers=ip_user,ldap_group,session,unix_group,wbinfo_group' '--enable-arp-acl' '--enable-esi' '--enable-zph-qos' '--enable-wccpv2' '--disable-translation' '--with-logdir=/var/log/squid3' '--with-pidfile=/var/run/squid3.pid' '--with-filedescriptors=65536' '--with-large-files' '--with-default-user=proxy' '--enable-linux-netfilter' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2 -fPIE -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Werror=format-security' 'LDFLAGS=-Wl,-Bsymbolic-functions -fPIE -pie -Wl,-z,relro -Wl,-z,now' 'CPPFLAGS=-D_FORTIFY_SOURCE=2' 'CXXFLAGS=-g -O2 -fPIE -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Werror=format-security' --with-squid=/home/myuser/squid3/squid3-3.1.19

```

and it didn't solve the problem - proxy server is refusing connections when I try to connect to e.g. [https://help.ubuntu.com](https://help.ubuntu.com).

Thank you for reading this post!
Please help!
Robert

---

### Post by mentalcic on 2012-09-03
Ok, found it.

It was a PEBKAC kind of problem that required a RTFM answer.

squid3.conf
section 

# ADMINISTRATIVE PARAMETERS
# =====================
#
cache_mgr **<INSERT YOUR HOSTNAME>**
cache_effective_user proxy
cache_effective_group proxy
httpd_suppress_version_string on
visible_hostname **<INSERT YOUR HOSTNAME>**

And it works like a charm...

Thank you all for reading this long post.
Robert

---

### Post by t3ch on 2012-12-24
hello, i have follow your steps and add --enable-ssl but now i get following in log:

**Ignoring https_port 0.0.0.0:443 due to SSL initialization failure**

anyone now what am i missing?

mentalcic: i dont see you have https_port 443 line in your squid.conf
do you have open that port by squid?

tnx :confused:

EDIT:

**compiled with: file ( debian/rules )**
> 
DEB_CONFIGURE_EXTRA_FLAGS := --datadir=/usr/share/squid3 \
		--sysconfdir=/etc/squid3 \
		--mandir=/usr/share/man \
		--with-cppunit-basedir=/usr \
                --enable-ssl \
#                --enable-ssl-crtd \
		--enable-inline \
		--enable-async-io=8 \
		--enable-storeio="ufs,aufs,diskd" \
		--enable-removal-policies="lru,heap" \
		--enable-delay-pools \
		--enable-cache-digests \
		--enable-underscores \
		--enable-icap-client \
		--enable-follow-x-forwarded-for \
		--enable-auth="basic,digest,ntlm,negotiate" \
		--enable-basic-auth-helpers="LDAP,MSNT,NCSA,PAM,SASL,SMB,YP,DB,POP3,getpwnam,squid_radius_auth,multi-domain-NTLM" \
		--enable-ntlm-auth-helpers="smb_lm," \
		--enable-digest-auth-helpers="ldap,password" \
		--enable-negotiate-auth-helpers="squid_kerb_auth" \
		--enable-external-acl-helpers="ip_user,ldap_group,session,unix_group,wbinfo_group" \
		--enable-arp-acl \
		--enable-esi \
		--enable-zph-qos \
		--enable-wccpv2 \
		--disable-translation \
		--with-logdir=/var/log/squid3 \
		--with-pidfile=/var/run/squid3.pid \
		--with-filedescriptors=65536 \
		--with-large-files \
		--with-default-user=proxy


**awk '!/^\ *#/&&(length > 0)' /etc/squid3/squid.conf**
> 
acl manager proto cache_object
acl localhost src 127.0.0.1/32 ::1
acl to_localhost dst 127.0.0.0/8 0.0.0.0/32 ::1
acl mynet src 192.168.0.0/24
acl SSL_ports port 443
acl Safe_ports port 80		# http
acl Safe_ports port 21		# ftp
acl Safe_ports port 443		# https
acl Safe_ports port 70		# gopher
acl Safe_ports port 210		# wais
acl Safe_ports port 1025-65535	# unregistered ports
acl Safe_ports port 280		# http-mgmt
acl Safe_ports port 488		# gss-http
acl Safe_ports port 591		# filemaker
acl Safe_ports port 777		# multiling http
acl CONNECT method CONNECT
http_access allow manager localhost
http_access deny manager
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localhost
http_access allow mynet
http_access deny all
http_port 80 transparent
https_port 443 sslBump cert=/etc/squid3/ssl/squid.cert key=/etc/squid3/ssl/squid.key transparent
always_direct allow all
ssl_bump allow all
sslproxy_cert_error allow all
sslproxy_flags DONT_VERIFY_PEER
coredump_dir /var/spool/squid3
refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern -i (/cgi-bin/|\?) 0	0%	0
refresh_pattern (Release|Packages(.gz)*)$      0       20%     2880
refresh_pattern .		0	20%	4320
cache_mgr [email]test@test.com[/email]
cache_effective_user proxy
cache_effective_group proxy
httpd_suppress_version_string on
visible_hostname test.com

**tail /var/log/squid3/cache.log:**
> 
2012/12/25 00:37:45| Using Least Load store dir selection
2012/12/25 00:37:45| Set Current Directory to /var/spool/squid3
2012/12/25 00:37:45| Loaded Icons.
2012/12/25 00:37:45| Accepting  intercepted HTTP connections at 0.0.0.0:80, FD 12.
2012/12/25 00:37:45| Ignoring https_port 0.0.0.0:443 due to SSL initialization failure.
2012/12/25 00:37:45| HTCP Disabled.
2012/12/25 00:37:45| Squid plugin modules loaded: 0
2012/12/25 00:37:45| Adaptation support is off.
2012/12/25 00:37:45| Ready to serve requests.
2012/12/25 00:37:46| storeLateRelease: released 0 objects


---

### Post by t3ch on 2012-12-25
SOLVED! :)

Problem was in https_port it is only for reverse proxy so comment that line or remove.

Working config with line:

> http_port 8080 sslBump cert=/etc/squid3/ssl/squid.cert key=/etc/squid3/ssl/squid.key

or if you want transparent, add transparent at the end of line.

Thanx to elico from irc.freenode.org #squid

useful links:
[http://www.squid-cache.org/Doc/config/ssl_bump/]("http://www.squid-cache.org/Doc/config/ssl_bump/")
[http://www.squid-cache.org/Doc/config/http_port/]("http://www.squid-cache.org/Doc/config/http_port/")

:D :popcorn:

---

