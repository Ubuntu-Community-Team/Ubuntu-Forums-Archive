---
title: "apt-get install libssl0.9.8 freezing. HELP!"
date: 2012-06-14
forum: Installation &amp; Upgrades
---

### Post by Giggitus on 2012-06-14
I am trying to update php5-cli and it freezing. Then I was trying to update libssl0.9.8 and for some reason it tries to install php5-cli and again it freeze.

I see the following:

root@m1309:/tmp# apt-get install libssl0.9.8
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libssl-dev php5-cli
Suggested packages:
  php-pear
The following packages will be upgraded:
  libssl-dev libssl0.9.8 php5-cli
3 upgraded, 0 newly installed, 0 to remove and 31 not upgraded.
1 not fully installed or removed.
Need to get 3,132kB/6,039kB of archives.
After this operation, 7,950kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main libssl-dev 0.9.8k-7ubuntu8.13 [2,151kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main libssl0.9.8 0.9.8k-7ubuntu8.13 [981kB]
Fetched 3,132kB in 0s (7,028kB/s)
Preconfiguring packages ...
(Reading database ...
dpkg: warning: files list file for package `php5-cli' missing, assuming package has no files currently installed.
(Reading database ... 78309 files and directories currently installed.)
Preparing to replace libssl-dev 0.9.8k-7ubuntu8.8 (using .../libssl-dev_0.9.8k-7ubuntu8.13_amd64.deb) ...
Unpacking replacement libssl-dev ...


In log file apt/history.log I see the following:

Start-Date: 2012-06-13  16:57:34
End-Date: 2012-06-13  16:57:36

Start-Date: 2012-06-13  17:08:35
Upgrade: nginx (0.7.65-1ubuntu2.2, 1.2.1-1~lucid)
End-Date: 2012-06-13  17:11:28

Start-Date: 2012-06-13  18:24:33
Install: php5-cli (5.3.2-1ubuntu4.15)

Start-Date: 2012-06-13  19:04:01
Upgrade: apparmor (2.5.1-0ubuntu0.10.04.3, 2.5.1-0ubuntu0.10.04.4), php5-cli (5.3.2-1ubuntu4.15, 5.3.2-1ubuntu4.15)

Start-Date: 2012-06-13  20:08:29
Upgrade: php5-cli (5.3.2-1ubuntu4.15, 5.3.2-1ubuntu4.15)

Start-Date: 2012-06-14  14:12:03
Upgrade: libssl-dev (0.9.8k-7ubuntu8.8, 0.9.8k-7ubuntu8.13), libssl0.9.8 (0.9.8k-7ubuntu8.8, 0.9.8k-7ubuntu8.13), php5-cli (5.3.2-1ubuntu4.15, 5.3.2-1ubuntu4.15)


Please help...

---

### Post by drmrgd on 2012-06-14
Please try running:

```
sudo dpkg --configure -a
```

followed by:

```
sudo apt-get install -f
```

That may fix the broken package and allow you to upgrade.

---

### Post by Giggitus on 2012-06-14
root@m1309:/etc/php5/cli# sudo dpkg --configure -a
dpkg: status database area is locked by another process
root@m1309:/etc/php5/cli# sudo apt-get install -f
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Giggitus on 2012-06-14
I can unlock it only by server restart.

---

### Post by irv on 2012-06-14
> **Giggitus said:**
> root@m1309:/etc/php5/cli# sudo dpkg --configure -a
dpkg: status database area is locked by another process
root@m1309:/etc/php5/cli# sudo apt-get install -f
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Make sure you don't have the package manager or software center open. If you try running this command it will give you this message.

---

### Post by irv on 2012-06-14
I also notice you are logged in as root. You should log in as yourself and just use the sudo before the command. It will asks for your password and then run the command. It is safer to do it this way.

---

### Post by Giggitus on 2012-06-15
I make reboot server and than again send this commands -

root@m1309:~# sudo dpkg --configure -a
Processing triggers for man-db ...
root@m1309:~# sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libssl-dev libssl0.9.8 php5-cli
Suggested packages:
  php-pear
The following packages will be upgraded:
  libssl-dev libssl0.9.8 php5-cli
3 upgraded, 0 newly installed, 0 to remove and 31 not upgraded.
2 not fully installed or removed.
Need to get 0B/6,039kB of archives.
After this operation, 7,950kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ...
dpkg: warning: files list file for package `php5-cli' missing, assuming package has no files currently installed.
(Reading database ... 78309 files and directories currently installed.)
Preparing to replace libssl-dev 0.9.8k-7ubuntu8.8 (using .../libssl-dev_0.9.8k-7ubuntu8.13_amd64.deb) ...
Unpacking replacement libssl-dev ...

  Problemthe same - it tries to install php5-cli and again it freeze on "Unpacking replacement libssl-dev ..."

---

