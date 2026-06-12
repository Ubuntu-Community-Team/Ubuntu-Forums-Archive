---
title: "Need help with LAMP, fresh install"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by Soop_ on 2010-01-08
Hi there.
I've been trying to install a webserver.  Should be easy; I used to make them all the time about 10 years ago.

This time I started with a copy of fedora.  That had problems with the installer and generally being not very good.

So I installed Ubuntu today.  I used the package manager thing to look for Apache (apparantly you don't use binaries anymore due to dependancy issues) and it wasnt there...

I installed Ubuntu server over the top figuring this might be the problem, but still no apache.  And sshd doesn't seem to be running.

Can someone give me a simple guide bearing in mind the above for installing LAMP and getting sshd working?  I've tried all those "sudo apt-get install lamp-server" things, and that seems to do nothing.  This is a fresh install.  Thanks in advance.

---

### Post by lewisforlife on 2010-01-08
I used this guide to set up an Ubuntu LAMP server: [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies).

You might also have a look at [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP).

Also, if you havn't already, run:

```
sudo apt-get update
```

This will update the local copy of the list of software available in the repos.

Also, I do not use the graphical package manager program, but I just looked and I don't see apache listed either.  But if you open a shell and do a search:

```
apt-cache search apache
```

You will see that there are dozens of packages with "apache" in the name.  The one you want will be called "apache2".

---

### Post by Soop_ on 2010-01-08
Ok, it might be that the proxy needed to be updated for everything

Oh thanks, I've just run the apt-get command, but it was this that initially clued me in on the proxy

Update: sudo apt-get install lamp-server did nothing.  I've proceeded to install Apache on it's own.  Is this wise?

---

### Post by lewisforlife on 2010-01-08
> **Soop_ said:**
> Ok, it might be that the proxy needed to be updated for everything

Oh thanks, I've just run the apt-get command, but it was this that initially clued me in on the proxy

Update: sudo apt-get install lamp-server did nothing.  I've proceeded to install Apache on it's own.  Is this wise?

Yeah, that will be fine, that is how I did it.  Just make sure you follow the rest of the instructions at [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies) after you install apache, because it will show you how to set up PHP, MySQL, etc...

To my knowledge there is no package called lamp-server, so apt-get install lamp-server will do nothing.  There is a program called tasksel that you can use to install a lamp server with.  I believe:

```
sudo tasksel install lamp-server
```

would do the trick.

Or you can use

```
sudo tasksel
```

and select lamp server.

---

### Post by Soop_ on 2010-01-08
Thankyou Lewis, that's really helpful!

---

