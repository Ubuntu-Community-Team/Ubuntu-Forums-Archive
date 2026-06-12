---
title: "Problem Upgrading Perl"
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by makekee on 2008-10-25
Hi guys 

I need to do both an update and an upgrade on Ubuntu 8.04. the update goes fine but the after entering the command:
[CENTER]sudo apt-get upgrade[/CENTER]

i get this error at the end of the process:

[B]ldconfig deferred processing now taking place
Errors were encountered while processing:
 libxml-sax-perl
 libxml-libxml-perl
 libxml-libxslt-perl
 libxml-simple-perl
E: Sub-process /usr/bin/dpkg returned an error code (1)
user@eg-server1:~$ [/B]

I tried using synaptic package manager to do the same job it returns:
E: libxml-sax-perl: subprocess post-installation script returned error exit status 255
E: libxml-libxml-perl: dependency problems - leaving unconfigured
E: libxml-libxslt-perl: dependency problems - leaving unconfigured
E: libxml-simple-perl: dependency problems - leaving unconfigured

Is there a way out of this?

ephraim

---

### Post by Magneus on 2008-11-12
I'll confess I'm not a Linux/Ubuntu guru, (only been a Linux guy for 3 months or so) but I'll tell you this much.

All of these files:

libxml-sax-perl
libxml-libxml-perl
libxml-libxslt-perl
libxml-simple-perl

Are Perl modules (~= libraries), and as such can either be tracked down on websites, through APT (if it were working for you), or from Perl's CPAN.

I'm guessing that this should solve your problem (not sure, though!), as it looks like APT is complaining about dependencies for those modules. 

If you're willing to give it a shot, you can find a tutorial to CPAN here:
[http://perl.about.com/od/packagesmodules/qt/perlcpan.htm](http://perl.about.com/od/packagesmodules/qt/perlcpan.htm)

**One Note!**
Those libraries are known by slightly different names in Perl/CPAN. 
For example: libxml-simple-perl in Ubuntu/Debian is  [XML::Simple]("http://www.perlmonks.org/index.pl?node_id=30695") in Perl land.

Good luck!

---

