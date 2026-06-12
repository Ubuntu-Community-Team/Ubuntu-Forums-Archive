---
title: "Cacti Syslog Plugin Installation &amp; Configuration"
date: 2016-07-30
forum: Installation &amp; Upgrades
---

### Post by prodigy1984 on 2016-07-30
Hi Everyone,

I am trying to install cacti syslog plugin following instructions from [http://docs.cacti.net/plugin:syslog.config](http://docs.cacti.net/plugin:syslog.config) but it gives me the following error when i try to install the plugin using cacti. 
[B]"Can not connect"

[/B]when i run the following command the i get the below output.```
kevin@cacti:/usr/share/cacti/site/plugins/syslog$ php syslog.php
PHP Warning:  include(/etc/cacti/debian.php): failed to open stream: Permission denied in /usr/share/cacti/site/include/global.php on line 49
PHP Warning:  include(): Failed opening '/usr/share/cacti/site/include/config.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /usr/share/cacti/site/include/global.php on line 49
PHP Warning:  mysql_pconnect(): Access denied for user 'cactiuser'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 461
PHP Warning:  mysql_pconnect(): Access denied for user 'cactiuser'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 461
PHP Warning:  mysql_pconnect(): Access denied for user 'cactiuser'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 461
PHP Warning:  mysql_pconnect(): Access denied for user 'cactiuser'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 461
PHP Warning:  mysql_pconnect(): Access denied for user 'cactiuser'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 461
PHP Warning:  mysql_pconnect(): Access denied for user 'cactiuser'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 461
PHP Warning:  mysql_pconnect(): Access denied for user 'cactiuser'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 461
PHP Warning:  mysql_pconnect(): Access denied for user 'cactiuser'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 461
PHP Warning:  mysql_pconnect(): Access denied for user 'cactiuser'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 461
PHP Warning:  mysql_pconnect(): Access denied for user 'cactiuser'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 461
PHP Warning:  mysql_pconnect(): Access denied for user 'cactiuser'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 461
PHP Warning:  mysql_pconnect(): Access denied for user 'cactiuser'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 461
PHP Warning:  mysql_pconnect(): Access denied for user 'cactiuser'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 461
PHP Warning:  mysql_pconnect(): Access denied for user 'cactiuser'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 461
PHP Warning:  mysql_pconnect(): Access denied for user 'cactiuser'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 461
PHP Warning:  mysql_pconnect(): Access denied for user 'cactiuser'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 461
PHP Warning:  mysql_pconnect(): Access denied for user 'cactiuser'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 461
PHP Warning:  mysql_pconnect(): Access denied for user 'cactiuser'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 461
PHP Warning:  mysql_pconnect(): Access denied for user 'cactiuser'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 461
PHP Warning:  mysql_pconnect(): Access denied for user 'cactiuser'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 461
PHP Warning:  mysql_pconnect(): Access denied for user 'cactiuser'@'localhost' (using password: YES) in /usr/share/php/adodb/drivers/adodb-mysql.inc.php on line 461
FATAL: Cannot connect to MySQL server on 'localhost'. Please make sure you have specified a valid MySQL database name in 'include/config.php'
```


I am not an expert in ubuntu, so i really appreciate any help. I really need to get this working...

PS - Moderators if this is not the correct forum pls move it.

My system is 
Ubuntu Server 15.10
Cacti v0.8.8f
Plugin Architecture v3.1
Syslog plugin v1.22


So far this is what i've done,

1. created a db called syslog.
 [COLOR=#0000ff][I]   CREATE database syslog;
[/I][/COLOR]
2. imported the /usr/share/cacti/site/plugins/syslog/syslog.sql into the new db.
    [COLOR=#0000ff]*mysql -u root -p -h localhost syslog < /usr/share/cacti/site/plugins/syslog/syslog.sql*[/COLOR]

3. ran the following commands under sql; (i did this after a lot of googling)
  [COLOR=#0000ff][I]  grant all on syslog.* to cacti;
[FONT=&amp]     flush privileges;[/FONT][/I][/COLOR]

3. installed rsyslog.
[I][COLOR=#0000ff]     sudo apt-get install rsyslog rsyslog-mysql

[/COLOR][/I][COLOR=#000000]my use/share/cacti/site/plugins/syslog/config.php
[/COLOR][COLOR=#ff0000]```
<?php[/COLOR]
[COLOR=#ff0000]/*[/COLOR]
[COLOR=#ff0000] +-------------------------------------------------------------------------+[/COLOR]
[COLOR=#ff0000] | Copyright (C) 2007 The Cacti Group                                      |[/COLOR]
[COLOR=#ff0000] |                                                                         |[/COLOR]
[COLOR=#ff0000] | This program is free software; you can redistribute it and/or           |[/COLOR]
[COLOR=#ff0000] | modify it under the terms of the GNU General Public License             |[/COLOR]
[COLOR=#ff0000] | as published by the Free Software Foundation; either version 2          |[/COLOR]
[COLOR=#ff0000] | of the License, or (at your option) any later version.                  |[/COLOR]
[COLOR=#ff0000] |                                                                         |[/COLOR]
[COLOR=#ff0000] | This program is distributed in the hope that it will be useful,         |[/COLOR]
[COLOR=#ff0000] | but WITHOUT ANY WARRANTY; without even the implied warranty of          |[/COLOR]
[COLOR=#ff0000] | MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the           |[/COLOR]
[COLOR=#ff0000] | GNU General Public License for more details.                            |[/COLOR]
[COLOR=#ff0000] +-------------------------------------------------------------------------+[/COLOR]
[COLOR=#ff0000] | Cacti: The Complete RRDTool-based Graphing Solution                     |[/COLOR]
[COLOR=#ff0000] +-------------------------------------------------------------------------+[/COLOR]
[COLOR=#ff0000] | This code is designed, written, and maintained by the Cacti Group. See  |[/COLOR]
[COLOR=#ff0000] | about.php and/or the AUTHORS file for specific developer information.   |[/COLOR]
[COLOR=#ff0000] +-------------------------------------------------------------------------+[/COLOR]
[COLOR=#ff0000] | [http://www.cacti.net/](http://www.cacti.net/)                                                   |[/COLOR]
[COLOR=#ff0000] +-------------------------------------------------------------------------+[/COLOR]
[COLOR=#ff0000]*/[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]global $config, $database_type, $database_default, $database_hostname;[/COLOR]
[COLOR=#ff0000]global $database_username, $database_password, $database_port;[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]/* revert if you dont use the Cacti database */[/COLOR]
[COLOR=#ff0000]$use_cacti_db = false;[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]if (!$use_cacti_db) {[/COLOR]
[COLOR=#ff0000]        $syslogdb_type     = 'mysql';[/COLOR]
[COLOR=#ff0000]        $syslogdb_default  = 'syslog';[/COLOR]
[COLOR=#ff0000]        $syslogdb_hostname = 'localhost';[/COLOR]
[COLOR=#ff0000]        $syslogdb_username = 'cacti';[/COLOR]
[COLOR=#ff0000]        $syslogdb_password = 'J&P=GTP%22';[/COLOR]
[COLOR=#ff0000]        $syslogdb_port     = 3306;[/COLOR]
[COLOR=#ff0000]}else{
[/COLOR][COLOR=#ff0000]        $syslogdb_type     = $database_type;[/COLOR]
[COLOR=#ff0000]        $syslogdb_default  = $database_default;[/COLOR]
[COLOR=#ff0000]        $syslogdb_hostname = $database_hostname;[/COLOR]
[COLOR=#ff0000]        $syslogdb_username = $database_username;[/COLOR]
[COLOR=#ff0000]        $syslogdb_password = $database_password;[/COLOR]
[COLOR=#ff0000]        $syslogdb_port     = $database_port;[/COLOR]
[COLOR=#ff0000]}[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]/* field in the incomming table */[/COLOR]
[COLOR=#ff0000]$syslog_incoming_config['dateField']          = 'date';[/COLOR]
[COLOR=#ff0000]$syslog_incoming_config['timeField']          = 'time';[/COLOR]
[COLOR=#ff0000]$syslog_incoming_config['priorityField']      = 'priority';[/COLOR]
[COLOR=#ff0000]$syslog_incoming_config['facilityField']      = 'facility';[/COLOR]
[COLOR=#ff0000]$syslog_incoming_config['hostField']          = 'host';[/COLOR]
[COLOR=#ff0000]$syslog_incoming_config['textField']          = 'message';[/COLOR]
[COLOR=#ff0000]$syslog_incoming_config['id']                 = 'seq';[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]?>
```[/COLOR]



My rsyslog.conf is as follows;```

[COLOR=#ff0000]#  /etc/rsyslog.conf    Configuration file for rsyslog.[/COLOR]
[COLOR=#ff0000]#[/COLOR]
[COLOR=#ff0000]#                       For more information see[/COLOR]
[COLOR=#ff0000]#                       /usr/share/doc/rsyslog-doc/html/rsyslog_conf.html[/COLOR]
[COLOR=#ff0000]#[/COLOR]
[COLOR=#ff0000]#  Default logging rules can be found in /etc/rsyslog.d/50-default.conf[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]$ModLoad ommysql[/COLOR]
[COLOR=#ff0000]$template cacti_syslog,"INSERT INTO syslog_incoming(facility, priority, date, time, host, message) values (%syslogfacility%, %syslogpriority%,  '%timereported:::date-m$[/COLOR]
[COLOR=#ff0000]*.*             >localhost,syslog,cacti,J&P=GTP%22;cacti_syslog[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]#################[/COLOR]
[COLOR=#ff0000]#### MODULES ####[/COLOR]
[COLOR=#ff0000]#################[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]module(load="imuxsock") # provides support for local system logging[/COLOR]
[COLOR=#ff0000]module(load="imklog")   # provides kernel logging support[/COLOR]
[COLOR=#ff0000]#module(load="immark")  # provides --MARK-- message capability[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]# provides UDP syslog reception[/COLOR]
[COLOR=#ff0000]module(load="imudp")[/COLOR]
[COLOR=#ff0000]input(type="imudp" port="514")[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]# provides TCP syslog reception[/COLOR]
[COLOR=#ff0000]module(load="imtcp")[/COLOR]
[COLOR=#ff0000]input(type="imtcp" port="514")[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]# Enable non-kernel facility klog messages[/COLOR]
[COLOR=#ff0000]$KLogPermitNonKernelFacility on

[/COLOR][COLOR=#ff0000]###########################[/COLOR]
[COLOR=#ff0000]#### GLOBAL DIRECTIVES ####[/COLOR]
[COLOR=#ff0000]###########################[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]#[/COLOR]
[COLOR=#ff0000]# Use traditional timestamp format.[/COLOR]
[COLOR=#ff0000]# To enable high precision timestamps, comment out the following line.[/COLOR]
[COLOR=#ff0000]#[/COLOR]
[COLOR=#ff0000]$ActionFileDefaultTemplate RSYSLOG_TraditionalFileFormat[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]# Filter duplicated messages[/COLOR]
[COLOR=#ff0000]$RepeatedMsgReduction on[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]#[/COLOR]
[COLOR=#ff0000]# Set the default permissions for all log files.[/COLOR]
[COLOR=#ff0000]#[/COLOR]
[COLOR=#ff0000]$FileOwner syslog[/COLOR]
[COLOR=#ff0000]$FileGroup adm[/COLOR]
[COLOR=#ff0000]$FileCreateMode 0640[/COLOR]
[COLOR=#ff0000]$DirCreateMode 0755[/COLOR]
[COLOR=#ff0000]$Umask 0022[/COLOR]
[COLOR=#ff0000]$PrivDropToUser syslog[/COLOR]
[COLOR=#ff0000]$PrivDropToGroup syslog

[/COLOR][COLOR=#ff0000]#[/COLOR]
[COLOR=#ff0000]# Where to place spool and state files[/COLOR]
[COLOR=#ff0000]#[/COLOR]
[COLOR=#ff0000]$WorkDirectory /var/spool/rsyslog[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]#[/COLOR]
[COLOR=#ff0000]# Include all config files in /etc/rsyslog.d/[/COLOR]
[COLOR=#ff0000]#[/COLOR]
[COLOR=#ff0000]$IncludeConfig /etc/rsyslog.d/*.conf

[/COLOR][COLOR=#000000]
Thank you,
Kevin
[/COLOR][COLOR=#ff0000]

[/COLOR]
```

---

