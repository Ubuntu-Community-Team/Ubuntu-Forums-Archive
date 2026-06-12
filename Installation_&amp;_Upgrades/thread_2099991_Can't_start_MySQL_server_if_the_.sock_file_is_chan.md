---
title: "Can't start MySQL server if the .sock file is changed in /etc/mysql/my.cnf"
date: 2012-12-31
forum: Installation &amp; Upgrades
---

### Post by pravsemilo on 2012-12-31
have installed MySQL server 5.5 on Ubuntu 12.04. I am trying to start  MySQL server on a different sock file. By default MySQL runs on  /var/run/mysqld/mysqld.sock. 
 
I am trying to run the same server on /var/run/mysqld/mysqld1.sock. 
 
For this I have made the following changes: 
 
    Changes to /etc/mysql/my.cnf 
 
    ```
[client] 
    port = 3306 
    socket = /var/run/mysqld/mysqld1.sock 
``````
[mysqld_safe] 
    socket = /var/run/mysqld/mysqld1.sock 
    nice = 0 
``` ```

    [mysqld] 
    user = mysql 
    pid-file = /var/run/mysqld/mysqld.pid 
    socket = /var/run/mysqld/mysqld1.sock 
    port = 3306 
    basedir = /usr 
    datadir = /var/lib/mysql 
    tmpdir = /tmp 
    lc-messages-dir = /usr/share/mysql 
```    I also added the following line to /etc/apparmor.d/usr/sbin.mysqld 
 
```
/var/run/mysqld/mysqld1.sock w, 
/var/run/mysqld/mysqld[1-9].sock w, 
```    I also changed the ownership for the directory /var/run/mysqld to mysql user.

```
 ls -lA /var/run/ | grep mysqld 
drwxrwxrwx 2 mysql mysql 40 Dec 31 17:24 mysqld 
```However when I try to start MySQL server I get the following error (As a root user) 
 
```
mysqld --user=mysql --verbose 
121231 18:40:56 [Note] Plugin 'FEDERATED' is disabled. 
121231 18:40:56 InnoDB: The InnoDB memory heap is disabled 
121231 18:40:56 InnoDB: Mutexes and rw_locks use GCC atomic builtins 
121231 18:40:56 InnoDB: Compressed tables use zlib 1.2.3.4 
121231 18:40:56 InnoDB: Initializing buffer pool, size = 128.0M 
121231 18:40:56 InnoDB: Completed initialization of buffer pool 
121231 18:40:56 InnoDB: highest supported file format is Barracuda. 
121231 18:40:57 InnoDB: Waiting for the background threads to start 
121231 18:40:58 InnoDB: 1.1.8 started; log sequence number 1595685 
121231 18:40:58 [Note] Server hostname (bind-address): '127.0.0.1'; port: 3306 
121231 18:40:58 [Note] - '127.0.0.1' resolves to '127.0.0.1'; 
121231 18:40:58 [Note] Server socket created on IP: '127.0.0.1'. 
121231 18:40:58 [ERROR] Can't start server : Bind on unix socket:  Permission denied 121231 18:40:58 [ERROR] Do you already have another  mysqld server running on socket: /var/run/mysqld/mysqld1.sock ? 121231  18:40:58 [ERROR] Aborting 
121231 18:40:58 InnoDB: Starting shutdown... 
121231 18:40:58 InnoDB: Shutdown completed; log sequence number 1595685 
121231 18:40:58 [Note] mysqld: Shutdown complete 
```If I start the server with the default socket file, I am able to start  the server. I have googled about this issue but only found solutions  suggesting it to be permissions issue. However the permissions seems  fine. Some have suggested that AppArmor might be a cause, but I have  checked that too - snippet is pasted above. 
 
Can someone provide some clues?

---

### Post by pravsemilo on 2013-01-02
I have resolved the problem. The fix was to add  a new entry to the /etc/apparmor.d/usr.sbin.mysqld file.

/var/run/mysqld/mysqld1.sock w,

This fixed the issue.

---

### Post by vksingh on 2013-01-02
It looks like a port conflict

---

