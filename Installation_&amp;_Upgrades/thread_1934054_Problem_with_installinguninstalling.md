---
title: "Problem with installing/uninstalling"
date: 2012-03-01
forum: Installation &amp; Upgrades
---

### Post by Net1 on 2012-03-01
Hi all, I comment my problem.

A few days ago I try to install the package **postgres_9.1.2-1.i386.openscg.deb** but during the installation, and without being completed, the system was restarted.

Now the installation of the package is pending. The problem is that now I can not install or uninstall any other packages, it allways try to install this broken package first. If I try to do **sudo dpkg - configure-a** I get the message **Configuring postgres91 (9.1.2-1) ...** but the installation never finish, so I can not open the Synaptic Package Manager to remove the broken package.

How should I proceed? Any ideas? I would avoid having to reinstall the OS.

---

### Post by Lasall on 2012-03-01
Hi Net1,

you can debug installation process. Insert "*set -x*" as second line in **/var/lib/dpkg/info/PACKAGENAME.postinst**. Then please show complete terminal output of "*dpkg --configure -a*".


Kind regards

Lasall

---

### Post by Net1 on 2012-03-02
Thanks for the tip, Lasall.

This is the message that I obtain:

net1@rantanplan:~$ sudo dpkg --configure -a
[sudo] password for net1: 
Configurando postgres91 (9.1.2-1) ...
+ case "$1" in
+ '[' '!' -f /etc/init.d/postgres-9.1-openscg ']'
+ LD_PRELOAD_VALUE=
++ find -L /lib -type f -name 'libreadline.*'

---

### Post by Lasall on 2012-03-02
Can you please attach your postinst-Script or point to sourcecode or distribution which this package is from?

Please show results of:
```

dpkg -S lib*libreadline

```

---

### Post by Net1 on 2012-03-02
This is the sourcecode of the package **/var/lib/dpkg/info/postgres91.postinst** and I downloaded the package from *[http://oscg-downloads.s3.amazonaws.com/packages/postgres_9.1.2-1.i386.openscg.deb]("http://oscg-downloads.s3.amazonaws.com/packages/postgres_9.1.2-1.i386.openscg.deb")*:

#!/bin/bash
set -x
case "$1" in
configure)

   if [ ! -f /etc/init.d/postgres-9.1-openscg ]
   then
      ln -s /opt/postgres/9.1/bin/postgres-9.1-openscg /etc/init.d/postgres-9.1-openscg
   fi

  #Dump environment values file in case of upgrade.

  #Fix for psql dumb terminal issue
  LD_PRELOAD_VALUE=""
  for libreadline in `find -L /lib -type f -name libreadline.\* 2> /dev/null`
  do
    LD_PRELOAD_VALUE="$libreadline:$LD_PRELOAD_VALUE"
  done
  if [ x"$LD_PRELOAD_VALUE" != x"" ];
  then
    LD_PRELOAD_VALUE="export LD_PRELOAD=$LD_PRELOAD_VALUE"
  fi

  #Dump environment values
cat <<ENVEOF > /opt/postgres/9.1/pg91-openscg.env 
#!/bin/bash
$LD_PRELOAD_VALUE
export PGHOME=/opt/postgres/9.1
export PGDATA=/opt/postgres/9.1/data
export PATH=/opt/postgres/9.1/bin:\$PATH
export LD_LIBRARY_PATH=/opt/postgres/9.1/lib:\$LD_LIBRARY_PATH
export PGUSER=postgres
export PGDATABASE=postgres
ENVEOF

 #Determine port from postgresql.conf
 PGPORT_VALUE=""
 if [ -f /opt/postgres/9.1/data/postgresql.conf ]; then
  PGPORT_VALUE=`grep "port =" /opt/postgres/9.1/data/postgresql.conf | sed -e      "s/^.*port[[:space:]]=[[:space:]]\([0-9]\+\).*$/\1/"`
  PGPORT_VALUE="export PGPORT=$PGPORT_VALUE"
  cat <<ENVEOF >> /opt/postgres/9.1/pg91-openscg.env 
$PGPORT_VALUE
ENVEOF
 fi

 #Determine if we stopped server
 if [ -f /tmp/pg_9.1.stopped ];
 then
  rm /tmp/pg_9.1.stopped
  /etc/init.d/postgres-9.1-openscg start
 fi
  echo "PostgreSQL 9.1 is now installed in /opt/postgres/9.1."
  echo
  echo "To initialize, sudo /etc/init.d/postgres-9.1-openscg start"
;;
esac


The results of **dpkg -S lib*libreadline** are:

net1@rantanplan:~$ dpkg -S lib*libreadline
libreadline5: /lib/libreadline.so.5
libreadline6: /lib/libreadline.so.6
libreadline6: /lib/libreadline.so.6.1
libreadline5: /lib/libreadline.so.5.2

---

### Post by Lasall on 2012-03-02
Try to replace following line:
```

for libreadline in `find -L /lib -type f -name libreadline.\* 2> /dev/null`

```

with:
```

libreadarray=( /lib/libreadline.so.5
/lib/libreadline.so.6
/lib/libreadline.so.6.1
/lib/libreadline.so.5.2 )
for libreadline in ${libreadarray[@]}

```

Then re-run:
```

sudo dpkg --configure -a

```

I don't know why find does not work in your case. Have you checked it manually?
```

find -L /lib -type f -name libreadline.\* 2> /dev/null
find -L /lib -type f -name 'libreadline\.*' 2> /dev/null

```

---

### Post by Net1 on 2012-03-02
Thank you so much. It works now :D

---

