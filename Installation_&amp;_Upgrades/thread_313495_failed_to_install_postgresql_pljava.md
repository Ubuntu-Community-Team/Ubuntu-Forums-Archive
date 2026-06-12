---
title: "failed to install postgresql pljava"
date: 2006-12-06
forum: Installation &amp; Upgrades
---

### Post by TizianoTissino on 2006-12-06
Hi,

I'm trying to install java procedural language on my postgresql server, but psql -U postgres -d template1 -f /usr/share/postgresql-8.1-pljava/install.sql
doesn't work and I got this error message:

could not load library "/usr/lib/postgresql/8.1/lib/pljava.so": /usr/lib/postgresql/8.1/lib/pljava.so: undefined symbol: JNI_CreateJavaVM

Can anybody help me?

I'm using edgy and these packages are currently installed:
postgresql-8.1
postgresql-8.1-pljava-gcj
libgcj7-0
libgcj7-awt
libgcj7-jar
libgcj7-bc
libgcj7-common

---

### Post by MarceloZunino on 2006-12-08
I got the same error in this system:

edgy kernel: 
2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686


pg_config out is:

BINDIR = /usr/lib/postgresql/8.1/bin
DOCDIR = /usr/share/doc/postgresql-doc-8.1
INCLUDEDIR = /usr/include/postgresql
PKGINCLUDEDIR = /usr/include/postgresql
INCLUDEDIR-SERVER = /usr/include/postgresql/8.1/server
LIBDIR = /usr/lib
PKGLIBDIR = /usr/lib/postgresql/8.1/lib
LOCALEDIR = /usr/share/locale
MANDIR = /usr/share/postgresql/8.1/man
SHAREDIR = /usr/share/postgresql/8.1
SYSCONFDIR = /etc/postgresql
PGXS = /usr/lib/postgresql/8.1/lib/pgxs/src/makefiles/pgxs.mk
CONFIGURE = '--build=i486-linux-gnu' '--prefix=/usr' '--includedir=/usr/include' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--sysconfdir=/etc' '--localstatedir=/var' '--libexecdir=/usr/lib/postgresql-8.1' '--disable-maintainer-mode' '--disable-dependency-tracking' '--srcdir=.' '--mandir=/usr/share/postgresql/8.1/man' '--with-docdir=/usr/share/doc/postgresql-doc-8.1' '--datadir=/usr/share/postgresql/8.1' '--bindir=/usr/lib/postgresql/8.1/bin' '--includedir=/usr/include/postgresql/' '--enable-nls' '--enable-integer-datetimes' '--enable-thread-safety' '--enable-debug' '--disable-rpath' '--with-tcl' '--with-perl' '--with-python' '--with-pam' '--with-krb5' '--with-openssl' '--with-gnu-ld' '--with-tclconfig=/usr/lib/tcl8.4' '--with-tkconfig=/usr/lib/tk8.4' '--with-includes=/usr/include/tcl8.4' '--with-pgport=5432' 'CFLAGS=-g -Wall -O2 -fPIC' 'LDFLAGS=-Wl,--as-needed' 'CC=cc' 'CPPFLAGS=' 'build_alias=i486-linux-gnu'
CC = cc
CPPFLAGS = -D_GNU_SOURCE -I/usr/include/tcl8.4
CFLAGS = -g -Wall -O2 -fPIC -Wall -Wmissing-prototypes -Wpointer-arith -Winline -Wdeclaration-after-statement -Wendif-labels -fno-strict-aliasing -g
CFLAGS_SL = -fpic
LDFLAGS = -Wl,--as-needed
LDFLAGS_SL =
LIBS = -lpgport -lpam -lssl -lcrypto -lkrb5 -lk5crypto -lcom_err -lz -lreadline -lcrypt -lresolv -lnsl -ldl -lm
VERSION = PostgreSQL 8.1.4


dpkg -l postg* | grep ^ii

ii  postgresql-8.1            8.1.4-7ubuntu0.1 object-relational SQL database, version 8.1
ii  postgresql-8.1-pljava-gcj 1.3.0-1build1    Java procedural language for PostgreSQL
ii  postgresql-client-8.1     8.1.4-7ubuntu0.1 front-end programs for PostgreSQL 8.1
ii  postgresql-client-common  62               manager for multiple PostgreSQL client versi
ii  postgresql-common         62               manager for PostgreSQL database clusters
ii  postgresql-contrib-8.1    8.1.4-7ubuntu0.1 additional facilities for PostgreSQL
ii  postgresql-doc-8.1        8.1.4-7ubuntu0.1 documentation for the PostgreSQL database ma
ii  postgresql-plpython-8.1   8.1.4-7ubuntu0.1 PL/Python procedural language for PostgreSQL


dpkg -l java* | grep ^ii

ii  java-common          0.25ubuntu1     Base of all Java packages
ii  java-gcj-compat      1.0.65-6ubuntu1 Java runtime environment using GIJ
ii  java-package         0.27            utility for building Java(TM) 2 related Debi


dpkg -l libgcj* | grep ^ii

ii  libgcj-common  4.1.1-14ubuntu7 Java runtime library (common files)
ii  libgcj7-0      4.1.1-14ubuntu7 Java runtime library for use with gcj
ii  libgcj7-awt    4.1.1-14ubuntu7 AWT peer runtime libraries for use with gcj
ii  libgcj7-jar    4.1.1-14ubuntu7 Java runtime library for use with gcj (jar f


out error:

psql:/usr/share/postgresql-8.1-pljava/install.sql:6: ERROR:  could not load library "/usr/lib/postgresql/8.1/lib/pljava.so": 

/usr/lib/postgresql/8.1/lib/pljava.so: undefined symbol: JNI_CreateJavaVM
psql:/usr/share/postgresql-8.1-pljava/install.sql:8: ERROR:  function sqlj.java_call_handler() does not exist ...
...

and so on

any ideas?

---

### Post by yaloveda on 2008-02-23
I'm installing Adempiere on Feisty, postgresql 8.2 and java 6 
I have the same problem with PLjava, any ideas about how to solve it? 
This is what I get each time I try to install pljava:


org.postgresql.util.PSQLException: ERROR: could not load library "/usr/lib/postgresql/8.2/lib/pljava.so": /usr/lib/postgresql/8.2/lib/pljava.so: undefined symbol: SetUserId
        at org.postgresql.core.v3.QueryExecutorImpl.receiveErrorResponse(QueryExecutorImpl.java:1548)
        at org.postgresql.core.v3.QueryExecutorImpl.processResults(QueryExecutorImpl.java:1316)
        at org.postgresql.core.v3.QueryExecutorImpl.execute(QueryExecutorImpl.java:191)
        at org.postgresql.jdbc2.AbstractJdbc2Statement.execute(AbstractJdbc2Statement.java:452)
        at org.postgresql.jdbc2.AbstractJdbc2Statement.executeWithFlags(AbstractJdbc2Statement.java:337)
        at org.postgresql.jdbc2.AbstractJdbc2Statement.execute(AbstractJdbc2Statement.java:329)
        at org.postgresql.pljava.deploy.Deployer.initJavaHandlers(Deployer.java:474)
        at org.postgresql.pljava.deploy.Deployer.main(Deployer.java:269)

I'm new to Ubuntu , this is my first month, so please if u have any solutions put as much details as possible, thanks everybody.

---

