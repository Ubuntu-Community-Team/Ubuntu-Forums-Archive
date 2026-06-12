---
title: "phpMyAdmin"
date: 2011-12-02
forum: Installation &amp; Upgrades
---

### Post by moonguide on 2011-12-02
I'm trying to get WordPress working on my Lucid machine. I have Apache2 and  suPHP running and can successfully navigate to localhost. mysqld is running, although I have done nothing with it. phpMyAdmin is installed but I can't log in. I can navigate to [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) and get the login screen. I understand that I should be able to login as root with no password (after which I would set a password). When I enter root in the Username box and click on "Go" I get an error message:

Login without a password is forbidden by configuration (see allowNoPassword)

I found the place in /etc/phpmyadmin/config.inc.php that tells me to uncomment a line "to enable logging in to passwordless accounts..." 

$cfg['Servers'][$i]['AllowNoPassword'] = TRUE;

I did uncomment that line. And I restarted Apache. But I still get the same error message when I try to log in.

Is there a step I missed somewhere?

Thanks.

---

### Post by moonguide on 2011-12-02
I just tried going directly to mysql via mysqladmin. I dug out my copy of SAMS PHP and MySQL Web Development and turned to the appendix. That reminded me of mysqladmin. It says that after the installation is complete one should run:

# mysqladmin -u root password 'new-password'

replacing new-password with whatever I want for a password. Since this is an Ubuntu machine my  prompt is $ instead of # so I ran the command with sudo in front of it. After putting in my sudo password I get the error message:

mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root@'localhost' (using password: NO)'

I know I've never done anything with this installation of mysql before this week. So I know I've never set a password for root or any other user. Any ideas on what the packagers decided was the default password? Or is there some other problem I'm missing?

---

### Post by moonguide on 2011-12-03
The solution was to reset the password for mysql by following the instructions found here:

[https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)

Once a new password was set there was no problem logging in to phpMyAdmin.

---

