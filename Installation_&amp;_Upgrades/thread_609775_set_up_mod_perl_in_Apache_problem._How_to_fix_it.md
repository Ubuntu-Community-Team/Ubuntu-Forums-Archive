---
title: "set up mod_perl in Apache problem. How to fix it?"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by oalexandrino on 2007-11-11
Hello all,

I'm trying to set up mod_perl "mod_perl-2.0.2" to "Apache/2.2.6" in ubuntu.

what have I done already?

1. I've downloaded mod_perl-2.0.2.tar.gz 
2. unpack it
3. I followed the steps found in the INSTALL file

Simple install:

  % perl Makefile.PL MP_APXS=/usr/local/apache2/bin/apxs
  % make && make test
  % make install

The location of "apxs" is really correct in my system as the command above says

but the results of the first command is not as I was expecting

```


oalexandrino@oalexandrino:~/Desktop/downloads/perl/mod_perl-2.0.2$ perl Makefile.PL MP_APXS=/usr/local/apache2/bin/apxs
Reading Makefile.PL args from @ARGV
   MP_APXS = /usr/local/apache2/bin/apxs
no conflicting prior mod_perl version found - good.
************* WARNING *************

  Your Perl is configured to link against libgdbm,
  but libgdbm.so was not found.
  You could just symlink it to /usr/lib/libgdbm.so.3.0.0


************* WARNING *************
Configuring Apache/2.2.60 mod_perl2/2.0.2 Perl/v5.8.8
[   info] generating script t/TEST
[   info] generating script ./t/cgi-bin/cookies.pl
Writing Makefile for Apache::Test
Checking for File::Spec...ok
Checking for Cwd...ok
[   info] generating script t/TEST
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for ModPerl::Registry
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for APR::Base64
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for APR::Brigade
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for APR::Bucket
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for APR::BucketAlloc
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for APR::BucketType
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for APR::Date
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for APR::Error
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for APR::Finfo
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for APR::IpSubnet
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for APR::OS
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for APR::Pool
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for APR::SockAddr
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for APR::Socket
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for APR::Status
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for APR::String
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for APR::Table
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for APR::ThreadMutex
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for APR::URI
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for APR::UUID
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for APR::Util
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for APR
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for Apache2::Access
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for Apache2::CmdParms
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for Apache2::Command
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for Apache2::Connection
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for Apache2::Directive
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for Apache2::Filter
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for Apache2::FilterRec
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for Apache2::HookRun
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for Apache2::Log
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for Apache2::MPM
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for Apache2::Module
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for Apache2::Process
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for Apache2::RequestIO
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for Apache2::RequestRec
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for Apache2::RequestUtil
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for Apache2::Response
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for Apache2::ServerRec
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for Apache2::ServerUtil
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for Apache2::SubProcess
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for Apache2::SubRequest
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for Apache2::URI
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for Apache2::Util
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for Apache2
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for ModPerl::Global
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for ModPerl::Util
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for ModPerl
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for ModPerl::WrapXS
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for APR
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for APR::Const
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for APR::PerlIO
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for libaprext
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for APR_build
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for Apache2::Const
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for Apache2_build
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for ModPerl::Const
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for ModPerl
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for ModPerl::XS
Argument "6.30_01" isn't numeric in numeric ge (>=) at lib/ModPerl/BuildMM.pm line 196.
Writing Makefile for mod_perl2
[warning] mod_perl dso library will be built as mod_perl.so
[warning] You'll need to add the following to httpd.conf:
[warning] 
[warning]   LoadModule perl_module modules/mod_perl.so
[warning] 
[warning] depending on your build, mod_perl might not live in
[warning] the modules/ directory.

[warning] Check the results of
[warning] 
[warning]   $ /usr/local/apache2/bin/apxs -q LIBEXECDIR
[warning] 
[warning] and adjust the LoadModule directive accordingly.


```

So, after that obviously there is no "mode_perl.so" under Apache folder module.

How could I fix it?

---

### Post by oalexandrino on 2007-11-12
anybody could reply yet, but I have already found an answer

[http://www.mail-archive.com/dev@perl.apache.org/msg10968.html](http://www.mail-archive.com/dev@perl.apache.org/msg10968.html)

there is a bug in a script called BuildMM.pm

there wasn't a reg expression so that the 6.30_01 version run

thanks anyway

---

