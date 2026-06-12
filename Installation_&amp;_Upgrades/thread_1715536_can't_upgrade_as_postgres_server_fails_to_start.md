---
title: "can't upgrade as postgres server fails to start"
date: 2011-03-27
forum: Installation &amp; Upgrades
---

### Post by tanvi on 2011-03-27
when I upgrade my system , having ubuntu -10.04, get the following output:- 


Setting up postgresql-8.4 (8.4.7-0ubuntu0.10.04) ...
 * Starting PostgreSQL 8.4 database server                                                                                                                    * The PostgreSQL server failed to start. Please check the log output:
2011-03-27 14:31:58 IST FATAL:  private key file "server.key" has group or world access
2011-03-27 14:31:58 IST DETAIL:  File must be owned by the database user or root, must have no write permission for "group", and must have no permissions for "other".
                                                                                                                                                      [fail]
invoke-rc.d: initscript postgresql-8.4, action "start" failed.
dpkg: error processing postgresql-8.4 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 postgresql-8.4


plz help soon... :(

---

### Post by Dutch70 on 2011-03-27
First of all, you need to give some details of what & how you're doing it. The error alone isn't much help.

Also, I know the server was down in India, is it back up?

---

### Post by reqqq on 2011-03-27
i agree with the above Dutch70 but you can take a look & here-->>[https://help.ubuntu.com/community/PostgreSQL](https://help.ubuntu.com/community/PostgreSQL)
if this can help you out

---

### Post by SeijiSensei on 2011-03-27
```
2011-03-27 14:31:58 IST FATAL: private key file "server.key" has group or world access
2011-03-27 14:31:58 IST DETAIL: File must be owned by the database user or root, must have no write permission for "group", and must have no permissions for "other".
```

Actually the message is pretty clear.  You need to find the file 'server.key' associated with PostgreSQL and fix its permissions.  The server runs as user "postgres" which should own the file.  According to [this documentation](http://www.postgresql.org/docs/current/static/ssl-tcp.html) that file is in the server's data directory.  That's /var/lib/pgsql/data on most default installations; /usr/local/lib/pgsql/data if you compiled from source and installed to /usr/local with "sudo make install".

So you need to do something like this (depending on the location of server.key).  (This is easiest to do if you first become root as I do below.)

```

$ sudo su
[Enter your password]
# cd /var/lib/pgsql/data
# chown postgres server.key
# chmod 0640 server.key
# exit
$

```

That makes user postgres the owner of server.key with read/write permissions, grants read-only permissions to the file's group, and no permissions to anyone else.

---

### Post by tanvi on 2011-03-28
The **server.key** file exists under the directory:

/opt/lampp/etc/ssl.key

by using the above commands along the respective path, nothing occured :-/

---

### Post by reqqq on 2011-03-28
an idea 
 try to ping your localhost 
or try this -->>sudo dpkg --configure -a

---

### Post by SeijiSensei on 2011-03-28
> **tanvi said:**
> The **server.key** file exists under the directory:

/opt/lampp/etc/ssl.key

by using the above commands along the respective path, nothing occured :-/

Is that where PostgreSQL is storing its data?  Did you read the documentation to which I linked, specifically 

[quote=PostgreSQL docs]To start in SSL mode, the files server.crt and server.key must exist in the server's data directory. These files should contain the server certificate and private key, respectively. On Unix systems, the permissions on server.key must disallow any access to world or group; achieve this by the command chmod 0600 server.key. If the private key is protected with a passphrase, the server will prompt for the passphrase and will not start until it has been entered. [/quote]

You can't just put the key anywhere.  It has to be in the data directory.  Oh, and it's complaining about the file "server.key" not "ssl.key" unless /opt/lampp/etc/ssl.key is a directory.

It doesn't look like your installation is from the repositories, nor it is located in the /usr/local hierarchy that a version of PostgreSQL would use when built from source.  Where did you get this version from?

Edit:  Oh, I suspect I know where part of the confusion is coming from.  Are you trying to use SSL to connect securely between a browser and a web page, or are you trying to use SSL to encrypt the connection to the PG server itself?  Those are very different things.  The keys to encrypt a connection to the browser reside wherever they are defined in the Apache <VirtualHost> container that defines the HTTPS server.  The keys to encrypt a connection to the PG server reside in the PG server's /data/ directory.

Frankly, there's no real need to encrypt the connection to the PG server if it's on the same machine as Apache.  Just make sure the PG server accepts connections on the localhost (127.0.0.1) interface and don't specify a hostname (or use "localhost") in the connection string passed to pg_connect() .  That's entirely secure since the data never leaves the server.  The pg_connect command should look something like this:

```
$db=pg_connect("dbname=mydb user=me password=goober");
```

See the [PHP page for pg_connect()]("http://www.php.net/manual/en/function.pg-connect.php") for more details.  If you need to connect to a remote PG server using SSL, that page and the PG docs should tell you how.

---

### Post by tanvi on 2011-03-30
> **reqqq said:**
> an idea 
 try to ping your localhost 
or try this -->>sudo dpkg --configure -a


well, i tried this command but the problem remains the same.... no changes .....

---

### Post by zazuge on 2012-12-10
well had the same problem
but the solution was to remove read access from other groups
the file server.key is symlink to /etc/ssl/private/ssl-cert-snakeoil.key
which must be owned by root and not postgres
> 
chmod 640 /etc/ssl/private/ssl-cert-snakeoil.key

solved it

---

