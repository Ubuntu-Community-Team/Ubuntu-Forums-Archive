---
title: "mysqld_safe A mysqld process already exists"
date: 2013-10-26
forum: Installation &amp; Upgrades
---

### Post by diego.uribe.gamez on 2013-10-26
I have a problem very curious,


I have two projects in Django, one if I is working well where for example if I want to run the migrate from south works well .


but the other does not run the migration project and I take this error: OperationalError : (2002, " Can not connect to the local MySQL server through socket ' / var / run / mysqld / mysqld.sock ' ( 2)" )


in mysql I are coming out two errors in this order:


```
$ sudo / etc / init.d / mysql restart
 * Stopping MySQL database server mysqld [fail ]
 * Starting MySQL database server mysqld [fail ]


$ Tail -5 / var / log / mysql / error.log
131026 15:13:51 [ Note] Server socket created on IP : '127 .0.0.1 ' .
131026 15:13:52 [ Note] Event Scheduler : Loaded 0 events
131026 15:13:52 [ Note] / usr / sbin / mysqld : ready for connections.
Version: '5 .5.34 - 0ubuntu0 .13.10.1 'socket : ' / tmp / mysqld.sock 'port : 3306 (Ubuntu )
131026 15:17:12 mysqld_safe A mysqld process already exists


Project 1 $ python manage.py syncdb
Syncing ...
OperationalError : (2002, " Can not connect to the local MySQL server through socket ' / var / run / mysqld / mysqld.sock ' ( 2)" )


$ Mysql- h localhost- u root -p
Enter password:
ERROR 2002 ( HY000 ) : Can not connect to the local MySQL server through socket ' / tmp / mysqld.sock ' (2)


$ Sudo mv / tmp / mysql.sock / tmp / mysqld.sock
[ sudo ] password for diegoug :
@ diegoug :/ home / p $ mysql- h localhost- u root -p
Enter password:
Welcome to the MySQL monitor.
mysql > exit ;


Project 2 $ sudo python manage.py runserver
Validating models ...


0 errors found
October 26, 2013 - 16:34:48
Django version 1.5.4 ,
Development server is running at http://127.0.0.1:8000/
Quit the server with CONTROL- C .
  File " / usr/local/lib/python2.7/dist-packages/django/db/models/manager.py " , line 143, in get
    self.get_query_set return ( .) get ( * args, ** kwargs )
  File " / usr/local/lib/python2.7/dist-packages/django/db/models/query.py " , line 398, in get
    num = len ( clone)
  File " / usr/local/lib/python2.7/dist-packages/django/db/models/query.py " , line 106, in __ len__
    self._result_cache = list ( self.iterator ( ) )
  File " / usr/local/lib/python2.7/dist-packages/django/db/models/query.py " , line 317 , in iterator
    for row in compiler.results_iter ( ) :
  File " / usr/local/lib/python2.7/dist-packages/django/db/models/sql/compiler.py " , line 775, in results_iter
    for rows in self.execute_sql (MULTI ) :
  File " / usr/local/lib/python2.7/dist-packages/johnny/cache.py " , line 367, in newfun
    val = Original ( cls, * args, ** kwargs )
  File " / usr/local/lib/python2.7/dist-packages/django/db/models/sql/compiler.py " , line 839, in execute_sql
    self.connection.cursor cursor = ()
  File " / usr/local/lib/python2.7/dist-packages/django/db/backends/__init__.py " line 324, in cursor
    cursor = self.make_debug_cursor ( self._cursor ())
  File " / usr/local/lib/python2.7/dist-packages/django/db/backends/mysql/base.py " , line 406, in _cursor
    self.connection = Database.connect (** kwargs )
  File " / usr/lib/python2.7/dist-packages/MySQLdb/__init__.py " , line 81 , in Connect
    return Connection ( * args, ** kwargs )
  File " / usr/lib/python2.7/dist-packages/MySQLdb/connections.py " , line 187, in __ init__
    super ( Connection, self ) . __init__ ( * args, ** kwargs2 )
OperationalError : (2002, " Can not connect to the local MySQL server through socket ' / tmp / mysql.sock ' ( 2)" )




$ Sudo mv / tmp / mysqld.sock / tmp / mysql.sock

Project 2  $ sudo python manage.py runserver
Validating models...


0 errors found
October 26, 2013 - 16:37:49
Django version 1.5.4, using settings 'p.settings'
Development server is running at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
[26/Oct/2013 16:38:17] "GET / HTTP/1.1" 200 56924



```

---

