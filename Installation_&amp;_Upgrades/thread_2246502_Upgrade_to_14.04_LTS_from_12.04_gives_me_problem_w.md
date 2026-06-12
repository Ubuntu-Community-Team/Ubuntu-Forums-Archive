---
title: "Upgrade to 14.04 LTS from 12.04 gives me problem with MariaDB (MySQL 5.5)"
date: 2014-10-01
forum: Installation &amp; Upgrades
---

### Post by LonelyMountain on 2014-10-01
Hi,
My life became a whole lot of interesting now...
During my lunchbreak I just jumped into my Linux Server to check status of my SQL server, it wanted to restart. I should have read the warning sign "do not restart". Bah, I forgot edit the sudo vi /etc/apt/apt.conf.d/10periodic and put APTperiodic::Unattended-Upgrade "0"; (it is mispelled after APT because the board interprets it to be a smiley) so during the night it had upgraded to 14.04 LTS somehow. So my SQL database refused to start after my reboot, checking the status of MySQL "service mysql status" gives me "mysql stop/waiting" and I refuse to restart the server, so any advice how to solve this will be much appreciated. How do I get the MariaDB back online when I upgraded to 14.04? If I try service mysql start/stop or whatever it responds "Unknown instance", and mysql -uroot -p gives me socket problem (Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) or something similar I dare not to restart the server to check the errormessage) checking the Mysql.err file is useless because it is completly empty.

I did a similar test with a clone of the server and did following
sudo apt-get install update-manager-core
do-release-upgrade
Same problem, can't start the MySQL instance and trying to update/upgrade MariaDB doesn't help either.
Upgrade reports no problem.

I'm running the Linux Server on a Windows Server 2012 Datacenter, in a Hyper-V enviroment nothing fancy about it and my kernelversion is Linux forgedinmordor 3.8.0-29-generic #42~precise1-Ubuntu SMP Wed Aug 14 16:19:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux.
forgedinmordor:~$ lsb_release -sr
14.04

Me, the administrator is a experienced Windows technician and becoming a intermediate technician on Linux.....;)

---

### Post by LonelyMountain on 2014-10-02
> **LonelyMountain said:**
> Hi,
My life became a whole lot of interesting now...
During my lunchbreak I just jumped into my Linux Server to check status of my SQL server, it wanted to restart. I should have read the warning sign "do not restart". Bah, I forgot edit the sudo vi /etc/apt/apt.conf.d/10periodic and put APTperiodic::Unattended-Upgrade "0"; (it is mispelled after APT because the board interprets it to be a smiley) so during the night it had upgraded to 14.04 LTS somehow. So my SQL database refused to start after my reboot, checking the status of MySQL "service mysql status" gives me "mysql stop/waiting" and I refuse to restart the server, so any advice how to solve this will be much appreciated. How do I get the MariaDB back online when I upgraded to 14.04? If I try service mysql start/stop or whatever it responds "Unknown instance", and mysql -uroot -p gives me socket problem (Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) or something similar I dare not to restart the server to check the errormessage) checking the Mysql.err file is useless because it is completly empty.

I did a similar test with a clone of the server and did following
sudo apt-get install update-manager-core
do-release-upgrade
Same problem, can't start the MySQL instance and trying to update/upgrade MariaDB doesn't help either.
Upgrade reports no problem.

I'm running the Linux Server on a Windows Server 2012 Datacenter, in a Hyper-V enviroment nothing fancy about it and my kernelversion is Linux forgedinmordor 3.8.0-29-generic #42~precise1-Ubuntu SMP Wed Aug 14 16:19:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux.
forgedinmordor:~$ lsb_release -sr
14.04

Me, the administrator is a experienced Windows technician and becoming a intermediate technician on Linux.....;)


Solved, did a new installation of Ubuntu Server 14.04, moved the SQL database from the old server and it is now up and running. Sometimes it's nice to have virtual machines ;)

---

### Post by Vladlenin5000 on 2014-10-02
I'm glad it's working now. Please use the thread tools to mark this one as solved so other can benefit from your experience.

---

