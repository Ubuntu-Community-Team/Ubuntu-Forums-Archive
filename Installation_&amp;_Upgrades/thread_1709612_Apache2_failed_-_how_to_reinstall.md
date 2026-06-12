---
title: "Apache2 failed - how to reinstall"
date: 2011-03-18
forum: Installation &amp; Upgrades
---

### Post by spindler on 2011-03-18
I was attempting to add a module to my wordpress website and the system lock up.  I noticed all of my websites went down and the Mysql database is down as well.    

I attempted to restart Apache2  using the following

sudo /etc/init.d/apache2 restart

When I do this I get the following error message.

 * Restarting web server apache2                                                
(98 ) Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
Action 'start' failed.
The Apache error log may have more information.
                                                                                                                             [fail]

The ERROR logs shows the following:

[Fri Mar 18 11:13:54 2011] [notice] caught SIGTERM, shutting down


[Fri Mar 18 11:38:16 2011] [error] Init: Private key not found
[Fri Mar 18 11:38:16 2011] [error] SSL Library Error: 218710120 error:0D094068:asn1 encoding routines:d2i_ASN1_SET:bad tag
[Fri Mar 18 11:38:16 2011] [error] SSL Library Error: 218529960 error:0D0680A8:asn1 encoding routines:ASN1_CHECK_TLEN:wrong tag
[Fri Mar 18 11:38:16 2011] [error] SSL Library Error: 218595386 error:0D07803A:asn1 encoding routines:ASN1_ITEM_EX_D2I:nested asn1 error
[Fri Mar 18 11:38:16 2011] [error] SSL Library Error: 218734605 error:0D09A00D:asn1 encoding routines:d2i_PrivateKey:ASN1 lib


I think something happened when wordpress attempted to update the database.   I cannot log into [http://localhost/phpmyadmin](http://localhost/phpmyadmin) however I can log into the shell MySQl 

How can I fix this issue.  All of my websites are down so I know it is not a specific database.  

How do I reinstall apache2?

What could my issue be?

Thanks

Spindler

---

### Post by abdellatef1 on 2011-03-18
sudo apt-get autoremove apache2 mysql-server php5 php5-mysql 

 was Re-install 

good luck my friend


[IMG]http://fc00.deviantart.net/fs31/f/2008/231/f/c/_Hacker__by_DEVlANT.gif[/IMG]

---

### Post by spindler on 2011-03-18
What does this command do?

I assume it will remove the following:

Apache2
Mysql - server
PHP5
PHP5-mysql


This is a lot to remove....wow

How do I reinstall the above?  What is the command?

Will I need to reload the mysql database(s) ?

Will I need to re-setup Apache2?

What else will I need to do once I reinstall the 4 above ?

Thanks,

Spindler

---

