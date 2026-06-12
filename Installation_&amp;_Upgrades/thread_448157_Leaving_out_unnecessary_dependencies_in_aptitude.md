---
title: "Leaving out unnecessary dependencies in aptitude"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by rmsx99 on 2007-05-18
I was wondering how one can omit packages from being installed from aptitude.

For example, when installing Gallery2. The requirements are MySQL *or* PostgreSQL, yet it wants to install PostgreSQL despite MySQL already being on my system. 

Is aptitude somehow not recognizing MySQL properly or is this a known issue?

I've been trying to search quite a bit on this issue but have no luck, but thanks in advance for any tips on this.

---

### Post by earobinson on 2007-05-18
do you have the same version of MySQL that Gallery2 needs?

---

### Post by rmsx99 on 2007-05-18
Yes. I have 5.0 installed.

From the Gallery2 requirements:

Database (Gallery 2 only) - MySQL 3.x, 4.x or 5.x, PostgreSQL 7.x or 8.x, Oracle 9i or 10g, DB2 8.2, MS SQL Server 2005 (Gallery 1.x does NOT require a database)

When I go to install Gallery2, it asks me:

```

The following NEW packages will be automatically installed:
  dcraw defoma ffmpeg fontconfig-config gs gs-common gs-gpl gsfonts jhead
  liba52-0.7.4 libavcodec0d libavformat0d libdc1394-13 libdirectfb-0.9-25
  libfontconfig1 libfreetype6 libft-perl libgd2-xpm libgsm1 libice6
  libjpeg-progs libjpeg62 liblcms1 libnetpbm10 libogg0 libpaper-utils
  libpaper1 libpng12-0 libpq4 libraw1394-8 libsdl1.2debian
  libsdl1.2debian-alsa libsm6 libt1-5 libtiff4 libttf2 libvorbis0a
  libvorbisenc2 libx11-6 libx11-data libxau6 libxdmcp6 libxext6 libxpm4
  libxt6 netpbm openssl php5-gd [B]postgresql-8.1 postgresql-client-8.1
  postgresql-client-common postgresql-common[/B] psfontmgr ssl-cert ttf-dejavu
  unzip wwwconfig-common x11-common zip

```

Searching apt for mysql provides this (to show it's installed):

```

i   mysql-server                    - mysql database server (meta package depend
p   mysql-server-4.1                - mysql database server (transitional packag
i   mysql-server-5.0                - mysql database server binaries
p   mysqltcl                        - Interface to the MySQL database for the Tc

```

Typing "aptitude show gallery2" provides this output:

```

Depends: apache | apache-ssl | apache-perl | apache2 | httpd, php4 | php4-cgi |
         libapache-mod-php4 | libapache2-mod-php4 | php5 | php5-cgi |
         libapache-mod-php5 | libapache2-mod-php5, netpbm (>= 9.20) | imagemagick,
         debconf (>= 0.2.26) | debconf-2.0, mysql-client | postgresql-client-7.4 |
         postgresql-client-8.1, wwwconfig-common, php4-mysql | php5-mysql |
         php4-pgsql | php5-pgsql
Recommends: jhead, unzip, libjpeg-progs, php4-gd | php5-gd, dcraw, ffmpeg,
            mysql-server-4.1 | mysql-server, postgresql-7.4 | postgresql-8.1, zip


```

---

### Post by rmsx99 on 2007-05-21
Sorry for posting again, but I'm utterly stumped on this.

Either I'm searching wrong or there's no info on why it's doing this.

Is it just a problem with this one package, you think? 

I suppose it doesn't matter since postgreSQL doesn't take up *that* much space from the total drive, but figured I'd point out the potential flaw/bug to anyone who might wanna look into it in the event there are other packages that force the installation of items that's aren't really needed.

---

