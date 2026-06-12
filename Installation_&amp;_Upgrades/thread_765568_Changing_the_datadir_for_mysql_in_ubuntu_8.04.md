---
title: "Changing the datadir for mysql in ubuntu 8.04"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by colawrence on 2008-04-24
Folks,

Here is my story about getting mysql to work after changing the datadir location.  Of course, use your own location instead of mine in the below text.

After installing ubuntu 8.04 and using tasksel to install a lamp server, mysql worked OK until I went to change the location of the datadir, a task I had done many times before in previous versions of Ubuntu.

This is how it used to work under 7.10.  I have all my previous  mysql data files stored on my /home/mysql partition, which I do not re-format ever when installing a new ubuntu version.  In 7.10 it was simply a matter of changing the appropriate line in /etc/mysql/my.cnf to point to the /home/mysql dir instead of the default /var/lib/mysql dir and restarting mysql with a sudo /etc/init.d/mysql restart, well almost.  In order to do a clean startup (with no reported problems) you have to set the password for the debian-sys-maint account in the user table located in /home/mysql to be the same as the new password set for the debian-sys-maint account in the just created /var/lib/mysql.  First you have to obtain the password used by the new mysql debian-sys-maint account (this is a 40 hex character string prefixed with an *), write it down or copy it to a file, or somehow save it, then change the datadir in my.cnf, restart mysql and go into mysql and change your old /home/mysql debian-sys-maint password to the new one.  Use a command sequence like this to reset the old password to the new one:
mysql -uroot -pwhatever mysql
select user,host,password from user; (just to see what is there)
update user set password = 'newpassword' where user = 'debian-sys-maint'; (don't forget the where clause!)
select user,host,password from user; (to see if it changed ok)
exit;
If you restart with a sudo /etc/init.d/mysql restart, you will probably not get a clean restart.  Just reboot and it will be OK.  Try the restart once again to see that it works with no complaints.

Now comes 8.04.  I did the same old routine that I had done many times before as described above.  Lo and behold mysql will not start!  The /var/log/syslog file says there is a permissions problem.  Do not believe it.  If /home/mysql worked before it should still work.  I come to find out there is this thing called apparmor.  Now apparmor has been around at least since 7.04, unbeknownst to me, of course, and probably most everybody else too.  It uses profiles that configure how it is to protect an application.  These are text files stored in the /etc/apparmor.d/ dir.  The mysql profile is in usr.sbin.mysqld.  Apparantly the mysql profile was absent in 7.10, but shows up in 8.04.  Hmm!! (7.04 apparmor was not started automatically.) In fact, if you look closely at the 8.04 my.cnf file when changing the datadir location, you will see above that section of the file a comment stating that if apparmor is used you might need to tweak the apparmor profile.  I overlooked this tidbit of news!  Well you do have to tweak it too.  Just edit it and change the two lines that contain /var/lib/mysql/ to /home/mysql/ (don't change anything past /mysql/.  Don't forget to restart apparmor with a sudo /etc/init.d/apparmor restart.  Now restarting mysql will work just fine pointing to your own location for the datadir.

If you prefer you can put the mysql profile into a non-enforcing mode by doing a sudo aa-complain /etc/apparmor.d/usr.sbin.mysqld and then it won't enforce the profile.  I don't know where the complaints go to, I have not looked into this.  Maybe someone out there can answer that.  A sudo aa-status will show you info about all the profiles loaded.  Do an aa-(tab tab) to see all the commands.  Look into man apparmor.d and other apparmor man pages to see more info.

I hope this will help others having the same problem.  I have seen many google hits complaining of this problem, but no real solution.  Most answers say check your permissions.  The culprit is apparmor not permissions.

Good luck,
Charles Lawrence

---

### Post by valk on 2008-04-29
Hi there,

Thanks a lot for the tips ;) !! helped a lot.

Valk.

---

### Post by Oncle Tom on 2008-05-03
Hello,

thank you for this help, I was in the same trouble !
I did not understand what I done wrong by symlinking /var/lib/mysql as it was working for Ubuntu 7.10.

Thanks again :)

---

### Post by simon_w on 2008-09-15
great post, thanks

---

### Post by kotya2 on 2009-10-11
very very helpful.
thanks

---

