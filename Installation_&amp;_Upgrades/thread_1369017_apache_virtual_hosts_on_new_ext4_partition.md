---
title: "apache virtual hosts on new ext4 partition"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by hinge on 2009-12-31
I run a development lamp on my laptop. I have been doing this for looong a time - no hassel.
I run each project (cakephp) as a different virtual host on apache. e.g. one project is defined like this:
```

<VirtualHost *:80>
	DocumentRoot /home/martin/development/dosmer/trunk/app/webroot
	ServerName dosmer
	<Directory /home/martin/development/dosmer/trunk/app/webroot/>
                AllowOverride All
                Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
        </Directory>
</VirtualHost>


```

This has been working!!!!
Until....

My home is mounted as a separate partition, and this partition was giving me some problems. So I decided to delete it and format it as a ext4 system. The former was ext3. After doing this I get this in my apache log:
```

 [crit] [client 127.0.1.1] (13)Permission denied: /home/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable

```

And a 403 in my browser...

Each time I try to access one of the virtual hosts. Permissions should be OK - set to 777.

I have tried to make a virtual host that resides on my root partition ("/"), which is ext3 - this works fine.

My fstab is:

```

proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=12525790-5876-4034-af19-2c62240413a9 /               ext4    errors=remount-ro 	0       1
# swap was on /dev/sda2 during installation
UUID=ec06167e-8f05-439d-8f05-b65c012e4d12 none            swap    sw                	0       0

UUID=82755c2e-a5c4-46d0-a828-9738b1f547cd /media/store	  ext4	  defaults		0       2
#/dev/sda3 /media/store	  ext4	  errors=remount-ro 0       1

/media/store/home 	/home 	none 	defaults,bind 	0 0 

```

What could be causing this - I suspect that it is the way my partition is mounted...but I don't know what to do about it.

---

### Post by phillw on 2009-12-31
Hi,

what do you get if you ```
 ls -al /home/.htaccess
```

Regards,

Phill.

---

### Post by hinge on 2010-01-01
> **phillw said:**
> Hi,

what do you get if you ```
 ls -al /home/.htaccess
```

Regards,

Phill.

I get:

```
 ls -al /home/.htaccess
ls: cannot access /home/.htaccess: No such file or directory

```
I know that the apache error.log says /home/.htaccess - I take it that when apache says home it means the virtual home folder - i.e. the looong path /home/martin/.....
Even so I don't have any .htaccess files in the test site - it should not be necessary -IMHO.

---

### Post by hinge on 2010-01-01
> **hinge said:**
> I get:

```
 ls -al /home/.htaccess
ls: cannot access /home/.htaccess: No such file or directory

```
I know that the apache error.log says /home/.htaccess - I take it that when apache says home it means the virtual home folder - i.e. the looong path /home/martin/.....
Even so I don't have any .htaccess files in the test site - it should not be necessary -IMHO.

Maybe what I wrote above is not true....

I tried to set up at virtual host in my root partition which had wrong permissions. The error in my apache error.log is:
```
 [crit] [client 127.0.1.1] (13)Permission denied: /var/www/dosmer/trunk/.htaccess pcfg_openfile: unable to check htaccess file, ensure...
```


Whereas when I move the same virtual host til the new partition I get:

```
[crit] [client 127.0.1.1] (13)Permission denied: /home/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable

```

The virtual host file for the first is:

```

<VirtualHost *:80>
        DocumentRoot /var/www/dosmer/trunk/app/webroot
        ServerName gotest
        <Directory /var/www/dosmer/trunk/app/webroot/>
                AllowOverride All
                Options FollowSymLinks
                Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
        </Directory>
</VirtualHost>


```

and the latter:

```

<VirtualHost *:80>
	DocumentRoot /home/martin/development/dosmer/trunk/app/webroot
	ServerName dosmer
	<Directory /home/martin/development/dosmer/trunk/app/webroot/>
                AllowOverride All
                Options FollowSymLinks
                Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec       
        </Directory>
</VirtualHost>

```

Why would it report the paths differently in the error log - when it says /home/ - does it atually mean /home/???? and why that????

---

### Post by kerdany on 2010-01-02
I'm also facing the same problem on Ubuntu 9.10 (Karmic) installed on my Acer Aspire One netbook. The problem goes as follows:

I have an apache2 installed on my netbook, I want to create a virtualhost on that points to a directory on a mounted drive (mounted via an entry in /etc/fstab)

The problem is that the virtualhost always returns a 403 Forbidden error.
I did some research online, but I couldn't find a clue .. All keys lead to allowing permission on files in the virtualhost directory files ..

I tried to chmod -R 775 and even 777 the directory of the virtualhost on the mounted drive (and even its parent), but the problem persists.

Information:
The drive is an ext4 partition mounted on /var/work
fstab line:
```
# /var/work was on /dev/sda3 during installation
UUID=3b0298b6-7002-4c62-9335-69d09b376ef4 /var/work       ext4    defaults        0       2
```

Virtual Host configuration (actually it's a copy of the default virtual host, and it works fine if it points to a non-mounted directory instead) .. This is a name-based virtual host:
```
<VirtualHost *:80>
    ServerName blog
    DocumentRoot /var/work/wife/blog/public_html
    <Directory /var/work/wife/blog/public_html/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None       
        Order allow,deny
        Allow from all
    </Directory>                    
</VirtualHost>
```

/etc/hosts entry:
[HTML]127.0.0.1        blog[/HTML]

Apache log error:
```
[Sun Dec 27 17:15:09 2009] [crit] [client 127.0.0.1] (13)Permission denied: /var/work/wife/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable
```

Note: notice that the server is looking for .htaccess two directories above the vhost directory?? not even one directory above it.
Also note that the error message is somehow misleading .. check this reported bug:
[http://mail-archives.apache.org/mod_mbox/httpd-bugs/200507.mbox/%3C20050707174643.4D01713@ajax.apache.org%3E](http://mail-archives.apache.org/mod_mbox/httpd-bugs/200507.mbox/%3C20050707174643.4D01713@ajax.apache.org%3E)

---

### Post by hinge on 2010-01-03
I solved my troubles lasyt night - I'm sorry to say - but apparently it was a simple matter of permissions.

```
 
sudo chmod -R 755 /home/martin/
sudo chown -R martin.users /home/martin/

```

After that it all works.

and kerdany, I can confirm you setup, it should work - try out the permissions

---

