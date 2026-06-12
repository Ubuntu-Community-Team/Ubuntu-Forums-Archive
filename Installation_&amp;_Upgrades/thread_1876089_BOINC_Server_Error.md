---
title: "BOINC Server Error"
date: 2011-11-05
forum: Installation &amp; Upgrades
---

### Post by pedronevespinguim on 2011-11-05
Hello, i'm trying to make a boinc Project on Ubuntu Server virtual machine for some academic experiments but it happens that i have some errors when i'm trying to create the project. I'm following this manual:


[http://www.boinc-wiki.info/How_to_create_a_BOINC_Project_-_Step_By_Step_instructions](http://www.boinc-wiki.info/How_to_create_a_BOINC_Project_-_Step_By_Step_instructions)


The problem is, when i get the step "Creating a Project - Using make project" and execute the following command: 

./tools/make_project YourProjectName

i get the errors the manual specifies:

Traceback (most recent call last):
  File "./tools/make_project", line 208, in ?
    project.install_project()
  File "/software/boinc_public/py/Boinc/setup_project.py", line 500, in install_project
    drop_first = options.drop_db_first
  File "/software/boinc_public/py/Boinc/database.py", line 257, in create_database
    connect(config, nodb=True)
  File "/software/boinc_public/py/Boinc/database.py", line 244, in connect
    passwd=config.__dict__.get('db_passwd', ))
  File "/software/boinc_public/py/Boinc/db_base.py", line 492, in do_connect
    cursorclass=MySQLdb.cursors.DictCursor)
  File "/usr/lib/python2.2/site-packages/MySQLdb/__init__.py", line 64, in Connect
    return apply(Connection, args, kwargs)
  File "/usr/lib/python2.2/site-packages/MySQLdb/connections.py", line 116, in __init__
    self._make_connection(args, kwargs2)
  File "/usr/lib/python2.2/site-packages/MySQLdb/connections.py", line 41, in _make_connection
    apply(super(ConnectionBase, self).__init__, args, kwargs)
_mysql_exceptions.OperationalError: (2002, "Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2)")


The manual also says that to solve the problem i need to have the MySql socket in /var/lib/mysql/mysql.sock or /tmp/mysql.sock. The problem is that that socket don't even exists, i execute the commands the manual says (mysqld_safe --socket=/var/lib/mysql/mysql.sock
or
mysqld_safe --socket=/tmp/mysql.sock) 
and the output is:


nohup: ignoring input and redirecting stderr to stdout
mysqld_safe[2658]: A mysqld process already exists

Trying to solve the problem i kill the mysqld proccess and i execute the command again. The command start and stops in runwhile.. i can only get my console line again if a press ctrl+z (wich the output is something about he could not access the mysql socket. Curious that he tries to access the same socket i'm trying to create). 

Besides all this, the mysql Socket is created but the command:

./tools/make_project YourProjectName   is still showing the same output

i'm a bit worried about this becaus i do really want to make this work out.

kind regards for everyone and sorry about my poor english

---

