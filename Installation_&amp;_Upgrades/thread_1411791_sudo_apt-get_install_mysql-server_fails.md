---
title: "sudo apt-get install mysql-server fails"
date: 2010-02-20
forum: Installation &amp; Upgrades
---

### Post by woodsonoversoul on 2010-02-20
Hi all,
    I'm coming from a fresh install of Ubuntu server 9.10 and trying to install mysql-server by using 'sudo apt-get mysql-server'

I get the following errors:
```
dan@dev:~$ sudo apt-get install mysql-server                   
[sudo] password for dan:                                       
Reading package lists... Done                                  
Building dependency tree                                       
Reading state information... Done                              
The following extra packages will be installed:                
  libdbd-mysql-perl libdbi-perl libhtml-template-perl          
  libnet-daemon-perl libplrpc-perl mysql-client-5.1            
  mysql-server-5.1                                             
Suggested packages:                                            
  dbishell libipc-sharedcache-perl tinyca                      
The following NEW packages will be installed:                  
  libdbd-mysql-perl libdbi-perl libhtml-template-perl          
  libnet-daemon-perl libplrpc-perl mysql-client-5.1            
  mysql-server mysql-server-5.1                                
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded. 
Need to get 16.5MB of archives.                                
After this operation, 39.0MB of additional disk space will be used.                                                           
Do you want to continue [Y/n]? y                               
Get:1 http://us.archive.ubuntu.com karmic/main libnet-daemon-perl 0.43-1 [46.9kB]                                             
Get:2 http://us.archive.ubuntu.com karmic/main libplrpc-perl 0.2020-2 [36.0kB]                                                
Get:3 http://us.archive.ubuntu.com karmic/main libdbi-perl 1.609-1 [800kB]                                                    
Get:4 http://us.archive.ubuntu.com karmic/main libdbd-mysql-perl 4.011-1ubuntu1 [136kB]                                       
Get:5 http://us.archive.ubuntu.com karmic-updates/main mysql-client-5.1 5.1.37-1ubuntu5.1 [8,202kB]                           
Get:6 http://us.archive.ubuntu.com karmic-updates/main mysql-server-5.1 5.1.37-1ubuntu5.1 [7,186kB]                           
Get:7 http://us.archive.ubuntu.com karmic/main libhtml-template-perl 2.9-1 [65.8kB]                                           
Get:8 http://us.archive.ubuntu.com karmic-updates/main mysql-server 5.1.37-1ubuntu5.1 [64.3kB]                                
Fetched 16.5MB in 1min 34s (175kB/s)                           
Preconfiguring packages ...                                    
Selecting previously deselected package libnet-daemon-perl.    
(Reading database ... 123083 files and directories currently installed.)                                                      
Unpacking libnet-daemon-perl (from .../libnet-daemon-perl_0.43-1_all.deb) ...                                                 
Selecting previously deselected package libplrpc-perl.         
Unpacking libplrpc-perl (from .../libplrpc-perl_0.2020-2_all.deb) ...                                                         
Selecting previously deselected package libdbi-perl.           
Unpacking libdbi-perl (from .../libdbi-perl_1.609-1_i386.deb) ...                                                             
Selecting previously deselected package libdbd-mysql-perl.     
Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_4.011-1ubuntu1_i386.deb) ...                                          
Selecting previously deselected package mysql-client-5.1.      
Unpacking mysql-client-5.1 (from .../mysql-client-5.1_5.1.37-1ubuntu5.1_i386.deb) ...                                         
Selecting previously deselected package mysql-server-5.1.      
Unpacking mysql-server-5.1 (from .../mysql-server-5.1_5.1.37-1ubuntu5.1_i386.deb) ...                                         
Selecting previously deselected package libhtml-template-perl. 
Unpacking libhtml-template-perl (from .../libhtml-template-perl_2.9-1_all.deb) ...                                            
Selecting previously deselected package mysql-server.          
Unpacking mysql-server (from .../mysql-server_5.1.37-1ubuntu5.1_all.deb) ...                                                  
Processing triggers for man-db ...                             
Processing triggers for ureadahead ...                         
ureadahead will be reprofiled on next reboot                   
Setting up libnet-daemon-perl (0.43-1) ...                     
Setting up libplrpc-perl (0.2020-2) ...                        
Setting up libdbi-perl (1.609-1) ...                           
Setting up libdbd-mysql-perl (4.011-1ubuntu1) ...              
Setting up mysql-client-5.1 (5.1.37-1ubuntu5.1) ...            

Setting up mysql-server-5.1 (5.1.37-1ubuntu5.1) ...
 * Stopping MySQL database server mysqld                [ OK ] 
 * Starting MySQL database server mysqld                [fail] 
invoke-rc.d: initscript mysql, action "start" failed.          
dpkg: error processing mysql-server-5.1 (--configure):         
 subprocess installed post-installation script returned error exit status 1                                                   
Setting up libhtml-template-perl (2.9-1) ...                   
dpkg: dependency problems prevent configuration of mysql-server:                                                              
 mysql-server depends on mysql-server-5.1; however:            
  Package mysql-server-5.1 is not configured yet.              
dpkg: error processing mysql-server (--configure):             
 dependency problems - leaving unconfigured                    
No apport report written because the error message indicates its a followup error from a previous failure.
                                           Errors were encountered while processing:
 mysql-server-5.1
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

What am I missing?

Update: mysqld returns:
```
dan@dev:~$ sudo mysqld                                                                           
[sudo] password for dan:                                                                         
100220 12:18:17 [Note] Plugin 'FEDERATED' is disabled.                                           
InnoDB: Unable to lock ./ibdata1, error: 11                                                      
InnoDB: Check that you do not already have another mysqld process                                
InnoDB: using the same InnoDB data or log files.                                                 
100220 12:18:17  InnoDB: Retrying to lock the first data file                                    
InnoDB: Unable to lock ./ibdata1, error: 11                                                      
InnoDB: Check that you do not already have another mysqld process  
```

This goes on for a while...

```
InnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
^[[BInnoDB: Unable to lock ./ibdata1, error: 11
InnoDB: Check that you do not already have another mysqld process
InnoDB: using the same InnoDB data or log files.
100220 12:19:57  InnoDB: Unable to open the first data file
InnoDB: Error in opening ./ibdata1
100220 12:19:57  InnoDB: Operating system error number 11 in a file operation.
InnoDB: Error number 11 means 'Resource temporarily unavailable'.
InnoDB: Some operating system error numbers are described at
InnoDB: http://dev.mysql.com/doc/refman/5.1/en/operating-system-error-codes.html
InnoDB: Could not open or create data files.
InnoDB: If you tried to add new data files, and it failed here,
InnoDB: you should now edit innodb_data_file_path in my.cnf back
InnoDB: to what it was, and remove the new ibdata files InnoDB created
InnoDB: in this failed attempt. InnoDB only wrote those files full of
InnoDB: zeros, but did not yet use them in any way. But be careful: do not
InnoDB: remove old data files which contain your precious data!
100220 12:19:57 [ERROR] Plugin 'InnoDB' init function returned error.
100220 12:19:57 [ERROR] Plugin 'InnoDB' registration as a STORAGE ENGINE failed.
100220 12:19:57 [ERROR] Can't start server: Bind on TCP/IP port: Address already in use
100220 12:19:57 [ERROR] Do you already have another mysqld server running on port: 3306 ?
100220 12:19:57 [ERROR] Aborting

100220 12:19:57 [Warning] Forcing shutdown of 1 plugins
100220 12:19:57 [Note] mysqld: Shutdown complete
```

How can I check which process is running on port 3306?

---

### Post by Barriehie on 2010-02-20
Try:
```

netstat | grep 3306
```

---

### Post by woodsonoversoul on 2010-02-20
netstat | grep 3306

Returns nothing

---

### Post by woodsonoversoul on 2010-02-20
What exactly does:
```
100220 15:09:42  InnoDB: Operating system error number 11 in a file operation.
InnoDB: Error number 11 means 'Resource temporarily unavailable'.
InnoDB: Some operating system error numbers are described at
InnoDB: http://dev.mysql.com/doc/refman/5.1/en/operating-system-error-codes.html
InnoDB: Could not open or create data files.
InnoDB: If you tried to add new data files, and it failed here,
InnoDB: you should now edit innodb_data_file_path in my.cnf back
InnoDB: to what it was, and remove the new ibdata files InnoDB created
InnoDB: in this failed attempt. InnoDB only wrote those files full of
InnoDB: zeros, but did not yet use them in any way. But be careful: do not
InnoDB: remove old data files which contain your precious data!
100220 15:09:42 [ERROR] Plugin 'InnoDB' init function returned error.
100220 15:09:42 [ERROR] Plugin 'InnoDB' registration as a STORAGE ENGINE failed.
100220 15:09:42 [ERROR] Can't start server: Bind on TCP/IP port: Address already in use
100220 15:09:42 [ERROR] Do you already have another mysqld server running on port: 3306 ?
100220 15:09:42 [ERROR] Aborting

100220 15:09:42 [Warning] Forcing shutdown of 1 plugins
100220 15:09:42 [Note] mysqld: Shutdown complete
```

Mean?

---

### Post by woodsonoversoul on 2010-02-20
I can log into mysql if that makes a difference...

---

