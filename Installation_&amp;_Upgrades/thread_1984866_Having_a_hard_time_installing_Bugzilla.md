---
title: "Having a hard time installing Bugzilla"
date: 2012-05-22
forum: Installation &amp; Upgrades
---

### Post by YourSurrogateGod on 2012-05-22
Not sure if this is the best part of the forum to post at.  If not, someone please move it :-) .

I'm following these instructions to install Bugzilla on my machine.
[http://vibhurishi.blogspot.com/2009/05/howto-install-bugzilla-on-ubuntu-9.html](http://vibhurishi.blogspot.com/2009/05/howto-install-bugzilla-on-ubuntu-9.html)

I got to the part about installing all of the Perl modules and after checking if I had everything installed (which I didn't) and installing them... I got this error:
```
Checking for                 CPAN (v1.81)     ok: found v1.94 
Checking for                 YAML (any)       ok: found v0.81 
Checking for   ExtUtils-MakeMaker (v6.31)     ok: found v6.55_02 
Use of uninitialized value in open at /usr/local/bugzilla-4.2.1/lib/i686-linux-gnu-thread-multi/Test/Taint.pm line 334, <DATA> line 558.
Use of uninitialized value in open at /usr/local/bugzilla-4.2.1/lib/i686-linux-gnu-thread-multi/Test/Taint.pm line 334, <DATA> line 558.
Use of uninitialized value in open at /usr/local/bugzilla-4.2.1/lib/i686-linux-gnu-thread-multi/Test/Taint.pm line 334, <DATA> line 558.
Use of uninitialized value in open at /usr/local/bugzilla-4.2.1/lib/i686-linux-gnu-thread-multi/Test/Taint.pm line 334, <DATA> line 558.
Use of uninitialized value in open at /usr/local/bugzilla-4.2.1/lib/i686-linux-gnu-thread-multi/Test/Taint.pm line 334, <DATA> line 558.
Going to read '/home/ats/.cpan/Metadata'
  Database was generated on Tue, 22 May 2012 14:03:03 GMT
Installing DateTime version 0.74...
DateTime is up to date (0.74).
Installing DateTime::TimeZone version 1.46...
DateTime::TimeZone is up to date (1.46).
Installing Apache2::SizeLimit version 0.96...
Running install for module 'Apache2::SizeLimit'
Running make for P/PH/PHRED/Apache-SizeLimit-0.96.tar.gz
Checksum for /home/ats/.cpan/source/authors/id/P/PH/PHRED/Apache-SizeLimit-0.96.tar.gz ok

  CPAN.pm: Going to build P/PH/PHRED/Apache-SizeLimit-0.96.tar.gz

Can't find the mod_perl include dir (reason: path /usr/include/apache2 doesn't exist) at /usr/lib/perl5/Apache2/Build.pm line 2030.
Warning: No success on command[/usr/bin/perl Makefile.PL  LIB="/usr/local/bugzilla-4.2.1/lib" INSTALLMAN1DIR="/usr/local/bugzilla-4.2.1/lib/man/man1" INSTALLMAN3DIR="/usr/local/bugzilla-4.2.1/lib/man/man3" INSTALLBIN="/usr/local/bugzilla-4.2.1/lib/bin" INSTALLSCRIPT="/usr/local/bugzilla-4.2.1/lib/bin" INSTALLDIRS=perl]
  PHRED/Apache-SizeLimit-0.96.tar.gz
  /usr/bin/perl Makefile.PL  LIB="/usr/local/bugzilla-4.2.1/lib" INSTALLMAN1DIR="/usr/local/bugzilla-4.2.1/lib/man/man1" INSTALLMAN3DIR="/usr/local/bugzilla-4.2.1/lib/man/man3" INSTALLBIN="/usr/local/bugzilla-4.2.1/lib/bin" INSTALLSCRIPT="/usr/local/bugzilla-4.2.1/lib/bin" INSTALLDIRS=perl -- NOT OK
Skipping test because of notest pragma
Running make install
  Make had some problems, won't install

```

And now... I'm stuck.  I tried installing mod_perl using this command:
```
sudo apt-get install libapache2-mod-perl2
```

But that did not get rid of the above error.

Thoughts?

I have Ubuntu 11.04 running.

---

### Post by YourSurrogateGod on 2012-05-22
The other annoying thing is when I check for all of the modules:
```
$ sudo ./checksetup.pl
* This is Bugzilla 4.2.1 on perl 5.10.1
* Running on Linux 2.6.38-15-generic-pae #59-Ubuntu SMP Fri Apr 27 16:22:25 UTC 2012

Checking perl modules...
Checking for               CGI.pm (v3.51)     ok: found v3.59 
Checking for           Digest-SHA (any)       ok: found v5.47 
Checking for             TimeDate (v2.21)     ok: found v2.24 
Checking for             DateTime (v0.28)     not found 
Checking for    DateTime-TimeZone (v0.71)     not found 
Checking for                  DBI (v1.41)     ok: found v1.612 
Checking for     Template-Toolkit (v2.22)     ok: found v2.24 
Checking for           Email-Send (v2.00)     ok: found v2.198 
Checking for           Email-MIME (v1.904)    ok: found v1.910 
Checking for                  URI (v1.37)     ok: found v1.60 
Checking for       List-MoreUtils (v0.22)     ok: found v0.33 
Checking for    Math-Random-ISAAC (v1.0.1)    ok: found v1.004 

Checking available perl DBD modules...
Checking for               DBD-Pg (v1.45)     ok: found v2.19.2 
Checking for            DBD-mysql (v4.001)    ok: found v4.016 
Checking for           DBD-SQLite (v1.29)     ok: found v1.29 
Checking for           DBD-Oracle (v1.19)     not found 

The following Perl modules are optional:
Checking for                   GD (v1.20)     ok: found v2.41 
Checking for                Chart (v2.1)      ok: found v2.4.5 
Checking for          Template-GD (any)       ok: found v1.56 
Checking for           GDTextUtil (any)       ok: found v0.86 
Checking for              GDGraph (any)       ok: found v1.44 
Checking for           MIME-tools (v5.406)    ok: found v5.502 
Checking for          libwww-perl (any)       ok: found v6.04 
Checking for             XML-Twig (any)       ok: found v3.40 
Checking for          PatchReader (v0.9.6)    ok: found v0.9.6 
Checking for            perl-ldap (any)       ok: found v0.44 
Checking for          Authen-SASL (any)       ok: found v2.15 
Checking for           RadiusPerl (any)       ok: found v0.20 
Checking for            SOAP-Lite (v0.712)    ok: found v0.714 
Checking for             JSON-RPC (any)       ok: found v1.01 
Checking for              JSON-XS (v2.0)      ok: found v2.3 
Use of uninitialized value in open at lib/i686-linux-gnu-thread-multi/Test/Taint.pm line 334, <DATA> line 558.
Use of uninitialized value in open at lib/i686-linux-gnu-thread-multi/Test/Taint.pm line 334, <DATA> line 558.
Use of uninitialized value in open at lib/i686-linux-gnu-thread-multi/Test/Taint.pm line 334, <DATA> line 558.
Use of uninitialized value in open at lib/i686-linux-gnu-thread-multi/Test/Taint.pm line 334, <DATA> line 558.
Use of uninitialized value in open at lib/i686-linux-gnu-thread-multi/Test/Taint.pm line 334, <DATA> line 558.
Checking for           Test-Taint (any)       ok: found v1.04 
Checking for          HTML-Parser (v3.40)     ok: found v3.68 
Checking for        HTML-Scrubber (any)       ok: found v0.09 
Checking for               Encode (v2.21)     ok: found v2.35 
Checking for        Encode-Detect (any)       ok: found v1.01 
Checking for Email-MIME-Attachment-Stripper (any)       ok: found v1.316 
Checking for          Email-Reply (any)       ok: found v1.202 
Checking for          TheSchwartz (any)       ok: found v1.10 
Checking for       Daemon-Generic (any)       ok: found v0.82 
Checking for             mod_perl (v1.999022) ok: found v2.000004 
Checking for     Apache-SizeLimit (v0.96)     not found 
Checking for          mod_headers (any)       not found 
Checking for          mod_expires (any)       not found 
Checking for              mod_env (any)       ok 
***********************************************************************
* REQUIRED MODULES                                                    *
***********************************************************************
* Bugzilla requires you to install some Perl modules which are either *
* missing from your system, or the version on your system is too old. *
* See below for commands to install these modules.                    *
***********************************************************************
* OPTIONAL MODULES                                                    *
***********************************************************************
* Certain Perl modules are not required by Bugzilla, but by           *
* installing the latest version you gain access to additional         *
* features.                                                           *
*                                                                     *
* The optional modules you do not have installed are listed below,    *
* with the name of the feature they enable. Below that table are the  *
* commands to install each module.                                    *
***********************************************************************
*      MODULE NAME * ENABLES FEATURE(S)                               *
***********************************************************************
* Apache-SizeLimit * mod_perl                                         *
***********************************************************************
* APACHE MODULES                                                      *
***********************************************************************
* Normally, when Bugzilla is upgraded, all Bugzilla users have to     *
* clear their browser cache or Bugzilla will break. If you enable     *
* certain modules in your Apache configuration (usually called        *
* httpd.conf or apache2.conf) then your users will not have to clear  *
* their caches when you upgrade Bugzilla. The modules you need to     *
* enable are:                                                         *
*                                                                     *
*    mod_headers, mod_expires                                         *
*                                                                     *
***********************************************************************
COMMANDS TO INSTALL OPTIONAL MODULES:

Apache-SizeLimit: /usr/bin/perl install-module.pl Apache2::SizeLimit

COMMANDS TO INSTALL REQUIRED MODULES (You *must* run all these commands
and then re-run checksetup.pl):

    /usr/bin/perl install-module.pl DateTime
    /usr/bin/perl install-module.pl DateTime::TimeZone

To attempt an automatic install of every required and optional module
with one command, do:

  /usr/bin/perl install-module.pl --all

*** Installation aborted. Read the messages above. ***

```
I've tried installing those modules through aptitude and compiling by hand and _still_ it won't "see" those modules.

:(

---

