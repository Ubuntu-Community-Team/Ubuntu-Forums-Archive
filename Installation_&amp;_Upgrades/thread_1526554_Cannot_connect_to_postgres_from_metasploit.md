---
title: "Cannot connect to postgres from metasploit"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by agan on 2010-07-08
Hai all,
 
                I have installed and customised my UBUNTU 10.04 LTS. Installed metasploit and it is working fine. To enable autopwn, i have used sqlite3 and it is working fine. However, I cant use postgres,it is giving me error.

> 1.NETSTAT OUTPUT
netstat -antp
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      1913/apache2    
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1039/sshd       
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1855/cupsd      
tcp        0      0 127.0.0.1:5432          0.0.0.0:*               LISTEN      17851/postgres  
tcp        0      0 0.0.0.0:1241            0.0.0.0:*               LISTEN      1779/nessusd    
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      1749/exim4      
tcp        0      0 127.0.0.1:9050          0.0.0.0:*               LISTEN      1797/tor        
tcp        0      0 127.0.0.1:8123          0.0.0.0:*               LISTEN      1784/polipo     
tcp6       0      0 :::22                   :::*                    LISTEN      1039/sshd       
tcp6       0      0 ::1:631                 :::*                    LISTEN      1855/cupsd      
tcp6       0      0 ::1:5432                :::*                    LISTEN      17851/postgres  
tcp6       0      0 :::1241                 :::*                    LISTEN      1779/nessusd    
tcp6       0      0 ::1:25                  :::*                    LISTEN      1749/exim4 


> 2. vi /etc/passwd filtered
postgres:x:115:123:PostgreSQL administrator,,,:/var/lib/postgresql:/bin/bash

> 3.db_driver postgresql 
[*] Using database driver postgresql

> db_connect 
[*]    Usage: db_connect <user:pass>@<host:port>/<database>
[*] Examples:
[*]        db_connect user@metasploit3
[*]        db_connect user:pass@192.168.0.2/metasploit3
[*]        db_connect user:pass@192.168.0.2:1500/metasploit3



db_connect postgres:mypostgrespassword@127.0.0.1/metasploit3
[-] Error while running command db_connect: Failed to connect to the database: FATAL:  Ident authentication failed for user "postgres"


Call stack:
/opt/metasploit3/msf3/lib/msf/ui/console/command_dispatcher/db.rb:1609:in `db_connect_postgresql'
/opt/metasploit3/msf3/lib/msf/ui/console/command_dispatcher/db.rb:1277:in `send'
/opt/metasploit3/msf3/lib/msf/ui/console/command_dispatcher/db.rb:1277:in `cmd_db_connect'
/opt/metasploit3/msf3/lib/rex/ui/text/dispatcher_shell.rb:246:in `send'
/opt/metasploit3/msf3/lib/rex/ui/text/dispatcher_shell.rb:246:in `run_command'
/opt/metasploit3/msf3/lib/rex/ui/text/dispatcher_shell.rb:208:in `run_single'
/opt/metasploit3/msf3/lib/rex/ui/text/dispatcher_shell.rb:202:in `each'
/opt/metasploit3/msf3/lib/rex/ui/text/dispatcher_shell.rb:202:in `run_single'
/opt/metasploit3/msf3/lib/rex/ui/text/shell.rb:141:in `run'
./msfconsole:112

my metasploit is in /opt/metasploit/msf3 as well /home/cert/Downloads/msf3 - i tried from both places same error

pse help to solve this.


thanks in advance

---

### Post by qwertsa on 2010-09-25
yea u can use other db management systems like sqlite3. open new console than type msfconsole
after that type db_driver sqlite3 and db_creat.Thats all.happy hours with autopwn

---

