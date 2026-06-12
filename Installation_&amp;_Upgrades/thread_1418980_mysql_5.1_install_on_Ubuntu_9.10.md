---
title: "mysql 5.1 install on Ubuntu 9.10"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by douglegge on 2010-03-01
[LEFT]Relative newcomer to Linux I have been attempting to install mysql 5.1 onto Ubuntu 9.10.[/LEFT]
 
[LEFT]The commands for the binary distro state:[/LEFT]
 
[LEFT]shell> groupadd mysql
shell> useradd -g mysql mysql
shell> cd /usr/local
&#12288;
shell> [FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]gunzip < mysql-VERSION.tar.gz | tar -xvf -[/SIZE][/FONT][/SIZE][/FONT] 
# Replaced gunzip command with tar command below with additional –xvzf switch
shell > tar -xvzf /usr/local/ mysql-VERSION-OS.tar.gz[/LEFT]
 
 
[LEFT]shell> ln -s full-path-to-mysql-VERSION-OS mysql
shell> cd mysql[/LEFT]
 
[LEFT]shell> chown -R mysql .
shell> chgrp -R mysql .[/LEFT]
 
 
[LEFT]# script below run as scripts/mysql_install_db --user=mysql –no-defaults to avoid error message. See [http://www.bitbybit.dk/carsten/blog/?p=117](http://www.bitbybit.dk/carsten/blog/?p=117) for more detail[/LEFT]
 
[LEFT]shell> scripts/mysql_install_db --user=mysql [/LEFT]
 
[LEFT]shell> chown -R root .
shell> chown -R mysql data[/LEFT]
 
[LEFT]shell> bin/mysqld_safe --user=mysql &[/LEFT]
 
 
[LEFT]But am failing at the last hurdle as I cannot get the server to start. I’m guessing it’s a permissions issue, the error message displayed is:[/LEFT]
 
 
[LEFT]root@lab05:/usr/local/mysql# bin/mysqld_safe --user=mysql &
[1] 5619
root@lab05:/usr/local/mysql# 100301 14:23:12 mysqld_safe Logging to '/var/lib/mysql/lab05.err'.
touch: cannot touch `/var/lib/mysql/lab05.err': No such file or directory
chown: cannot access `/var/lib/mysql/lab05.err': No such file or directory
100301 14:23:12 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
bin/mysqld_safe: 563: cannot create /var/lib/mysql/lab05.err: Directory nonexistent
eval: 1: cannot create /var/lib/mysql/lab05.err: Directory nonexistent
100301 14:23:12 mysqld_safe mysqld from pid file /var/run/mysqld/mysqld.pid ended
bin/mysqld_safe: 607: cannot create /var/lib/mysql/lab05.err: Directory nonexistent[/LEFT]
 
[LEFT][1]+ Exit 2 bin/mysqld_safe --user=mysql[/LEFT]
 
 
 
[LEFT]I don’t appear to have mysql folder in /var/lib:[/LEFT]
 
[LEFT]root@lab05:/var/lib# ls
acpi-support dbus hp os-prober synaptic
alsa defoma initramfs-tools pam ucf
apparmor DeviceKit-disks initscripts pm-utils update-manager
apt DeviceKit-power insserv polkit-1 update-notifier
aptitude dhcp3 libuuid pulseaudio update-rc.d
apt-xapian-index dictionaries-common locales pycentral urandom
aspell doc-base logrotate python-support vim
avahi-autoipd dpkg misc samba x11
belocs gconf mlocate sgml-base xkb
binfmts gdm NetworkManager snmp xml-core
computer-janitor hal openoffice sreadahead[/LEFT]
 
[LEFT]Any help gratefully received[/LEFT]
 
[LEFT]Doug[/LEFT]

---

### Post by stephaneeybert on 2012-01-29
Adding my little weight to it.. I have the same error.

stephane-ThinkPad-X60 stephane # 120129 10:59:56 mysqld_safe Logging to '/var/lib/mysql/stephane-ThinkPad-X60.err'.
touch: cannot touch `/var/lib/mysql/stephane-ThinkPad-X60.err': No such file or directory
chown: cannot access `/var/lib/mysql/stephane-ThinkPad-X60.err': No such file or directory
120129 10:59:56 mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
./bin/mysqld_safe: 568: cannot create /var/lib/mysql/stephane-ThinkPad-X60.err: Directory nonexistent
eval: 1: cannot create /var/lib/mysql/stephane-ThinkPad-X60.err: Directory nonexistent
120129 10:59:56 mysqld_safe mysqld from pid file /var/lib/mysql/stephane-ThinkPad-X60.pid ended
./bin/mysqld_safe: 612: cannot create /var/lib/mysql/stephane-ThinkPad-X60.err: Directory nonexistent

---

### Post by douglegge on 2012-01-29
I think I managed to solve this one, but can't remeber of the top of my head how. Give me a couple of days to go through some old notes and I'll get back to you
 
Doug

---

### Post by stephaneeybert on 2012-01-29
I just solved it by specifying some options in the my.cnf file:

user = stephane
basedir=/home/stephane/programs/mysql
datadir=/home/stephane/programs/mysql/data
log_error = /home/stephane/programs/install/var/stephane-ThinkPad-X60.err

In our case, the log error directive solved my issue.

---

