---
title: "Help repairing apache in 8.04"
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by JiminSD on 2008-06-20
Hi,

I apologize if this is a dumb question or answered elsewhere. I've been searching unsuccessfully for a while and giving up (asking for help).

I've been involved with Linux to varying degrees since '93, but mostly on internals and not at the system configuration level. I'm a little new with Ubuntu (but like it very much). Anyway, onto my problem...

I've been trying (unsuccessfully) to learn ROR and in trying to install rails/gem/ruby (also unsuccessful) I seem to have corrupted my apache configuration and of course did not make a backup before jumping in and modifying files so now my webserver no longer works and fails (dump below).

Is there a way with ubuntu to just reload the original configuration files and start over?

Thanks,
jim
============================================

./apache2 restart
open: Permission denied
 * Restarting web server apache2                                                                            Warning: DocumentRoot [/home/klothos/www/phpix] does not exist
Warning: DocumentRoot [/home/myuser/www/mynewapp/public] does not exist
apache2: Could not reliably determine the server's fully qualified domain name, using 75.36.32.227 for ServerName
httpd (no pid file) not running
Warning: DocumentRoot [/home/klothos/www/phpix] does not exist
Warning: DocumentRoot [/home/myuser/www/mynewapp/public] does not exist
apache2: Could not reliably determine the server's fully qualified domain name, using [xxx.xxx.xxx.xxx] for ServerName
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
open: Permission denied

---

