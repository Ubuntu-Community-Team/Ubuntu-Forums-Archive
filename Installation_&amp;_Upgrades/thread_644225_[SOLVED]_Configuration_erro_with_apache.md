---
title: "[SOLVED] Configuration erro with apache"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by adster101 on 2007-12-18
Would anyone be kind enough to help me out?

I was making changes to my apache config which was working OK. Just wanted to amend the setup so that it ran .html as .php...ooops

so my error log looks like:
[Mon Dec 17 23:21:37 2007] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.2 configured -- resuming normal operations
[Mon Dec 17 23:46:17 2007] [notice] caught SIGWINCH, shutting down gracefully
[Tue Dec 18 07:20:33 2007] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.2 configured -- resuming normal operations
[Tue Dec 18 07:55:19 2007] [notice] caught SIGWINCH, shutting down gracefully
[Tue Dec 18 20:34:36 2007] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.2 configured -- resuming normal operations
[Tue Dec 18 21:10:20 2007] [error] [client 127.0.0.1] Negotiation: discovered file(s) matching request: /var/www/commerce (None could be negotiated).
[Tue Dec 18 21:15:33 2007] [notice] caught SIGWINCH, shutting down gracefully
[Tue Dec 18 21:15:43 2007] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.2 configured -- resuming normal operations
[Tue Dec 18 21:17:43 2007] [notice] caught SIGTERM, shutting down
[Tue Dec 18 21:20:42 2007] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.2 configured -- resuming normal operations
[Tue Dec 18 21:22:21 2007] [error] [client 127.0.0.1] File does not exist: /var/www/apache2
[Tue Dec 18 21:22:26 2007] [error] [client 127.0.0.1] File does not exist: /var/www/apache2
[Tue Dec 18 21:22:31 2007] [error] [client 127.0.0.1] File does not exist: /var/www/apache2
[Tue Dec 18 21:22:35 2007] [error] [client 127.0.0.1] File does not exist: /var/www/apache
[Tue Dec 18 21:24:52 2007] [notice] caught SIGWINCH, shutting down gracefully
[Tue Dec 18 21:25:02 2007] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.2 configured -- resuming normal operations
[Tue Dec 18 21:29:58 2007] [notice] caught SIGWINCH, shutting down gracefully
[Tue Dec 18 21:30:09 2007] [notice] Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.2 configured -- resuming normal operations
[Tue Dec 18 21:32:31 2007] [notice] caught SIGTERM, shutting down

and whenever I do sudo /etc/init.d/apache2 restart i get:

 * Restarting web server apache2                                                                                             apache2: Syntax error on line 187 of /etc/apache2/apache2.conf: Syntax error on line 204 of /etc/apache/httpd.conf: Syntax error on line 8 of /etc/apache/modules.conf: Cannot load /usr/lib/apache/1.3/mod_log_config.so into server: /usr/lib/apache/1.3/mod_log_config.so: cannot open shared object file: No such file or directory
                                                                                                                      [fail]
root@oslicku:/var/log/apache2# 

:confused:

---

