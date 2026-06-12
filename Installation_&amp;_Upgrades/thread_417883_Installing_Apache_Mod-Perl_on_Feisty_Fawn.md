---
title: "Installing Apache Mod-Perl on Feisty Fawn?"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by kmslinux on 2007-04-22
I used this command:
```
root@Connubuntu:~# apt-get install apache libapache-mod-perl
```
and tested it with a CGI file. It didn't work. Also, I changed the extension from .cgi to .pl. It still didn't work. Please help!

---

### Post by kabronkline on 2007-04-22
Hopefully there is a tutorial somewhere... I'll post back if I have any progress.

---

### Post by sibijv on 2007-04-25
Might be a stupid question but do u have perl 5.8.8 and apache 2?

---

### Post by kmslinux on 2007-04-25
> **sibijv said:**
> Might be a stupid question but do u have perl 5.8.8 and apache 2?

Not a stupid question at all. Yes, I do.

---

### Post by sibijv on 2007-04-27
Hi 

did you get a solution? Pls do post. I am trying to speedup my twiki ([www.twiki.org](www.twiki.org)) using mod_perl running on Ubuntu 7.04. As per the posting at [http://twiki.org/cgi-bin/view/Codev/ModPerlUnix#Enabling_mod_perl](http://twiki.org/cgi-bin/view/Codev/ModPerlUnix#Enabling_mod_perl) it works for apache2.

i get the error

> Syntax error on line 1 of /etc/apache2/httpd.conf:
Invalid command 'PerlRequire', perhaps misspelled or defined by a module not included in the server configuration
   ...fail!

sibi

---

### Post by kmslinux on 2007-04-28
I haven't found a solution yet, sadly...

---

### Post by kwadroke on 2007-04-30
Try
```
apt-get install libapache2-mod-perl2
```
I had to do this with Edgy and Feisty.
Make sure you restart apache2 after installation.
```
sudo /etc/init.d/apache2 force-reload
```

You can check this by going to a non-existent page and look at the bottom line of the 404 page. Here's the bottom of my 404 error page.
[HTML] Apache/2.2.3 (Ubuntu) PHP/5.2.1 mod_perl/2.0.2 Perl/v5.8.8 Server at localhost Port 80[/HTML]

---

### Post by sibijv on 2007-05-03
hi kwadroke  

Tried but it did not work. My 404 page reads 

> Apache/2.2.3 (Ubuntu) PHP/5.2.1 Server at test.testserver.net Port 80

i even restarted the machine but no use :-(

---

### Post by kmslinux on 2007-05-04
I got so frustrated with everything so I just started from scratch...

```
root@Connubuntu:~#  apt-get install apache2 libapache2-mod-perl2
Blah blah blah...
Unpacking blah...
Something or other...
root@Connubuntu:~# apache2
line 29 of /etc/apache2/httpd.conf: ServerRoot takes one argument, Common directory of server-related files (logs, confs, etc.)
```

What the heck just happened?!

---

### Post by tr333 on 2007-05-05
you probably need to enable mod_perl with "sudo a2enmod".  it can be disabled later with "sudo a2dismod".

the best way to restart apache2 is with the "sudo apache2ctl graceful" command.

---

### Post by kmslinux on 2007-05-05
I basically fixed all the httpd.conf problems. When I "sudo apache2ctl start", it's warning me about a bunch of modules already loaded. I did some googling and came to the conclusion that they were declared twice. They weren't. I rebooted my machine and it still warns me. Help please! By the way, I'm a noob when it comes to the internet... :P

---

### Post by tr333 on 2007-05-05
the main config file for apache2 is located at /etc/apache2/apache2.conf.  if you look in this file, you will notice the line:
```
# Include all the user configurations:
Include /etc/apache2/httpd.conf
```
this will include whatever exists in the file /etc/apache2/httpd.conf, so if you declare stuff in httpd.conf that already exists in apache2.conf this might give the error you're describing.

---

### Post by kmslinux on 2007-05-06
Thanks! That helped a lot! Except for the fact that when I run "sudo apache2ctl start" apache2 doesn't start... I honestly have no clue as to what's going on...

---

### Post by tr333 on 2007-05-06
"sudo apache2ctl start" gives an error if apache2 is already running.
if it says "httpd (pid xxxx) already running", then you don't need to start it.
try running the command "sudo apache2ctl graceful" and see whether that restarts it for you.

if you want to check your apache config files for syntax validity, run the command "sudo apache2ctl configtest".
you can see what the other "apache2ctl" commands are with "man apache2ctl".

---

### Post by kmslinux on 2007-05-07
I've run every single "apache2ctl" command out there, including the syntax check. My syntax is okay. It's just not starting. This is what it looks like...

root@Connubuntu:~# apache2ctl start
root@Connubuntu:~# nmap localhost

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-05-07 20:45 CDT
Interesting ports on localhost (127.0.0.1):
Not shown: 1695 closed ports
PORT    STATE SERVICE
443/tcp open  https /* That's my ssh server. Don't be fooled. */
631/tcp open  ipp

Nmap finished: 1 IP address (1 host up) scanned in 0.162 seconds
root@Connubuntu:~#

---

### Post by tr333 on 2007-05-08
```
ps aux | grep apache2
```
this should give a list of process running under the user "www-data" if apache2 is running.

can you access "http://localhost/index.html" (assuming /var/www/index.html exists) from the machine?

---

### Post by kmslinux on 2007-05-08
I've tried accessing localhost in Firefox, but it says the server was not found. It's not that an error is happening, it's that the server isn't starting.

---

### Post by tr333 on 2007-05-08
sorry, but I think your problem goes beyond the depth of my knowledge of linux.  hopefully someone else with more knowledge can help you on this one.

EDIT:  can you see any apache2 process running, and have you tried reinstalling apache2 with "sudo apt-get install --reinstall apache2"?

---

### Post by kmslinux on 2007-05-13
I reinstalled it and the same error occurs. Woe is me... Do you think I should quit while I'm ahead and build it from source?


EDIT: Answer: Yes. It works perfectly. Especially when I have the "<path_to_httpd>/httpd -k start" script in my bootmisc.

---

