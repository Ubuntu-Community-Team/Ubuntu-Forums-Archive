---
title: "FTP Upload failed"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by gabrie on 2012-04-27
Hi
I got an Ubuntu VM at amazon EC2. It was pre configured for the most part. I added vsftpd and wordpress to the install. Now when trying to upload a file I run into an error:  553 could not create file. I want the user to upload a file into /var/www

What I did:
Created an user   ftpupload
added the user to  /etc/vsftpd.chroot_list
checked the permissions in /var/www and saw all files and directories have:
-rw-r--r-- 1 www-data www-data 16899 2011-06-08 18:18 license.txt

So I added the user ftpupload to the www-data group (I think I did).
Running the groups command gives me this:
groups ftpupload
ftpupload : ftpupload www-data ftp

When I make a ftp connection and logon as ftpupload I can upload files into /home/ftpupload.

However, I can't upload to /var/www.

When I now perform a sudo chown -R ftpupload /var/www/   the ftpupload user CAN upload. But this doesn't seem to be the way to go, is it?

I'm used to Windows permissions and find these linux permissions very confusing.

Gabrie

How can I fix this?

---

### Post by Lars Noodén on 2012-04-27
> **gabrie said:**
> When I now perform a sudo chown -R ftpupload /var/www/   the ftpupload user CAN upload. But this doesn't seem to be the way to go, is it

That's the way to go if there is only one user that will be working in that directory.  If you are going to be sharing the folder among several users, then you'll want to use groups.

```

# do once
sudo addgroup webmasters
sudo chgrp -R webmasters /var/www

sudo find /var/www -type d -exec chmod g=rwxs "{}" \;
sudo find /var/www -type f -exec chmod g=rws  "{}" \;

# repeat for each user:
sudo gpasswd --add gabrie webmasters

```

You might also want to reconsider the use of FTP and use SFTP instead.  

[list]
[*] [http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/)
[*] [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)
[/list]

SFTP is built into clients like FileZilla an Nautilus.

---

### Post by gabrie on 2012-04-27
[QUOTE=Lars Noodén;11879498]That's the way to go if there is only one user that will be working in that directory.  If you are going to be sharing the folder among several users, then you'll want to use groups.

```

# do once
sudo addgroup webmasters
sudo chgrp -R webmasters /var/www

sudo find /var/www -type d -exec chmod g=rwxs "{}" \;
sudo find /var/www -type f -exec chmod g=rws  "{}" \;

# repeat for each user:
sudo gpasswd --add gabrie webmasters

```

Thanks, what did I miss, because I also added the ftpupload user to the www-data group which has all recurring permissions. 

Is this the crucial part?
sudo find /var/www -type d -exec chmod g=rwxs "{}" \;

---

### Post by Lars Noodén on 2012-04-27
> **gabrie said:**
> 
Thanks, what did I miss, because I also added the ftpupload user to the www-data group which has all recurring permissions. 


The www-data group is used for privilege separation by the HTTP daemon.  It should not be used for or by anything else.  The only things that should be in that group are web servers.  Trying to use it in other ways defeats the security advantage.  If a group is needed, create a new one, www-data is already spoken for.

> **gabrie said:**
> 
Is this the crucial part?
sudo find /var/www -type d -exec chmod g=rwxs "{}" \;

Both [find](http://manpages.ubuntu.com/manpages/precise/en/man1/find.1posix.html)s are crucial.  One (-type d) sets the directory permissions, the other (-type f) sets the file permissions.

---

### Post by matt_symes on 2012-04-27
Hi

> The www-data group is used for privilege separation by the HTTP daemon.   It should not be used for or by anything else.  The only things that  should be in that group are web servers.  Trying to use it in other ways  defeats the security advantage.  If a group is needed, create a new  one, www-data is already spoken for.

Thanks for this comment Lars. 

It makes so much sense and answers a security question that has been bothering me for a long while now.

Kind regards

---

### Post by gabrie on 2012-04-27
> **Lars Noodén said:**
> The www-data group is used for privilege separation by the HTTP daemon.  It should not be used for or by anything else.  The only things that should be in that group are web servers.  Trying to use it in other ways defeats the security advantage.  If a group is needed, create a new one, www-data is already spoken for.



Both [find](http://manpages.ubuntu.com/manpages/precise/en/man1/find.1posix.html)s are crucial.  One (-type d) sets the directory permissions, the other (-type f) sets the file permissions.

Thank you !!!

---

### Post by Lars Noodén on 2012-04-29
You're welcome.

If you are using Apache2 you can see where it is specified in the configuration file by looking for [user](https://httpd.apache.org/docs/2.2/mod/mpm_common.html#user) and [group](https://httpd.apache.org/docs/2.2/mod/mpm_common.html#group).

If you're working with scripts (perl, python, php, etc.) then you can take it a step further and assign membership using the [SuExecUserGroup](https://httpd.apache.org/docs/2.2/mod/mod_suexec.html#suexecusergroup) directive.  That way you could assign write access to a directory or device to a specific routine without having to give the whole system the same level of access.

---

