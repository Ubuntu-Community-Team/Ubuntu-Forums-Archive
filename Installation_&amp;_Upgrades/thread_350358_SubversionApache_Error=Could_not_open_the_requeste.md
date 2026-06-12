---
title: "Subversion/Apache Error=Could not open the requested SVN filesystem"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by mattc58 on 2007-01-31
Hello Friends,

I have installed Subversion 1.4.3 on my Ubuntu 6.10 system and all is well.  I then followed the directions in [this post]("http://ariejan.net/2006/12/01/how-to-setup-a-ubuntu-development-server-part-1/") to install **libapache2-svn** and that works also.

I've edited my config file to point Apache to my repository, but when I go there in a browser I get:


<D:error>
<C:error/>
<m:human-readable errcode="165005">
Could not open the requested SVN filesystem
</m:human-readable>
</D:error>

Any ideas here?  I've got Apache (www-data) owning my SVN repository and the permissions are set to 777 for now just to see if it will work.

Thanks,

Matt

---

### Post by l0co on 2007-04-04
You probably have incompatible version of your subversion and apache2 svn module, installed from repositories. I have the same problem, and it's what appears in the /var/log/apache2/error.log after accessing the repository by http:

```

[Wed Apr 04 16:44:15 2007] [notice] Apache/2.0.55 (Ubuntu) DAV/2 SVN/1.3.1 PHP/5.1.2 mod_ssl/2.0.55 OpenSSL/0.9.8a configured -- resuming normal operations
[Wed Apr 04 16:58:16 2007] [error] [client 127.0.0.1] (20014)Error string not specified yet: Expected format '3' of repository; found format '5'
[Wed Apr 04 16:58:16 2007] [error] [client 127.0.0.1] Could not fetch resource information.  [500, #0]
[Wed Apr 04 16:58:16 2007] [error] [client 127.0.0.1] Could not open the requested SVN filesystem  [500, #165005]
[Wed Apr 04 16:58:16 2007] [error] [client 127.0.0.1] Could not open the requested SVN filesystem  [500, #165005]

```

Try accessing it by:

```

 svn log file:///your/repository/path

```

what should end without error to see whether the subversion is installed properly, and the problem is with apache.

---

### Post by tjombka on 2008-03-02
It looks like enforcing SELinux

---

### Post by dougdyer on 2008-03-24
Perhaps others are not having the same problem based on lack of information on the web, but I found that a Location variable in the Apache configuration files needed changing when I tried to install Subversion with Apache 2.0.   After installing Subversion and the mod_dav_svn plug-in to mod_dav, I edited /etc/apache2/mods-enabled/dav_svn.conf and entered the parent directory of my repositories, unfortunately setting it as the value of SVNPath.   As frequently happens when you rush, I didn't realize that was the wrong variable.  SVNPath refers to a repository directory and is only useful if you have a single repository.   As a result, I got the dreaded "Could not open the requested SVN filesystem" error.  Changing SVNPath to SVNParentPath made everything work fine.

---

### Post by doctorfilter on 2008-04-14
> **dougdyer said:**
>  Changing SVNPath to SVNParentPath made everything work fine.

So how do you actually do that then? Cause I changed it and broke and cant find the tute I used to set it. :guitar:

---

