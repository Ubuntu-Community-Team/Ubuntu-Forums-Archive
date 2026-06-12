---
title: "Which web server running"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by dereckfun on 2008-11-05
Hi, i installed ubuntu for second time. After new installation with same cd i see i have a web server running. When i type my ip on explorer i see a page saying "it works". I tried to stop or uninstall apache2 but it didnot work. It says apachee is not installed so not removed. What should i do to stop and/or remove this server and not to respond outer requests like explorer or ping.
thanks for help.

---

### Post by Coreigh on 2008-11-05
First a question; If you open firefox and type [http://localhost/](http://localhost/) in the address bar do you get the same "It works!" page? This confirms that the server is in fact on this computer.

In a Terminal window type ```
ps -A | grep apache
```

the results from above command will confirm it is apache.

```
sudo /etc/init.d/apache2 stop
``` command above will stop the server

```
sudo apt-get remove apache2
``` command above will uninstall the web server apache.



If it is not apache you will need to identify it, but it is unlikely to be anything else.

---

### Post by dereckfun on 2008-11-05
i dont have desktop on my server. so i  cannot try localhost.

when i give command 
```
#ps -A | grep apache 
result is : 
4662 ?        00:00:00 apache2
```
but result for ```
#ps -ef | grep apache
www-data  4662     1  0 22:43 ?        00:00:00 /usr/sbin/apache2 -k start
```


result for command-:
```
#/etc/init.d/apache2 stop
 * Stopping web server apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (pid 4636?) not running
   ...done.
```


result for command 
```
#apt-get remove apache2
Building dependency tree       
Reading state information... Done
Package apache2 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 75 not upgraded.

```

Still i see the "it works" page with my ip address.

---

### Post by Coreigh on 2008-11-05
Neat.

Sorry about the local host idea I glassed over the server vs. desktop part.

Well more ideas.
this will show you what apache packages are installed
```
sudo dpkg -l | grep apache
```
You can try to remove them with apt-get remove

Also: Look through each of /etc/rc*.d (where * = 0 thru 6) and delete the references to apache. Then re-boot the machine. Removing the references should prevent apache from starting.

---

### Post by dereckfun on 2008-11-05
i tried to uninstall but still remaining some files.
"apache2.2-common                      2.2.8-1                     Next generation, scalable, extendable web se
rc  libapache2-mod-php5                   5.2.4-2ubuntu5              server-sid"

i removed apache from rc0 and rc1 files in /etc. but it didnot work again.

---

### Post by Coreigh on 2008-11-05
Type this:
```
sudo apt-get remove apache2.2-common
```


Here is the out put you should see (or very similar)

```

me@myserver:~$ sudo apt-get remove apache2.2-common
[sudo] password for me:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmcrypt4 php5-mcrypt libltdl3
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  apache2 apache2-mpm-prefork apache2.2-common libapache2-mod-php5 phpmyadmin
0 upgraded, 0 newly installed, 5 to remove and 5 not upgraded.
Remv apache2 [2.2.4-3ubuntu0.1]
Remv phpmyadmin [4:2.10.3-1ubuntu0.2]
Remv libapache2-mod-php5 [5.2.3-1ubuntu6.4]
Remv apache2-mpm-prefork [2.2.4-3ubuntu0.1]
Remv apache2.2-common [2.2.4-3ubuntu0.1]

```

I did this on my 7.10 LAMP server

---

### Post by dereckfun on 2008-11-05
its ok now... 
thank you very much for your help.

---

