---
title: "Install DBD::mysql Perl5 Database Interface driver for MySQL database"
date: 2012-10-29
forum: Installation &amp; Upgrades
---

### Post by 1cookie on 2012-10-29
hi

I'm trying to install DBD::mysql - Perl5 Database Interface driver for the MySQL database. 
In other words: DBD::mysql is an interface between the Perl programming language and MySQL - from Google.

```

cpan[2]> install DBD:mysql
Running install for module 'DBD::mysql'
Running make for C/CA/CAPTTOFU/DBD-mysql-4.022.tar.gz
Checksum for /home/cookie/.cpan/sources/authors/id/C/CA/CAPTTOFU/DBD-mysql-4.022.tar.gz ok
Scanning cache /home/cookie/.cpan/build for sizes
............................................................................DONE

  CPAN.pm: Building C/CA/CAPTTOFU/DBD-mysql-4.022.tar.gz



PLEASE NOTE:

For 'make test' to run properly, you must ensure that the 
database user 'cookie' can connect to your MySQL server 
and has the proper privileges that these tests require such 
as 'drop table', 'create table', 'drop procedure', 'create procedure'
as well as others. 

mysql> grant all privileges on test.* to 'cookie'@'localhost' identified by 's3kr1t';

You can also optionally set the user to run 'make test' with:

perl Makefile.PL --testuser=username

I will use the following settings for compiling and testing:

  cflags        (mysql_config) = -I/usr/include/mysql -g -pipe -m32 -fPIC -g -static-libgcc -fno-omit-frame-pointer -fno-strict-aliasing -DMY_PTHREAD_FASTMUTEX=1
  embedded      (mysql_config) = 
  ldflags       (mysql_config) = 
  libs          (mysql_config) = -L/usr/lib -lmysqlclient -lpthread -lm -lrt -ldl
  mysql_config  (guessed     ) = mysql_config
  nocatchstderr (default     ) = 0
  nofoundrows   (default     ) = 0
  ssl           (guessed     ) = 0
  testdb        (default     ) = test
  testhost      (default     ) = 
  testpassword  (default     ) = 
  testsocket    (default     ) = 
  testuser      (guessed     ) = cookie

To change these settings, see 'perl Makefile.PL --help' and
'perldoc INSTALL'.

Checking if your kit is complete...
Looks good
Using DBI 1.622 (for perl 5.014002 on i686-linux-gnu-thread-multi-64int) installed in /usr/lib/perl5/auto/DBI/
Writing Makefile for DBD::mysql
Writing MYMETA.yml and MYMETA.json
cp lib/DBD/mysql.pm blib/lib/DBD/mysql.pm
cp lib/DBD/mysql/GetInfo.pm blib/lib/DBD/mysql/GetInfo.pm
cp lib/DBD/mysql/INSTALL.pod blib/lib/DBD/mysql/INSTALL.pod
cp lib/Bundle/DBD/mysql.pm blib/lib/Bundle/DBD/mysql.pm
cc -c  -I/usr/lib/perl5/auto/DBI -I/usr/include/mysql -g -pipe -m32 -fPIC -g -static-libgcc -fno-omit-frame-pointer -fno-strict-aliasing -DMY_PTHREAD_FASTMUTEX=1 -DDBD_MYSQL_INSERT_ID_IS_GOOD -g  -D_REENTRANT -D_GNU_SOURCE -DDEBIAN -fstack-protector -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2 -g   -DVERSION=\"4.022\" -DXS_VERSION=\"4.022\" -fPIC "-I/usr/lib/perl/5.14/CORE"   dbdimp.c
In file included from dbdimp.c:20:0:
dbdimp.h:23:49: fatal error: mysql.h: No such file or directory
compilation terminated.
make: *** [dbdimp.o] Error 1
  CAPTTOFU/DBD-mysql-4.022.tar.gz
  /usr/bin/make -- NOT OK
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Failed during this command:
 CAPTTOFU/DBD-mysql-4.022.tar.gz              : make NO

cpan[3]> 


```Done:
```

mysql> grant all privileges on test.* to 'cookie'@'localhost' identified by 's3kr1t';

cd /usr/include/mysql/mysql.h
no such file or directory

```I downloaded MySQL-devel-5.5.28-1.linux2.6.i386.rpm from MySQL
```

locate mysql.h
/home/cookie/Downloads/usr/include/mysql/mysql.h

```From the above then the error reports
```

dbdimp.h:23:49: fatal error: mysql.h: No such file or directory

```Can I use a symlink (from my ~/Downloads dir) or something? Which path do I use?
```

which mysql
/usr/bin/mysql

```Do I point it here?

---

### Post by 1cookie on 2012-10-29
Standing in directory
```
~/Downloads/usr/include/mysql$ 
```
I copied all folder contents across to 

```
/usr/include/mysql
```
 ```

sudo cp decimal.h my_dbug.h mysqld_ername.h plugin_ftparser.h errmsg.h my_dir.h mysqld_error.h /usr/include/mysql
sudo cp plugin.h keycache.h my_getopt.h mysql_embed.h sql_common.h m_ctype.h my_global.h mysql.h /usr/include/mysql
sudo cp sql_state.h m_string.h my_list.h mysql_time.h sslopt-case.h my_alloc.h my_net.h mysql_version.h /usr/include/mysql
sudo cp sslopt-longopts.h my_attribute.h my_pthread.h my_sys.h sslopt-vars.h my_compiler.h my_xml.h typelib.h /usr/include/mysql
sudo cp my_config.h mysql_com.h plugin_audit.h /usr/include/mysql 

```
Missing file errors seem to disappear but it still wont install:

```

Reading '/home/cookie/.cpan/Metadata'
  Database was generated on Sat, 27 Oct 2012 21:55:04 GMT
Running install for module 'DBD::mysql'
Running make for C/CA/CAPTTOFU/DBD-mysql-4.022.tar.gz
Checksum for /home/cookie/.cpan/sources/authors/id/C/CA/CAPTTOFU/DBD-mysql-4.022.tar.gz ok
Scanning cache /home/cookie/.cpan/build for sizes
............................................................................DONE

  CPAN.pm: Building C/CA/CAPTTOFU/DBD-mysql-4.022.tar.gz



PLEASE NOTE:

For 'make test' to run properly, you must ensure that the 
database user 'cookie' can connect to your MySQL server 
and has the proper privileges that these tests require such 
as 'drop table', 'create table', 'drop procedure', 'create procedure'
as well as others. 

mysql> grant all privileges on test.* to 'cookie'@'localhost' identified by 's3kr1t';

You can also optionally set the user to run 'make test' with:

perl Makefile.PL --testuser=username

I will use the following settings for compiling and testing:

  cflags        (mysql_config) = -I/usr/include/mysql -g -pipe -m32 -fPIC -g -static-libgcc -fno-omit-frame-pointer -fno-strict-aliasing -DMY_PTHREAD_FASTMUTEX=1
  embedded      (mysql_config) = 
  ldflags       (mysql_config) = 
  libs          (mysql_config) = -L/usr/lib -lmysqlclient -lpthread -lm -lrt -ldl
  mysql_config  (guessed     ) = mysql_config
  nocatchstderr (default     ) = 0
  nofoundrows   (default     ) = 0
  ssl           (guessed     ) = 0
  testdb        (default     ) = test
  testhost      (default     ) = 
  testpassword  (default     ) = 
  testsocket    (default     ) = 
  testuser      (guessed     ) = cookie

To change these settings, see 'perl Makefile.PL --help' and
'perldoc INSTALL'.

Checking if your kit is complete...
Looks good
Using DBI 1.622 (for perl 5.014002 on i686-linux-gnu-thread-multi-64int) installed in /usr/lib/perl5/auto/DBI/
Writing Makefile for DBD::mysql
Writing MYMETA.yml and MYMETA.json
cp lib/DBD/mysql.pm blib/lib/DBD/mysql.pm
cp lib/DBD/mysql/GetInfo.pm blib/lib/DBD/mysql/GetInfo.pm
cp lib/DBD/mysql/INSTALL.pod blib/lib/DBD/mysql/INSTALL.pod
cp lib/Bundle/DBD/mysql.pm blib/lib/Bundle/DBD/mysql.pm
cc -c  -I/usr/lib/perl5/auto/DBI -I/usr/include/mysql -g -pipe -m32 -fPIC -g -static-libgcc -fno-omit-frame-pointer -fno-strict-aliasing -DMY_PTHREAD_FASTMUTEX=1 -DDBD_MYSQL_INSERT_ID_IS_GOOD -g  -D_REENTRANT -D_GNU_SOURCE -DDEBIAN -fstack-protector -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2 -g   -DVERSION=\"4.022\" -DXS_VERSION=\"4.022\" -fPIC "-I/usr/lib/perl/5.14/CORE"   dbdimp.c
dbdimp.c: In function ‘mysql_db_FETCH_attrib’:
dbdimp.c:2549:15: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
dbdimp.c: In function ‘mysql_st_FETCH_attrib’:
dbdimp.c:4480:16: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/usr/bin/perl -p -e "s/~DRIVER~/mysql/g" /usr/lib/perl5/auto/DBI/Driver.xst > mysql.xsi
/usr/bin/perl /usr/share/perl/5.14/ExtUtils/xsubpp  -typemap /usr/share/perl/5.14/ExtUtils/typemap  mysql.xs > mysql.xsc && mv mysql.xsc mysql.c
Warning: duplicate function definition 'do' detected in mysql.xs, line 242
Warning: duplicate function definition 'rows' detected in mysql.xs, line 752
cc -c  -I/usr/lib/perl5/auto/DBI -I/usr/include/mysql -g -pipe -m32 -fPIC -g -static-libgcc -fno-omit-frame-pointer -fno-strict-aliasing -DMY_PTHREAD_FASTMUTEX=1 -DDBD_MYSQL_INSERT_ID_IS_GOOD -g  -D_REENTRANT -D_GNU_SOURCE -DDEBIAN -fstack-protector -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2 -g   -DVERSION=\"4.022\" -DXS_VERSION=\"4.022\" -fPIC "-I/usr/lib/perl/5.14/CORE"   mysql.c
mysql.xs: In function ‘XS_DBD__mysql__GetInfo_dbd_mysql_get_info’:
mysql.xs:931:4: warning: format ‘%i’ expects argument of type ‘int’, but argument 2 has type ‘struct SV *’ [-Wformat]
Running Mkbootstrap for DBD::mysql ()
chmod 644 mysql.bs
rm -f blib/arch/auto/DBD/mysql/mysql.so
LD_RUN_PATH="/usr/lib/i386-linux-gnu:/lib/i386-linux-gnu" /usr/bin/perl myld cc  -shared -L/usr/local/lib -fstack-protector dbdimp.o mysql.o  -o blib/arch/auto/DBD/mysql/mysql.so     \
       -L/usr/lib -lmysqlclient -lpthread -lm -lrt -ldl      \
      
/usr/bin/ld: cannot find -lmysqlclient
collect2: error: ld returned 1 exit status
make: *** [blib/arch/auto/DBD/mysql/mysql.so] Error 1
  CAPTTOFU/DBD-mysql-4.022.tar.gz
  /usr/bin/make -- NOT OK
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Failed during this command:
 CAPTTOFU/DBD-mysql-4.022.tar.gz              : make NO

 cpan[2]> 

```

---

### Post by Lars Noodén on 2012-10-29
I would try using the package manager to install [libdbd-mysql-perl](apt:libdbd-mysql-perl)  The method you are trying is only necessary on systems that don't have a package manager or are missing that specific package.  Ubuntu has both.

Spend a little time browsing the perl modules in Synaptic.

---

### Post by 1cookie on 2012-10-29
> **Lars Noodén said:**
> I would try using the package manager to install [libdbd-mysql-perl]("apt:libdbd-mysql-perl")  The method you are trying is only necessary on systems that don't have a package manager or are missing that specific package.  Ubuntu has both.

Spend a little time browsing the perl modules in Synatpic.

Thanks Lars

---

