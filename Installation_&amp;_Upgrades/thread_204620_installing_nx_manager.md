---
title: "installing nx manager"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by krisravn on 2006-06-27
Hey

I have just installing the new version 2.x of nx server, and it works greate, but I also need the nx manager, so I install the nx manager2.x and apache2 , and follow the guide, but I can't get it to work. I will post my httpd.conf, manager.conf and manager.cfg.
After I have restartet the apacer, the server is runnig, but if I try to go to [http://server-ip/cgi-bin/nxmanager/](http://server-ip/cgi-bin/nxmanager/) it 
re-direct me to this site [http://help.prtracker.com/DetermineServerIpAddress.html](http://help.prtracker.com/DetermineServerIpAddress.html)

httpd.conf
```

# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so

#Use for nxserver manager
Include /usr/NX/etc/manager.conf

```

manager.conf
```

Alias /nxmanager/ "/usr/NX/htdocs/nxmanager/"

ScriptAlias "/cgi-bin/nxmanager" "/usr/NX/bin/nxmanager"

<Directory "/usr/NX/">
    AllowOverride None
    Options None
    Order allow,deny
### ADDRESS RESTRICTIONS START ###
    Allow from all
### ADDRESS RESTRICTIONS STOP  ###
</Directory>

```


manager.cfg
```

#/**************************************************************************/
#/*                                                                        */
#/* Copyright (c) 2004, 2006 NoMachine, http://www.nomachine.com.          */
#/*                                                                        */
#/* NXMANAGER, NX protocol compression and NX extensions to this software  */
#/* are copyright of NoMachine. Redistribution and use of the present      */
#/* software is allowed according to terms specified in the file LICENSE   */
#/* which comes in the source distribution.                                */
#/*                                                                        */
#/* Check http://www.nomachine.com/licensing.html for applicability.       */
#/*                                                                        */
#/* NX and NoMachine are trademarks of Medialogic S.p.A.                   */
#/*                                                                        */
#/* All rights reserved.                                                   */
#/*                                                                        */
#/**************************************************************************/

#
#  Log
#

ENABLE_DEBUG = "0"

#Level can be ERROR | WARNING | INFO | DEBUG
LOG_LEVEL = "INFO"

#
#Specify user name of Apache owner
#
APACHE_UNAME = "nobody"

#
#Specify group name of Apache owner
#
APACHE_GNAME = "nogroup"


#
# Specify the Apache reload command.
#
APACHE_HTTPD_RELOAD_COMMAND = "/etc/init.d/apache2 graceful"

#
# Specify the location of the NX Server Manager configuration file to
# be included in the Apache configuration file.
#
NXMANAGER_CONF_PATH = "/usr/NX/etc/manager.conf"

#
# Specify the directory where the statistics images are placed.
#
STAT_PATH_TEMP_FS = "/usr/NX/htdocs/nxmanager/images/stats/tmp"

#
# Specify the URL where the statistics images are placed.
#
STAT_PATH_TEMP_WEB = "/nxmanager/images/stats/tmp"

#
# Specify the location of the nxssh binary.
#
NXSSH_PATH_BINARY = "/usr/NX/bin/nxssh"

#
# Specify the location and file name of the DSA key.
#
NXSSH_PATH_IDENTITY = "/usr/NX/share/keys/server.id_dsa.key"

#
# Specify the location of the NX libraries required by nxssh.
#
NXSSH_PATH_LIB = "/usr/NX/lib"

#
# Specify the absolute path and name of the NX Server Manager DB.
#
NXMANAGER_PATH_DB = "/usr/NX/var/db/nxmanager/nxmanager_conf.db"

#
# Specify the absolute path for the NX Server Manager templates used
# to visualize NX server data.
#
TEMPLATE_PATH = "/usr/NX/htdocs/nxmanager/templates"

#
# Specify the number of items to be visualized in the templates.
#
TEMPLATE_ITEMS_PER_PAGE = "10"

```

Regards
krisstoffer

---

### Post by pansapiens on 2006-09-13
I followed the [ NX Server Manager Installation Instructions]("http://www.nomachine.com/documents/manager/install.html"), essentially doing what you did using Dapper with apache2 and nxmanager_2.0.0-43_i386.deb, but was getting:

> 
Forbidden

You don't have permission to access /cgi-bin/ on this server.


When I went to [http://localhost/cgi-bin/nxmanager](http://localhost/cgi-bin/nxmanager)

This seemed to be due to an overriding ScriptAlias for cgi-bin in /etc/apache2/sites-enabled/000-default ??

So I changed the line in /usr/NX/etc/manager.conf

from:
```
ScriptAlias "/**cgi-bin**/nxmanager" "/usr/NX/bin/nxmanager"
```
to ```
ScriptAlias "/**nx**/nxmanager" "/usr/NX/bin/nxmanager"
```

And re-ran ```
/usr/NX/scripts/setup/nxmanager --update
``` as required, and restarted apache just to be sure.

This seemed to work, when I go to [http://localhost/nx/nxmanager](http://localhost/nx/nxmanager) I get the login screen and it all functions as expected.

I'm a complete apache novice, so this could be a 
silly way to do it .. but it works for me, so I'm happy. :D

---

### Post by ls5302 on 2007-06-09
On Feisty with Apache 2.2.3 the current versions of NX Manager v2.1.0-6 works out of the box when installed iff you correctly modify the nxmanager.conf file with the correct details as below:

#
#Specify user name of Apache owner
#
APACHE_UNAME = "**www-data**"

#
#Specify group name of Apache owner
#
APACHE_GNAME = "**www-data**"

#
# Specify the Apache reload command.
#
APACHE_HTTPD_RELOAD_COMMAND = "**/etc/init.d/apache2 reload**"

---

