---
title: "MySql crashed on upgrade from 10.04 to 12.04"
date: 2012-07-09
forum: Installation &amp; Upgrades
---

### Post by bhasina on 2012-07-09
Hi,

I recently upgraded my server from 10.04 to 12.04 LTS 

Everything went smooth except my MySQL wouldn't work now. I keep getting the following error:

```
ERROR 1524 (HY000): Plugin 'none' is not loaded

```

I get the above error whenever I do

```
mysql status
```

I have tried to do a fresh install of MySQL but it continues to give the same error.  I cannot login to the server using 

```
mysql -u root -p
``` 

as it gives the same error. 

Any help will be greatly appreciated.

---

### Post by lukeiamyourfather on 2012-07-09
When you reinstalled MySQL did you purge the previous? It deletes the associated configuration files as well.

```
sudo apt-get purge mysql
```

If you haven't already be sure to have a backup of the databases before doing anything else. :shock:

---

### Post by bhasina on 2012-07-09
Yup. Purged it but still the same!

And yes I do have the backup of the /var/lib/mysql folder :)

---

### Post by jopa1234 on 2012-12-28
Just had a very similar problem.

Doing a routine server package upgrade after not doing one for a few months. Mysql 5.5 borked. No users can login, same error as above. "Plugin 'none' is not loaded".

I am reporting this because I don't see anyone else talking about this particular issue yet, and I finally cured it in my case.

Upgrading to:
mysql  Ver 14.14 Distrib 5.5.28, for debian-linux-gnu (i686) using readline 6.2

From a slightly older version not sure exactly about 5.5.22 which is the version on another box I last upgraded about the same time.

For some reason that I don't think is anything I installed, there was an extra column in the mysql.users table named 'dtcowner' which apparently is connected to "Domain Technologie Control" which I don't recall using. Maybe something I tried and removed but I doubt it.

I don't have time to track down all of the "why?" now, but I dropped the column restarted mysql server and it fixed it.

There is a similar bug reported here:
[http://bugs.mysql.com/bug.php?id=60432](http://bugs.mysql.com/bug.php?id=60432)

But this little chatroom snippet is what led me to the problem.
[http://bots.wmflabs.org/~wm-bot/logs/%23wikimedia-labs/20120827.txt](http://bots.wmflabs.org/~wm-bot/logs/%23wikimedia-labs/20120827.txt)

---

