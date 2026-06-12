---
title: "apt-get &amp; Synaptic"
date: 2005-04-15
forum: Installation &amp; Upgrades
---

### Post by Halfdan on 2005-04-15
I'm sitting behind a proxy. The emailing and web browsing is OK, but I can't update the system nor by Synaptic nor via terminal. 

407 Proxy Authentication Required - the server and the port number is OK, but where and how can I give the username and password for it?

The problem is, that my proxy username is the full email address with @? What is the syntax?

THX, Halfdan absolutely newbie

---

### Post by speedman on 2005-04-15
You will need to create an apt config file here:

/etc/apt/apt.conf

... and specify the proxy/user settings in that file.

From man apt.conf:

       http   HTTP URIs; http::Proxy is the default http proxy to use.  It  is
              in the standard form of [http://[](http://[)[user][:pass]@]host[:port]/. Per
              host  proxies  can  also  be  specified  by   using   the   form
              http::Proxy::<host>  with  the special keyword DIRECT meaning to
              use no proxies. The http_proxy environment variable  will  over&#8208;
              ride all settings.

Specific apt.conf config examples can be found here:

/usr/share/doc/apt/examples/configure-index.gz

Google can also shed some light for you:

[http://www.google.com/search?hl=en&lr=&q=apt-get+proxy+auth&btnG=Search](http://www.google.com/search?hl=en&lr=&q=apt-get+proxy+auth&btnG=Search)

HTH


Regards,

SM

---

### Post by PeteJ on 2005-04-15
My proxy is for http only, following:  
A parent's guide to Linux Web filtering, by Joe Bolin
[http://desktops.linux.com/desktops/04/07/01/1833212.shtml?tid=49&tid=99&tid=13](http://desktops.linux.com/desktops/04/07/01/1833212.shtml?tid=49&tid=99&tid=13)

I couldn't get apt--get to get through the proxy using various tools including apt-setup, export http_proxy, and editing  /etc/apt/apt.conf.d/70debconf.

So...I'm experimenting with upgrading from Warty to Hoary by replacing the http with ftp in my /etc/apt/sources.list repository.  It's Get-ting pkg 390 at the moment, with about 30 minutes to go.

Is there any problem with that ftp replacement trick?  

I copied the below sources.list from somewhere.  

I noticed that deb [ftp://jrfonseca.dyndns.org/debian/](ftp://jrfonseca.dyndns.org/debian/) ./ doesn't accept ftp--updating my java via ftp is a project for another day.

Thanks,
Pete 

petjal@ubuntu:~ $ cat /etc/apt/sources.list
## The following lines pertain to supported packages:
deb [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) hoary main restricted
deb-src [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) hoary main restricted

## The following lines pertain to security updates:
deb [ftp://security.ubuntu.com/ubuntu/](ftp://security.ubuntu.com/ubuntu/) hoary-security main restricted
deb-src [ftp://security.ubuntu.com/ubuntu/](ftp://security.ubuntu.com/ubuntu/) hoary-security main restricted

## Uncomment after release to continue getting updates:
deb [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) hoary-updates main restricted

## IMPORTANT:
## Software from the following repositories are ENTIRELY UNSUPPORTED by
## the Ubuntu team, and may not be under a free licence. This means that
## software in these repositories WILL NOT receive any review or updates
## from the Ubuntu security team either. These packages are provided as a
## service to our users and nothing more.

## Uncomment the following two lines to add software from the 'universe' and
## 'multiverse' repositories:
deb [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) hoary universe multiverse
deb-src [ftp://archive.ubuntu.com/ubuntu/](ftp://archive.ubuntu.com/ubuntu/) hoary universe multiverse

## Uncomment the following line to add Java software:
deb [ftp://jrfonseca.dyndns.org/debian/](ftp://jrfonseca.dyndns.org/debian/) ./

petjal@ubuntu:~ $

---

### Post by Halfdan on 2005-04-18
I've made the changes, made 01acquire file in apt.conf.d folder, but no succes...

What can I do in that case, if my firewall-login is [email]xy@mail.zz[/email].

http_proxy=http://xy@mail.zz:pass@proxy:port/ ??? If I define this, the answer: Couldn't resolve host!

---

### Post by Halfdan on 2005-04-21
Succes, the apostrophes :-)

Acquire::http::Proxy "http://[COLOR=Red]"[/COLOR]xx@yy.zz[COLOR=Red]"[/COLOR]:[COLOR=Red]"[/COLOR]password[COLOR=Red]"[/COLOR]@myproxy:3128"

---

### Post by ReefShark on 2005-05-27
I've tried the above...
```
/etc/apt/apt.conf.d/01aquire
acquire::http::proxy "http://username:pwd@proxyserver:port";
```
... and a view variations on the theme  :wink: 

When I try to update (as root) I get the errors:
```
Err http://security.ubuntu.com hoary-security/main Packages
  502 Proxy Error ( The ISA Server denies the specified Uniform Resource Locator (URL).  )
Err http://security.ubuntu.com hoary-security/restricted Packages
  502 Proxy Error ( The ISA Server denies the specified Uniform Resource Locator (URL).  )
Err http://security.ubuntu.com hoary-security/universe Packages
  502 Proxy Error ( The ISA Server denies the specified Uniform Resource Locator (URL).  )
Err http://security.ubuntu.com hoary-security/multiverse Packages
  502 Proxy Error ( The ISA Server denies the specified Uniform Resource Locator (URL).  )
```
etc...

What am I doing wrong? I can connect to the internet with the same proxysettings (in Firefox) just fine, even the security.ubuntu.com (and any other) website.  :?

---

### Post by x3ja on 2005-06-20
I have had the same error (ISA Server denies the specified URL).  I have tried all the above plus I tried something from [http://wiki.colinux.org/cgi-bin/coLinuxIAQ#A3](http://wiki.colinux.org/cgi-bin/coLinuxIAQ#A3) where it suggests:

export http_proxy=http://domainname\\user:password@YOUR_PROXY:8080/

But that doesn't work for me either (I've even tried domainname.local)

Any more ideas?

---

### Post by x3ja on 2006-01-11
**FINALLY** found my way around this using this script to be a proxy to my ISA Server...
[http://ntlmaps.sourceforge.net/]("http://ntlmaps.sourceforge.net/"). 

WOO! :D

---

### Post by ailanpair on 2006-12-28
WOW!!! It works across a Novell network too! THANKS HEAPS!!!

---

