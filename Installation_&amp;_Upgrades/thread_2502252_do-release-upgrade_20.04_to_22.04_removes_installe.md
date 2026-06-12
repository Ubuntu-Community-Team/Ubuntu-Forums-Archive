---
title: "do-release-upgrade 20.04 to 22.04 removes installed packages"
date: 2024-11-07
forum: Installation &amp; Upgrades
---

### Post by snoozer70 on 2024-11-07
Hello,

I am trying to upgrade 20.04LTS to 22.04LTS and have the problem that the upgrade process uninstalls cacti and phpmyadmin. I did install the server version 20.04LTS on a system. After that I installed caci, cacti-spine and phpmyadmin from the ubuntu repository. All software is ONLY installed from ubuntu. If I now try do-release-upgrade and look at the details it shows me that it will uninstall cacti, cacti-spine, phpmyadmin and all automatically installed dependencies. How can I prevent that and do the upgrade including the above mentioned software ? 

Kind Regards
Jan P.

---

### Post by snoozer70 on 2024-11-07
Just a quick update, I have also tried to adjust the sources list manually and run apt-get dist-upgrade but that also shows me that it wants to remove cacti, cacti-spine and phpmyadmin.

---

### Post by Dennis N on 2024-11-07
You could let the upgrade remove packages, and when the upgrade is completed, install them again in the new Ubuntu version.

---

### Post by snoozer70 on 2024-11-07
Cacti is configured and has a LOT of home made templates and historic data, that is the reason why I set up the 20.04 server in the 1st place to move my historic and custom cacti internals to a fresh setup with mariadb instead of mysql. If I just reinstall cacti on 22.04 its a higher version of cacti and I can't be certain that moving files and importing the dstabase from cacti 1.2.10 to the cati version on 22.04 10.2.19 works. The move of all cacti data and templates etc between the system 20.04 with mysql and the fresh 20.04 with mariadb worked flawless, but thats both cacti version 1.2.10.

Also just for context, I started of from a 16.04LTS to 18.04LTS to 20.04LTS without these issues, 20.04LTS to 22.04LTS on that old system gave me grief because of mysql, thats why I decided to set up fresh on 20.04LTS with mariadb instead of mysql hoping to proceed from there with upgrading to a current LTS version. On this last set-up 20.04LTS server the only packages I installed after the initial setup was phpmyadmin, cacti and cacti-pine, those and the automatically installed dependencies are somehow recognised my the release-upgrade process I presume, I am hoping it is just a matter of updating some config or file to include those packages.

---

### Post by ian-weisser on 2024-11-07
Please show us your 'apt policy <packagename>' output for those packages.

The complete output of 'sudo apt update' would also be helpful.

---

### Post by snoozer70 on 2024-11-07
Hi, here the apt policy output:

```
apt policy cacti
cacti:
  Installed: 1.2.10+ds1-1ubuntu1.1
  Candidate: 1.2.10+ds1-1ubuntu1.1
  Version table:
 *** 1.2.10+ds1-1ubuntu1.1 500
        500 [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 Packages
        500 [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) focal-security/universe amd64 Packages
        100 /var/lib/dpkg/status
     1.2.10+ds1-1ubuntu1 500
        500 [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) focal/universe amd64 Packages

apt policy cacti-spine
cacti-spine:
  Installed: 1.2.6-1build1
  Candidate: 1.2.6-1build1
  Version table:
 *** 1.2.6-1build1 500
        500 [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) focal/universe amd64 Packages
        100 /var/lib/dpkg/status

apt policy phpmyadmin
phpmyadmin:
  Installed: 4:4.9.5+dfsg1-2
  Candidate: 4:4.9.5+dfsg1-2
  Version table:
 *** 4:4.9.5+dfsg1-2 500
        500 [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) focal/universe amd64 Packages
        100 /var/lib/dpkg/status

```
And here apt update:

```
apt update
Hit:1 [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) focal InRelease
Get:2 [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) focal-updates InRelease [128 kB]
Hit:3 [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) focal-backports InRelease
Hit:4 [http://ie.archive.ubuntu.com/ubuntu](http://ie.archive.ubuntu.com/ubuntu) focal-security InRelease
Fetched 128 kB in 1s (114 kB/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done
All packages are up to date.
```

---

### Post by snoozer70 on 2024-11-07
I have just to be sure run apt upgrade and see with Ubuntu "Pro" I would get updates for Cacti and Phpmyadmin, can that be the issue ?

```
sudo apt upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  php-symfony-expression-language libphp-phpmailer cacti fail2ban phpmyadmin
  php-twig php-symfony-cache php-symfony-var-exporter
Learn more about Ubuntu Pro at https://ubuntu.com/pro
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



```

I hope I am not forced to purchase a subscription of sorts. I am just thinking out loud here now, no clue if that would work as intended. Could I install a fresh 24.04LTS on a system and install the Cacti 1.2.10 package from 20.04LTS, import my database and all cacti data etc and then use apt upgrade to update Cacti to what ever comes with 24.04LTS usually ?

---

### Post by Tadaen_Sylvermane on 2024-11-07
For the record your configuration files will not disappear on a standard upgrade. It will ask you for your choice on that. So just run the upgrade, then install the packages again. Why it won't just upgrade them I don't know but this is a common thing. You should have them backed up anyway if they are that critical that you are afraid to lose them that much.

---

### Post by ian-weisser on 2024-11-07
The output you posted does not seem to say that any packages will be removed or deleted.

It says that those packages, which are all in the Universe repository, have security patches available.
Why you are offered a (free) Pro subscription to get security updates in the Universe repository has been written about many times.
- Canonical provides security patches in Main, not in Universe.
- Security patches in Universe are a community responsibility.
- Community hasn't been doing it, so Canonical uses Pro to charge enterprise customers while making the patches available to all users.
- Pro is optional. You are welcome to patch your own packages. You are welcome to upload Universe packages. You can use the six-month releases of Ubuntu to get updated packages instead of waiting two years. You have choices.

---

### Post by snoozer70 on 2024-11-08
Hi,

I have backups, that's not the issue. Applying the backup to a version of cacti that is newer than the backup might, IDK. I give it a shot and see what happens when just installing the uninstalled packages after the upgrade.

@ian-weisser, I did not say that I had seen the removal of packages in the output I posted above, I am not familiar enough with Ubuntu to state anything re Pro or not Pro version, hence my confusion. I am usually running Debian, just so happens that this was an Ubuntu installation for what ever reason. The technical issue is only that the packages will be removed in the 1st place. Here the details I can look at from do-release-upgrade. Its just the top few lines.

```
Remove: cacti cacti-spine phpmyadmin

Remove (was auto installed) fuse galera-3 libsemanage1 libtss2-esys0
  mariadb-client-10.3 mariadb-client-core-10.3 mariadb-server-10.3
  mariadb-server-core-10.3 php7.4 php7.4-bz2 php7.4-cli php7.4-common
  php7.4-curl php7.4-gd php7.4-gmp php7.4-json php7.4-ldap
  php7.4-mbstring php7.4-mysql php7.4-opcache php7.4-readline
  php7.4-snmp php7.4-xml php7.4-zip python3-twisted-bin
```

Kind regards
Jan P.

---

### Post by ian-weisser on 2024-11-08
Thanks for clarifying, and for curing my misunderstanding.

Hmmm. Whatever the problem might be, it's none of the common causes: Wrong sources and non-Ubuntu packages. Kudos for doing things the right way and for staying on top of maintenance.

Were it my system, I would run a 24.04 LiveUSB, enter the 'Try Ubuntu" environment, install cacti, and test if my customizations work in the updated environment. Knowing that answer will give you options to move forward,

---

