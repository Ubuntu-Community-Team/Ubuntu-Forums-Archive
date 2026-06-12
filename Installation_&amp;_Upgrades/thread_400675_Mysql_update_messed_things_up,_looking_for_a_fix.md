---
title: "Mysql update messed things up, looking for a fix?"
date: 2007-04-03
forum: Installation &amp; Upgrades
---

### Post by unn on 2007-04-03
Earlier I installed the most recent update to mysql via automatic update.  I'm currently running 5.0.24a-Debian_9ubuntu0.1-log.  Later on I noticed that I could no longer access the mysql server from any of my other hosts on my network.  After doing some poking around I tried to flush privileges and I got the following error from mysql #130 - Incorrect file format 'tables_priv' 

I ran a repair table for pretty much every table in my 'mysql' database I saw error 130 on mysql.proc, mysql.tables_priv, and mysql_time_zone. I restarted mysql and it successfully started however, it was now "Checking for corrupt, not cleanly closed and upgrade needing tables."

I did a little googling around and i found [this thread]("http://ubuntuforums.org/showthread.php?t=284950") but this computer isn't 64 bit and none of the solutions seemed to fix the situation.

Anyone know what's going on here or know how to fix things?  Thanks.

---

### Post by kidders on 2007-04-03
Hi there and welcome,

What was the original MySQL version you were running?

---

### Post by unn on 2007-04-03
Off the top of my head I have no idea, an old dump from Dec says 5.0.24.

---

### Post by kidders on 2007-04-03
Sorry... I should've been less cryptic about my reason for asking. Essentially, I was really only interested in whether you went straight from pre-4.1 to 5.x, which is fraught with problems. Based on what you noticed in your old dumps though, I really wouldn't have expected any issues.

"Checking for corrupt, not cleanly closed and upgrade needing tables." is a standard (albeit interestingly phrased!) message -- the result of the execution of /etc/mysql/debian-start -- so you can happily pretend you never saw that. As for your system database issues, it's possible, I suppose, that MySQL didn't shut down cleanly before your last upgrade, for some reason. If I were you, I would check over everything (eg privileges), just to be sure things are as they should be. A quick visual inspection with phpMyAdmin, for instance, would make _me_ feel happier about things ... if this were *my* problem.

Are there any lasting problems, now that your MySQL has had a chance to restart a couple of times? Unfortunately, starting MySQL with corrupted databases can be quite destructive, so I realllllly hope not! If you do, my advice is to _immediately downgrade to your previous MySQL version_. (I should say this now, rather than waiting for you to post back, so too much more time doesn't pass.)

Personally, there are certain updates (MySQL, OpenLDAP, ...) I **never** perform without dumping the relevant database first. If your data are important, I would suggest adopting a similar policy, to be honest. That way, if you encounter problems, you can generally just erase the on-disk database, and re-import the dump. Since most applications' database dump formats change very little (MySQL Is a good example), it tends to work very nicely.

---

### Post by unn on 2007-04-05
Weird thing, just before I was about to downgrade I got another update for mysql via adept.. I thought I'd give the install another shot, maybe they fixed the problem, I thought.  Well I ran the update and it appears to not have updated anything, I'm still running the same version I had been earlier.

And more bad news the downgrade didn't do anything, I still have the same issue.

---

### Post by kidders on 2007-04-05
Eww... so your MySQL server won't start?

---

### Post by unn on 2007-04-05
No it seems to start fine, I just have all the same issues I did earlier.

---

### Post by kidders on 2007-04-05
In that case, perhaps it would be worth considering dumping your databases (ie not the system database), erasing MySQL's entire database structure, and re-importing everything. If you give MySQL a chance to rewrite the "mysql" database from scratch, surely that would fix your problem. Unfortunately, as you probably know, doing this would leave you with some work to do afterwards. What do you think?

It would be all too easy to decide that a running server is a happy server, and just ignore your errors, but _*I*_ certainly wouldn't like that!

(Don't forget to tar up /var/lib/mysql before you go doing anything radical though, so you can get it all back if something goes pear-shaped.)

---

### Post by unn on 2007-04-06
I gave that a shot, i ended up restoring my /var/lib/mysql to the backup but mysql won't start now  *sigh*  I guess I've got too limited experience with linux to figure this mess out.

---

### Post by kidders on 2007-04-06
Oh hell.

Assuming it doesn't contain anything personal, commercially sensitive, or otherwise private (and assuming it's small enough), perhaps you should send me a gzipped SQL dump, so I can take a quick look at it. I'm happy to continue to offer you suggestions, but I _really_ don't want to risk losing your data. If the worst comes to the worst, I would be perfectly happy to expose your data remotely, and let you replicate it back into your own systems.

Could you describe your MySQL setup for me? Are you doing anything special like running databases over multiple filesystems, replication. etc? At this point (assuming you have a complete SQL dump), it seems like the best option may be to force Ubuntu to reinstall & reconfigure (ie from scratch) the most recent _stable_ version of MySQL, and go from there.

---

### Post by unn on 2007-04-06
> **kidders said:**
> it seems like the best option may be to force Ubuntu to reinstall & reconfigure (ie from scratch) the most recent _stable_ version of MySQL, and go from there.

How do I do it?  I've got a dump of the only database I need so everything is backed up.

---

### Post by kidders on 2007-04-06
If it were me, I would use **apt** to remove & reinstall MySQL. To try to be as sure as possible that no configuration files/etc survive the process, I would delete directories such as /var/lib/mysql (that may otherwise remain untouched) and **dpkg-reconfigure** MySQL, just to be sure.

As you may know, you have to be pretty thorough when reinstalling certain things, especially when switching between software versions that may have compatibility problems.

Some things to watch out for... hopefully these are already obvious to you...

[LIST]
[*]Never manipulate on-disk databases in any way, while MySQL is running.
[*]When you're having problems, never trust that MySQL is offline, just because your system says it is ... look at a process list, and see for yourself.
[*]After uninstalling MySQL, none of the files or directories mentioned (or implied) in my.cnf should exist. MySQL won't forgive you for it!
[*]Be sure that the access permissions of anything you manually recreate are *exactly* correct. Again, MySQL won't let you away with mistakes.
[*]If you find you don't have to completely reconfigure MySQL privileges, admin passwords, etc., you've done something wrong.[/LIST]Once MySQL is up and running, and has been restarted at least once, you can reimport your data *slowly*, so you can easily spot (and assess the impact of) any errors.

---

### Post by unn on 2007-04-08
Hey I got it all working, now I've just got to restore my privs.  apt-get --purge remove mysql-server-5.0 did the job!  Thanks for all your help.

---

### Post by kidders on 2007-04-08
Kewl :-) Now, if only there were a way to identify what went wrong!

---

