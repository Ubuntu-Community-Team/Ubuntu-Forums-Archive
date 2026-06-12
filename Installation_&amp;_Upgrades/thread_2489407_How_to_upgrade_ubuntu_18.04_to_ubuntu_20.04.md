---
title: "How to upgrade ubuntu 18.04 to ubuntu 20.04 ?"
date: 2023-07-29
forum: Installation &amp; Upgrades
---

### Post by nilovsergey on 2023-07-29
I try to upgrade ubuntu 18.04 with apache 2 under digital ocean to ubuntu 20.04

I try to follow steps in the [https://help.ubuntu.com/community/FocalUpgrades](https://help.ubuntu.com/community/FocalUpgrades) article , but I got unexpected error
> Please install all available updates for your release before upgrading

even after I upgraded the system:

```
root@remote-server:~# uname -r; uname -a
4.15.0-213-generic
Linux remote-server 4.15.0-213-generic #224-Ubuntu SMP Mon Jun 19 13:30:12 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux

root@remote-server:~# do-release-upgrade
Checking for a new Ubuntu release
Please install all available updates for your release before upgrading.

root@remote-server:~# sudo apt-get update
Ign:1 http://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/6.0 InRelease
Hit:2 http://ppa.launchpad.net/certbot/certbot/ubuntu bionic InRelease
Hit:3 http://security.ubuntu.com/ubuntu bionic-security InRelease
Get:4 https://download.docker.com/linux/ubuntu bionic InRelease [64.4 kB]
Hit:5 https://deb.nodesource.com/node_16.x bionic InRelease
Hit:6 http://ppa.launchpad.net/ondrej/php/ubuntu bionic InRelease
Hit:7 http://mirrors.digitalocean.com/ubuntu bionic InRelease
Hit:8 http://mirrors.digitalocean.com/ubuntu bionic-updates InRelease
Hit:9 http://mirrors.digitalocean.com/ubuntu bionic-backports InRelease
Hit:10 http://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/6.0 Release
Fetched 64.4 kB in 1s (70.6 kB/s)
Reading package lists... Done
root@remote-server:~# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  base-files docker-ce docker-ce-cli ubuntu-advantage-tools ubuntu-server
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

root@remote-server:~# do-release-upgrade
Checking for a new Ubuntu release
Please install all available updates for your release before upgrading.

```
How to fix this error and move next?

---

### Post by TheFu on 2023-07-29
So, standard support for 18.04 ended a few months ago. The repos and updates you need aren't available anymore for free.  You need to either get coverage with the ESM program, then patch 18.04, then attempt the upgrade 

OR 

backup all your files that you can't lose and do a fresh install, restore the files where they were, with the owner, group, permissions, ACLs and xattrs as they were then install the software you need.

BTW, major upgrades for many server processes don't go cleanly.  There's usually no automatic migration that happens for different settings in DBMS or web servers, so you'll need to address those issues manually.  Same for webapps built using newer versions of languages like ruby, php, perl, go, javascript, etc.  

If you would have performed the upgrade before standard support ended in early May, it may have been possible.  NEVER, EVER, let a system lose support if you hope to upgrade it.

I've found that OS upgrades only work well for 1 LTS to the next LTS and only if 100% of the software is part of the core Ubuntu repos.  If there's any software outside those core repos, expect issues, sometimes major issues that are sufficient to waste 2+ hrs of downtime for the upgrade attempt, which then fails.  In the end, I'm forced to perform a new install .... all because I wanted to avoid doing a new install.  So, I've wasted both the time/effort in the failed upgrade process AND still have to do the new install.  This has me convinced that doing a fresh install and just moving the data and software over manually into the new system actually saves time.

Plus, a fresh install will remove any left over cruft that the different subsystems leave behind.

In my migrations off 18.04 the last year, only a few systems have "upgraded" cleanly. These were bog, stock, 18.04 core software servers with nothing extra and ZERO local data.  Any server with data required a fresh install, I'm sad to say.

---

### Post by guiverc on 2023-07-29
Did you try the `apt-get dist-upgrade` or `apt full-upgrade` as I suggested on AU?

Next I suggested checking you'd not put any holds on packages, though IF those package upgrades you've not applied are ESM related; it's harder now as I stated & may require ESM to perform the upgrades (*I don't believe it will, it didn't for xenial upgrades, but things keep changing*).

Extra note:  if you've not rebooted after any changes/upgrades; reboot too may help.

Switching to the main archive may also be worth trying (*you're using a mirror currently*); though I suspect not.

---

### Post by francwalter on 2023-11-24
Hallo, I still have 18.04 LTS too and want to update to 20.04 and then 22.04.
Now I read this thread and I fear the worst :(

After all, I have ESM active (some time before EOL) and I do these updates always when shown on login.
But I have ondrej PHP 8.0 running and I hope that the 20.04 update could just install the new 8.1. 
Also I have a different source for MariaDB to get 10.5 at least, but this also is now too old and I hope that 20.04 will bring a new one too, 10.6+ I hope (to be of use for Moodle 4.2).

I remember that I already did that kind of upgrade once, from 14.04 to 16.04 in June 2019 (also after EOL, which was April 2019) and in 2020 then to 18.04 (that one before EOL), and at this time I didnt have the ESM active.
So I hope it will work and be of not too much work after. In June 2019 I had some little difficulties, but nothing too severe. Logwatch, certbot, owncloud, CouchDB, fail2ban, roundcube such things. But Postfix, Apache and PHP were of no issues, which was crucial.

---

### Post by ian-weisser on 2023-11-24
You may have bigger fish to fry than a few kept-back packages.

If your goal for release-upgrading is to avoid rebuilding your  virtual server, then consider the possibility that your goal may fail  through no fault of yours. Virtual servers like Digital Ocean are often  not designed for long-term uses like release-upgrades, so unexpected  failures may occur. Many such services are designed to be built and  destroyed as-needed.

Before you begin, be 100% prepared to  rebuild your server from a clean 22.04 install. Have complete notes on  how to access and install every container and application to rebuild  your workflow, and a complete data backup (...and notes on how to  restore your data from that backup!)

Once that is done, and you are ready to tackle the problem in front of you...

```

The following packages have been kept back:
  base-files docker-ce docker-ce-cli ubuntu-advantage-tools ubuntu-server
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

```

Step 1: Check for phased updates.
Run "apt policy <package_name>" on all of those held-back packages. See if they are phasing.

```
# sudo apt-get update
Ign:1 http://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/6.0 InRelease
Hit:2 http://ppa.launchpad.net/certbot/certbot/ubuntu bionic InRelease
...
Get:4 https://download.docker.com/linux/ubuntu bionic InRelease [64.4 kB]
Hit:5 https://deb.nodesource.com/node_16.x bionic InRelease
Hit:6 http://ppa.launchpad.net/ondrej/php/ubuntu bionic InRelease
...
Hit:10 http://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/6.0 Release

``` 

Step 2: You have a lot of non-Ubuntu sources and software to uninstall.
The #1 cause of failed release-upgrades is non-Ubuntu software left on the system.

---

### Post by ActionParsnip on 2023-11-24
As you are root, you don't need sudo. Just a pointer

---

### Post by francwalter on 2023-11-29
> **francwalter said:**
> Hallo, I still have 18.04 LTS too and want to update to 20.04 and then 22.04.
...
OK then, I upgraded these days :)
From 18 to 20 no issues, so I immediately continued to 22.04 and here I had issues with Dovecot and OpenSSL 3 I think (I am not very sure, in the end It worked with updated and jammy Dovecot sources but the hack didnt work).
Spend a day or so to find it but after all, to reinstall all new this is much more than a day, very much more.
I know that I have now some more "old fish to fry in the attic" but a clean and new install is a thing which can create very huge fish to fry,  at least in my experience.

---

### Post by TheFu on 2023-11-29
> **francwalter said:**
> OK then, I upgraded these days :)
From 18 to 20 no issues, so I immediately continued to 22.04 and here I had issues with Dovecot and OpenSSL 3 I think (I am not very sure, in the end It worked with updated and jammy Dovecot sources but the hack didnt work).
Spend a day or so to find it but after all, to reinstall all new this is much more than a day, very much more.
I know that I have now some more "old fish to fry in the attic" but a clean and new install is a thing which can create very huge fish to fry,  at least in my experience.

Nice necroposts.

I use my versioned backups to help migrations to new releases.  I also review the release notes.  When a VPS, migrations are 100% risk free, since moving to a new OS while leaving the older OS up and running is expected.  If you aren't doing that, I think you are doing it wrong.  The last thing that should change in the migration process is switching the DNS from the old IP to the new IP **AFTER** everything is confirmed moved.  Might be a good idea to set the DNS TTL to 5 minutes and wait for that to spread across the internet too, so you limit the period when the service switch actually impacts people.

It isn't like another VPS will cost $50 .... for just a day, running both will likely cost under $1.

If you can't migrate to a new OS with minimal downtime, then I'd say you are missing some critical knowledge and need more research. Backups and restore are a key aspect to these migrations.  If the restore takes over 45 minutes for less than 30G of stuff, then there are better ways to do backups and selective restores.  Of course, we all have limited time for learning stuff and perhaps _paying_ all at once during system migrations with downtime is the choice you've made.  It is a choice.

---

