---
title: "Wrong MariaDB Version After Upgrade from Xenial to Bionic"
date: 2019-10-01
forum: Installation &amp; Upgrades
---

### Post by SAH62 on 2019-10-01
I just upgraded a server from xenial to bionic:

```

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:        18.04
Codename:       bionic
$ 

```

I have my MariaDB repository defined like this:

```

deb [arch=amd64] http://nyc2.mirrors.digitalocean.com/mariadb/repo/10.4/ubuntu bionic main
deb-src http://nyc2.mirrors.digitalocean.com/mariadb/repo/10.4/ubuntu bionic main

```

I've done an ```
apt-get update
``` and an ```
apt-get upgrade
```, but when I look at the installed version of mariadb-client and mariadb-server I see this:

```

$ dpkg -l|grep maria
ii  libmariadb3:amd64                    1:10.4.8+maria~xenial                      amd64        MariaDB database client library
ii  libmariadbclient18                   1:10.4.8+maria~xenial                      amd64        Virtual package to satisfy external libmariadbclient18 depends
ii  mariadb-client-10.4                  1:10.4.8+maria~xenial                      amd64        MariaDB database client binaries
ii  mariadb-client-core-10.4             1:10.4.8+maria~xenial                      amd64        MariaDB database core client binaries
ii  mariadb-common                       1:10.4.8+maria~xenial                      all          MariaDB database common files (e.g. /etc/mysql/conf.d/mariadb.cnf)
ii  mariadb-server                       1:10.4.8+maria~xenial                      all          MariaDB database server (metapackage depending on the latest version)
ii  mariadb-server-10.4                  1:10.4.8+maria~xenial                      amd64        MariaDB database server binaries
ii  mariadb-server-core-10.4             1:10.4.8+maria~xenial                      amd64        MariaDB database core server files
ii  mysql-common                         1:10.4.8+maria~xenial                      all          MariaDB database common files (e.g. /etc/mysql/my.cnf)
$

```

When I try to upgrade mariadb-server (for example), I'm told that the newest xenial version is already installed:

```

$ sudo apt-get upgrade mariadb-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mariadb-server is already the newest version (1:10.4.8+maria~xenial).
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
$

```

Something's not right here. How can I get the bionic versions installed properly?

---

### Post by deadflowr on 2019-10-01
Issue most likely because xenial is a higher version name than bionic.
Same version though, package-wise.

Workaround would be to backup the databases, remove the packages and reinstall.
Then restore the databases.

---

### Post by SAH62 on 2019-10-07
Thanks, @deadflowr. That did the trick. I also made sure to clean out the apt cache before re-installing MariaDB.

---

### Post by deadflowr on 2019-10-07
If it worked please [mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

