---
title: "Broke Apache when Upgrading to Maverick :("
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by Gremlyn1 on 2010-10-13
So I was foolish and while upgrading to 10.10, I opted to keep my apache conf files as they were (since I forgot to back them up before starting) and now apache isn't happy at all. At first it just wasn't working, so I backed up my entire /etc/apache2 dir, ran 
```
'sudo apt-get purge apache2'
```
and then deleted all references and left over config files, then ran
```
'sudo apt-get install apache2'
```
and still apache wasn't working - in fact it did not seem to properly/completely reinstall with all dependencies.

Next I went through in Synaptic and removed a bunch of stuff myself, tried another apt-get purge and install, and still nada. Next I tried 
```
'sudo aptitude purge apache2'
```
which seemed to run a little more robustly. So naturally next I ran 
```
'sudo aptitude install apache2'
```
and though it seemed to install everything appropriately, apache was not started and trying to run 
```
'sudo service apache2 start'
```
I get an unrecognised service error.

When trying to directly run 
```
'sudo /usr/sbin/apache2'
```
I get 
```
'apache2: Could not open configuration file /etc/apache2/apache2.conf: No such file or directory'
```
which is true... it does not exist but I don't understand why it's not reinstalling properly.

Luckily this is just a local test server and I don't need to right now, but it would be good to get it back up and running... Any help would be greatly appreciated!

PS: could this really be all because I didn't replace my old files with the new conf files?

---

### Post by Gremlyn1 on 2010-10-13
OK, I think I am getting somewhere. I ran the following:
```

sudo aptitude purge apache2.2-common
sudo aptitude purge apache2-utils
sudo aptitude install apache2

```

Apache now starts like it should, though it isn't working properly, I think I just need to diff the conf files and get my settings back in there...

---

### Post by Gremlyn1 on 2010-10-13
OK, I got all my settings restored and all is well. maybe this will serve as a guide for someone else out there that is a boneheaded as me :)

---

### Post by geo.cohn on 2010-10-31
My apache2 server also broke when I went from Lucid to Maverick.  I have tried everything I can think of, including a complete remove/purge and re-install.  I still receive the same message when I try to start the service:
```
* Starting web server apache2
apache2: Syntax error on line 203 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/php5.load: Cannot load /usr/lib/apache2/modules/libphp5.so into server: /lib/libssl.so.0.9.8: symbol ENGINE_load_ssl_client_cert, version OPENSSL_0.9.8 not defined in file libcrypto.so.0.9.8 with link time reference
Action 'start' failed.
```

---

### Post by geo.cohn on 2010-11-29
Still broken.  My configuration includes libapache2-mod-php5.  Since this is typical in a LAMP configuration, we should be seeing a lot more complaints like this.  I must be doing something wrong.  Any ideas?

---

### Post by geo.cohn on 2010-12-04
I did some more investigation and came up with a workaround.

first I looked to see how many places had the file or link libcrypto.so.0.9.8:

```
geo@maverick:~$ locate libcrypto.so.0.9.8
/lib/libcrypto.so.0.9.8
/usr/lib/libcrypto.so.0.9.8
/usr/lib/i686/cmov/libcrypto.so.0.9.8
geo@maverick:~$

```I found that /usr/lib/libcrypto.so.0.9.8 was a symbolic link to /lib/libcrypto.so.0.9.8, but /usr/lib/i686/cmov/libcrypto.so.0.9.8 was a separate file.  It turned out that the entry ENGINE_load_ssl_client_cert existed in /lib/libcrypto.so.0.9.8 but not in /usr/lib/i686/cmov/libcrypto.so.0.9.8.

```
geo@maverick:~$ objdump -T /lib/libcrypto.so.0.9.8 | grep ENGINE_load_ssl_client_cert
00096890 g    DF .text    00000175  OPENSSL_0.9.8 ENGINE_load_ssl_client_cert
geo@maverick:~$ objdump -T /usr/lib/i686/cmov/libcrypto.so.0.9.8 | grep ENGINE_load_ssl_client_cert
geo@maverick:~$

```Evidently a funny version of libcrypto.so.0.9.8 is being installed into /usr/lib/i686/cmov/ and that version is taking precedence.  My remedy was to replace the funny version with a symbolic link to the good version:

```
geo@maverick:~$ sudo rm /usr/lib/i686/cmov/libcrypto.so.0.9.8
geo@maverick:~$ sudo ln -s /lib/libcrypto.so.0.9.8 /usr/lib/i686/cmov/libcrypto.so.0.9.8
geo@maverick:~$

```After doing that, apache2 can be started and runs with php5 and mysql server.

---

