---
title: "Update Manager no longer works post upgrade to lucid"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by alas-poor-yorick on 2010-05-28
When I run update manager, it gives me an error message saying:
```
Not all updates can be installed
Run a partial upgrade, to install as many updates as possible.
This can be caused by:
* A previous update which didn't complete
* Problems with some of the installed software
* Unofficial software packages not provided by Ubuntu
* Normal changes of a pre-release version of Ubuntu
```

if I click partial upgrade, it looks like it did during the upgrade, then says:
```
Your system is up-to-date

There are no upgrades available for your system. The upgrade will now be canceled.
```

if I click close from the first "not all updates can be installed" dialog, it says:
```
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
```

running the suggested line gives the following output:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

in Synaptic, fixing broken packages does nothing. Mark All Updates > Apply seems to work, but I'd still like to figure out why Update Manager does not?

Thanks in advance. I've looked at other threads with people having the same problem, but none of those suggestions worked.

---

### Post by alas-poor-yorick on 2010-05-29
Bump? Anyone having the same problem?

---

### Post by napzilla on 2010-05-31
Yes, I'm encountering the same issue. According to Apt, the packages that need to be removed are as follows:
```

  linux-restricted-modules-2.6.22-14-generic
  linux-restricted-modules-2.6.24-23-generic
  linux-restricted-modules-2.6.27-14-generic
  linux-restricted-modules-2.6.28-17-generic

```

I'm going to download an ISO of 10.04, back up /home, and then try letting Apt do what it wants to do. If I survive, I'll let you know how it goes.

---

### Post by Vined Adobo on 2010-05-31
> **alas-poor-yorick said:**
> Bump? Anyone having the same problem?

My problem is similar.  About 5 days ago, I started getting this output:

Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg)  Could not connect to archive.getdeb.net:80 (81.92.203.249). - connect (110: Connection timed out)
Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/i18n/Translation-en_US.bz2](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/i18n/Translation-en_US.bz2)  Unable to connect to archive.getdeb.net:http:
Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/binary-i386/Packages.gz](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/binary-i386/Packages.gz)  Unable to connect to archive.getdeb.net:http:
Some index files failed to download, they have been ignored, or old ones used instead.

I'm seeing some reports that getdeb.net is down.

Are there other ways to get updates?

Dave

---

### Post by conway.federico on 2010-05-31
> **Vined Adobo said:**
> My problem is similar.  About 5 days ago, I started getting this output:

Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg)  Could not connect to archive.getdeb.net:80 (81.92.203.249). - connect (110: Connection timed out)
Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/i18n/Translation-en_US.bz2](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/i18n/Translation-en_US.bz2)  Unable to connect to archive.getdeb.net:http:
Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/binary-i386/Packages.gz](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/binary-i386/Packages.gz)  Unable to connect to archive.getdeb.net:http:
Some index files failed to download, they have been ignored, or old ones used instead.

I'm seeing some reports that getdeb.net is down.

Are there other ways to get updates?

Dave

My problem as well! Anybody know what is up? I reloaded my Uberstudent distro and I need my lucid lynx update.

---

### Post by napzilla on 2010-06-01
Okay, here's what I did, and it *seems* to have resolved the issue.

First, I ran Apt's dist upgrade with the "fix" flag:
```

sudo apt-get -f dist-upgrade

```
Apt then uninstalled some older kernel modules and updated a whole bunch of held back packages.

Next, I updated my package list:
```

sudo apt-get update

```

Then, just to be sure everything checked out, I ran Apt's install procedure with the "fix" flag:
```

sudo apt-get -f install

```

This told me that there was nothing that needed to be fixed, but that I had a whole bunch of automatically installed packages that could be removed. So, I cleaned those up with "autoremove":
```

sudo apt-get autoremove

```

That was it. I still have one package that's being held back, but that's because I installed GRASS from a different repository, I think. So, go ahead and give that a shot, and see if it fixes Update Manager for you.

---

### Post by Vined Adobo on 2010-06-01
> **napzilla said:**
> Okay, here's what I did, and it *seems* to have resolved the issue.

First, I ran Apt's dist upgrade with the "fix" flag:
```

sudo apt-get -f dist-upgrade

```Apt then uninstalled some older kernel modules and updated a whole bunch of held back packages.

Next, I updated my package list:
```

sudo apt-get update

```Then, just to be sure everything checked out, I ran Apt's install procedure with the "fix" flag:
```

sudo apt-get -f install

```This told me that there was nothing that needed to be fixed, but that I had a whole bunch of automatically installed packages that could be removed. So, I cleaned those up with "autoremove":
```

sudo apt-get autoremove

```That was it. I still have one package that's being held back, but that's because I installed GRASS from a different repository, I think. So, go ahead and give that a shot, and see if it fixes Update Manager for you.

Output I get:
dave@FUSION:~$ sudo apt-get -f dist-upgrade
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dave@FUSION:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                         
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release.gpg                   
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/multiverse Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/multiverse Sources          
Err [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release.gpg                      
  Could not connect to archive.getdeb.net:80 (81.92.203.249). - connect (110: Connection timed out)
Err [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) lucid-getdeb/apps Translation-en_US
  Unable to connect to archive.getdeb.net:http:
Ign [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release
Ign [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/apps Packages
Ign [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/apps Packages
Err [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/apps Packages
  Unable to connect to archive.getdeb.net:http:
W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg)  Could not connect to archive.getdeb.net:80 (81.92.203.249). - connect (110: Connection timed out)

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/i18n/Translation-en_US.bz2](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/i18n/Translation-en_US.bz2)  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/binary-i386/Packages.gz](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/binary-i386/Packages.gz)  Unable to connect to archive.getdeb.net:http:

E: Some index files failed to download, they have been ignored, or old ones used instead.
dave@FUSION:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dave@FUSION:~$ 
dave@FUSION:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dave@FUSION:~$ 

Didn't install grass at all

Nothing changed.  Any ideas?

Dave

---

### Post by Vined Adobo on 2010-06-10
> **Vined Adobo said:**
> My problem is similar.  About 5 days ago, I started getting this output:

Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg)  Could not connect to archive.getdeb.net:80 (81.92.203.249). - connect (110: Connection timed out)
Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/i18n/Translation-en_US.bz2](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/i18n/Translation-en_US.bz2)  Unable to connect to archive.getdeb.net:http:
Failed to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/binary-i386/Packages.gz](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/apps/binary-i386/Packages.gz)  Unable to connect to archive.getdeb.net:http:
Some index files failed to download, they have been ignored, or old ones used instead.

I'm seeing some reports that getdeb.net is down.

Are there other ways to get updates?

Dave


UPDATE:
Link seems to finally be working as I no longer get failure to fetch [http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/lucid-getdeb/Release.gpg) message.  I assume it's been fixed.  Also, I got an Adobe update today (which I think was on archive.getdeb.net.

Dave

---

