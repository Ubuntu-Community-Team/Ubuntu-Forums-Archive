---
title: "Downloading source code from luanchpad and making a few .configure tweaks"
date: 2006-09-11
forum: Installation &amp; Upgrades
---

### Post by supanova on 2006-09-11
Hi All

My apologies... I'm actually posting this again from the Respository help forum... wish one could move ones own post... I don't think posting it there made sense...

Anyway

Please help :D 

I would like to install mysql (or anything else for that fact) to a dir called /apps

I can't find the build log for mysql 5.0.22-0ubuntu6.06.2 ([https://launchpad.net/+builds/+build/242389)](https://launchpad.net/+builds/+build/242389)). I downloaded the source from here but can't find the file to run that would have their configure options...

From looking at the build log of an older version, it would be something like

```
./configure \ --build=i486-linux-gnu \ --host=i486-linux-gnu \ \ --prefix=/usr \ --exec-prefix=/usr \ --libexecdir=/usr/sbin \ --datadir=/usr/share \ --sysconfdir=/etc/mysql \ --localstatedir=/var/lib/mysql \ --includedir=/usr/include \ --infodir=/usr/share/info \ --mandir=/usr/share/man \ \ --with-server-suffix="-Debian_3ubuntu1" \ --with-comment="Debian Etch distribution" \ \ --enable-shared \ --enable-static \ --enable-thread-safe-client \ --enable-assembler \ --enable-local-infile \ \ --with-big-tables \ --with-raid \ --with-unix-socket-path=/var/run/mysqld/mysqld.sock \ --with-mysqld-user=mysql \ --with-libwrap \ \ --with-vio \ --without-openssl \ --without-docs \ --without-bench \ --without-readline \ --with-extra-charsets=all \ --with-innodb \ \ --with-isam \ --with-archive-storage-engine \ --with-csv-storage-engine \ --with-federated-storage-engine \ --without-embedded-server \ --with-ndbcluster \ --with-ndb-shm \ --without-ndb-sci \ --without-ndb-test \ --with-embedded-server \ --with-embedded-privilege-control \ --with-ndb-docs'

```

All i'm trying to do is utilise the exact Ubuntu version with the exact method/settings except for certain directory locations.... please help someone...

Thanks

---

### Post by supanova on 2006-09-11
Sorry here is the nicley formatted code block

```

./configure \
		--build=i486-linux-gnu \
		--host=i486-linux-gnu \
		\
		--prefix=/usr \
	        --exec-prefix=/usr \
	        --libexecdir=/usr/sbin \
	        --datadir=/usr/share \
	        --sysconfdir=/etc/mysql \
	        --localstatedir=/var/lib/mysql \
	        --includedir=/usr/include \
	        --infodir=/usr/share/info \
	        --mandir=/usr/share/man \
		\
		--with-server-suffix="-Debian_3ubuntu1" \
		--with-comment="Debian Etch distribution" \
		\
		--enable-shared \
		--enable-static \
		--enable-thread-safe-client \
	        --enable-assembler  \
		--enable-local-infile \
		\
                --with-big-tables \
		--with-raid \
		--with-unix-socket-path=/var/run/mysqld/mysqld.sock \
	       	--with-mysqld-user=mysql \
		--with-libwrap \
		 \
		--with-vio \
		--without-openssl \
	    	--without-docs \
		--without-bench \
		--without-readline \
		--with-extra-charsets=all \
		--with-innodb \
		\
		--with-isam \
		--with-archive-storage-engine \
		--with-csv-storage-engine \
		--with-federated-storage-engine \
		--without-embedded-server \
		--with-ndbcluster \
		--with-ndb-shm \
		--without-ndb-sci \
		--without-ndb-test \
		--with-embedded-server \
		--with-embedded-privilege-control \
		--with-ndb-docs'


```

---

