---
title: "Server 20.04 VM &quot;minimal&quot; high CPU after installing Mysql Server 8"
date: 2020-09-24
forum: Installation &amp; Upgrades
---

### Post by kg6doq on 2020-09-24
Hi all -

I am currently trying to run a Ubuntu 20.04 public image as a Google Compute Engine cloud instance. The image is tagged as "minimal" which is fine because all I am doing is running a LLMP server. 

After creating the VM instance, I log in and do the following:

apt update
apt upgrade
apt install emacs-nox  (emacs text editor)
apt install lighttpd
apt-get install php php-cgi php-cli php-fpm php-curl php-gd php-mysql php-mbstring zip unzip apache2-

I enable lighttpd and verify the PHP install with a phpinfo() simple web page. So far, so good.

Next, I do:
apt install mysql-server

This runs and gets about 90% of the way thru the install and then everything freezes. The one time I was able to SSH in (and this took about 30 mins) I had found the load average was over 18.0 ! I also found a process call snapd eating alot of CPU. I googled snapd and I do see that there was a bug in previous Ubuntu versions but this bug manifested only after a reboot, causing high CPU for a few minutes and then returning to normal. Mine stays high.

Here are the last few lines of the Mysql install before the system hangs:

[FONT=courier new]reading /usr/share/mecab/dic/ipadic/Noun.name.csv ... 34202[/FONT]
[FONT=courier new]reading /usr/share/mecab/dic/ipadic/Noun.proper.csv ... 27328[/FONT]
[FONT=courier new]reading /usr/share/mecab/dic/ipadic/Prefix.csv ... 221[/FONT]
[FONT=courier new]emitting double-array: 100% |###########################################|[/FONT]
[FONT=courier new]reading /usr/share/mecab/dic/ipadic/matrix.def ... 1316x1316[/FONT]
[FONT=courier new]emitting matrix      : 100% |###########################################|[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]done![/FONT]
[FONT=courier new]update-alternatives: using /var/lib/mecab/dic/ipadic-utf8 to provide /var/lib/mecab/dic/debian (mecab-dictionary) in auto mode[/FONT]
[FONT=courier new]Setting up libhtml-parser-perl (3.72-5) ...[/FONT]
[FONT=courier new]Setting up libhttp-message-perl (6.22-1) ...[/FONT]
[FONT=courier new]Setting up mysql-server-8.0 (8.0.21-0ubuntu0.20.04.4) ...[/FONT]
[FONT=courier new]debconf: unable to initialize frontend: Dialog[/FONT]
[FONT=courier new]debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 76.)[/FONT]
[FONT=courier new]debconf: falling back to frontend: Readline[/FONT]
[FONT=courier new]update-alternatives: using /etc/mysql/mysql.cnf to provide /etc/mysql/my.cnf (my.cnf) in auto mode[/FONT]
[FONT=courier new]Renaming removed key_buffer and myisam-recover options (if present)[/FONT]
[FONT=courier new]mysqld will log errors to /var/log/mysql/error.log[/FONT]
[FONT=courier new]2020-09-24T07:36:42.084115Z 0 [ERROR] [MY-011065] [Server] Unable to determine if daemon is running: No such file or directory (rc=0).[/FONT]
[FONT=courier new]2020-09-24T07:36:42.176988Z 0 [ERROR] [MY-010946] [Server] Failed to start mysqld daemon. Check mysqld error log.[/FONT]
[FONT=courier new]Warning: Unable to start the server.[/FONT]
[FONT=courier new]Created symlink /etc/systemd/system/multi-user.target.wants/mysql.service &#8594; /lib/systemd/system/mysql.service.[/FONT]
[FONT=courier new]
[/FONT]
Any ideas on how to fix would be most welcome. 

- Steve

---

### Post by SeijiSensei on 2020-09-24
First verify if there is a MySQL instance running on your machine.

```
sudo systemctl status mysql
```

On my machine that returns
```

seiji@big-linux:~$ sudo systemctl status mysql
[sudo] password for seiji: 
&#9679; mysql.service - MySQL Community Server
     Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: enabled)
     Active: active (running) since Wed 2020-09-23 15:28:44 EDT; 18h ago
    Process: 1023 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=exited, status=0/SUCCESS)
   Main PID: 1232 (mysqld)
     **Status: "Server is operational"**
      Tasks: 39 (limit: 19021)
     Memory: 400.6M
     CGroup: /system.slice/mysql.service
             &#9492;&#9472;1232 /usr/sbin/mysqld

```

If it's not running, try 
```
sudo systemctl start mysql
```
then re-run the status command.

Check your disk usage with df, too.  Do you have any partitions with no space?

You can disable snapd from running at all with
```

sudo systemctl disable snapd

```
Then rebooting.

---

### Post by kg6doq on 2020-09-28
Thanks for the info. I tried the suggestions above. I don't think Mysql finished it's install - there were no startup scripts found.

This Ubuntu "minimal" image is provided by Google for use on their compute engine platform. They also have a non-minimal image available. I spun that up and I get the same errors when trying to install mysql-server. I suspect this is most likely related to the repository Google has setup to pull apt content from. Most likely mysql-server requires some dependencies and isn't getting them. All of my disks have lots of free space.

I've run Ubuntu 20.04 server on server hardware and installed mysql-server many times without any issues, so I think it's a Google Compute problem.

To get around this, I went with Debian 10 (Buster) and installed MariaDB. So far, so good !

---

