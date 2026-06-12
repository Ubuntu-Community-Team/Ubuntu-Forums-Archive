---
title: "Upgrade broke apache2 and mythweb"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by AndrewWalker on 2008-05-01
I've upgraded to Hardy 8.04 64bit  and now Mythweb no longer works. I tried reconfiguring mythweb and I get this message

mythtv@mythtvbox:~$ sudo dpkg-reconfigure mythweb
Your apache2 configuration is broken, so we're not restarting it for you.
mythtv@mythtvbox:~$ 

It looks like apache2 is broken by the upgrade, it was all working before hand.
Is it pilot error or a bug and how do I fix it?

---

### Post by OldGaf on 2008-05-03
> **AndrewWalker said:**
> I've upgraded to Hardy 8.04 64bit  and now Mythweb no longer works. I tried reconfiguring mythweb and I get this message

mythtv@mythtvbox:~$ sudo dpkg-reconfigure mythweb
Your apache2 configuration is broken, so we're not restarting it for you.
mythtv@mythtvbox:~$ 

It looks like apache2 is broken by the upgrade, it was all working before hand.
Is it pilot error or a bug and how do I fix it?

Did you try to reinstall apache2?

---

### Post by AndrewWalker on 2008-05-04
I reinstalled apache2 and no change. When I try to restart apache2 I get the following response.
mythtv@mythtvbox:/var/www/mythweb$ sudo /etc/init.d/apache2 restart
[sudo] password for mythtv:
 * Restarting web server apache2                                                                                                             Syntax error on line 104 of /etc/apache2/sites-enabled/mythweb.conf:
Invalid command 'php_value', perhaps misspelled or defined by a module not included in the server configuration
                                                                                                                                      [fail]
mythtv@mythtvbox:/var/www/mythweb$ 


anyone got any ideas what the problem is? I haven't altered the mythweb.conf file and it was working ok before Hardy Heron upgrade.

---

