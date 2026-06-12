---
title: "How to Install The Latest Perl version 5.10"
date: 2008-08-19
forum: Installation &amp; Upgrades
---

### Post by udaykiranchapala on 2008-08-19
Hello everyone.
I am basically a windows user, and i've recently shifted to Ubuntu.

I actually need to install below CPAN modules

Net::SSLeay
IO::Socket::SSL (requires Net::SSLeay)
Net::LDAP (requires IO::Socket::SSL)

and
libnet-1.22

I have downloaded the Net::SSLeay package from CPAN site and tried to install with terminal by

perl Makefile.PL
sudo make
sudo make test
sudo make install

which gave me the error saying

*** Found OpenSSL-0.9.8g installed in /usr
*** Be sure to use the same compiler and options to compile your OpenSSL, perl,
and Net::SSLeay. Mixing and matching compilers is not supported.

and while installing libnet it says

system already has 0.38 version.

I tried to uninstall these from the synaptic pakage manager, but was uninstalling almost everthing and has caused great system instability.

Finally I searched on the answers.launchpad.net and found that installing
libio-socket-ssl-perl_1.13-1_all and libnet-ssleay-perl_1.35-1ubuntu1_i386 would help.
I have downloaded the intrepid .deb packages of them and libio-socket-ssl-perl_1.13-1 got successfully installed and while installing libnet-ssleay-perl_1.35-1ubuntu1_i386 was showing an error
Dependency not satisfiable: perl

I tried to install the latest perl 5.10 by downloading another deb package and it shows
dependency perl-base
when i was installing perl-base it says

dpkg: regarding .../perl-base_5.10.0-11.1ubuntu2_i386.deb containing perl-base:
 perl-base breaks doc-base (<<0.8.16)
dpkg: error processing /home/sympa/Desktop/perl-base_5.10.0.11.1ubuntu2_i386.deb (--install):
installing perl-base would break doc base, and deconfiguration is not permitted.

when i tried to install perl manually it returned make [1] after make install.
After this I again tried to install libnet-ssleay-perl_1.35-1ubuntu1_i386 but with no success.

Can anyone please help me with this.
Thanks in advance.

Regards,
UdayKiran Chapala.

---

