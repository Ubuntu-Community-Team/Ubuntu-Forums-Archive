---
title: "How to run Apache"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by kannanjagadeesan on 2010-03-28
Hi Experts,

I have installed Apache2 for my PHP study. I do not know how to start and stop it. I ran with the command which I got from this forum

apache2 start

and I got these following things....

vignesh@vignesh:/etc/apache2$ sudo apache2 start
[sudo] password for vignesh: 
Usage: apache2 [-D name] [-d directory] [-f file]
               [-C "directive"] [-c "directive"]
               [-k start|restart|graceful|graceful-stop|stop]
               [-v] [-V] [-h] [-l] [-L] [-t] [-S] [-X]
Options:
  -D name            : define a name for use in <IfDefine name> directives
  -d directory       : specify an alternate initial ServerRoot
  -f file            : specify an alternate ServerConfigFile
  -C "directive"     : process directive before reading config files
  -c "directive"     : process directive after reading config files
  -e level           : show startup errors of level (see LogLevel)
  -E file            : log startup errors to file
  -v                 : show version number
  -V                 : show compile settings
  -h                 : list available command line options (this page)
  -l                 : list compiled in modules
  -L                 : list available configuration directives
  -t -D DUMP_VHOSTS  : show parsed settings (currently only vhost settings)
  -S                 : a synonym for -t -D DUMP_VHOSTS
  -t -D DUMP_MODULES : show all loaded modules 
  -M                 : a synonym for -t -D DUMP_MODULES
  -t                 : run syntax check for config files
  -X                 : debug mode (only one worker, do not detach)


I ran this command

sudo /etc/init.d/apache2 restart

And it gave this:

 * Starting web server apache2                                                  
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (pid 5477) already running


I do not know to proceed further.

Kindly help me. Kindly forgive me if I it is the wrong place to post this thread.
With kind regards,
Kannan

---

