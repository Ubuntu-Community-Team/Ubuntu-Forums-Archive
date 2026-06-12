---
title: "dpkg was interrupted, and --configure -a does not help..."
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by SymenTimmermans on 2010-09-15
Since trying to update the Zend Server CE 5.2 php packages, something went wrong. With every apt-get or aptitude command, I'm told:

```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

When I run the suggested command manually, it gives the following output:

```

$ sudo dpkg --configure -a
Setting up php-5.2-gui-zend-server (5.0.134+b36) ...
Site zendserver_gui.conf already enabled
 * Reloading web server config apache2                                          apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Sep 15 22:07:05 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
                                                                         [ OK ]
Restarting lighttpd to refresh Zend Server GUI
Terminated

```

Of course I searched google and this forum and tried some stuff suggested in other posts:
- I tried purging and re-installing the offending(?) package php-5.2-gui-zend-server, did not help. 
- I tried removing the dpkg info files ($ sudo rm /var/lib/dpkg/info/*zend*pre*), no help.
- I tried rebooting and forcing a fsck, no help.
- I tried moving the dpkg update files ($ sudo mv /var/lib/dpkg/updates/ /root/), followed by update/upgrade. No help.

I am hoping someone on this forum has had similar issues after a recent upgrade, and help me with a solution.

---

### Post by bst_28 on 2010-09-16
I confirm this, same problem is happening to me, when I downloaded updates for zend server.
```

sudo dpkg --configure -a

```
Running this command give me this error.
> 
Setting up php-5.3-gui-zend-server (5.0.134+b35) ...
Site zendserver_gui.conf already enabled
 * Reloading web server config apache2                                          Restarting lighttpd to refresh Zend Server GUI
Terminated
Is there any way by which i can remove zend-server using apt, and then I can install it.So this issue don't occur.

---

### Post by sikander3786 on 2010-09-16
Have you tried removing via aptitude?

```

sudo aptitude remove <offending package>

```

Aptitude has worked for me before in these type of cases so I think you should give it a try.

---

### Post by SymenTimmermans on 2010-09-16
Synaptic reminded me this is also part of the error message:

```

E: _cache->open() failed, please report.

```

---

### Post by SymenTimmermans on 2010-09-16
I think it has something to do with Lighttpd:

```

Setting up php-5.2-common-extensions-zend-server-ce (5.0.0+b15) ...
Setting up libframework1-zend-server (1.10.4+b8) ...
Setting up php-5.2-gui-zend-server (5.0.134+b36) ...
Enabling site zendserver_gui.conf.
Run '/etc/init.d/apache2 reload' to activate new configuration!
 * Reloading web server config apache2                                                                                                                                        apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Thu Sep 16 10:44:54 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
                                                                                                                                                                       [ OK ]
Restarting lighttpd to refresh Zend Server GUI
E: Sub-process /usr/bin/dpkg exited unexpectedly
A package failed to install.  Trying to recover:
Setting up zend-server-doc (5.0.6+b12) ...
Setting up php-5.2-gui-zend-server (5.0.134+b36) ...
Site zendserver_gui.conf already enabled
 * Reloading web server config apache2                                                                                                                                        apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Thu Sep 16 10:44:55 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
                                                                                                                                                                       [ OK ]
Restarting lighttpd to refresh Zend Server GUI
Terminated

```

---

### Post by SymenTimmermans on 2010-09-16
I found the following post regarding the not-functioning lighttpd after the upgrade:

[http://forums.zend.com/viewtopic.php?f=44&t=7809#p26232](http://forums.zend.com/viewtopic.php?f=44&t=7809#p26232)

I tried the 'fixes', but that did not solve the problem for me.

---

### Post by SymenTimmermans on 2010-09-16
I found this code

```

    sudo /usr/local/zend/bin/zendctl.sh stop
    sudo rm -rfv /usr/local/zend/tmp/*
    sudo /usr/local/zend/bin/zendctl.sh start

```

on this page: [http://forums.zend.com/viewtopic.php?f=44&t=7675&p=25922&hilit=lighttpd#p25922](http://forums.zend.com/viewtopic.php?f=44&t=7675&p=25922&hilit=lighttpd#p25922)

After running that code, followed by a 'sudo dpkg --configure -a' everything started working again and the error message went away.

Good luck!

---

### Post by mfrna on 2010-09-16
> **SymenTimmermans said:**
> I found this code

```

    sudo /usr/local/zend/bin/zendctl.sh stop
    sudo rm -rfv /usr/local/zend/tmp/*
    sudo /usr/local/zend/bin/zendctl.sh start

```

on this page: [http://forums.zend.com/viewtopic.php?f=44&t=7675&p=25922&hilit=lighttpd#p25922](http://forums.zend.com/viewtopic.php?f=44&t=7675&p=25922&hilit=lighttpd#p25922)

After running that code, followed by a 'sudo dpkg --configure -a' everything started working again and the error message went away.

Good luck!

I love you :D
:popcorn:

---

### Post by bst_28 on 2010-09-17
Thanks, SymenTimmermans.You have solved my problem, at least my package manager is fine.

Although, I am getting these error messages in synaptic, when I reinstall zend-server-ce
> E: php-5.3-debugger-zend-server: subprocess installed post-installation script returned error exit status 1
E: php-5.3-zend-extensions-ce: dependency problems - leaving unconfigured
E: zend-server-ce-php-5.3: dependency problems - leaving unconfigured
E: help-zend-server-ce: dependency problems - leaving unconfigured


---

