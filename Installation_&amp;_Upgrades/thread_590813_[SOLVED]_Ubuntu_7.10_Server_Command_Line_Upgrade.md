---
title: "[SOLVED] Ubuntu 7.10 Server Command Line Upgrade"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by md5hash on 2007-10-25
is there a command line how-to on ubuntu 7.10 server upgrade?

---

### Post by gtdaqua on 2007-10-25
yeah there is:

```

sudo apt-get install update-manager-core
sudo do-release-upgrade

```

You can see it [here]("https://help.ubuntu.com/community/GutsyUpgrades").

---

### Post by md5hash on 2007-10-25
it says **No new release found**

---

### Post by gtdaqua on 2007-10-25
what is ur current version?

---

### Post by md5hash on 2007-10-25
Im using the server edition

```
lsb_release -a
```

```

Distributor ID: Ubuntu
Description: Ubuntu 7.04
Release: 7.04
Codename: feisty

```

---

### Post by gtdaqua on 2007-10-25
ok. post the exact output of the following two commands:
```

sudo apt-get install update-manager-core

```
```

sudo do-release-upgrade

```

---

### Post by md5hash on 2007-10-25
> **gtdaqua said:**
> ok. post the exact output of the following two commands:
```

sudo apt-get install update-manager-core

```
```

sudo do-release-upgrade

```

```
Reading package lists...
Building dependency tree...
Reading state information...
update-manager-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded
```.

```
Checking for a new ubuntu release
No new release found
```

---

### Post by gtdaqua on 2007-10-25
Strange! Actually I could not upgrade as well but that was a different problem. 

Update was found and while installing it said my installation of python was wrong and quit. 

ok just try this. may not really help but you may find something.
```

sudo apt-get update
sudo apt-get upgrade

```

and try doing the upgrade again. I would even try restarting the server and doing the update again (its just this whole 'restart and it works' idea is from windows! - see, what they do to us!!)

---

### Post by md5hash on 2007-10-25
the same

---

### Post by nospoftombl on 2007-10-25
I have exactly the same problem; first tried 
```
sudo apt-get install update-manager-core
sudo do-release-upgrade
```
->
```
Checking for a new ubuntu release
No new release found
```
After that I tried
```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude dist-upgrade
```
and again
```
sudo apt-get install update-manager-core
sudo do-release-upgrade
```
with the same result. Also rebooted the machine (the users where very happy :mad:), but nothing changed ...

---

### Post by riftt on 2007-10-26
> **nospoftombl said:**
> I have exactly the same problem; first tried 
```
sudo apt-get install update-manager-core
sudo do-release-upgrade
```
->
```
Checking for a new ubuntu release
No new release found
```
After that I tried
```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude dist-upgrade
```
and again
```
sudo apt-get install update-manager-core
sudo do-release-upgrade
```
with the same result. Also rebooted the machine (the users where very happy :mad:), but nothing changed ...

Same problem here. Yes we can change the sources.list but it's weird that it is not a known issue that server does not upgrade. I am behind a proxy but apt-get/aptitude are upgrading just fine.

---

### Post by kenny1948 on 2007-10-29
I too am having the same problem. Each time I get the same message. That upgrade is complete! I have 7.04 installed.:(

I also am having another problem with installed applications. I can only use Real Player as when I try to download anything I get a message that :W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisc11_9.3.4-2ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisc11_9.3.4-2ubuntu2.1_i386.deb)
  Could not connect to 10.98.224.1:8080 (10.98.224.1). - connect (111 Connection refused) 

I get this same message every time I try to get updates or download anything.

Sorry, but I am still confused on how to get things running under ubuntu!

---

### Post by simonpearson on 2007-10-30
I too have the same problems that have been described above.

cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.04
DISTRIB_CODENAME=feisty
DISTRIB_DESCRIPTION="Ubuntu 7.04"

apt-get install update-manager-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
update-manager-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

sudo do-release-upgrade
Checking for a new ubuntu release
No new release found

It may boil down to a clean install by the looks :(

---

### Post by turqy on 2007-10-31
Did this ever get resolved?  I too have 7.04 Server running, and the output of `sudo do-release-upgrade` states that there is no new release to upgrade to...

Any hints?

---

### Post by zvacet on 2007-11-01
[https://help.ubuntu.com/community/GutsyUpgrades]("https://help.ubuntu.com/community/GutsyUpgrades")

---

### Post by riftt on 2007-11-01
> **zvacet said:**
> [https://help.ubuntu.com/community/GutsyUpgrades]("https://help.ubuntu.com/community/GutsyUpgrades")

We did that and it's not working. It should be reproductible:
Install a fresh SERVER ubuntu 7.04
upgade it to date.
do a 
sudo apt-get install update-manager-core
and
sudo do-release-upgrade

and you will get No new release found

---

### Post by oriongr on 2007-11-01
Same here...
Fully updated Ubuntu 7.04
Behind proxy...do-release-upgrade gives back No new release found


Is do-release-upgrade work behind proxy?

---

### Post by nospoftombl on 2007-11-06
No ideas??? I can't believe that this is a problem of handful of users! I also can't believe that nobody of the "officials" at Ubuntu is interested in providing a solution for this, instead all we get is a link to the commandline-upgrade which definitely does not work for us!

---

### Post by nospoftombl on 2007-11-07
Ok, I managed to get this working by disabling the proxy for this server -> the 'sudo do-release-upgrade' than did the upgrade.

---

### Post by oriongr on 2007-11-07
Where did you disable it?
I removed the proxy info from apt.conf file but nothing changed...

---

### Post by md5hash on 2007-11-07
will it connect to the internet if i disable the proxy?

---

### Post by willy1 on 2007-11-07
beste 

ik zoek iemand die mij de lastig versie van kubunto kan bezorgen ,ik ben van veldegem ,en voeger was er iemand ,die me hielp maaar helaas vindt ik hen niet neer  
alvast bedankt:confused:

---

### Post by Scottworld on 2007-11-14
Define the shell network proxy settings before the upgrade.
this allows the do-release-upgrade script, to proxy to the outside world.
 
 
sudo -s **Become root (be careful)**
 
export http_proxy=http://user:password@my.proxy.server:port/
export ftp_proxy=http://user:password@my.proxy.server:port/
 
**Then run the standard server upgrade**
 
apt-get install update-manager-core
do-release-upgrade

ps: This will also allow access for other commands to proxy outside...
eg: 
wget [http://a.domain.com/file/to/download](http://a.domain.com/file/to/download)

---

### Post by md5hash on 2007-11-14
> **Scottworld said:**
> Define the shell network proxy settings before the upgrade.
this allows the do-release-upgrade script, to proxy to the outside world.
 
 
sudo -s **Become root (be careful)**
 
export http_proxy=http://user:password@my.proxy.server:port/
export ftp_proxy=http://user:password@my.proxy.server:port/
 
**Then run the standard server upgrade**
 
apt-get install update-manager-core
do-release-upgrade

This method works for me.. thanks alot **Scottworld**

---

### Post by oriongr on 2007-11-20
With this the do-release-upgrade script worked...
Thanks

---

### Post by tesseract_rider on 2007-12-06
Anyone have any ideas?

> root@hancock-desktop:/tmp# do-release-upgrade
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading
extracting '/tmp/tmplQ8qvA/gutsy.tar.gz'
authenticate '/tmp/tmplQ8qvA/gutsy.tar.gz' against '/tmp/tmplQ8qvA/gutsy.tar.gz.gpg'

Reading cache

Checking package manager
Reading package lists: Doneeisty-proposed/universe Packages: 95    92
Reading state information: Done
Reading state information: Done
Reading state information: Done


A fatal error occured
Please report this as a bug and include the files /var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in your report. The upgrade aborts now.
Your original sources.list was saved in /etc/apt/sources.list.distUpgrade.
Traceback (most recent call last):

  File "/tmp/tmplQ8qvA/gutsy", line 59, in <module>
    app.run()

  File "/tmp/tmplQ8qvA/DistUpgradeControler.py", line 1346, in run
    self.fullUpgrade()

  File "/tmp/tmplQ8qvA/DistUpgradeControler.py", line 1251, in fullUpgrade
    if not self.getRequiredBackports():

  File "/tmp/tmplQ8qvA/DistUpgradeControler.py", line 1140, in getRequiredBackports
    outfile = open(os.path.join(apt_pkg.Config.FindDir("Dir::Etc::sourceparts"), sourceslistd), "w")

IOError: [Errno 2] No such file or directory: '/etc/apt/sources.list.d/prerequists-sources.list'


---

### Post by MatthewWild on 2008-04-28
> **Scottworld said:**
> Define the shell network proxy settings before the upgrade.
this allows the do-release-upgrade script, to proxy to the outside world.
 
 
sudo -s **Become root (be careful)**
 
export http_proxy=http://user:password@my.proxy.server:port/
export ftp_proxy=http://user:password@my.proxy.server:port/
 
**Then run the standard server upgrade**
 
apt-get install update-manager-core
do-release-upgrade

ps: This will also allow access for other commands to proxy outside...
eg: 
wget [http://a.domain.com/file/to/download](http://a.domain.com/file/to/download)

Thanks Scottworld. This had me defeated for a while. It's a pity there's no documentation for do-release-upgrade.

Is there any way of setting the proxy value system wide? This is configured on all our SuSE servers and works well for avoiding having to do this for all possible network dependent applications.

Cheers

Matthew

---

