---
title: "cpan DBD::mysql UBUNTU server 14.04.03"
date: 2015-12-08
forum: Installation &amp; Upgrades
---

### Post by oho27m on 2015-12-08
Hi, 

I'm trying to install DBI module, but I have some problems with it.
this is output:

```
cpan DBD::mysql
Reading '/root/.cpan/Metadata'
  Database was generated on Mon, 07 Dec 2015 23:17:02 GMT
Running install for module 'DBD::mysql'
Running make for C/CA/CAPTTOFU/DBD-mysql-4.033.tar.gz
Checksum for /root/.cpan/sources/authors/id/C/CA/CAPTTOFU/DBD-mysql-4.033.tar.gz ok
---- Unsatisfied dependencies detected during ----
----      CAPTTOFU/DBD-mysql-4.033.tar.gz     ----
    DBI [build_requires]
Running make test
  Make had some problems, won't test
  Delayed until after prerequisites
Running make install
  Make had some problems, won't install
  Delayed until after prerequisites
Running install for module 'DBI'
Running make for T/TI/TIMB/DBI-1.634.tar.gz
Checksum for /root/.cpan/sources/authors/id/T/TI/TIMB/DBI-1.634.tar.gz ok


  CPAN.pm: Building T/TI/TIMB/DBI-1.634.tar.gz




*** Your LANG environment variable is set to 'en_US.UTF-8'
*** This may cause problems for some perl installations.
*** If you get test failures, please try again with LANG unset.
*** If that then works, please email [EMAIL="dbi-dev@perl.org"]dbi-dev@perl.org[/EMAIL] with details
*** including the output of 'perl -V'


Your perl was compiled with gcc (version 4.8.2), okay.
Creating test wrappers for DBD::Gofer:
t/zvg_01basics.t 
t/zvg_02dbidrv.t 
t/zvg_03handle.t 
t/zvg_04mods.t 
t/zvg_05concathash.t 
t/zvg_06attrs.t 
t/zvg_07kids.t 
t/zvg_08keeperr.t 
t/zvg_09trace.t 
t/zvg_10examp.t 
t/zvg_11fetch.t 
t/zvg_12quote.t 
t/zvg_13taint.t 
t/zvg_14utf8.t 
t/zvg_15array.t 
t/zvg_16destroy.t 
t/zvg_19fhtrace.t 
t/zvg_20meta.t 
t/zvg_30subclass.t 
t/zvg_31methcache.t 
t/zvg_35thrclone.t (use threads)
t/zvg_40profile.t 
t/zvg_41prof_dump.t 
t/zvg_42prof_data.t 
t/zvg_43prof_env.t 
t/zvg_48dbi_dbd_sqlengine.t 
t/zvg_49dbd_file.t 
t/zvg_50dbm_simple.t 
t/zvg_51dbm_file.t 
t/zvg_52dbm_complex.t 
t/zvg_60preparse.t 
t/zvg_65transact.t 
t/zvg_70callbacks.t 
t/zvg_72childhandles.t 
t/zvg_80proxy.t 
t/zvg_85gofer.t 
t/zvg_86gofer_fail.t 
t/zvg_87gofer_cache.t 
t/zvg_90sql_type_cast.t 
Creating test wrappers for DBI::SQL::Nano:
t/zvn_48dbi_dbd_sqlengine.t 
t/zvn_49dbd_file.t 
t/zvn_50dbm_simple.t 
t/zvn_51dbm_file.t 
t/zvn_52dbm_complex.t 
t/zvn_85gofer.t 
Creating test wrappers for DBI::PurePerl:
t/zvp_01basics.t 
t/zvp_02dbidrv.t 
t/zvp_03handle.t 
t/zvp_04mods.t 
t/zvp_05concathash.t 
t/zvp_06attrs.t 
t/zvp_07kids.t 
t/zvp_08keeperr.t 
t/zvp_09trace.t 
t/zvp_10examp.t 
t/zvp_11fetch.t 
t/zvp_12quote.t 
t/zvp_13taint.t 
t/zvp_14utf8.t 
t/zvp_15array.t 
t/zvp_16destroy.t 
t/zvp_19fhtrace.t 
t/zvp_20meta.t 
t/zvp_30subclass.t 
t/zvp_31methcache.t 
t/zvp_35thrclone.t (use threads)
t/zvp_40profile.t 
t/zvp_41prof_dump.t 
t/zvp_42prof_data.t 
t/zvp_43prof_env.t 
t/zvp_48dbi_dbd_sqlengine.t 
t/zvp_49dbd_file.t 
t/zvp_50dbm_simple.t 
t/zvp_51dbm_file.t 
t/zvp_52dbm_complex.t 
t/zvp_60preparse.t 
t/zvp_65transact.t 
t/zvp_70callbacks.t 
t/zvp_72childhandles.t 
t/zvp_80proxy.t 
t/zvp_85gofer.t 
t/zvp_86gofer_fail.t 
t/zvp_87gofer_cache.t 
t/zvp_90sql_type_cast.t 
Creating test wrappers for DBD::Gofer + DBI::SQL::Nano:
t/zvxgn_48dbi_dbd_sqlengine.t 
t/zvxgn_49dbd_file.t 
t/zvxgn_50dbm_simple.t 
t/zvxgn_51dbm_file.t 
t/zvxgn_52dbm_complex.t 
t/zvxgn_85gofer.t 
Creating test wrappers for DBD::Gofer + DBI::PurePerl:
t/zvxgp_01basics.t 
t/zvxgp_02dbidrv.t 
t/zvxgp_03handle.t 
t/zvxgp_04mods.t 
t/zvxgp_05concathash.t 
t/zvxgp_06attrs.t 
t/zvxgp_07kids.t 
t/zvxgp_08keeperr.t 
t/zvxgp_09trace.t 
t/zvxgp_10examp.t 
t/zvxgp_11fetch.t 
t/zvxgp_12quote.t 
t/zvxgp_13taint.t 
t/zvxgp_14utf8.t 
t/zvxgp_15array.t 
t/zvxgp_16destroy.t 
t/zvxgp_19fhtrace.t 
t/zvxgp_20meta.t 
t/zvxgp_30subclass.t 
t/zvxgp_31methcache.t 
t/zvxgp_35thrclone.t (use threads)
t/zvxgp_40profile.t 
t/zvxgp_41prof_dump.t 
t/zvxgp_42prof_data.t 
t/zvxgp_43prof_env.t 
t/zvxgp_48dbi_dbd_sqlengine.t 
t/zvxgp_49dbd_file.t 
t/zvxgp_50dbm_simple.t 
t/zvxgp_51dbm_file.t 
t/zvxgp_52dbm_complex.t 
t/zvxgp_60preparse.t 
t/zvxgp_65transact.t 
t/zvxgp_70callbacks.t 
t/zvxgp_72childhandles.t 
t/zvxgp_80proxy.t 
t/zvxgp_85gofer.t 
t/zvxgp_86gofer_fail.t 
t/zvxgp_87gofer_cache.t 
t/zvxgp_90sql_type_cast.t 
Creating test wrappers for DBI::SQL::Nano + DBI::PurePerl:
t/zvxnp_48dbi_dbd_sqlengine.t 
t/zvxnp_49dbd_file.t 
t/zvxnp_50dbm_simple.t 
t/zvxnp_51dbm_file.t 
t/zvxnp_52dbm_complex.t 
t/zvxnp_85gofer.t 
Creating test wrappers for DBD::Gofer + DBI::SQL::Nano + DBI::PurePerl:
t/zvxgnp_48dbi_dbd_sqlengine.t 
t/zvxgnp_49dbd_file.t 
t/zvxgnp_50dbm_simple.t 
t/zvxgnp_51dbm_file.t 
t/zvxgnp_52dbm_complex.t 
t/zvxgnp_85gofer.t 
Checking if your kit is complete...
Looks good


    I see you're using perl 5.018002 on x86_64-linux-gnu-thread-multi, okay.
    Remember to actually *read* the README file!
    Use  'make' to build the software (dmake or nmake on Windows).
    Then 'make test' to execute self tests.
    Then 'make install' to install the DBI and then delete this working
    directory before unpacking and building any DBD::* drivers.


Writing Makefile for DBI
Writing MYMETA.yml and MYMETA.json
/usr/bin/perl -MExtUtils::Command -e 'mkpath' -- blib/lib/DBI
rm -f blib/lib/DBI/Changes.pm
cp Changes blib/lib/DBI/Changes.pm
cp lib/DBI/Gofer/Serializer/Storable.pm blib/lib/DBI/Gofer/Serializer/Storable.pm
cp DBIXS.h blib/arch/auto/DBI/DBIXS.h
cp lib/DBI/FAQ.pm blib/lib/DBI/FAQ.pm
cp lib/DBI/SQL/Nano.pm blib/lib/DBI/SQL/Nano.pm
cp lib/DBI/Gofer/Transport/Base.pm blib/lib/DBI/Gofer/Transport/Base.pm
cp dbixs_rev.h blib/arch/auto/DBI/dbixs_rev.h
cp lib/DBI/Util/CacheMemory.pm blib/lib/DBI/Util/CacheMemory.pm
cp lib/DBI/Const/GetInfoType.pm blib/lib/DBI/Const/GetInfoType.pm
cp dbixs_rev.pl blib/lib/dbixs_rev.pl
cp lib/Win32/DBIODBC.pm blib/lib/Win32/DBIODBC.pm
cp DBI.pm blib/lib/DBI.pm
cp lib/DBI/Gofer/Serializer/DataDumper.pm blib/lib/DBI/Gofer/Serializer/DataDumper.pm
cp lib/DBI/Profile.pm blib/lib/DBI/Profile.pm
cp lib/DBD/Sponge.pm blib/lib/DBD/Sponge.pm
cp lib/DBI/ProfileData.pm blib/lib/DBI/ProfileData.pm
cp lib/DBD/Proxy.pm blib/lib/DBD/Proxy.pm
cp lib/DBI/ProfileSubs.pm blib/lib/DBI/ProfileSubs.pm
cp lib/DBI/DBD.pm blib/lib/DBI/DBD.pm
cp lib/DBI/ProfileDumper/Apache.pm blib/lib/DBI/ProfileDumper/Apache.pm
cp lib/DBD/Gofer/Policy/classic.pm blib/lib/DBD/Gofer/Policy/classic.pm
cp lib/DBI/DBD/SqlEngine/Developers.pod blib/lib/DBI/DBD/SqlEngine/Developers.pod
cp lib/DBD/NullP.pm blib/lib/DBD/NullP.pm
cp lib/DBI/Util/_accessor.pm blib/lib/DBI/Util/_accessor.pm
cp lib/DBD/Gofer/Policy/Base.pm blib/lib/DBD/Gofer/Policy/Base.pm
cp lib/DBI/Const/GetInfo/ANSI.pm blib/lib/DBI/Const/GetInfo/ANSI.pm
cp lib/DBI/DBD/SqlEngine/HowTo.pod blib/lib/DBI/DBD/SqlEngine/HowTo.pod
cp lib/DBI/DBD/SqlEngine.pm blib/lib/DBI/DBD/SqlEngine.pm
cp lib/DBD/Gofer/Transport/pipeone.pm blib/lib/DBD/Gofer/Transport/pipeone.pm
cp lib/DBD/Gofer/Policy/rush.pm blib/lib/DBD/Gofer/Policy/rush.pm
cp Driver.xst blib/arch/auto/DBI/Driver.xst
cp dbd_xsh.h blib/arch/auto/DBI/dbd_xsh.h
cp lib/DBD/File.pm blib/lib/DBD/File.pm
cp lib/DBI/Gofer/Execute.pm blib/lib/DBI/Gofer/Execute.pm
cp lib/DBD/File/Developers.pod blib/lib/DBD/File/Developers.pod
cp lib/DBD/File/HowTo.pod blib/lib/DBD/File/HowTo.pod
cp dbipport.h blib/arch/auto/DBI/dbipport.h
cp lib/DBD/File/Roadmap.pod blib/lib/DBD/File/Roadmap.pod
cp lib/DBD/ExampleP.pm blib/lib/DBD/ExampleP.pm
cp lib/DBI/Gofer/Request.pm blib/lib/DBI/Gofer/Request.pm
cp lib/DBD/Gofer/Transport/stream.pm blib/lib/DBD/Gofer/Transport/stream.pm
cp dbi_sql.h blib/arch/auto/DBI/dbi_sql.h
cp lib/DBI/Gofer/Transport/stream.pm blib/lib/DBI/Gofer/Transport/stream.pm
cp lib/DBI/ProxyServer.pm blib/lib/DBI/ProxyServer.pm
cp lib/DBD/DBM.pm blib/lib/DBD/DBM.pm
cp lib/DBI/Const/GetInfoReturn.pm blib/lib/DBI/Const/GetInfoReturn.pm
cp lib/DBI/Gofer/Transport/pipeone.pm blib/lib/DBI/Gofer/Transport/pipeone.pm
cp dbivport.h blib/arch/auto/DBI/dbivport.h
cp lib/DBI/ProfileDumper.pm blib/lib/DBI/ProfileDumper.pm
cp lib/DBI/Gofer/Response.pm blib/lib/DBI/Gofer/Response.pm
cp lib/DBD/Gofer/Transport/corostream.pm blib/lib/DBD/Gofer/Transport/corostream.pm
cp Driver_xst.h blib/arch/auto/DBI/Driver_xst.h
cp lib/DBI/PurePerl.pm blib/lib/DBI/PurePerl.pm
cp lib/DBD/Gofer/Policy/pedantic.pm blib/lib/DBD/Gofer/Policy/pedantic.pm
cp lib/DBI/DBD/Metadata.pm blib/lib/DBI/DBD/Metadata.pm
cp lib/DBI/Gofer/Serializer/Base.pm blib/lib/DBI/Gofer/Serializer/Base.pm
cp lib/DBD/Gofer/Transport/Base.pm blib/lib/DBD/Gofer/Transport/Base.pm
cp lib/DBI/Const/GetInfo/ODBC.pm blib/lib/DBI/Const/GetInfo/ODBC.pm
cp lib/DBI/W32ODBC.pm blib/lib/DBI/W32ODBC.pm
cp lib/DBD/Gofer/Transport/null.pm blib/lib/DBD/Gofer/Transport/null.pm
cp lib/Bundle/DBI.pm blib/lib/Bundle/DBI.pm
cp lib/DBD/Gofer.pm blib/lib/DBD/Gofer.pm
/usr/bin/perl -p -e "s/~DRIVER~/Perl/g" ./Driver.xst > Perl.xsi
/usr/bin/perl /usr/share/perl/5.18/ExtUtils/xsubpp  -typemap /usr/share/perl/5.18/ExtUtils/typemap -typemap typemap  Perl.xs > Perl.xsc && mv Perl.xsc Perl.c
cc -c   -D_REENTRANT -D_GNU_SOURCE -DDEBIAN -fstack-protector -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2 -g   -DVERSION=\"1.634\" -DXS_VERSION=\"1.634\" -fPIC "-I/usr/lib/perl/5.18/CORE"  -W -Wall -Wpointer-arith -Wbad-function-cast -Wno-comment -Wno-sign-compare -Wno-cast-qual -Wmissing-noreturn -Wno-unused-parameter Perl.c
/bin/sh: 1: cc: not found
make: *** [Perl.o] Error 127
  TIMB/DBI-1.634.tar.gz
  make -- NOT OK
'YAML' not installed, will not store persistent state
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running make for C/CA/CAPTTOFU/DBD-mysql-4.033.tar.gz
Warning: Prerequisite 'DBI => 1.08' for 'CAPTTOFU/DBD-mysql-4.033.tar.gz' failed when processing 'TIMB/DBI-1.634.tar.gz' with 'make => NO'. Continuing, but chances to succeed are limited.


  CPAN.pm: Building C/CA/CAPTTOFU/DBD-mysql-4.033.tar.gz


Can't locate DBI/DBD.pm in @INC (you may need to install the DBI::DBD module) (@INC contains: /etc/perl /usr/local/lib/perl/5.18.2 /usr/local/share/perl/5.18.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.18 /usr/share/perl/5.18 /usr/local/lib/site_perl .) at Makefile.PL line 15.
Warning: No success on command[/usr/bin/perl Makefile.PL INSTALLDIRS=site]
  CAPTTOFU/DBD-mysql-4.033.tar.gz
  /usr/bin/perl Makefile.PL INSTALLDIRS=site -- NOT OK
Running make test
  Make had some problems, won't test
Running make install
  Make had some problems, won't install
Could not read metadata file. Falling back to other methods to determine prerequisites
```

---

